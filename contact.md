---
layout: page
title: Contact
permalink: /contact/
---

Get in touch for collaboration opportunities, consulting inquiries, or just to say hello!

<div class="contact-container">
  <div class="contact-info">
    <h2>Let's Connect</h2>
    <p>I'm always open to discussing new projects, creative ideas, or opportunities to be part of your visions.</p>
    
    <div class="contact-methods">
      <div class="contact-item">
        <strong>📧 Email</strong>
        <a href="mailto:dieudonneishara@gmail.com">dieudonneishara@gmail.com</a>
      </div>
      <div class="contact-item">
        <strong>📱 Phone</strong>
        <a href="tel:+27713363312">+27 713 363 312</a>
      </div>
      <div class="contact-item">
        <strong>📍 Location</strong>
        <span>Cape Town, South Africa</span>
      </div>
      <div class="contact-item">
        <strong>🔗 Social</strong>
        <div class="social-links">
          <a href="https://www.linkedin.com/in/dieudonn%C3%A9-munganga-b01111b7/" target="_blank" rel="noopener">LinkedIn</a>
          <a href="https://github.com/monsieurpapa" target="_blank" rel="noopener">GitHub</a>
          <a href="https://twitter.com/dieudonneishara" target="_blank" rel="noopener">Twitter</a>
        </div>
      </div>
    </div>
  </div>

  <div class="contact-form-container">
    <h2>Send a Message</h2>
    <form class="contact-form" id="contact-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
      <input type="hidden" name="_subject" value="New Contact Form Submission from {{site.name}}">
      <input type="hidden" name="_next" value="{{site.url}}{{site.baseurl}}/contact/thanks">
      <div class="form-group">
        <label for="name">Name *</label>
        <input type="text" id="name" name="name" required>
      </div>
      <div class="form-group">
        <label for="email">Email *</label>
        <input type="email" id="email" name="email" required>
      </div>
      <div class="form-group">
        <label for="subject">Subject</label>
        <input type="text" id="subject" name="subject">
      </div>
      <div class="form-group">
        <label for="message">Message *</label>
        <textarea id="message" name="message" rows="6" required></textarea>
      </div>
      <button type="submit" class="submit-btn">Send Message</button>
    </form>
    <p class="form-note">Or reach out directly via email: <a href="mailto:dieudonneishara@gmail.com">dieudonneishara@gmail.com</a></p>
  </div>
</div>

<style>
.contact-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-top: 30px;
}

.contact-info h2, .contact-form-container h2 {
  margin-top: 0;
  color: var(--blue);
}

.contact-methods {
  margin-top: 30px;
}

.contact-item {
  margin-bottom: 25px;
  padding-bottom: 25px;
  border-bottom: 1px solid var(--border-color);
}

.contact-item:last-child {
  border-bottom: none;
}

.contact-item strong {
  display: block;
  margin-bottom: 8px;
  color: var(--black);
}

.contact-item a {
  color: var(--blue);
  text-decoration: none;
}

.contact-item a:hover {
  text-decoration: underline;
}

.social-links {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
}

.social-links a {
  padding: 6px 12px;
  background: var(--lightGray);
  border-radius: 6px;
  transition: background 0.2s;
}

.social-links a:hover {
  background: var(--blue);
  color: white;
}

.contact-form {
  margin-top: 30px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
  color: var(--darkGray);
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid var(--border-color);
  border-radius: 6px;
  font-size: 1rem;
  font-family: inherit;
  background: var(--white);
  color: var(--black);
  transition: border-color 0.2s;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--blue);
}

.submit-btn {
  background: var(--blue);
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

.submit-btn:hover {
  background: var(--hover-blue);
}

.form-note {
  margin-top: 20px;
  font-size: 0.9rem;
  color: var(--gray);
}

@media (max-width: 768px) {
  .contact-container {
    grid-template-columns: 1fr;
  }
}
</style>

<script>
  document.getElementById('contact-form').addEventListener('submit', function(e) {
    // Form will submit to Formspree if configured
    // Otherwise, you can add custom handling here
  });
</script>

