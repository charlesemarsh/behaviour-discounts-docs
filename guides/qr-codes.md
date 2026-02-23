---
layout: default
title: QR codes
parent: Guides
nav_order: 3
---

# QR Codes

Create branded QR codes that trigger a discount when scanned. Print them on packaging, flyers, in-store displays, or event materials. When someone scans the QR code and visits your store, the discount is applied instantly.

QR codes work like magic links — they take priority over behavioural triggers. If a shopper scans a QR code, behavioural triggers will be suppressed to prevent conflicting discounts.

## How It Works

1. You create a QR code campaign and configure the discount
2. The app generates a unique QR code image you can download
3. A customer scans the code from printed material, packaging, a display, etc.
4. They're redirected to your store with the discount parameter attached
5. The discount is applied automatically, with an optional popup shown
6. The order is tracked and attributed to that QR code in your stats

## Creating a QR Code

From the app, go to **QR codes** → **Create QR code**.

### Campaign Details

- **Internal name** — For your own reference (e.g., "Summer Packaging Insert"). This is not visible to customers.
- **Description** — Optional notes for your team about the campaign's purpose.

### Destination

Choose where customers land after scanning:

| Destination | Example |
|---|---|
| Homepage | `/` |
| Product page | `/products/summer-bundle` |
| Collection page | `/collections/new-arrivals` |
| Cart page | `/cart` |
| Custom path | `/pages/summer-sale` |

The QR parameter is appended automatically, so a homepage destination becomes `https://your-store.com/?qr=abc123`.

### Discount Configuration

Configure one or more discount types. At least one must be enabled with a value greater than zero.

#### Product Discounts

- **Percentage off** — e.g., 15% off selected products
- **Fixed amount off** — e.g., £5 off each item
- **Free gift** — Automatically add free products to cart

Product discounts can target:
- All products
- Specific products
- Collections
- Vendors
- Product types

For free gifts, choose how the gift is added:
- **Auto-add** — Gift appears in cart automatically when requirements are met
- **Manual** — Customer adds the gift to cart themselves
- **Manual with popup** — A popup lets the customer choose their gift from a selection

#### Order Discounts

- **Percentage off** — e.g., 20% off the entire order
- **Fixed amount off** — e.g., £10 off the order subtotal

#### Shipping Discounts

- **Percentage off** — e.g., 50% off shipping
- **Fixed amount off** — e.g., £5 off shipping
- **Free shipping** — 100% off shipping costs

### Requirements

Set optional minimum thresholds customers must meet:

- **Minimum cart total** — e.g., "Spend £50 to unlock this discount"
- **Minimum quantity** — e.g., "Buy 3+ items to qualify"
- **Exclude collections** — Don't count items from specific collections toward the minimum

### Popup (Optional)

Show a branded popup when the customer arrives on your store after scanning:

- **Heading** — e.g., "Welcome! Your discount is ready"
- **Body text** — Additional details about the offer
- **Primary CTA** — Main button label (e.g., "Shop now")
- **Secondary CTA** — Alternative action (e.g., "Browse first")
- **Image** — Promotional image displayed in the popup
- **Terms link** — Optional terms and conditions link

Popup styling (colours, border radius, overlay) is configured globally in **Customize → Info popup**.

### Short URL (Optional)

Create a vanity redirect for your QR code, making it easy to share as a typed link too:

```
https://your-store.com/go/scan → your-store.com/?qr=abc123
```

Enter a path starting with `/` (e.g., `/go/scan`, `/promo/summer`). The redirect is created natively in Shopify and works immediately.

Short URLs are useful when you want to print the link alongside the QR code, or share it in channels where a QR code isn't practical (SMS, social bios, etc.).

{: .note }
Each short URL path must be unique across your store. If the path is already in use, you'll see a warning asking you to choose a different one.

## QR Code Design

Customise the look of your QR code to match your brand.

### Colours

- **Foreground colour** — The colour of the QR modules (default: black)
- **Background colour** — The background behind the QR code (default: white)

### Corner Style

- **Square** — Standard sharp corners
- **Rounded** — Softer, rounded module corners

### Logo

Add your logo to the centre of the QR code:

- Upload a square image (Shopify CDN recommended)
- The logo occupies roughly 22% of the QR code area
- Error correction is automatically increased to ensure the code remains scannable

### Frame

Add a text bar below the QR code:

- **Frame text** — e.g., "Scan for 15% off"
- **Frame colour** — Background colour of the bar

The frame is useful for print materials where you want to explain what the QR code does.

## Limits & Scheduling

### Usage Limits

- **Maximum redemptions** — Cap the total number of times this discount can be used. Leave empty for unlimited.

### Date Scheduling

- **Start date** — When the discount becomes active. Leave empty to start immediately.
- **End date** — When the discount expires. Leave empty for no expiry.

### Combining with Other Discounts

By default, QR code discounts do not combine with other discounts. You can enable combining with:

- Product discounts
- Order discounts
- Shipping discounts

This is subject to Shopify's discount stacking rules.

## Status

| Status | Meaning |
|---|---|
| **Draft** | The QR code is saved but the discount is not active. Use this while setting things up. |
| **Active** | The discount is live. Scanning the QR code will apply it. |
| **Paused** | Temporarily disabled. The QR code still exists but the discount won't apply. |

## Stats & Analytics

Each QR code has a stats page showing campaign performance:

- **Revenue** — Total revenue attributed to this QR code
- **Orders** — Number of orders placed using this discount
- **AOV** — Average order value

You can also see a breakdown of individual orders including order number, date, total, discount amount, and items purchased. Order numbers link directly to the Shopify admin.

## Testing

After creating or editing a QR code, use the **Preview for testing** button. This opens your storefront with a special preview parameter that forces the popup to display regardless of status, so you can verify the experience before going live.

You can also scan the QR code directly with your phone to test the full flow.

## Use Cases

### Packaging Insert

```
Name: Spring Order Insert
Destination: Homepage
Discount: 15% off next order
Popup: "Thanks for your order! Here's 15% off your next one."
```

Print the QR code on a card inside each package. Customers scan it and get a discount on their next purchase.

### In-Store Display

```
Name: In-Store Exclusive
Destination: /collections/in-store-only
Discount: 10% off + free shipping
Short URL: /go/instore
Frame text: "Scan for 10% off online"
```

Place QR codes on shelf displays or window signage to drive online purchases from physical shoppers.

### Event Flyer

```
Name: Pop-Up Market
Destination: /products/event-bundle
Discount: Free gift with purchase over £50
Short URL: /go/popup
Frame text: "Scan to shop online"
```

Hand out flyers at events. The QR code sends people directly to a featured product with an exclusive offer.

### Product Packaging

```
Name: Reorder Discount
Destination: Homepage
Discount: 20% off reorder
Usage limit: 1 per customer
Popup: "Ready for a refill? Enjoy 20% off."
```

Print on consumable product packaging to encourage repeat purchases.

## Best Practices

1. **Test before printing** — Always scan the QR code and verify the full flow before committing to print
2. **Use high contrast colours** — Ensure the QR code is easily scannable (dark foreground on light background works best)
3. **Add a frame with context** — Customers are more likely to scan a QR code that tells them what they'll get
4. **Set a destination that makes sense** — Don't just send people to the homepage if the offer is for a specific product
5. **Use short URLs alongside QR codes** — For print materials, include the typed URL as a fallback
6. **Monitor stats** — Track which QR codes are converting and adjust your campaigns
7. **Use usage limits for exclusive offers** — Prevent overuse of high-value discounts
8. **Pause instead of delete** — If you need to stop a campaign temporarily, pause it to preserve your stats
