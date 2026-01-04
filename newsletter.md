---
layout: page
title: Newsletter
permalink: /newsletter/
---

Stay updated with the latest posts, projects, and insights on software engineering, data science, and ICT4D.

<div class="newsletter-page">
  <div class="newsletter-intro">
    <h2>📬 Subscribe to My Newsletter</h2>
    <p>Get notified about:</p>
    <ul class="newsletter-benefits">
      <li>✨ New blog posts on software engineering and data science</li>
      <li>🚀 Project updates and case studies</li>
      <li>💡 Technical insights and best practices</li>
      <li>🌍 ICT4D research findings and impact stories</li>
    </ul>
    <p class="newsletter-privacy">🔒 Your email will never be shared. Unsubscribe anytime with one click.</p>
  </div>

  <div class="newsletter-form-wrapper">
    <h3>Subscribe Now</h3>
    
    <!-- Option 1: Formspree (Simple, Free) -->
    <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST" class="newsletter-form-single">
      <input type="hidden" name="_subject" value="Newsletter Subscription">
      <input type="hidden" name="_next" value="{{site.url}}{{site.baseurl}}/newsletter/thanks">
      <div class="form-group">
        <input type="email" name="email" placeholder="Enter your email address" required class="newsletter-email-input">
        <button type="submit" class="newsletter-submit-btn">Subscribe</button>
      </div>
      <p class="form-note">Powered by Formspree</p>
    </form>

    <!-- Option 2: Mailchimp (Advanced, recommended for larger lists) -->
    <!-- 
    <form action="YOUR_MAILCHIMP_FORM_ACTION" method="POST" target="_blank" class="newsletter-form-single">
      <div class="form-group">
        <input type="email" name="EMAIL" placeholder="Enter your email address" required class="newsletter-email-input">
        <button type="submit" class="newsletter-submit-btn">Subscribe</button>
      </div>
      <input type="hidden" name="b_YOUR_LIST_ID" value="">
      <p class="form-note">Powered by Mailchimp</p>
    </form>
    -->

    <!-- Option 3: ConvertKit (Great for creators) -->
    <!--
    <form action="https://app.convertkit.com/forms/YOUR_FORM_ID/subscriptions" method="POST" class="newsletter-form-single">
      <div class="form-group">
        <input type="email" name="email_address" placeholder="Enter your email address" required class="newsletter-email-input">
        <button type="submit" class="newsletter-submit-btn">Subscribe</button>
      </div>
      <p class="form-note">Powered by ConvertKit</p>
    </form>
    -->
  </div>

  <div class="newsletter-alternative">
    <h3>Alternative Ways to Stay Connected</h3>
    <div class="alternative-links">
      <a href="{{site.baseurl}}/feed.xml" class="alt-link">
        <strong>📡 RSS Feed</strong>
        <span>Subscribe via RSS reader</span>
      </a>
      <a href="https://twitter.com/{{site.footer-links.twitter}}" target="_blank" rel="noopener" class="alt-link">
        <strong>🐦 Twitter</strong>
        <span>Follow for quick updates</span>
      </a>
      <a href="https://www.linkedin.com/in/{{site.footer-links.linkedin}}" target="_blank" rel="noopener" class="alt-link">
        <strong>💼 LinkedIn</strong>
        <span>Connect professionally</span>
      </a>
    </div>
  </div>
</div>

<style>
.newsletter-page {
  max-width: 700px;
  margin: 40px auto;
}

.newsletter-intro {
  text-align: center;
  margin-bottom: 50px;
}

.newsletter-intro h2 {
  color: var(--blue);
  margin-bottom: 20px;
}

.newsletter-benefits {
  text-align: left;
  max-width: 500px;
  margin: 30px auto;
  list-style: none;
  padding: 0;
}

.newsletter-benefits li {
  padding: 12px 0;
  border-bottom: 1px solid var(--border-color);
  color: var(--darkGray);
}

.newsletter-benefits li:last-child {
  border-bottom: none;
}

.newsletter-privacy {
  margin-top: 30px;
  font-size: 0.9rem;
  color: var(--gray);
  font-style: italic;
}

.newsletter-form-wrapper {
  background: var(--lightGray);
  padding: 40px;
  border-radius: 12px;
  border: 1px solid var(--border-color);
  margin-bottom: 40px;
  text-align: center;
}

.newsletter-form-wrapper h3 {
  margin-top: 0;
  margin-bottom: 25px;
  color: var(--black);
}

.newsletter-form-single {
  max-width: 500px;
  margin: 0 auto;
}

.newsletter-form-single .form-group {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

.newsletter-email-input {
  flex: 1;
  padding: 14px 18px;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  font-size: 1rem;
  background: var(--white);
  color: var(--black);
  transition: border-color 0.2s;
}

.newsletter-email-input:focus {
  outline: none;
  border-color: var(--blue);
}

.newsletter-submit-btn {
  padding: 14px 30px;
  background: var(--blue);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  white-space: nowrap;
}

.newsletter-submit-btn:hover {
  background: var(--hover-blue);
}

.form-note {
  font-size: 0.85rem;
  color: var(--gray);
  margin: 10px 0 0 0;
}

.newsletter-alternative {
  text-align: center;
  padding: 30px;
  background: var(--lightGray);
  border-radius: 10px;
}

.newsletter-alternative h3 {
  margin-top: 0;
  margin-bottom: 25px;
}

.alternative-links {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}

.alt-link {
  display: flex;
  flex-direction: column;
  padding: 20px;
  background: var(--white);
  border-radius: 8px;
  border: 1px solid var(--border-color);
  text-decoration: none;
  transition: all 0.2s;
}

.alt-link:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  border-color: var(--blue);
}

.alt-link strong {
  color: var(--black);
  margin-bottom: 5px;
}

.alt-link span {
  color: var(--gray);
  font-size: 0.85rem;
}

@media (max-width: 640px) {
  .newsletter-form-single .form-group {
    flex-direction: column;
  }
  
  .newsletter-submit-btn {
    width: 100%;
  }
}
</style>

