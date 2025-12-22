---
layout: default
title: Contact
nav_order: 5
---

# Contact

Use this form to reach the Behaviour Discounts team. The example below works on GitHub Pages by posting to a form service (e.g., Formspree); swap in your own endpoint.

<form action="https://formspree.io/f/xykgnwap" method="POST">
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
