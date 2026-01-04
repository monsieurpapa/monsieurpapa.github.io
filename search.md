---
layout: page
title: Search
permalink: /search/
---

<div class="search-container">
  <input type="text" id="search-input" placeholder="Search posts, projects, and content..." class="search-box" autofocus>
  <div id="search-results" class="search-results"></div>
</div>

<script>
  (function() {
    const searchInput = document.getElementById('search-input');
    const searchResults = document.getElementById('search-results');
    
    // Fetch all posts data
    const posts = [
      {% for post in site.posts %}
      {
        title: {{ post.title | jsonify }},
        url: {{ post.url | jsonify }},
        excerpt: {{ post.excerpt | default: post.content | strip_html | truncatewords: 30 | jsonify }},
        date: {{ post.date | date: "%B %e, %Y" | jsonify }},
        categories: {{ post.categories | jsonify }}
      }{% unless forloop.last %},{% endunless %}
      {% endfor %}
    ];

    function performSearch(query) {
      if (query.length < 2) {
        searchResults.innerHTML = '';
        return;
      }

      const queryLower = query.toLowerCase();
      const results = posts.filter(post => {
        return post.title.toLowerCase().includes(queryLower) ||
               post.excerpt.toLowerCase().includes(queryLower) ||
               (post.categories && post.categories.some(cat => cat.toLowerCase().includes(queryLower)));
      });

      displayResults(results, query);
    }

    function displayResults(results, query) {
      if (results.length === 0) {
        searchResults.innerHTML = '<p class="no-results">No results found for "' + query + '"</p>';
        return;
      }

      let html = '<div class="results-count">Found ' + results.length + ' result' + (results.length !== 1 ? 's' : '') + '</div>';
      html += '<ul class="results-list">';
      
      results.forEach(post => {
        html += `
          <li class="result-item">
            <h3><a href="{{site.baseurl}}${post.url}">${highlightText(post.title, query)}</a></h3>
            <p class="result-excerpt">${highlightText(post.excerpt, query)}</p>
            <div class="result-meta">
              <span class="result-date">${post.date}</span>
              ${post.categories && post.categories.length > 0 ? 
                '<span class="result-categories">' + 
                post.categories.map(cat => `<span class="category-tag">${cat}</span>`).join('') + 
                '</span>' : ''}
            </div>
          </li>
        `;
      });
      
      html += '</ul>';
      searchResults.innerHTML = html;
    }

    function highlightText(text, query) {
      const regex = new RegExp(`(${query})`, 'gi');
      return text.replace(regex, '<mark>$1</mark>');
    }

    // Debounce search
    let searchTimeout;
    searchInput.addEventListener('input', function() {
      clearTimeout(searchTimeout);
      searchTimeout = setTimeout(() => {
        performSearch(this.value);
      }, 300);
    });

    // Handle URL hash for search
    if (window.location.hash) {
      const hash = decodeURIComponent(window.location.hash.substring(1));
      searchInput.value = hash;
      performSearch(hash);
    }
  })();
</script>

<style>
.search-container {
  max-width: 800px;
  margin: 40px auto;
}

.search-box {
  width: 100%;
  padding: 15px 20px;
  font-size: 1.1rem;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  background: var(--white);
  color: var(--black);
  transition: border-color 0.2s ease;
}

.search-box:focus {
  outline: none;
  border-color: var(--blue);
}

.search-results {
  margin-top: 30px;
}

.results-count {
  color: var(--gray);
  margin-bottom: 20px;
  font-weight: 600;
}

.results-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.result-item {
  padding: 25px;
  margin-bottom: 20px;
  background: var(--lightGray);
  border-radius: 8px;
  border: 1px solid var(--border-color);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.result-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.result-item h3 {
  margin: 0 0 10px 0;
  font-size: 1.3rem;
}

.result-item h3 a {
  color: var(--black);
  text-decoration: none;
}

.result-item h3 a:hover {
  color: var(--blue);
}

.result-excerpt {
  color: var(--gray);
  margin: 10px 0;
  line-height: 1.6;
}

.result-meta {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-top: 15px;
  font-size: 0.9rem;
}

.result-date {
  color: var(--gray);
}

.result-categories {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.category-tag {
  background: var(--white);
  color: var(--blue);
  padding: 3px 10px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 600;
  border: 1px solid var(--blue);
}

mark {
  background: var(--blue);
  color: white;
  padding: 2px 4px;
  border-radius: 3px;
}

.no-results {
  text-align: center;
  padding: 40px;
  color: var(--gray);
  font-size: 1.1rem;
}
</style>

