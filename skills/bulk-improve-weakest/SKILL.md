---
name: bulk-improve-weakest
description: Improve the N weakest products one at a time. Use when the merchant asks to fix their worst listings, improve many products, or bulk-optimize (e.g. "fix my 5 weakest products").
---

# Bulk improve the weakest products

1. Ask for N if not given (default 5). Call `account` for the credit balance.
2. Call `show_products` sorted by weakest score, limited to N.
3. For each product in order:
   a. Show `product_details` briefly.
   b. Call `propose_optimize`, show the card and its cost plus the running total so far.
   c. Pause. Ask: apply, skip, or stop. Only call `apply` on an explicit yes.
   d. After applying, ask whether to publish now (`propose_publish` then `apply`) or batch publishing at the end.
4. Stop immediately if the merchant says stop or the balance would go negative.
5. Finish with a summary table: product, old score, new score, credits spent, published yes/no, and how to undo with `propose_undo`.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
