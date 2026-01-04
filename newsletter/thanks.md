---
layout: page
title: Thank You
permalink: /newsletter/thanks/
---

<div class="thank-you-page">
  <h1>🎉 Thank You for Subscribing!</h1>
  <p>You've successfully subscribed to my newsletter. You'll receive updates about new posts, projects, and insights.</p>
  <div class="thank-you-actions">
    <a href="{{site.baseurl}}/" class="btn-primary">Back to Blog</a>
    <a href="{{site.baseurl}}/archive" class="btn-secondary">Browse Archive</a>
  </div>
</div>

<style>
.thank-you-page {
  max-width: 600px;
  margin: 80px auto;
  text-align: center;
  padding: 40px;
}

.thank-you-page h1 {
  color: var(--blue);
  margin-bottom: 20px;
}

.thank-you-actions {
  display: flex;
  gap: 15px;
  justify-content: center;
  margin-top: 40px;
  flex-wrap: wrap;
}

.btn-primary, .btn-secondary {
  padding: 12px 30px;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.2s;
}

.btn-primary {
  background: var(--blue);
  color: white;
}

.btn-primary:hover {
  background: var(--hover-blue);
  color: white;
}

.btn-secondary {
  background: var(--lightGray);
  color: var(--black);
  border: 1px solid var(--border-color);
}

.btn-secondary:hover {
  background: var(--white);
  border-color: var(--blue);
  color: var(--blue);
}
</style>

