---
name: social-week
description: Plan and schedule a week of social media posts from store products. Use when the merchant asks for a content calendar, weekly posts, or what to post this week on Instagram, Facebook, or other platforms.
---

# Social week

1. Call `social_status` to see which platforms are connected and allowed for auto-posting.
2. Call `content_planning` (and `calendar` for upcoming occasions) to pick about 5 to 7 products and angles for the week. Present the plan as a table (day, product, angle, platform) and ask for changes.
3. For each approved slot, call `propose_post` using the product's real photos. Show the caption and image card and cost; confirm, then `apply`.
4. Call `propose_schedule` with the agreed day and time; confirm, then `apply`.
5. Fallback: where auto-posting is unavailable for a platform, give the caption as text and call `offer_download` for the image so the merchant can post manually, or offer `propose_connect_platform`.
6. End with the final schedule and how to cancel a slot with `propose_cancel_schedule`.

## Ground rules (always)

- Reply in the merchant's language: Arabic if they write Arabic, English if they write English. Keep product copy in the language the merchant asks for.
- Every `propose_*` tool returns a card. Show the card, state its credit cost, and wait for the merchant to confirm before calling `apply`. Never spend credits, publish to the store, or post to social media without explicit confirmation.
- Never invent product facts (materials, sizes, certifications). If a claim is guessed, flag it and let the merchant confirm or remove it.
- This connector does not generate images in chat. When the merchant wants AI product photos, call `offer_link` to open the right page in the Nashrly app instead of promising an image.
- If a tool reports insufficient credits, show the cost and offer `propose_top_up`; do not retry silently.
