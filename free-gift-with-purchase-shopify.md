---
layout: default
title: How to add a free gift with purchase on Shopify
standfirst: Three ways to do it, what each one costs you, and the two things that break it. One of them needs no app.
permalink: /free-gift-with-purchase-shopify/
description: A free gift over a cart total on Shopify, done with a manual discount, with Buy X Get Y, or with an app. What each approach can and cannot do.
---

"Spend $50, get a free tote" is one offer. Shopify gives you at least three ways to build it. They
behave differently in ways that are not obvious until a customer hits the edge.

## Option 1: a Buy X Get Y automatic discount. No app.

Shopify's built-in automatic discounts include **Buy X Get Y**, and for some offers that is the
whole job. Discounts → Create discount → Buy X Get Y, set the customer-buys condition to a
minimum purchase amount, set the customer-gets item to your gift at 100% off.

**Start here.** If it works for your offer, you are finished and it costs nothing.

**Where it stops:**

- **The customer has to add the gift themselves.** Shopify discounts the gift when it is in the
  cart; they do not put it there. A shopper who never adds it never gets it, and most will not,
  because they do not know it exists.
- **It does not come back off.** If they add the gift and then remove other items so the cart
  drops under $50, the discount stops applying and the gift becomes a **paid** item. They can
  check out paying full price for something you advertised as free.

That second one is the expensive failure. It is silent, and it looks like a scam to the customer.

## Option 2: a theme edit

You can add cart-page JavaScript that calls `/cart/add.js` when the subtotal crosses your
threshold. It works, and plenty of stores do it.

**What it costs you:** the code lives in your theme. Change theme and it is gone. Update your
theme, and it may break silently. Every developer who touches the store has to know it is there.
And you still need the discount from option 1, because adding the item is not the same as making
it free.

## Option 3: an app

An app does the adding and the discounting together, and keeps them in step. That is the only
real argument for one.

**What to check before you install any of them:**

| Question | Why it matters |
|---|---|
| Does it **remove** the gift when the cart drops below? | This is the failure in option 1. If the app does not solve it, it has not solved the problem |
| Does it add code to your theme? | Theme app extensions uninstall cleanly. Injected code does not |
| What happens when the gift is **out of stock**? | The add silently fails, and the offer quietly stops working |
| Does it combine with your other discounts? | Shopify discounts do not combine by default. An app that ignores this will fight your sale |
| What does the **buyer** see? | Some apps render their own cart widget. Some use your theme's existing cart line |

## The two things that actually break free-gift offers

**1. The gift stops being free.** Any offer built from a discount depends on that discount still
applying. Delete it, let it expire, or have another promotion win instead, and the gift is still
in the cart, now at full price. Shopify's own App Store rules forbid an app adding a charge to a
buyer's cart, which tells you how seriously they take it.

**2. The threshold and the gift disagree about what counts.** If your gift counts toward the
subtotal that unlocks it, a $45 cart plus a $10 gift is a $55 cart that qualifies, and removing
the gift makes it not qualify again. Carts can oscillate. Decide whether the gift counts, and be
consistent.

## Where Giftline fits

<div class="note" markdown="1">
I make Giftline, so treat this section as what it is. The three options above are written to be
useful whether or not you ever install it, and option 1 needs no app at all.
</div>

[Giftline](https://apps.shopify.com/keel-giftline) does option 3: set a cart total and a product,
and it adds the gift when a cart qualifies and takes it back when it does not. It renders nothing
in your theme, and it withdraws the gift rather than let it be charged for.

**It is not the right tool if** you want tiered gifts, gift choice, BOGO, or a progress bar in
your cart. It does one offer shape. If you need those, other apps in the category do more.
