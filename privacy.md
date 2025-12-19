---
layout: default
title: Privacy & Data Usage
nav_order: 4
---

# Privacy & Data Usage

How Behaviour Discounts handles merchant and shopper data. Adapt this to your own policies and jurisdictional requirements.

## Data we store (app backend)

- **Magic links:** Param/value pairs, linked discount, popup settings, and campaign metadata (stored via Prisma).  
- **Behavioural triggers:** Rule type (product view, time-on-site/time-on-page), thresholds, popup copy, linked discount, and state.  
- **Discount metadata:** Benefit type, gifts, param/value, and options stored in a Shopify Function configuration metafield.  
- **Billing:** Plan selection (Free, Starter, Business, Enterprise) and Shopify billing identifiers.  
- **Operational logs:** Service and error logs for debugging; no sale of data.

## Data read/written client-side

- **Cookies/session:** `magic_link_discount` cookie plus a sessionStorage mirror to keep the active campaign.  
- **Cart attributes:** `magic_link_campaign` or `behaviour_trigger_campaign` written before checkout to tell the Function which discount to apply.  
- **Free gifts:** Gift variants tagged `_gift_campaign` may be auto-added to cart when configured.

## Shopper telemetry

- URL query params to detect magic link activation.  
- Product view events (to trigger popups) and time-on-site/time-on-page thresholds.  
- Popup accepts/dismissals tied to campaigns (for activation only; impression/accept metrics are planned but not yet implemented).

## API tokens and access

- Uses an offline Admin API token to hydrate discounts and read/write metafields.  
- Access is limited to the scopes granted during install; rotation follows Shopify app best practices.

## Data sharing and processors

- Shopify acts as the primary data processor; additional subprocessors are limited to infrastructure/monitoring providers.  
- No data is sold or rented. Production access is restricted to authorized personnel for support and operations.

## Retention and deletion

- Configurations and metafields are kept while the app is installed.  
- Logs are retained for operational needs and rotated on a standard schedule.  
- Upon uninstall or request, stored configurations and related metafields can be removed; submit deletion requests via support.

## Your obligations (merchants)

- Ensure you have a lawful basis to process personal data (e.g., consent, contract, legitimate interest).  
- Avoid sending sensitive personal data through campaign params or triggers.  
- Update this notice to reflect your own data flows, vendors, and applicable regulations (GDPR, CCPA).

## Rights

- We will assist with access, correction, or deletion requests for data we control, subject to verification.  
- Shoppers should contact the merchant first; merchants can relay requests to us.

## Security

- Transport encryption (HTTPS/TLS) is required for admin and storefront calls.  
- Principle of least privilege for operator access; audit access and discount changes periodically.

## Need help?

Privacy or data questions? Email `support@example.com` with your shop domain and the campaign/trigger in question.
