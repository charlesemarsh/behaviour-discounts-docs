---
layout: default
title: Merchant Help
nav_order: 2
---

# Behaviour Discounts — Merchant Help

Behaviour Discounts gates discounts behind magic links and behavioural triggers. Merchants control when a discount applies, which cart attribute is set, and whether free gifts are auto-added.

## Getting started

- Install the app and accept required scopes.  
- In Online Store → App embeds, enable the Behaviour Discounts theme embed.  
- Create your first magic link (campaign param + value) and link it to a discount.  
- Optional: add a behavioural trigger (product view or time-on-site/time-on-page) with popup copy.  
- Test in a theme preview before going live.

## How it works

- The theme app embed injects `magic-link-handler.js` on the storefront.  
- It fetches active configurations from `/api/magic-links` and `/api/behaviour-triggers`.  
- If the current URL matches a magic link param/value, it sets a `magic_link_discount` cookie, mirrors it in `sessionStorage`, and writes `magic_link_campaign` to the cart before checkout.  
- Behavioural triggers set `behaviour_trigger_campaign` via popup acceptance; they are suppressed whenever a magic link is active.  
- When a linked discount offers free products, the handler auto-adds gift variants tagged `_gift_campaign` according to the discount settings.

## Theme embed setup (once per theme)

1) In Shopify admin, go to **Online Store → Themes → Customize**.  
2) Open **App embeds** and toggle **Behaviour Discounts** on.  
3) Save the theme. The script now loads on storefront pages.

## Magic links

- Define a required URL query pair (e.g., `?campaign=spring15`) that must be present.  
- Link to a Shopify Function discount (Product, Order, or Shipping) whose metadata includes benefit type, gifts, and params.  
- Optional popup: collect acceptance before writing the cart attribute.  
- Share the full campaign URL in emails/ads; when clicked, the magic link stays active via cookie/session until cleared or expired.

### Editing or disabling

- Edit the param/value, linked discount, or popup copy directly in the app.  
- Disable a campaign to stop new activations; existing cookies expire on their normal schedule.

## Behavioural triggers

- Rule types: product view triggers, time-on-site, and time-on-page.  
- Configure popup headline/body and the linked discount.  
- Acceptance writes the `behaviour_trigger_campaign` cart attribute and, if applicable, adds configured gifts.  
- If a magic link is active, triggers stay suppressed to avoid stacking.

## Free gifts / free products

- Discounts can include gift variants tagged `_gift_campaign`.  
- Modes: **auto** (auto-add gift), **manual** (customer adds), or **manualPopup** (add after popup acceptance).  
- `autoAddGiftCount` controls how many gifts are added for the campaign.

## Priority

- Magic links have priority: when active, behavioural trigger popups and actions are suppressed so only the magic-link discount applies.

## Testing checklist

- In a theme preview, load a campaign URL with the expected query param/value and confirm the popup (if enabled) and discount state.  
- Check browser storage: `magic_link_discount` cookie and sessionStorage mirror are present.  
- Add items to cart; verify the cart attribute (`magic_link_campaign` or `behaviour_trigger_campaign`) is written before checkout.  
- For free gifts, confirm the correct variant(s) auto-add and remove if the discount deactivates.  
- Trigger a behavioural rule (product view or time threshold) without a magic link; confirm the popup and cart attribute.  
- Ensure triggers stay suppressed when a magic link is active.  
- Complete a test checkout and verify the correct discount/gift appears.

## Troubleshooting

- **No popup or discount:** Check the theme embed is enabled and published.  
- **Param not matching:** Ensure the shared URL includes the exact query pair and that the magic link is enabled.  
- **Gifts not adding:** Confirm the gift variant is tagged `_gift_campaign` and the discount benefit is set to Free products with the right `autoAddGiftCount`.  
- **Cart attribute missing:** Verify the customer accepted the popup (if required) and that the cart isn’t blocked by other scripts.  
- **Triggers always firing:** Make sure a magic link isn’t active from a previous session; clear cookies/session or use an incognito window.

## FAQ

- **What discount types are supported?** Product (percentage/fixed/gift), Order (percentage/fixed with optional min subtotal/quantity), and Shipping (percentage/fixed/free), all powered by Shopify Functions.  
- **Can I prevent stacking?** Yes. Magic links suppress behavioural triggers; within the discount, stacking rules are enforced by the Function configuration.  
- **Where do I edit popup copy?** In the Behavioural triggers settings for each rule.  
- **How are discounts configured?** Metadata (benefit type, gifts, param/value) is stored in the Function configuration metafield and read at runtime.

## Need help?

Email `support@example.com` with your shop domain, the campaign URL, and a brief description of what you expected vs. saw.
