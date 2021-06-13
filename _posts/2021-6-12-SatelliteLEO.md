---
layout: post
title: Les satellites LEO, Les bases
comments: true
---

![_config.yml]({{ site.baseurl }}/images/Leo.jpeg)

_Cet article est inspiré par Ulrich Speidel d'[APNIC](https://blog.apnic.net) dans ses articles sur les satellites en orbite terrestre basse (LEO). Nous avons trouvé important de vous en parler vu la potentialité de ce sujet sur l'échelle internationnale._

Si vous attendiez une connectivité Internet décente dans votre coin du monde, 2021 promet d'être une année passionnante. Au cours des dernières années, la société Starlink de SpaceX a mis en orbite environ 1 500 satellites de communication LEO. Ils ont également récemment commencé des tests bêta avec des clients finaux en Amérique du Nord, en Australie, en Nouvelle-Zélande et dans quelques économies européennes, alors qu'ils prévoient de mettre en place environ 10 000 autres satellites à terme. On dit que les opérations commerciales n'auront lieu que dans quelques semaines ou quelques mois. Leur concurrent le plus proche, OneWeb, se remet d'un hoquet financier mais est également en bonne voie vers une constellation de satellites exploitable. Quelques autres concurrents attendent leur heure pour l'instant, mais sont soutenus par des organisations dotées d'une puissance financière importante, telles qu'Amazon, il est donc probable qu'ils apparaîtront bientôt également sur scène.

## Qu'est-ce qui rend les satellites LEO intéressants ?

Pourquoi les systèmes LEO sont-ils passionnants pour les internautes ? Voici quelques raisons:

1. **_La Couverture_** : Les satellites géostationnaires conventionnels (GEO) sont situés au-dessus de l'équateur sur une longitude fixe. Les satellites GEO sont coûteux à construire, à déployer et à entretenir et ont tendance à se rassembler sur des longitudes où il y a beaucoup de clients avec des poches profondes. Cela favorise naturellement les Amériques, l'Europe et l'Afrique, et dans une moindre mesure l'Asie. Le Pacifique a tendance à être un peu une réflexion après coup, ce qui signifie que les nouveaux joueurs y sont toujours les bienvenus. Les satellites O3b mPower en orbite terrestre moyenne (MEO) de SES ont changé la donne dans les régions tropicales et subtropicales, mais ne couvrent pas les régions polaires. Les LEO, de par la nature de leur orbite, couvrent tous les degrés de longitude et, selon leur inclinaison orbitale (inclinaison par rapport à l'équateur), peuvent également couvrir toutes les latitudes, jusqu'aux pôles. Tout cela semble très intéressant pour les clients du Pacifique.

2. **_La Capacité du système_** : depuis l'émergence de la communication cellulaire, les ingénieurs ont appris qu'il est plus intelligent de rapprocher les émetteurs et les récepteurs dans des « cellules » que d'avoir un seul émetteur central puissant couvrant tout à travers le pays. C'est parce que l'on peut réutiliser des fréquences avec des transmissions de faible puissance à plusieurs endroits, ce qui réduit considérablement la pression sur la ressource rare du spectre radio. Les LEO sont l'équivalent satellite des stations de base des téléphones portables ; ils ne "voient" qu'un petit cercle à la surface de la Terre - généralement de quelques milliers de kilomètres de diamètre - tandis que leurs cousins ​​GEO entendent et voient près de la moitié de la planète depuis leur station élevée. De plus, être plus proche de la personne à laquelle vous transmettez ou recevez signifie que vous pouvez le faire avec moins de puissance et une antenne plus petite. Encore une fois, c'est quelque chose que nous savons de nos téléphones portables - les batteries durent plus longtemps maintenant (en ville), ne pèsent pas autant qu'une brique, et les antennes sont si petites qu'elles se cachent à l'intérieur du boîtier. Un satellite LEO à 500 km de frais généraux a un avantage d'environ 5 000:1 sur un satellite GEO de près de 36 000 km de frais généraux, en termes de puissance, et d'environ 250:1 par rapport à un satellite MEO. Adieu grosse parabole et gros satellite avec de grands panneaux solaires.

3. **_La Latence_** : Un signal circulant via un satellite GEO a un temps d'aller-retour minimum entre les stations au sol d'environ une demi-seconde. C'est extrêmement gênant pour la téléphonie, mais c'est aussi une douleur pour le protocole de transport de base d'Internet, TCP, qui s'appuie sur les commentaires de l'extrémité afin de « faire confiance » au canal avec plus de données. Si ce retour tarde à venir - et via un satellite GEO, c'est sûr - le TCP a du mal à obtenir son taux de transmission à travers le goulot d'étranglement de la liaison satellite. C'est pourquoi ceux qui ont la chance de vivre sur une île accédant à un satellite GEO savent que le transfert de grandes quantités de données peut parfois être plus rapide en avion ou en bateau. Les MEO d'O3b font un peu mieux ici, mais ils constituent toujours un goulot d'étranglement pour TCP. En principe, les LEO peuvent offrir une faible latence et une plus grande bande passante, et présentent donc moins de goulot d'étranglement pour TCP.

4. **_Le Coût_** : à ce jour, la capacité GEO est accompagnée d'un prix de plusieurs centaines de dollars américains par mégabit par seconde de bande passante par mois, une capacité qui s'accompagnait de toutes les mises en garde de latence ci-dessus. La tarification LEO est encore un peu floue, mais la tarification bêta de Starlink indique quelque chose de comparable à une connexion fibre domestique (si elle se situe du côté supérieur de cette échelle) et avec des performances revendiquées dans le même stade. De plus, le kit d'entrée est actuellement de 499 USD en version bêta. C'est peut-être moins cher que ce que coûtera la version commerciale, mais c'est encore loin des milliers à des dizaines de milliers que le matériel au sol de liaison par satellite GEO pour une capacité bien inférieure peut coûter.

## Les connus, les inconnus connus et peut-être des inconnus inconnus

Cela semble certainement très prometteur, et il est à juste titre approuvé comme un changeur de jeu potentiel. Mais comme les LEO suscitent l'espoir des gens quant à ce que cela pourrait faire pour eux, ce n'est sans doute pas si simple non plus. La foule actuelle de LEO n'a pas été trop ouverte aux détails techniques, et c'est là que les diables ont tendance à se cacher. Ce qui est devenu de notoriété publique a été révélé presque exclusivement à la suite de dépôts réglementaires publics, et a souvent changé par la suite à mesure que les plans et les circonstances des fournisseurs de LEO ont changé. La plupart des publications savantes dans le domaine doivent recourir à la spéculation quant à la configuration et à la stratégie plutôt que de pouvoir se référer à des normes ouvertes, des publications des fournisseurs et des brevets publiés qui permettent une évaluation de l'état de l'art.

Cela dit, il y a des choses que nous savons, et des calculs de fond que nous pouvons effectuer, pour déterminer approximativement où pourraient se trouver les limites des réseaux LEO actuels et proposés.
![_config.yml]({{ site.baseurl }}/images/leotwo.png)

## Quelles opportunités pour l'Afrique?
Pour apporter un éclairage sur cette question, nous noterons brièvement des réflexions applicables à un modèle économique simplifié intégrant les domaines de la **Technologie : Marché et Livraison.**

* **La Technologie** : La technologie détient certainement un grand potentiel pour l'Afrique et répondra à diverses demandes de connectivité. La technologie satellitaire s'est avérée être une solution très fiable et les dernières innovations dans le développement des constellations LEO dépasseront les contraintes actuelles de coût et de latence.

Bien que la technologie soit l'élément d'innovation le plus impressionnant, ce n'est probablement pas le plus difficile à réaliser et Kuiper sera démontré sur les marchés nord-américains. Pour l'Afrique, l'exigence technologique sera donc une option donnée et éprouvée.

* **Le Marché** :
La demande du marché est une discussion un peu plus complexe et se rapporte davantage aux métriques détaillées du marché. Il est quelque peu simpliste de citer des statistiques générales sur la « population non connectée » en Afrique et de supposer ensuite qu'il s'agit du marché adressable. La faisabilité du marché réside dans les détails relatifs au type de service, à l'abordabilité du service, au positionnement concurrentiel, etc.

* **La Livraison**:
La livraison est probablement l'exigence la plus critique et aussi la plus difficile. La livraison comprend les modèles commerciaux des fournisseurs de services, les différentes exigences réglementaires locales en matière de télécommunications, les modèles opérationnels requis pour un tel service technologique spécialisé, la livraison, la mise en œuvre et le support de 100 000 points de terminaison, etc.

À un prix utilisateur final de 100 $, le chiffre d'affaires annuel sera de 200 millions USD. En mettant cela en contexte, cela représentera environ 2% du chiffre d'affaires 2020 des sociétés comme Vodacom, MTN et autres. Ainsi, pour les grandes entreprises de télécommunications, cela ne sera probablement pas considéré comme suffisamment attrayant pour investir les ressources requises pour un produit de service par satellite aussi spécialisé.

### Une issue possible

Compte tenu des avantages techniques attendus en termes de vitesse et de performances de latence de LEO par OneWeb, et des avantages de la connexion de tous les utilisateurs « hors réseau » ainsi que de la fourniture d'un service de fibre alternatif très fiable et facile à déployer, cela constitue un argument convaincant pour OneWeb que l'Afrique n'ignore pas.

On peut donc s'attendre à ce qu'une nouvelle génération de fournisseurs de services par satellite hautement spécialisés et de niche cible cette opportunité. Pour des fournisseurs tels que le groupe Q-KON, qui est déjà en tête de ce secteur de marché avec les produits actuels de services par satellite HTS, il s'agira d'une prochaine étape logique pour répondre à la demande toujours croissante de services haut débit fiables en Afrique.

Merci pour votre temps!!!

Cet article est écrit par : [Dieudonné I. Munganga](https://dieudonnemunganga.pb.online/)


## REFERENCES

* G. E. Corazza et F. Vatalaro, « Un modèle statistique pour les canaux satellites mobiles terrestres
et son application aux systèmes d'orbite non géostationnaires », IEEE Trans. Véh. Technol., vol.
43, non. 3, pp.738-742, août 1994.
* M. Sforza et S. Buonomo, « Caractérisation du canal de propagation pour
systèmes LMS non géostationnaires en bandes L et S : données expérimentales à bande étroite et
modélisation de canaux, "Proc. XVII NAPEX Conf., Pasadena, CA, 14-15 juin 1993.
* Plan australien du spectre des radiofréquences comprenant des informations générales - janvier
1997, Agence de gestion du spectre, janvier 1997.
* Avant-projet de nouvelle Recommandation UIT-R M.[8D/XP], Pièce jointe 4 de la
Rapport de la sixième réunion du Groupe de travail UIT-R 8D, Genève, 29 octobre - 8
novembre 1996.
* Stations de radiodiffusion et de télévision 1996, Australian Broadcasting
Autorité, Canberra, janvier 1996.
* Paramètres et méthodes de planification technique pour la radiodiffusion terrestre, station
Direction de la planification, ministère des Transports et des Communications, Canberra, juin
1992.
* H. Fu, G. Bi et K. Arichandran, « _Performance of multi-beam CDMA-based LEO
systèmes satellitaires dans un canal Rice-lognormal_ », IEEE Commun. Lett., vol. 3, non. 4, p.
88-90, avril 1999.
* G. Maral et M. Bousquet, Satellite communications systems, 3e éd., John Wiley &
Fils, 1999.
* S.-Y. Li et C. H. Liu, _« Un modèle analytique pour prédire la densité de probabilité
fonction des angles d'élévation pour les systèmes satellites LEO_ »_, IEEE Commun. Lett., vol. 6, non.
4, p. 138-140, avril 2002.
* ‘Simulation de systèmes de communication’ Par Michel C. Jeruchim, Philip Balaban, K.
Sam Shanmugan-Chapitre 9 (545-548)
