---
layout: page
title: Message Sent
permalink: /contact/thanks/
---

<div class="thank-you-page">
  <h1>✅ Message Received!</h1>
  <p>Thank you for reaching out. I'll get back to you as soon as possible, usually within 24-48 hours.</p>
  <div class="thank-you-actions">
    <a href="{{site.baseurl}}/" class="btn-primary">Back to Home</a>
    <a href="{{site.baseurl}}/about" class="btn-secondary">Learn More About Me</a>
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

