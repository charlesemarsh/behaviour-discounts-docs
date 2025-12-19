---
layout: default
title: Rolling out safely
parent: Guides
nav_order: 3
---

# Rolling out safely

Launch Behaviour Discounts with a clear plan to monitor, communicate, and, if needed, rollback quickly.

## Pre-launch checklist

- [ ] Rule logic reviewed by product/finance.
- [ ] Guardrails set (caps, stack rules, geo/device filters).
- [ ] Test cases for both qualifying and non-qualifying traffic.
- [ ] Observability wired: events, issued codes, redemptions, error logs.
- [ ] Runbook for rollback (disable rule, pause issuing codes, expire active codes if supported).

## Launch phases

1. **Shadow / dry run:** Evaluate rules but do not deliver discounts; log what would have fired.
2. **Internal users:** Allow only employees or beta customers; validate UX and redemption.
3. **Limited exposure:** Roll out to a small % of eligible traffic; monitor lift vs. control.
4. **Scaled rollout:** Increase coverage when metrics and margin stay within guardrails.

## What to monitor

- Trigger volume vs. rule fire rate (are you over/under firing?).
- Issued vs. redeemed codes and redemption lag.
- AOV and margin impact compared to control traffic.
- Stacking behaviour: how often other promos coexist and whether stacking is blocked.
- Abuse signals: excessive redemptions per user/device/IP, rapid-fire attempts, or reselling codes.

## Rollback levers

- Disable the rule or set `max_daily_redemptions` to zero.
- Shorten validity windows for issued codes.
- Block specific segments (geo, device, payment method) if anomalies are isolated.
- Fall back to a lower-value offer while investigating issues.

## Communicating changes

- Announce rule changes in release notes with intended impact and monitoring plan.
- Record when rules were enabled/disabled so data teams can align reporting windows.
- Keep stakeholders informed of early results and any anomalies you are watching.
