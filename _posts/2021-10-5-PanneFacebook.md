---
layout: post
title: Comprendre comment Facebook a disparu d Internet
comments: true
---
![_config.yml]({{ site.baseurl }}/images/etworks.png)
### Lorsqu'elles sont combinées, les « entreprises Facebook » en savent énormément sur vous.
"Facebook ne peut pas être en panne, n'est-ce pas ?", nous le pensions, pour une seconde.

Hier à 17h51 UTC+2, tout le monde n arrivait pas à acceder à tous les services affiliés à Facebook notamment Whatsapp, Messenger and Instagram. Ces applications étaient, en fait, tous en panne. 
Leurs noms DNS ont cessé de se résoudre et leurs adresses IP d'infrastructure étaient inaccessibles. C'était comme si quelqu'un avait "tiré les câbles" de leurs centres de données d'un seul coup et les avait déconnectés d'Internet.

Comment est-ce possible ?

## Mise à jour de Facebook
Facebook a maintenant publié [un article de blog](https://engineering.fb.com/2021/10/04/networking-traffic/outage/) donnant quelques détails sur ce qui s'est passé en interne. 
En externe, les entreprises telles ques Cloudfare ont vu les problèmes BGP et DNS décrits dans cet article, mais le problème a en fait commencé par un changement de configuration qui a affecté l'ensemble du backbone interne.
Cela s'est répercuté sur la disparition de Facebook et d'autres propriétés et le personnel interne à Facebook avait du mal à rétablir le service.

## Passons maintenant à ce qui a été vu de l'extérieur.

Rencontrez BGP . BGP signifie Border Gateway Protocol. C'est un mécanisme permettant d'échanger des informations de routage entre des systèmes autonomes (AS) sur Internet. Les gros routeurs qui font fonctionner Internet ont d'énormes listes constamment mises à jour des routes possibles qui peuvent être utilisées pour livrer chaque paquet réseau à leurs destinations finales.
 Sans BGP, les routeurs Internet ne sauraient pas quoi faire et Internet ne fonctionnerait pas.

Internet est littéralement un réseau de réseaux, et il est lié par BGP. BGP permet à un réseau (par exemple Facebook) d'annoncer sa présence à d'autres réseaux qui forment Internet. 
Hier soir, Facebook ne faisait pas de publicité pour sa présence, les Fournisseur d Accès à Internet (FAI) et autres réseaux ne pouvaient pas trouver le réseau de Facebook 
et il était donc indisponible.

Les réseaux individuels ont chacun un ASN : un numéro de système autonome. Un système autonome (AS) est un réseau individuel 
avec une politique de routage interne unifiée. Un AS peut générer des préfixes (disons qu'il contrôle un groupe d'adresses IP), 
ainsi que des préfixes de transit (disons qu'il sait comment atteindre des groupes spécifiques d'adresses IP).

L'ASN de Airtel DRCongo par exemple c'est AS37020 . Chaque ASN doit annoncer ses routes de préfixe vers Internet en utilisant BGP ; 
sinon, personne ne saura comment se connecter à ses services .

L'expert Stéphane Bortzmeyer couvre un excellent article sur le BGP [ici](https://www.bortzmeyer.org/7454.html) .
Dans ce schéma simplifié, vous pouvez voir six systèmes autonomes sur Internet et deux routes possibles qu'un paquet peut utiliser pour aller du début à la fin. AS1 → AS2 → AS3 étant le plus rapide, et AS1 → AS6 → AS5 → AS4 → AS3 étant le plus lent, mais cela peut être utilisé si le premier échoue.
![_config.yml]({{ site.baseurl }}/images/ASNsCloudfare.png)


À 17h58 UTC+2, il a été remarqué que Facebook avait cessé d'annoncer les routes vers leurs préfixes DNS. Cela signifiait qu'au moins les serveurs DNS de Facebook n'étaient pas disponibles. 
À cause de cela, le résolveur DNS 1.1.1.1 de Cloudflare ne pouvait plus répondre aux requêtes demandant l'adresse IP de facebook.com ou instagram.com.


            routes-vues> afficher l'ip bgp 185.89.218.0/23
            % Réseau non dans le tableau
            routes-vues>

            route-views> afficher l'ip bgp 129.134.30.0/23
            % Réseau non dans le tableau
            routes-vues>


Pendant ce temps, d'autres adresses IP Facebook restaient routées mais n'étaient pas particulièrement utiles car sans DNS, Facebook et les services associés étaient effectivement indisponibles :


            route-views> afficher l'ip bgp 129.134.30.0
            Entrée de table de routage BGP pour 129.134.0.0/17, version 1025798334
            Chemins : (24 disponibles, meilleur n°14, table par défaut)
            Non annoncé à aucun pair
            Rafraîchir l'époque 2
            3303 6453 32934
            217.192.89.50 à 217.192.89.50 (138.187.128.158)
            Origine IGP, localpref 100, valide, externe
            Communauté : 3303 : 1004 3303 : 1006 3303 : 3075 6453 : 3000 6453 : 3400 6453 : 3402
            chemin 7FE1408ED9C8 État RPKI introuvable
            rx pathid : 0, tx pathid : 0
            Rafraîchir l'époque 1
            routes-vues> 

Un message BGP UPDATE informe un routeur de toute modification que vous avez apportée à une annonce de préfixe ou retire entièrement le préfixe. Comme anoncé dans ce [blog de Cloudfare](https://blog.cloudflare.com/october-2021-facebook-outage/), ils ont clairement vue le nombre de mises à jour reçues de Facebook lors de la vérification de leur base de données BGP de séries chronologiques.
 Pourtant Facebook n'apporte pas beaucoup de changements à son réseau minute par minute.

Mais vers 17h40 UTC+2, un pic de changements de routage de Facebook a été observé. C'est alors que les ennuis ont commencé.

Avec ces retraits, Facebook et ses sites se sont effectivement déconnectés d'Internet.

## Le DNS est affecté
En conséquence directe de cela, les résolveurs DNS du monde entier ont cessé de résoudre leurs noms de domaine.

            ➜ ~ dig @1.1.1.1 facebook.com
            ;; ->>HEADER<<- code opération : QUERY, statut : SERVFAIL, id : 31322
            ;facebook.com. DANS UN
            ➜ ~ dig @ 1.1.1.1 whatsapp.com
            ;; ->>HEADER<<- code opération : QUERY, statut : SERVFAIL, id : 31322
            ;whatsapp.com. DANS UN
            ➜ ~ dig @8.8.8.8 facebook.com
            ;; ->>HEADER<<- code opération : QUERY, statut : SERVFAIL, id : 31322
            ;facebook.com. DANS UN
            ➜ ~ dig @ 8.8.8.8 whatsapp.com
            ;; ->>HEADER<<- code opération : QUERY, statut : SERVFAIL, id : 31322
            ;whatsapp.com. DANS UN


Cela se produit parce que le DNS, comme de nombreux autres systèmes sur Internet, possède également son mécanisme de routage.
 Lorsque quelqu'un tape l'URL https://facebook.com dans le navigateur, le résolveur DNS, responsable de la traduction des noms de domaine en adresses IP réelles auxquelles se connecter, 
 vérifie d'abord s'il a quelque chose dans son cache et l'utilise. 
 Sinon, il essaie de récupérer la réponse des serveurs de noms de domaine, généralement hébergés par l'entité qui en est propriétaire.

Si les serveurs de noms sont inaccessibles ou ne répondent pas pour une autre raison, une erreur "SERVFAIL" est renvoyée et le navigateur envoie une erreur à l'utilisateur.

Encore une fois, une video interessante sur le fonctionnement DNS est disponible [ici](https://youtu.be/QHVK666TFUI).

En raison de l'arrêt de Facebook d'annoncer leurs routes de préfixe DNS via BGP, tous les résolveurs DNS du monde n'avaient aucun moyen de se connecter à leurs serveurs de noms. 
Par conséquent, 1.1.1.1, 8.8.8.8 et d'autres principaux résolveurs DNS publics ont commencé à émettre (et à mettre en cache) des réponses SERVFAIL.
Mais ce n'est pas tout. Maintenant, le comportement humain et la logique d'application entrent en jeu et provoquent un autre effet exponentiel. Un tsunami de trafic DNS supplémentaire s'ensuit.

Cela s'est produit en partie parce que les applications n'accepteront pas une erreur pour une réponse et commenceront à réessayer, parfois de manière agressive, et en partie parce que les utilisateurs finaux ne prendront pas non plus une erreur pour une réponse et commenceront à recharger les pages, ou à tuer et relancer leur applications, parfois aussi agressivement.

Alors, parce que Facebook et leurs sites sont si grands, des résolveurs DNS dans le monde entier qui traitent 30-40 fois plus de requêtes que d'habitude et peuvent causer des problèmes de latence et de délai d'attente à d'autres plates-formes.

## l'Impact sur d'autres services
Les gens recherchent des alternatives et veulent en savoir plus ou discuter de ce qui se passe.
 Lorsque Facebook est devenu inaccessible, une augmentation des requêtes DNS vers Twitter a surgi, Signal et d'autres plateformes de messagerie et de médias sociaux.

## L'Internet
Les événements d'aujourd'hui nous rappellent en douceur qu'Internet est un système très complexe et interdépendant de millions de systèmes et de protocoles fonctionnant ensemble. 
Cette confiance, cette normalisation et cette coopération entre les entités sont au cœur de son fonctionnement pour près de cinq milliards d'utilisateurs actifs dans le monde.































Merci pour votre temps!!!
N'hesitez pas d'Aimer , commenter et partager cet article avec vos proches.

Cet article est écrit par : [Dieudonné I. Munganga](https://monsieurpapa.github.io/about/)