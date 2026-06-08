---
layout: default
title: Merchant Help
nav_order: 2
---

**English** · [Deutsch](/de/help/) · [Français](/fr/help/)

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

## QR codes

- Create branded QR codes that trigger a discount when scanned from packaging, flyers, in-store displays, or event materials.
- Each QR code links to a Shopify Function discount (same types as magic links: Product, Order, or Shipping).
- Choose a destination page (homepage, product, collection, cart, or custom path). The `qr` parameter is appended automatically.
- Customise QR appearance: foreground/background colours, corner style (square or rounded), centre logo, and an optional frame with a call-to-action label.
- Optional popup: show a branded message when the customer lands on your store after scanning.
- Optional short URL: create a vanity redirect (e.g., `/go/scan`) so the link can be printed or shared alongside the QR code.
- QR codes share priority with magic links — when active, behavioural triggers are suppressed.

### Editing or disabling

- Edit the destination, discount, popup, QR design, or short URL directly in the app.
- Pause a campaign to stop new activations while keeping your stats. Delete removes the QR code, Shopify discount, and any associated URL redirect.

## Free gifts / free products

- Discounts can include gift variants tagged `_gift_campaign`.  
- Modes: **auto** (auto-add gift), **manual** (customer adds), or **manualPopup** (add after popup acceptance).  
- `autoAddGiftCount` controls how many gifts are added for the campaign.

## Priority

- Magic links and QR codes share the same priority: when either is active, behavioural trigger popups and actions are suppressed so only the magic-link or QR code discount applies.

## Testing checklist

- In a theme preview, load a campaign URL with the expected query param/value and confirm the popup (if enabled) and discount state.
- Check browser storage: `magic_link_discount` cookie and sessionStorage mirror are present.
- Add items to cart; verify the cart attribute (`magic_link_campaign` or `behaviour_trigger_campaign`) is written before checkout.
- For free gifts, confirm the correct variant(s) auto-add and remove if the discount deactivates.
- Trigger a behavioural rule (product view or time threshold) without a magic link; confirm the popup and cart attribute.
- Ensure triggers stay suppressed when a magic link or QR code is active.
- For QR codes, scan the generated code with a phone and confirm it redirects to the correct destination with the discount applied.
- If a short URL is configured, visit it in a browser and confirm it redirects correctly.
- Use the **Preview for testing** button on QR codes and magic links to force the popup without needing the campaign to be active.
- Complete a test checkout and verify the correct discount/gift appears.

## Troubleshooting

- **No popup or discount:** Check the theme embed is enabled and published.
- **Param not matching:** Ensure the shared URL includes the exact query pair and that the magic link is enabled.
- **QR code not working:** Verify the QR code status is Active, not Draft or Paused. Scan the code and check the destination URL includes the `?qr=` parameter.
- **Short URL not redirecting:** Confirm the redirect was created successfully (check for warnings on save). You can also verify in Shopify admin under Settings → Navigation.
- **Short URL path already taken:** Each path must be unique across your store. Choose a different path or remove the existing redirect in Settings → Navigation.
- **Gifts not adding:** Confirm the gift variant is tagged `_gift_campaign` and the discount benefit is set to Free products with the right `autoAddGiftCount`.
- **Cart attribute missing:** Verify the customer accepted the popup (if required) and that the cart isn’t blocked by other scripts.
- **Triggers always firing:** Make sure a magic link or QR code isn’t active from a previous session; clear cookies/session or use an incognito window.

## FAQ

- **What discount types are supported?** Product (percentage/fixed/gift), Order (percentage/fixed with optional min subtotal/quantity), and Shipping (percentage/fixed/free), all powered by Shopify Functions.
- **Can I prevent stacking?** Yes. Magic links and QR codes suppress behavioural triggers; within the discount, stacking rules are enforced by the Function configuration.
- **Where do I edit popup copy?** In the magic link, QR code, or behavioural trigger settings for each campaign.
- **How are discounts configured?** Metadata (benefit type, gifts, param/value) is stored in the Function configuration metafield and read at runtime.
- **What's the difference between a magic link and a QR code?** Magic links use a customisable query parameter (e.g., `?ref=summer`) and are designed for digital sharing. QR codes always use the `qr` parameter with an auto-generated value and include a scannable QR image for print and physical media. Both support the same discount types, popups, and short URLs.
- **Can I use the same short URL path for a magic link and a QR code?** No. Short URL paths must be unique across your entire store, regardless of whether they belong to a magic link or QR code.
- **Can I use "qr" as a magic link parameter name?** No. The parameter name `qr` is reserved for QR codes. Choose a different name for your magic links (e.g., `ref`, `promo`, `campaign`).
- **What happens if I delete a QR code or magic link with a short URL?** The Shopify URL redirect is automatically deleted along with the campaign and its associated discount.
- **Can I pause a QR code without deleting it?** Yes. Pausing stops the discount from applying but preserves your stats and configuration. You can reactivate it later.

## Need help?

Email `support@example.com` with your shop domain, the campaign URL, and a brief description of what you expected vs. saw.
