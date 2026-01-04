---
layout: page
title: Categories
permalink: /categories/
---

Browse posts by category.

<div class="categories-container">
  {% assign categories = site.posts | map: 'categories' | uniq | sort %}
  {% for category in categories %}
  <div class="category-section">
    <h2 id="{{category|slugize}}">{{ category }}</h2>
    <ul class="category-posts">
      {% for post in site.posts %}
      {% if post.categories contains category %}
      <li>
        <a href="{{site.baseurl}}{{post.url}}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%B %e, %Y" }}</span>
      </li>
      {% endif %}
      {% endfor %}
    </ul>
  </div>
  {% endfor %}
</div>

<style>
.categories-container {
  margin-top: 30px;
}

.category-section {
  margin-bottom: 50px;
  padding-bottom: 30px;
  border-bottom: 2px solid var(--border-color);
}

.category-section:last-child {
  border-bottom: none;
}

.category-section h2 {
  color: var(--blue);
  margin-bottom: 20px;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--blue);
  display: inline-block;
}

.category-posts {
  list-style: none;
  padding: 0;
  margin: 0;
}

.category-posts li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 0;
  border-bottom: 1px solid var(--border-color);
}

.category-posts li:last-child {
  border-bottom: none;
}

.category-posts a {
  color: var(--black);
  text-decoration: none;
  flex-grow: 1;
}

.category-posts a:hover {
  color: var(--blue);
}

.post-date {
  color: var(--gray);
  font-size: 0.9rem;
  margin-left: 20px;
}
</style>

