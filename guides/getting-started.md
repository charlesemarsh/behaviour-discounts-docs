---
layout: default
title: Getting started
parent: Guides
nav_order: 1
---

# Getting started

Use this guide to stand up Behaviour Discounts with a minimal, testable rule set.

## Prerequisites

- You can emit or ingest user events (e.g., web tracking, backend event bus, or CRM exports).
- You know how discounts should be applied in your commerce stack (promo codes, cart price rules, coupons, or wallet credits).
- Access to a non-production environment to validate rules before launch.

## 1) Pick the journey to influence

- Start with a single journey to keep scope tight:
  - First purchase completion
  - Abandoned cart recovery
  - Second/third purchase retention
  - Replenishment reminder
- Write down the success metric and guardrails (e.g., margin floor, max redemptions/day, geo restrictions).

## 2) Map events and attributes

Identify the signals you can observe and how they map to the journey.

| Event | Required attributes | Example use |
| ----- | ------------------- | ----------- |
| `cart_viewed` | `cart_value`, `items`, `session_id` | Size offers by basket value |
| `checkout_started` | `cart_value`, `coupon_used`, `shipping_country` | Avoid stacking with existing promos |
| `order_completed` | `order_value`, `order_id`, `loyalty_tier` | Trigger post-purchase rewards |

## 3) Define a first rule

Keep it simple to validate end-to-end wiring:

1. Trigger: `checkout_started` where `cart_value >= 50` and `coupon_used == false`.
2. Action: issue a 10% off code (single-use) valid for 24 hours.
3. Guardrails: limit to 500 redemptions/day and exclude wholesale customers.

Document the rule in version control so product, finance, and engineering agree on scope.

## 4) Connect discount delivery

- Decide how the discount is applied:
  - Generate a promo code and surface it in-app/onsite.
  - Automatically inject a cart rule via your commerce backend.
  - Send via email/SMS for abandoned cart journeys.
- Ensure redemptions are trackable so you can measure lift vs. control.

## 5) Test before launch

- Reproduce the triggering events in staging and confirm:
  - The rule fires only when conditions are met.
  - Guardrails (caps, geo, eligibility) block non-qualifying sessions.
  - The discount applies correctly and cannot be reused beyond limits.
- Shadow-launch with a 0% discount or an internal audience first, then roll out broadly.

## Next steps

- Hardening rules and guardrails: see [Configuring rules](configuration.md).
- Launching with observability and rollback: see [Rolling out safely](rollout.md).
