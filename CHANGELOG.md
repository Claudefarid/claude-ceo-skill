# Changelog

All notable changes to CEO Assistant are documented here.

---

## [2.0.0] — 2026-06-21

### Added
- **Any-CEO repositioning** — skill now adapts to CEO background (technical, sales, finance, first-time founder, general executive)
- `ceo_background` field added to `company-profile.md`
- CEO background question (Q8) added to onboarding flow in `setup.md`
- Output standards updated: explanation depth adjusts per background automatically
- **Fundraising Playbook domain** — new `references/fundraising.md` covering raise readiness, investor targeting, pitch structure, term sheet negotiation, and due diligence prep
- **SEO/AEO/GEO optimization** — README rewritten with outcome-based headings matching real search queries
- `llms.txt` added — structured for AI engine citation (Perplexity, ChatGPT, Google AI Overviews, Bing Copilot)
- GitHub repository topics expanded: `startup`, `founder`, `weekly-digest`, `hubspot-integration`, `chief-of-staff`, `saas`
- GitHub repository moved to canonical URL: `https://github.com/Claudefarid/claude-ceo-skill`

### Changed
- README restructured with 10 outcome-based how-to sections
- FAQ expanded from 8 to 10 entries covering comparison with ChatGPT and no-integration usage
- `llms.txt` expanded from 53 to 120+ lines with full Q&A pairs for AI engine indexing

---

## [1.5.0] — 2026-06-21

### Added
- **Live data integrations across all 21 domains** — previously only 4 domains had integration logic
- Integration sections added to: Customer Success, HR, Operations, Product, Investor Relations, Meetings, Communications, Strategy, Hiring
- **`references/connect.md`** — in-skill setup wizard for 20 business tools with step-by-step bash commands
- **`references/prompts.md`** — 60+ example prompts organized by domain (removes blank-page problem for new users)
- Integration status board — say "what's connected" to see all tools with ✅ ⚠️ status
- Troubleshooting guide for common setup errors

### Tools added with full setup guides
HubSpot, Google Analytics 4, QuickBooks, Xero, Stripe, Salesforce, Pipedrive, Mailchimp, ActiveCampaign, Google Ads, PostHog, Mixpanel, Intercom, Zendesk, Google Sheets, Google Drive, Gmail, Notion, Slack, Shopify

---

## [1.4.0] — 2026-06-21

### Added
- **`references/ma.md`** — M&A and exit planning: exit options, valuation basics, M&A process, LOI negotiation, due diligence checklist
- **`references/international.md`** — International expansion: 5 entry strategies, regional guides (South Asia, Southeast Asia, Middle East, UK/Europe), EOR guide, pricing strategy
- **`references/competitive.md`** — Competitive intelligence: competitor profiling, battle cards, win/loss analysis
- **`references/hiring.md`** — Hiring playbook: job descriptions, interview guides, offer negotiation, compensation benchmarks
- **`references/weekly-digest.md`** — Full weekly business digest format with auto-pull from connected tools
- 4 new M&A red flag triggers added to SKILL.md
- Routing table expanded to 23 entries

---

## [1.3.0] — 2026-06-20

### Added
- **Regional benchmarks** — `references/benchmarks.md` expanded with South Asia, Southeast Asia, Middle East, UK & Europe
- Each region includes: salary benchmarks, growth rates, gross margin, churn rates
- Fallback protocol for missing specialist skills

---

## [1.2.0] — 2026-06-20

### Added
- **`references/integrations.md`** — master integration logic: detect MCPs → pull data by domain → fallback
- Integration data pull logic for: QuickBooks, HubSpot, GA4, Salesforce, Mixpanel, MS Clarity, Google Drive, Gmail
- Step 0 added to SKILL.md: detect live integrations before any other step
- `connected_tools`, `primary_region`, `international_markets`, `last_updated` fields added to `company-profile.md`

---

## [1.1.0] — 2026-06-20

### Added
- **Company memory** — `company-profile.md` template with 9-question guided onboarding
- **`references/setup.md`** — memory persistence rules, auto-update logic from reports, data integration detection
- Auto-update rules: metric fields updated silently when CEO shares any report
- Profile health check: surfaces reminder when profile data is 30+ days old
- Insufficient data protocol: asks for minimum 3 fields rather than failing

---

## [1.0.0] — 2026-06-19

### Initial release
- SKILL.md with 5-step framework: integration detection, profile load, red flag check, domain routing, benchmark display
- 25+ red flag triggers across finance, sales, customer success, HR, operations, marketing
- 19 business domains with dedicated reference files
- Specialist skill routing to 11 external skills
- Industry benchmarks for North America (SaaS, services, ecommerce, marketplace)

### Reference files included
`finance.md` · `sales.md` · `marketing.md` · `hr.md` · `operations.md` · `product.md` · `customer-success.md` · `investor.md` · `meetings.md` · `communications.md` · `strategy.md` · `legal.md` · `pr.md` · `dashboard.md` · `summarize.md`
