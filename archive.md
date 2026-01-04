---
layout: page
title: Archive
permalink: /archive/
---

Browse all posts by date and category.

<div class="archive-container">
  <div class="archive-section">
    <h2>By Year</h2>
    {% assign postsByYear = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
    {% for year in postsByYear %}
    <div class="year-group">
      <h3>{{ year.name }}</h3>
      <ul class="archive-list">
        {% for post in year.items %}
        <li>
          <span class="archive-date">{{ post.date | date: "%b %e" }}</span>
          <a href="{{site.baseurl}}{{post.url}}">{{ post.title }}</a>
          {% if post.categories.size > 0 %}
          <span class="archive-categories">
            {% for category in post.categories %}
            <span class="category-badge">{{category}}</span>
            {% endfor %}
          </span>
          {% endif %}
        </li>
        {% endfor %}
      </ul>
    </div>
    {% endfor %}
  </div>

  <div class="archive-section">
    <h2>By Category</h2>
    {% assign categories = site.posts | map: 'categories' | uniq | sort %}
    {% for category in categories %}
    <div class="category-group">
      <h3 id="{{category|slugize}}">{{ category }}</h3>
      <ul class="archive-list">
        {% for post in site.posts %}
        {% if post.categories contains category %}
        <li>
          <span class="archive-date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{site.baseurl}}{{post.url}}">{{ post.title }}</a>
        </li>
        {% endif %}
        {% endfor %}
      </ul>
    </div>
    {% endfor %}
  </div>
</div>

<style>
.archive-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-top: 30px;
}

.archive-section h2 {
  margin-top: 0;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--blue);
}

.year-group, .category-group {
  margin-bottom: 30px;
}

.year-group h3, .category-group h3 {
  color: var(--blue);
  font-size: 1.3rem;
  margin-bottom: 15px;
}

.archive-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.archive-list li {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 10px 0;
  border-bottom: 1px solid var(--border-color);
}

.archive-date {
  font-size: 0.85rem;
  color: var(--gray);
  min-width: 80px;
  flex-shrink: 0;
}

.archive-list a {
  flex-grow: 1;
  color: var(--black);
  text-decoration: none;
}

.archive-list a:hover {
  color: var(--blue);
}

.archive-categories {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.category-badge {
  background: var(--lightGray);
  color: var(--gray);
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 600;
}

@media (max-width: 768px) {
  .archive-container {
    grid-template-columns: 1fr;
  }
}
</style>

