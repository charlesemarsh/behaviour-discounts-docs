---
layout: default
title: Data model
parent: Reference
nav_order: 1
---

# Data model

Key concepts used by Behaviour Discounts. Adjust naming to match your systems, but keep the same intent to ensure rules are portable.

## Events

An event is the atomic input Behaviour Discounts reacts to.

| Field | Description |
| ----- | ----------- |
| `name` | Event name, e.g., `checkout_started`, `order_completed`, `cart_abandoned`. |
| `occurred_at` | ISO-8601 timestamp. |
| `user` | Actor identifiers (user_id, email, device_id, session_id). |
| `attributes` | Event-specific data (cart value, items, coupon used, geo, device, traffic source). |
| `context` | Optional metadata (environment, experiment bucket, locale). |

Example event payload:

```json
{
  "name": "checkout_started",
  "occurred_at": "2024-07-15T18:24:10Z",
  "user": {
    "id": "user_123",
    "email": "shopper@example.com",
    "session_id": "sess_abc"
  },
  "attributes": {
    "cart_value": 145.75,
    "currency": "USD",
    "coupon_used": false,
    "items": [
      {"sku": "TEE-001", "qty": 2, "price": 25.0},
      {"sku": "DENIM-034", "qty": 1, "price": 95.75}
    ]
  },
  "context": {
    "traffic_source": "email",
    "device": "mobile",
    "country": "US"
  }
}
```

## Rules

- **Trigger:** Event name to listen for.
- **Conditions:** Checks against event attributes, user profile, history, or context. Support both `all` (AND) and `any` (OR) groups when possible.
- **Action:** What to issue or apply.
- **Guardrails:** Limits that short-circuit the rule when breached.

## Discount actions

| Type | Fields | Notes |
| ---- | ------ | ----- |
| `percentage_off` | `value` (e.g., 10), optional `max_amount` | Size cap prevents outsized discounts on large carts. |
| `amount_off` | `value` (currency), optional `min_cart_value` | Good for “$15 off $60+” style incentives. |
| `free_shipping` | `service_levels`, `regions` | Pair with cart minimums to protect margin. |
| `store_credit` | `value`, `expires_at` | Useful for post-purchase or retention rewards. |

Example issued discount record:

```json
{
  "code": "HV15-8K2F",
  "action": {
    "type": "percentage_off",
    "value": 15,
    "max_amount": 40
  },
  "expires_at": "2024-07-16T18:24:10Z",
  "metadata": {
    "rule": "high-value-cart-first-purchase",
    "issued_for_event_id": "evt_789",
    "user_id": "user_123"
  },
  "stackable": false,
  "status": "issued"
}
```

## Guardrails

Use guardrails to keep incentives sustainable.

| Guardrail | Purpose |
| --------- | ------- |
| `max_daily_redemptions` | Caps liability for a rule each day. |
| `per_user_limit` | Prevents repeated redemptions by the same user/device. |
| `stackable` | Controls if this discount can combine with others; prefer `false` by default. |
| `validity_window` | Short expiry windows keep incentives action-oriented and limit exposure. |
| `eligible_segments` / `excluded_segments` | Fine-grained control by geo, device, traffic source, loyalty tier. |

## Status lifecycle

- `issued`: Code or rule ready to apply.
- `applied`: Customer has added the discount to a cart.
- `redeemed`: Discount applied to a completed order.
- `expired`: Validity window passed; discount no longer usable.
- `revoked`: Manually invalidated (e.g., abuse or rollout rollback).
