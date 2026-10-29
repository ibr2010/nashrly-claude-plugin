# Submitting the Nashrly plugin to Anthropic's directory

Sources: https://claude.com/docs/plugins/build, https://claude.com/docs/plugins/pre-submission-checklist, https://claude.com/docs/plugins/submit

## 1. Validate locally

```bash
cd /home/hp/Projects/nashrly-claude-plugin
claude plugin validate ./        # expect: ✔ Validation passed
claude --plugin-dir ./           # optional: try the skills, run /mcp and sign in
```

## 2. Create the public GitHub repo (founder)

```bash
cd /home/hp/Projects/nashrly-claude-plugin
gh auth status || gh auth login
gh repo create nashrly-claude-plugin --public --source . --push --description "Nashrly plugin for Claude: store audits, product optimization, social posts, SEO, Arabic localization"
```

Then replace `<github-owner>` in README.md with your GitHub username/org, raise nothing else, commit and `git push`.

The repo may stay private during review (requires the Claude GitHub App installed on it), but must be public before the listing goes live.

## 3. Connect GitHub on claude.ai

1. Sign in to claude.ai in the organization you will submit from (Pro/Max, or Owner on Team/Enterprise).
2. Open https://claude.ai/directory/manage. When the portal shows "GitHub isn't connected for this Claude organization", click **Connect GitHub** and authorize the account that can push to `nashrly-claude-plugin`.
3. (Private repo only) install the Claude GitHub App on the repository when prompted.

## 4. Portal fields: Submit new > Plugin bundle

### Source
- **Repository:** `<github-owner>/nashrly-claude-plugin`
- **Plugin path:** leave empty (plugin is at repo root)
- **Branch or tag:** leave empty (default branch `main`)
- Click **Validate**; fix anything marked Blocking, push, **Re-validate**.

### Listing details (read from plugin.json + README)
- Name: `nashrly` / Display name: Nashrly
- Description: from plugin.json
- Homepage: https://anshrly.7okm.com/en/claude
- Privacy policy: https://anshrly.7okm.com/en/privacy
- Icon: `.claude-plugin/icon.png` (512x512; becomes the listing icon only on first save, so make sure it is final)
- License: MIT

### Data handling (suggested answers)
- **Reads or stores personal data?** Yes, reads: the merchant's Nashrly account info (name, email, plan, credit balance), product catalog, and connected store/social status via the Nashrly connector. The plugin files store nothing; data is held by Nashrly under its privacy policy.
- **Sends data to services other than its declared connectors?** No. Only `https://anshrly.7okm.com/mcp` (declared in `.mcp.json`).
- **Data retention:** Plugin retains nothing. Nashrly retains account and product data for the life of the account and deletes it on account deletion, as stated in https://anshrly.7okm.com/en/privacy (confirm the policy text matches before submitting).
- **Intended for people under 18?** No (business tool for merchants).

### Compliance
- Contact email: hello@7okm.com
- Tick all four acknowledgements (compliance with the Anthropic Software Directory Terms and Directory Policy, accuracy of the submission, and the remaining acknowledgements shown in the portal). Read each before ticking.

### Review and submit
- **How new versions reach the directory:** GitHub push webhook (default). Click **Set up push updates** afterwards (needs repo admin).
- Auto-publish toggle: leave off for the first release.
- Click **Submit for review**.

## 5. Also submit the connector

The docs recommend submitting the remote server itself as an **MCP connector** (Submit new > MCP connector, URL `https://anshrly.7okm.com/mcp`) if not already listed, so plugin and connector share one set of tools.

## 6. Releasing updates

Bump `version` in `.claude-plugin/plugin.json`, commit, push to `main`. The directory rescans; press **Publish** when the version passes.
