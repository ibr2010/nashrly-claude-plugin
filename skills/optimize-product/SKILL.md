---
name: optimize-product
description: End-to-end optimization of one product listing. Use when the merchant wants to improve, rewrite, or fix a specific product's title, description, or SEO and push it to their store.
---

# Optimize one product

1. Find the product with `product_lookup` or `show_products`, then call `product_details` and summarize its current score and weaknesses.
2. Call `propose_optimize`. Show the before/after card and its cost. Wait for confirmation, then `apply`.
3. Review guessed claims: call `propose_claims` for the product. List each claim the AI inferred and ask the merchant to keep, edit, or remove it; `apply` their choices.
4. Call `propose_publish` to push the result to the connected store (e.g. Shopify). Confirm, then `apply`.
5. Undo guidance: tell the merchant they can revert with `propose_undo` (confirm, then `apply`), and show the product with `product_details` afterwards.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
