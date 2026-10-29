---
name: launch-product
description: Launch a new product from a photo. Use when the merchant shares a product photo or says they have a new product to add, list, or launch on their store and social media.
---

# Launch a product

1. Get the photo (attachment or URL). Call `propose_create_from_photo`; show the drafted title, description, price fields and cost. Confirm, then `apply`.
2. Ask for any missing facts (price, sizes, materials) rather than guessing. Run `propose_claims` to review inferred claims.
3. Call `propose_optimize` for SEO polish if the merchant wants it; confirm, then `apply`.
4. Create it in the store: `propose_shopify_create` (or `propose_publish` for an existing product); confirm, then `apply`.
5. Announce it: check `social_status`, call `propose_post` using the real product photo, then `propose_schedule` for a time the merchant picks. Confirm each card before `apply`.
6. If no platform is connected, offer `offer_download` for the image plus a ready-to-paste caption, or `propose_connect_platform`.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
