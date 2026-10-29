---
name: arabic-market
description: Localize a store or products for Arabic-speaking MENA customers. Use when the merchant targets Saudi Arabia, UAE, Egypt, the Gulf, or other Arab markets, or asks for Arabic copy or occasion campaigns (Ramadan, Eid, National Day, White Friday).
---

# Arabic / MENA localization

1. Call `catalog_summary` to find products without Arabic copy.
2. For each chosen product, call `propose_translate` to Arabic (or `propose_optimize` in Arabic) and review the card for natural Gulf/Levantine/Egyptian tone as the merchant prefers; confirm, then `apply`.
3. Call `propose_keywords` for Arabic search terms in the target country.
4. Call `calendar` for upcoming regional occasions and propose a short campaign: which products, when, and post angles. Use `propose_post` / `propose_schedule` per post, each confirmed.
5. Respect cultural norms in copy and imagery; never promise discounts or prices the merchant has not set.
6. Offer `propose_publish` to push Arabic listings to the store after confirmation.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
