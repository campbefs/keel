---
layout: default
title: Field notes from shipping a Shopify app
standfirst: Where Shopify doesn't behave the way its documentation says.
permalink: /notes/
section: notes
description: Measured notes on Shopify platform behaviour, from building and shipping a Shopify app — including where the documentation and the API disagree.
---

Every one of these cost real time. None of them was discoverable by reading the docs, and one of
them the docs get flatly wrong.

## For developers

- **[Shopify cart price fields: what `line_price` and `final_line_price` actually mean]({{ '/notes/shopify-cart-price-fields/' | relative_url }})**
  <span class="tag">Measured</span>
  Shopify's docs call the two fields aliases. On a live cart with a cart-level discount they came
  back $120 apart. Here's which field reflects which discount, and which one to gate on.

## For merchants

- **[How to add a free gift with purchase on Shopify]({{ '/free-gift-with-purchase-shopify/' | relative_url }})**
  Three ways to build the offer and what each one costs you. The first needs no app at all. Also
  the two failures that quietly break free-gift promotions — one of them charges your shopper for
  the gift.
