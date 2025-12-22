---
layout: default
title: Getting started
parent: Guides
nav_order: 1
---

# Getting Started with Behaviour Discounts

Welcome to Behaviour Discounts! This guide will help you create your first campaigns and start rewarding customer behavior on your Shopify store.

## What is Behaviour Discounts?

Behaviour Discounts is a Shopify app that lets you create dynamic discount campaigns that respond to how customers interact with your store. You can trigger discounts based on browsing behavior, show personalized popups, and create unique discount links for marketing campaigns.

## Two Ways to Create Discounts

### 1. Behavioural Triggers

Behavioural triggers automatically activate discounts when customers perform specific actions on your store, such as:

- Viewing multiple products
- Spending time on your site
- Abandoning checkout
- Showing exit intent
- Being a returning visitor
- And more...

**Best for:** Organic traffic, on-site engagement, reducing cart abandonment

### 2. Magic Links

Magic Links are unique URLs with special discount parameters that activate when customers click them. They're perfect for:

- Email marketing campaigns
- Social media promotions
- Influencer partnerships
- QR codes on packaging
- SMS campaigns

**Best for:** External marketing, targeted campaigns, tracking specific channels

## Creating Your First Behavioural Trigger

### Step 1: Install the App Embed

Before triggers can work, you need to install the app embed on your theme:

1. Navigate to your Shopify admin
2. Go to **Online Store → Themes**
3. Click **Customize** on your active theme
4. In the theme editor, look for **App embeds** in the left sidebar
5. Enable **Behaviour Discounts**
6. Click **Save**

### Step 2: Create a Trigger

1. From the app home, click **Behavioural triggers** → **Create trigger**
2. Give your trigger a name (e.g., "Exit Intent - 10% Off")
3. Choose a **behaviour rule** (see [Trigger Types](./trigger-types.md) for details)
4. Configure your **discount settings**:
   - Product discounts (percentage, fixed amount, or free gift)
   - Order discounts
   - Shipping discounts
5. Decide whether to show a popup or auto-apply the discount
6. Set your trigger to **Active**

### Step 3: Test Your Trigger

1. Open your storefront in an incognito window
2. Perform the behavior that triggers your discount (e.g., view products, wait on page, move cursor to exit)
3. Verify the popup appears or discount applies as expected

## Creating Your First Magic Link

### Step 1: Choose a Template or Start Fresh

Magic Links come with pre-built templates for common use cases:

- **Email Welcome Series** - Reward new subscribers
- **Abandoned Cart Recovery** - Win back lost sales
- **Birthday Club** - Celebrate customer birthdays
- **Klaviyo Spin to Win** - Integrate with gamification popups
- **Or create your own custom campaign**

### Step 2: Configure Your Magic Link

1. From the app home, click **Magic links** → **Create magic link**
2. Select a template or start from scratch
3. Set your **URL parameters**:
   - **Parameter name** (e.g., `welcome`, `birthday`, `spin`)
   - **Parameter value** (e.g., `vip2024`, `win-x7k2m9p4`)
   - Use unguessable values for security
4. Configure your **discount settings** (same options as triggers)
5. Optionally show a popup when the link is clicked
6. Set status to **Active**

### Step 3: Get Your Magic Link URL

After creating your magic link, you'll get a URL like:

```
https://your-store.com?welcome=vip2024
```

Add this to your email campaigns, social media, or anywhere you want to offer a discount.

### Step 4: Test Your Magic Link

1. Open your magic link URL in an incognito window
2. Verify the popup appears (if configured)
3. Add products to cart
4. Check that the discount applies at checkout

## Understanding Discount Types

### Product Discounts

Apply discounts to specific products, collections, vendors, or product types:

- **Percentage off** - e.g., 15% off
- **Fixed amount off** - e.g., $5 off each item
- **Free gift** - Automatically add free products to cart

#### Minimum Requirements

Set requirements customers must meet to qualify:

- **Cart total** - e.g., "Spend $50 to get 10% off"
- **Quantity** - e.g., "Buy 3+ items to get free gift"
- **Exclude collections** - Don't count sale items toward minimums

### Order Discounts

Apply a discount to the entire cart subtotal:

- **Percentage off** - e.g., 20% off entire order
- **Fixed amount off** - e.g., $10 off order

### Shipping Discounts

Reduce or eliminate shipping costs:

- **Percentage off** - e.g., 50% off shipping
- **Fixed amount off** - e.g., $5 off shipping
- **Free shipping** - 100% off shipping

## Popup Customization

Both triggers and magic links can show branded popups:

1. Go to **Customize → Gift popup** or **Info popup**
2. Customize:
   - Background color
   - Text color
   - Border radius
   - Overlay opacity
3. Your popups will automatically match your brand

## Key Features

### Magic Link Priority

When a customer has both a magic link and a behavioural trigger active, **magic links always take priority**. This prevents popup spam and respects the customer's choice to engage with your promotional link.

### Auto-Add Free Gifts

For free gift campaigns, you can:

- **Auto-add** - Gifts automatically appear in cart when requirements are met
- **Manual selection** - Show popup letting customer choose their gift
- **Manual with popup** - Let customer choose from a limited selection

### Countdown Timers

Add urgency with countdown timers on popups:

- Set duration in seconds
- Customize the expired message
- Timer resets per session

## Best Practices

### For Behavioural Triggers

1. **Start conservative** - Don't trigger too easily (e.g., after 1 product view)
2. **Use exit intent wisely** - Great for capturing abandoning visitors
3. **Combine with requirements** - "Spend $50 to unlock 10% off"
4. **Test in incognito** - Always verify trigger behavior
5. **Monitor performance** - Check the analytics dashboard

### For Magic Links

1. **Use unguessable values** - Prevent unauthorized use (e.g., `win-x7k2m9p4` not `win`)
2. **Create unique links** - One per campaign for better tracking
3. **Test before sending** - Verify the link works and applies correctly
4. **Set expiry dates** - Use discount start/end dates for limited offers
5. **Track results** - Monitor clicks and conversions

## Priority and Combining Discounts

### Discount Priority

1. **Magic links override triggers** - Active magic links suppress behavioural triggers
2. **First trigger wins** - Only one behavioural trigger can be active per session
3. **Shopify validation** - All discounts validated at checkout by Shopify Functions

### Combining with Other Discounts

Configure which discounts can combine:

- Product discounts (e.g., automatic BOGO offers)
- Order discounts (e.g., seasonal sales)
- Shipping discounts (e.g., free shipping promotions)

**Note:** Combining is subject to Shopify's discount stacking rules.

## Next Steps

- [Explore all trigger types](./trigger-types.md) and when to use them
- [Set up your first campaign](./campaigns.md)
- [Customize popup styling](./customization.md)
- [Integrate with Klaviyo](./integrations.md)
- [View analytics and insights](./analytics.md)

## Need Help?

- Check our [FAQ](./faq.md) for common questions
- Review [troubleshooting tips](./troubleshooting.md)
- Contact support at [your-support-email]

---

**Ready to reward your customers?** Start creating your first trigger or magic link today!
