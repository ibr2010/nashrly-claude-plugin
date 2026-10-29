---
name: seo-keywords
description: Find SEO keywords or translate a product for a market. Use when the merchant asks about keywords, search terms, ranking on Google, or translating a listing for another language or country.
---

# SEO keywords and translation

1. Identify the product (`product_lookup` / `product_details`) or, for a market-level request, a representative set via `show_products`.
2. Ask for the target market and language if unclear.
3. Call `propose_keywords`; show the keyword card (primary, secondary, long-tail) and cost. Confirm, then `apply` to save them to the product.
4. If a translation is requested, call `propose_translate` with the target language; show the card, confirm, then `apply`.
5. Offer `propose_publish` to push the updated listing to the store, again only after confirmation.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
