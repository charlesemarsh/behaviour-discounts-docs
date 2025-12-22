---
layout: default
title: Contact
nav_order: 5
---

# Contact

Use this form to reach the Behaviour Discounts team.

<div class="contact-card">
  <form class="contact-form" action="https://formspree.io/f/xykgnwap" method="POST">
    <div class="contact-row">
      <label for="name">Name</label>
      <input id="name" name="name" type="text" required>
    </div>
    <div class="contact-row">
      <label for="email">Email</label>
      <input id="email" name="_replyto" type="email" required>
    </div>
    <div class="contact-row">
      <label for="message">How can we help?</label>
      <textarea id="message" name="message" rows="5" required></textarea>
    </div>
    <input type="hidden" name="_subject" value="Behaviour Discounts contact">
    <button type="submit">Send</button>
  </form>
</div>

<style>
.contact-card {
  max-width: 560px;
  margin: 1.5rem 0;
  padding: 1.5rem;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  background: #ffffff;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.04);
}
.contact-form {
  display: grid;
  gap: 1rem;
}
.contact-row label {
  display: block;
  font-weight: 600;
  margin-bottom: 0.35rem;
  color: #1f2933;
}
.contact-row input,
.contact-row textarea {
  width: 100%;
  padding: 0.75rem 0.85rem;
  border: 1px solid #cbd5e1;
  border-radius: 10px;
  font-size: 1rem;
  transition: border-color 0.15s ease, box-shadow 0.15s ease;
}
.contact-row textarea {
  min-height: 160px;
  resize: vertical;
}
.contact-row input:focus,
.contact-row textarea:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.16);
}
.contact-form button {
  justify-self: start;
  padding: 0.7rem 1.2rem;
  border: none;
  border-radius: 10px;
  background: linear-gradient(120deg, #2563eb, #1d4ed8);
  color: #ffffff;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: 0 10px 20px rgba(37, 99, 235, 0.18);
  transition: transform 0.12s ease, box-shadow 0.12s ease, filter 0.12s ease;
}
.contact-form button:hover {
  filter: brightness(1.03);
  box-shadow: 0 12px 22px rgba(37, 99, 235, 0.22);
}
.contact-form button:active {
  transform: translateY(1px);
  box-shadow: 0 8px 16px rgba(37, 99, 235, 0.18);
}
</style>
