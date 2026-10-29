---
name: store-audit
description: Weekly health check of a Nashrly store. Use when the merchant asks how their store is doing, wants an audit, a weekly review, or asks what to fix first (e.g. "audit my store", "راجع متجري").
---

# Store audit

1. Call `capabilities` and `account` to learn the connected store, plan, and credit balance.
2. Call `catalog_summary` for scores and gaps (missing descriptions, weak titles, missing SEO, missing photos, untranslated products).
3. Call `show_products` sorted by weakest score (about 10) and present them as cards.
4. Optionally call `performance` and `social_status` for traffic and connected platforms.
5. Produce a prioritized action plan: for each item give the problem, the affected products, the Nashrly action (optimize, claims review, keywords, translate, post), and the estimated credit cost. Total the cost and compare it with the balance.
6. Ask which items to start. Hand off to the optimize-product or bulk-improve-weakest workflow; do not apply anything from the audit itself.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
