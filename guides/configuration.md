---
layout: default
title: Configuring rules
parent: Guides
nav_order: 2
---

# Configuring rules

Design rules that react to behaviour, stay profitable, and are auditable.

## Core building blocks

- **Trigger event:** The event that starts evaluation (e.g., `checkout_started`, `order_completed`).
- **Eligibility conditions:** Attribute checks on the event, user, session, and cart.
- **Discount action:** What is issued or applied (percentage, fixed amount, free shipping, credit).
- **Guardrails:** Caps that prevent over-exposure (daily limits, geo blocks, stack rules).

## Example rule blueprint

```yaml
name: high-value-cart-first-purchase
description: Reward first-time buyers with a high basket with 15% off
trigger: checkout_started
conditions:
  all:
    - cart_value >= 120
    - is_first_purchase == true
    - coupon_used == false
    - shipping_country in ["US", "CA", "GB"]
action:
  type: percentage_off
  value: 15
  code_prefix: HV15-
  expires_in_hours: 24
guardrails:
  max_daily_redemptions: 300
  stackable: false
  exclude_segments: ["wholesale", "employee"]
```

Adapt the fields to match how your system stores events and applies discounts.

## Guardrails to consider

- **Redemption caps:** Daily or weekly limits per rule, per user, and global.
- **Stacking rules:** When a customer already has a code or automatic promotion, either block or pick the best value.
- **Budget controls:** Stop evaluation when projected liability or margin thresholds are exceeded.
- **Channel limits:** Restrict to specific channels (web, app, email) to observe impact before expanding.
- **Time windows:** Limit to certain hours, weekdays, seasons, or campaign periods.

## Segmentation patterns

- Lifecycle: first purchase, second purchase, lapsed (no purchase in 30/60/90 days).
- Value: high AOV, low AOV, high return rate, high item count.
- Context: geo, device, traffic source, payment method, inventory availability.
- Risk: fraud score, failed payments, high return probability.

## Testing rule changes

- Treat rules as code: commit changes with rationale, expected impact, and any data sources used.
- Test with synthetic events that target each branch of your conditions.
- Add monitoring on:
  - Trigger volume vs. rule fire rate
  - Redemption rate vs. issued codes
  - Margin impact and average discount per order
- Roll out incrementally (internal users → small % of traffic → broader audiences).
