---
layout: default
title: Field notes from shipping a Shopify app
standfirst: Where Shopify doesn't behave the way its documentation says.
permalink: /notes/
section: notes
description: Measured notes on Shopify platform behaviour, from building and shipping a Shopify app — including where the documentation and the API disagree.
---

These cost real time. None of them turned up by reading the documentation, because in one case the
documentation is wrong — it says two cart fields are the same field, and on a live cart they came
back $120 apart.

## For developers

- **[Shopify cart price fields: what `line_price` and `final_line_price` actually mean]({{ '/notes/shopify-cart-price-fields/' | relative_url }})**
  <span class="tag">Measured</span>
  The deprecation note says one is an alias for the other. It isn't. Which field reflects
  cart-level discounts, which reflects line-level, and which one you should actually gate on when
  you need to know a line is free.

## For merchants

- **[How to add a free gift with purchase on Shopify]({{ '/free-gift-with-purchase-shopify/' | relative_url }})**
  Three ways to run it. The first needs no app at all, and for some stores it's the right answer.
  Also the two failures that quietly break free-gift promotions, one of which ends with your
  shopper paying for the gift.
