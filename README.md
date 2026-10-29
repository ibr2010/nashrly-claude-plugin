# Nashrly for Claude

Nashrly is an AI assistant for e-commerce merchants. This plugin bundles the Nashrly remote MCP connector with workflow skills so Claude can run multi-step store tasks: auditing your catalog, optimizing product listings, launching new products from a photo, planning social posts, finding SEO keywords, and localizing for Arabic-speaking MENA markets. It works in Arabic and English and follows the language you write in.

## What's included

| Skill | Use it when |
|---|---|
| `store-audit` | You want a weekly health check and a prioritized, costed action plan |
| `optimize-product` | You want one product optimized, its guessed claims reviewed, and published |
| `bulk-improve-weakest` | You want your N weakest products improved one by one with a running cost total |
| `launch-product` | You have a photo of a new product to list and announce |
| `social-week` | You want a week of posts planned and scheduled |
| `seo-keywords` | You need keywords or a translation for a product or market |
| `arabic-market` | You are selling to Saudi Arabia, the UAE, Egypt or other MENA markets |

Commands (Claude Code and Cowork): `/nashrly:audit`, `/nashrly:optimize [product]`, `/nashrly:social-week`.

## How it behaves

Every change is proposed as a card showing what will change and its credit cost. Claude applies it only after you confirm. Nothing is spent, published to your store, or posted to social media without your explicit approval. Changes can be undone. The connector does not generate images inside the chat; for AI product photos Claude gives you a link to the right page in the Nashrly app.

## Requirements

- A Nashrly account (sign up at https://anshrly.7okm.com). Some actions use Nashrly credits.
- Optional: a connected store (e.g. Shopify) and social accounts inside Nashrly.

## Install

**Claude Code**

```
/plugin marketplace add ibr2010/nashrly-claude-plugin
/plugin install nashrly@nashrly-claude-plugin
```

Or test locally: `claude --plugin-dir ./nashrly-claude-plugin`. Then run `/mcp` and sign in to Nashrly.

**claude.ai and Cowork**

Open Customize > Plugins, find Nashrly in the directory (or upload this folder as a zip), then open the plugin's Connectors tab and connect Nashrly. You sign in through Nashrly's OAuth page.

## Example prompts

- "Audit my store and tell me what to fix first."
- "Optimize my best-selling hoodie and publish it to Shopify."
- "Improve my 5 weakest products, ask me before each one."
- "Here's a photo of a new mug. Launch it and post it on Instagram on Friday."
- "Plan this week's posts."
- "راجع متجري هذا الأسبوع واقترح خطة"
- "ترجم منتجاتي للعربي وجهّز حملة لرمضان"

## Data and privacy

The plugin itself contains only instructions and stores nothing. It connects to one server: `https://anshrly.7okm.com/mcp`, operated by Nashrly. Through it, Claude reads your Nashrly account, product catalog and social connection status, and sends the changes you approve (product text, keywords, translations, post captions and schedules) to your Nashrly account, which may then push them to your connected store or social platforms at your request. No other destinations are contacted. See the privacy policy: https://anshrly.7okm.com/en/privacy

## Support

hello@7okm.com · https://anshrly.7okm.com/en/claude

## License

MIT, see [LICENSE](LICENSE).
