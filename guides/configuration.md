---
layout: default
title: Trigger types
parent: Guides
nav_order: 2
---

# Behavioural Trigger Types

This guide explains each trigger type in detail, including when to use them, how to configure them, and best practices.

## Overview

Behaviour Discounts offers multiple trigger types to reward different customer behaviors:

| Trigger Type | Best For | Typical Conversion |
|-------------|----------|-------------------|
| [Product Views](#product-views) | Engaged browsers | Medium |
| [Exit Intent](#exit-intent) | Abandonment prevention | High |
| [Checkout Abandon](#checkout-abandon) | Cart recovery | Very High |
| [Time on Site](#time-on-site) | Engaged visitors | Medium |
| [Time on Page](#time-on-page) | Content engagement | Medium |
| [Returning Visitor](#returning-visitor) | Customer loyalty | High |
| [Wishlist Activity](#wishlist-activity) | Swym integration | Medium-High |
| [Cart Add](#cart-add) | Purchase intent | High |

---

## Product Views

**Trigger when customers view multiple products, showing genuine shopping interest.**

### How It Works

The trigger fires after a customer views a specified number of distinct product pages in a single session. Each product page is counted once, regardless of how many times they revisit it.

### Configuration

#### Any Products Mode
Track views across all products in your store:

- **Distinct product views required** - Number of unique products to view (e.g., 3, 5, 10)

#### Specific Products Mode
Track views for selected products only:

- **Select products** - Choose which products count toward the trigger
- **Match mode**:
  - **Any** - Trigger after viewing any selected product
  - **All** - Trigger only after viewing every selected product

### Use Cases

**Browse Reward**
```
Trigger: After viewing 5 distinct products
Discount: 10% off first order
Goal: Convert browsers to buyers
```

**Collection Discovery**
```
Trigger: View specific products (new arrivals)
Discount: Free shipping on orders over $50
Goal: Drive sales of new products
```

**High-Intent Shoppers**
```
Trigger: After viewing 10+ products
Discount: 15% off + free gift
Goal: Reward highly engaged shoppers
```

### Best Practices

- **Start at 3-5 views** - Too low (1-2) triggers too easily
- **Higher thresholds for expensive items** - Luxury brands might use 8-10 views
- **Combine with requirements** - "View 5 products, spend $75, get 15% off"
- **Use specific mode for launches** - Target new collection engagement
- **Test and adjust** - Monitor trigger rate and conversions

### Tips

✅ Great for fashion, home decor, and lifestyle stores
✅ Works well with "New Arrivals" campaigns
✅ Pair with countdown timer for urgency
❌ May be too aggressive for low SKU count stores
❌ Not ideal for single-product stores

---

## Exit Intent

**Capture customers attempting to leave your store without purchasing.**

### How It Works

Exit intent detects when a customer's mouse cursor moves toward the browser's top edge or when they switch tabs/windows. This indicates they're about to leave the site.

### Configuration

**Page Targeting**
Choose where the trigger fires:

- **All pages** - Trigger exit intent anywhere on site
- **Product pages only** - Only on `/products/*` URLs
- **Collection pages only** - Only on `/collections/*` URLs
- **Cart page only** - Only on `/cart` page

**Advanced Filters (for Product/Collection pages)**

When targeting product or collection pages, you can further filter:

- **Specific products** - Only trigger on selected product pages
- **Specific collections** - Only trigger on selected collection pages
- **Leave empty** - Trigger on any product/collection page

**Cooldown Settings**
- **Cooldown between prompts** - Minimum minutes before showing again (prevents spam)

### Use Cases

**Last Chance Offer**
```
Trigger: Exit intent on all pages
Discount: 15% off first order
Cooldown: 60 minutes
Goal: Convert abandoning visitors
```

**Product-Specific Recovery**
```
Trigger: Exit intent on specific high-value products
Discount: Free shipping + 10% off
Cooldown: 30 minutes
Goal: Close sales on key products
```

**Cart Abandonment**
```
Trigger: Exit intent on cart page only
Discount: Free shipping on orders over $50
Cooldown: 24 hours
Goal: Complete pending purchases
```

**Collection Browse Recovery**
```
Trigger: Exit intent on sale collection pages
Discount: Additional 10% off sale items
Cooldown: 120 minutes
Goal: Maximize sale collection conversions
```

### Best Practices

- **Use moderate cooldowns** - 30-60 minutes prevents annoyance
- **Target high-intent pages** - Cart and product pages convert best
- **Don't overdo the discount** - 10-15% is often enough
- **Test on mobile** - Exit intent works differently on touch devices
- **Combine with countdown** - "You have 5 minutes to claim this offer"

### Tips

✅ Highest converting trigger type
✅ Perfect for cart page abandonment
✅ Great for one-time offers
✅ Works well with countdown timers
⚠️ Can feel aggressive if overused
⚠️ Less effective on mobile (no cursor movement)
❌ Don't set cooldown too low (< 15 minutes)

---

## Checkout Abandon

**Re-engage customers who visited checkout but returned without completing purchase.**

### How It Works

When a customer visits any `/checkout` URL then navigates back to your store without completing their order, this trigger activates after a specified delay.

### Configuration

- **Delay before firing** - Seconds to wait after returning from checkout (e.g., 5, 10, 30)
- **Minimum cart subtotal** - Optional minimum cart value to trigger (prevents low-value offers)

### Use Cases

**High-Intent Recovery**
```
Trigger: Returned from checkout after 10s
Minimum cart: $50
Discount: Free shipping
Goal: Remove shipping objection
```

**Premium Cart Recovery**
```
Trigger: Returned from checkout after 5s
Minimum cart: $100
Discount: 10% off order + free shipping
Goal: Close high-value sales
```

**Quick Win**
```
Trigger: Returned from checkout after 30s
Minimum cart: $25
Discount: $5 off order
Goal: Small incentive to complete
```

### Best Practices

- **Short delay** - 5-15 seconds is optimal
- **Strong offer** - These are high-intent customers
- **Use minimum cart value** - Focus on profitable orders
- **Free shipping works best** - Often the main objection
- **Clear messaging** - "Complete your order and save"

### Tips

✅ Very high conversion rate
✅ Customers already decided to buy
✅ Great for free shipping offers
✅ Test different cart minimums
⚠️ Can indicate pricing issues if triggered often
❌ Don't spam with multiple checkout abandon triggers

---

## Time on Site

**Reward customers who spend time browsing your entire store.**

### How It Works

Tracks total time a customer has spent on your site during their current session. Time accumulates across all pages.

### Configuration

- **Seconds on site** - Total time required (e.g., 60, 120, 300)

### Use Cases

**Engaged Browser Reward**
```
Trigger: After 120 seconds on site
Discount: 10% off first order
Goal: Convert engaged traffic
```

**Deep Engagement**
```
Trigger: After 5 minutes on site
Discount: Free gift with purchase
Goal: Reward highly engaged visitors
```

**Content Consumer**
```
Trigger: After 3 minutes on site
Discount: 15% off + free shipping over $75
Goal: Convert content readers to buyers
```

### Best Practices

- **60-180 seconds is typical** - Balances engagement with trigger rate
- **Consider your content** - Blog-heavy sites might use longer times
- **Combine with other triggers** - Works well with exit intent
- **Test mobile vs desktop** - Mobile sessions are often shorter
- **Clear value prop** - "Thanks for spending time with us!"

### Tips

✅ Great for content-rich stores
✅ Works well with blogs
✅ Good for educational products
⚠️ Time can accumulate across tabs
⚠️ May trigger during inactive browsing
❌ Not ideal for quick purchase stores

---

## Time on Page

**Trigger based on time spent on specific pages or URL patterns.**

### How It Works

Tracks time spent on individual pages that match your specified URL patterns. Great for content engagement on specific pages.

### Configuration

- **Seconds on page** - Time required on matching page (e.g., 30, 60, 120)
- **Matching pages** - URL patterns to track (one per line)

**URL Pattern Examples:**
```
/products/*          → Any product page
/collections/sale    → Sale collection page
/                    → Homepage only
/pages/about         → About page
/blogs/*             → Any blog post
```

**Wildcard support:**
- Use `*` at the end for wildcard matching
- Patterns are relative paths (no domain)

### Use Cases

**Product Detail Engagement**
```
Trigger: 60 seconds on any product page
Matching: /products/*
Discount: 10% off that product
Goal: Convert detail readers
```

**Sale Collection**
```
Trigger: 45 seconds on sale page
Matching: /collections/sale
Discount: Additional 10% off sale items
Goal: Maximize sale conversions
```

**Content Conversion**
```
Trigger: 90 seconds on blog posts
Matching: /blogs/*
Discount: 15% off first order
Goal: Convert content readers
```

**Homepage Engagement**
```
Trigger: 120 seconds on homepage
Matching: /
Discount: Free shipping on first order
Goal: Convert homepage browsers
```

### Best Practices

- **30-90 seconds typical** - Enough time to read content
- **Match to page type** - Product pages shorter, blog posts longer
- **Test patterns** - Verify URLs match correctly
- **Use for key content** - Buying guides, product education
- **Clear trigger intent** - "Thanks for learning about our products"

### Tips

✅ Perfect for educational content
✅ Great for product detail pages
✅ Works well with buying guides
✅ Good for blog monetization
⚠️ Time counts even if tab not active
⚠️ Multiple tabs can trigger separately
❌ Don't set time too low (< 15 seconds)

---

## Returning Visitor

**Reward loyal customers who visit your store multiple times.**

### How It Works

Tracks how many times a customer has visited your store using browser storage. Triggers after reaching a specified visit threshold.

### Configuration

- **Visits required** - Number of visits to trigger (e.g., 2, 3, 5)
- **Cooldown between triggers** - Hours before trigger can fire again after discount applied

### Use Cases

**Second Visit Reward**
```
Trigger: On visit #2
Cooldown: 168 hours (7 days)
Discount: 10% off first order
Goal: Convert returning browsers
```

**Loyalty Threshold**
```
Trigger: On visit #5
Cooldown: 720 hours (30 days)
Discount: 20% off + free gift
Goal: Reward loyal visitors
```

**Weekly Shopper**
```
Trigger: On visit #3
Cooldown: 24 hours
Discount: Free shipping
Goal: Encourage frequent visits
```

### Best Practices

- **2-3 visits is typical** - Balance between accessible and meaningful
- **Use long cooldowns** - Prevent gaming the system (7+ days)
- **Clear messaging** - "Welcome back! Here's a thank you offer"
- **Strong discount** - Reward the loyalty
- **Track in analytics** - Monitor visit patterns

### Tips

✅ Great for building customer relationships
✅ Rewards genuine interest
✅ Works well for considered purchases
✅ Good for subscription/repeat purchase products
⚠️ Browser-based tracking (clearing cookies resets)
⚠️ Cooldown starts after discount applied, not trigger
❌ Not ideal for impulse purchase stores

---

## Wishlist Activity

**Reward customers who save products to their Swym wishlist.**

### How It Works

Integrates with the Swym Wishlist Plus app to trigger when customers add items to their wishlist.

**⚠️ Requires:** [Swym Wishlist Plus](https://apps.shopify.com/swym-relay) app installed and enabled in Behaviour Discounts settings.

### Configuration

#### Any Products Mode
Track wishlist additions across all products:

- **Wishlist items required** - Number of products to save (e.g., 1, 3, 5)

#### Specific Products Mode
Track wishlist additions for selected products only:

- **Select products** - Choose which products count
- **Match mode**:
  - **Any** - Trigger after wishlisting any selected product
  - **All** - Trigger only after wishlisting every selected product

### Use Cases

**Single Item Incentive**
```
Trigger: After adding 1 item to wishlist
Discount: 10% off wishlist items
Goal: Convert wishlist savers to buyers
```

**Collection Builder**
```
Trigger: After adding 3 items to wishlist
Discount: 15% off + free shipping over $100
Goal: Encourage wishlist shopping
```

**Targeted Product Push**
```
Trigger: Wishlisting specific high-margin products
Discount: Free gift with purchase
Goal: Drive sales of target products
```

### Best Practices

- **Low threshold** - 1-3 items is typical
- **Wishlist-specific discount** - "Save now on your wishlist"
- **Email integration** - Combine with wishlist reminder emails
- **Clear CTA** - "Your wishlist items are on sale!"
- **Test with Swym** - Ensure integration works correctly

### Tips

✅ Very high purchase intent
✅ Great for fashion and lifestyle
✅ Perfect for gift-givers
✅ Works well with email campaigns
⚠️ Requires Swym app (paid)
⚠️ Limited to Swym wishlist events
❌ Won't work with other wishlist apps

---

## Cart Add

**Trigger when customers add products to their cart, showing strong purchase intent.**

### How It Works

Fires when customers add products to their cart. Can trigger based on any products or specific selected products.

### Configuration

#### Any Products Mode
Track cart additions across all products:

- **Cart items required** - Number of products to add (e.g., 1, 2, 3)

#### Specific Products Mode
Track cart additions for selected products only:

- **Select products** - Choose which products count
- **Match mode**:
  - **Any** - Trigger after adding any selected product
  - **All** - Trigger only after adding every selected product

### Use Cases

**First Cart Item**
```
Trigger: After adding 1 item to cart
Discount: Free shipping on orders over $50
Goal: Increase average order value
```

**Multi-Item Bundle**
```
Trigger: After adding 3 items to cart
Discount: 15% off entire order
Goal: Encourage bulk purchases
```

**Specific Product Upsell**
```
Trigger: Adding specific flagship product
Discount: 20% off complementary products
Goal: Cross-sell related items
```

### Best Practices

- **Low threshold** - 1-2 items is common
- **Upsell opportunity** - "Add $X more for free shipping"
- **Complement cart items** - Offer related products
- **Clear value** - Show savings in popup
- **Test timing** - Immediate vs slight delay

### Tips

✅ Extremely high purchase intent
✅ Perfect for upselling
✅ Great for free shipping thresholds
✅ Works well with product bundles
⚠️ Can feel pushy if discount too aggressive
⚠️ May conflict with cart page design
❌ Don't spam with multiple cart triggers

---

## Trigger Comparison Matrix

### By Purchase Intent (Highest to Lowest)

1. **Checkout Abandon** - Already tried to buy
2. **Cart Add** - Added products to cart
3. **Wishlist Activity** - Saved products for later
4. **Exit Intent** - Attempting to leave
5. **Product Views** - Browsing products
6. **Returning Visitor** - Came back multiple times
7. **Time on Page** - Reading product details
8. **Time on Site** - General browsing

### By Use Case

**Abandonment Prevention**
- Exit Intent
- Checkout Abandon

**Engagement Rewards**
- Product Views
- Time on Site
- Time on Page
- Returning Visitor

**Purchase Intent**
- Cart Add
- Wishlist Activity
- Checkout Abandon

**Content Marketing**
- Time on Page
- Time on Site

---

## Combining Triggers Strategically

### The Welcome Journey

```
Visit 1: Product Views (5 products) → 10% off first order
Visit 2: Exit Intent → Free shipping reminder
Visit 3: Returning Visitor → VIP 15% off
```

### The High-Intent Path

```
Product Views (3+) → Browse reward eligible
Cart Add → Free shipping offer
Checkout Abandon → Final 10% off push
```

### The Content Consumer

```
Time on Page (blog) → 10% off for readers
Product Views (2+) → Additional 5% off
Exit Intent → Last chance 15% total
```

---

## Next Steps

- [Learn about Magic Links](./magic-links.md)
- [Customize your popups](./customization.md)
- [Set up analytics tracking](./analytics.md)
- [View discount configuration options](./discount-configuration.md)

Need help choosing the right trigger? Check our [strategy guide](./strategy-guide.md) or [contact support](./support.md).
