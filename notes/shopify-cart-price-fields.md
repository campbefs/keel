---
layout: default
title: Shopify cart price fields — what line_price and final_line_price actually mean
standfirst: Measured on a live cart carrying a cart-level discount. The docs say the two fields are aliases. On that cart they differ by $120.
permalink: /notes/shopify-cart-price-fields/
section: notes
description: line_price vs final_line_price vs original_line_price on Shopify's /cart.js, measured on a live cart with a cart-level discount — where the documentation and the response disagree.
---

If you are reading `/cart.js` and deciding what a line costs, there are three price fields and
they do not mean the same thing. Shopify's documentation carries a deprecation note saying
`line_price` is an alias for `final_line_price`. **On a cart with a cart-level discount, it is
not.**

## The measurement

A live cart on a development store, one line item, one **cart-level 20% discount** applied:

```json
{
  "original_line_price": 60000,
  "line_price":          48000,
  "final_line_price":    60000,
  "line_level_discount_allocations": [],
  "total_price":         52792,
  "items_subtotal_price": 65990
}
```

`line_price` and `final_line_price` differ by **12,000 cents**. If they were aliases they could
not.

## What each field is actually reporting

| Field | Reflects |
|---|---|
| `original_line_price` | before any discount |
| `line_price` | after **cart-level** discounts |
| `final_line_price` | after **line-level** discounts only |
| `cart.total_price` | after **all** discounts |

That explains the numbers. A cart-level discount moves `line_price` and leaves `final_line_price`
alone, because no *line-level* discount was applied. `line_level_discount_allocations` is empty
for the same reason: the allocation is not on the line.

Summing `line_price` across lines reproduces `cart.total_price` exactly.

## Why it matters

**If you are gating on a cart total**, read `cart.total_price`. It is one documented field, after
everything, and it does not change meaning depending on which kind of discount a merchant happens
to be running. Summing line fields yourself means picking which discounts to honour, and getting
it wrong in a way that only shows up when a merchant runs a promotion you did not anticipate.

**If you are checking whether one specific line is free**, say a gift that must not be charged
for, neither field alone is safe. The two disagree and each captures a different level.
Taking `min(line_price, final_line_price)` can only understate the discount, which fails in the
safe direction: you might conclude a free line is not free and act conservatively, but you will
never conclude a charged line is free.

## The general point

The deprecation note is not wrong so much as incomplete. The fields converge on a cart with only
line-level discounts, which is the common case and presumably where the alias claim came from.
They diverge as soon as a cart-level discount exists.

**Do not reason about these fields from the documentation.** Put a discount on a real cart, fetch
`/cart.js`, and read what comes back.

<div class="note" markdown="1">
Measured 2026-09-09 on a Shopify development store, `/cart.js`, one line item, one active
cart-level percentage discount. Re-check before relying on it — this is a note about observed
behaviour on one date, not a specification.
</div>

---

This came out of building [Giftline]({{ '/apps/' | relative_url }}), a Shopify app I make, which
has to prove a gift line is free before it will leave it in a cart. Shopify forbids an app adding a
charge to a buyer's cart, so reading the wrong field here breaks a platform rule before it costs
anyone money.
