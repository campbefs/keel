---
layout: default
title: Field notes from shipping a Shopify app
standfirst: Where Shopify does not behave the way its documentation says, measured against live stores.
permalink: /notes/
section: notes
description: Measured notes on Shopify platform behaviour, from building and shipping a Shopify app — including where the documentation and the API disagree.
---

Each of these cost real time to find, and none of them was discoverable by reading the docs.

## Notes for developers

- **[Shopify cart price fields: what `line_price` and `final_line_price` actually mean]({{ '/notes/shopify-cart-price-fields/' | relative_url }})**
  <span class="tag">Measured</span>
  The docs call the two fields aliases. On a live cart carrying a cart-level discount they came back
  $120 apart. Which field reflects which discount level, and which one to gate on.

## For merchants

- **[How to add a free gift with purchase on Shopify]({{ '/free-gift-with-purchase-shopify/' | relative_url }})**
  Three ways to build the offer, what each one costs, and the two failures that break free-gift
  promotions. The first approach needs no app.
