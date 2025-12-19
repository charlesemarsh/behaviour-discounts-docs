---
layout: default
title: FAQ
parent: Reference
nav_order: 99
---

# FAQ

**Does Behaviour Discounts require a specific commerce platform?**  
No. You only need a way to detect user behaviour (events) and a mechanism to apply discounts (promo codes, cart rules, wallet credits). The examples here are platform-agnostic.

**How do I avoid stacking with existing promotions?**  
Add a condition to detect existing coupons or automatic promotions and set `stackable: false`. When both are present, either block the new discount or pick the better one and log the decision.

**How long should codes stay valid?**  
Short windows (e.g., 24 hours) drive action and reduce exposure. Use longer windows for post-purchase rewards where the intent is future retention.

**What if I cannot emit every event?**  
Start with the most reliable signals you have (e.g., checkout started, order completed) and expand later. Build rules that fail closed when data is missing to avoid over-firing.

**How do I measure success?**  
Track lift vs. a control group: conversion, AOV, and margin. Also watch operational metrics: redemption rate vs. issued codes, over-firing, and abuse indicators.

**Can I pause quickly if something looks wrong?**  
Yes—disable the rule, set `max_daily_redemptions` to zero, or shorten validity windows. Having a rollback runbook before launch keeps this fast.
