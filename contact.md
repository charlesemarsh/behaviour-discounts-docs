---
layout: default
title: Contact
nav_order: 5
---

# Contact

Use this form to reach the Behaviour Discounts team. The example below works on GitHub Pages by posting to a form service (e.g., Formspree); swap in your own endpoint.

## Form

Replace `https://formspree.io/f/your-form-id` with the endpoint from your form provider. Formspree is a common choice for static sites.

<form action="https://formspree.io/f/your-form-id" method="POST">
  <div class="fs-row">
    <label for="name">Name</label>
    <input id="name" name="name" type="text" required>
  </div>
  <div class="fs-row">
    <label for="email">Email</label>
    <input id="email" name="_replyto" type="email" required>
  </div>
  <div class="fs-row">
    <label for="message">How can we help?</label>
    <textarea id="message" name="message" rows="5" required></textarea>
  </div>
  <input type="hidden" name="_subject" value="Behaviour Discounts contact">
  <button type="submit">Send</button>
</form>

> Tip: Formspree supports a simple confirmation page by adding `?redirect=https://yourdomain.com/thanks` to the action URL or by setting it in their dashboard.

## Setup notes

1. Create or log in to your form provider (e.g., Formspree) and make a new form.  
2. Copy the form endpoint it provides and replace the `action` URL above.  
3. Update the `_subject` value if you want a different email subject line.  
4. Submit a test message from the published site to confirm delivery.  

Prefer email? Use `mailto:hello@example.com` or your shared support inbox.
