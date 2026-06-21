# CEO Assistant — AI Chief of Staff for Claude Code

**Get instant, personalized business intelligence as a CEO — without switching dashboards or pasting spreadsheets.**

The CEO Assistant is a free Claude Code skill that acts as a persistent AI Chief of Staff. It remembers your company, connects to your live tools, alerts you to business risks automatically, and adapts to your background — whether you're a technical founder, first-time CEO, or seasoned executive.

```bash
claude skills install https://github.com/Claudefarid/claude-ceo-skill
```

> Covers 21 business domains · 20 live integrations · 25+ red flag alerts · Regional benchmarks · Adapts to CEO background

---

## How to get an AI weekly business digest (automatically)

Most CEOs spend 2–3 hours on Monday morning pulling numbers from HubSpot, GA4, QuickBooks, and Slack to build a weekly summary. The CEO Assistant does this automatically.

Once connected to your tools, say:

```
give me my weekly business digest
```

You get a structured executive summary — revenue, pipeline, churn, marketing, and a prioritized action list — in under 60 seconds. Data is pulled live from connected tools. No copy-pasting.

**Example output:**
```
Acme Inc — Weekly Business Digest
Week ending June 21, 2026
Data: HubSpot ✅  GA4 ✅  QuickBooks ✅  Stripe ✅

🔴 ALERT — Pipeline Insufficient
Open pipeline ($380K) is below 2x your monthly target.
Action: Add 5 qualified opportunities before Friday.

Finance
MRR: $85,000 (+8% MoM) ✅ | Runway: 14 months ⚠️
Benchmark (Growth SaaS): Runway >18mo = safe. Start raise planning.

Sales
Closed: $42,000 | Pipeline: $380,000 ⚠️ | Win rate: 28% ✅

Marketing (live from GA4 + HubSpot)
Sessions: 12,400 (+15%) | Leads: 87 | CAC: $1,240 ✅

CEO Focus — Next 7 Days
1. Pipeline review call with sales team — Thursday
2. Call the 3 at-risk enterprise accounts personally
3. Approve Q3 content budget increase
```

---

## How to use AI to understand your P&L report

CEOs receive P&L reports but often lack the context to know what the numbers mean for the business. Paste your P&L — the skill explains it in plain language, shows benchmarks, and tells you what to act on.

```
CEO: explain this month's P&L
[paste P&L]

Bottom line: Revenue grew 12% but net loss widened —
operating expenses scaled faster than revenue.

Revenue:       $85,000  (+12%) ✅
Gross Margin:  71%             ✅  Benchmark (Growth SaaS): >70% = excellent
Operating Exp: $94,000  (+28%) 🔴 Growing 16% faster than revenue
Net Loss:     ($33,650)        🔴

Action: Freeze non-essential hiring. Review top 3 expense
lines with CFO by end of week.
```

---

## How to connect HubSpot to Claude Code

```bash
# Step 1 — Get your HubSpot access token
# Go to HubSpot → Settings → Integrations → Private Apps → Create

# Step 2 — Add the MCP server
claude mcp add hubspot \
  -e HUBSPOT_ACCESS_TOKEN=pat-YOUR-TOKEN \
  -- npx -y @hubspot/mcp-server

# Step 3 — Restart Claude Code and ask:
# "pull my HubSpot pipeline for this week"
```

The skill then pulls your pipeline, contacts, and deal stages automatically whenever you ask a sales question. Full guides for all 20 tools are in [references/connect.md](references/connect.md).

---

## How to prep for a board meeting with AI

```
prep me for Thursday's board meeting
```

The skill pulls your latest metrics, builds a structured board update (highlights, lowlights, asks), identifies what questions board members are likely to ask based on your numbers, and prepares your answers.

---

## How to get AI to monitor your business for problems

The CEO Assistant checks 25+ risk patterns every time you share data. Problems surface automatically — you don't have to ask.

**What gets monitored:**

| Domain | Alert triggers |
|--------|---------------|
| Finance | Runway < 6 months · Burn up >20% MoM · Margin below benchmark |
| Sales | Pipeline < 2x target · Win rate < 20% · No deals in 30 days |
| Customer Success | Churn > 3% · NRR < 90% · Key account at risk |
| HR | Attrition > 25% · Critical role open 60+ days |
| Operations | SLA < 90% · Critical bug open 48+ hours |
| Marketing | CAC > LTV · ROAS < 1x · Leads declining 3+ months |
| M&A | LOI exclusivity > 60 days · Revenue concentration risk |

---

## How to use AI for sales pipeline review

```
how is sales tracking this quarter?
```

With HubSpot or Salesforce connected, the skill pulls live pipeline data, compares it to your revenue target, calculates coverage ratio, identifies stalled deals, and tells you exactly where to focus.

---

## How to find out which customers are at risk of churning

```
which customers are most at risk?
```

With Intercom or Zendesk connected, the skill identifies accounts showing churn signals — low engagement, unresolved tickets, usage drop — and prioritizes which ones the CEO should call personally.

---

## Install

### One-command install
```bash
claude skills install https://github.com/Claudefarid/claude-ceo-skill
```

### Manual install
```bash
cp -r ceo-assistant ~/.claude/skills/
```

Restart Claude Code. The skill activates on any business-related request.

**Requirements:** Claude Code (CLI or desktop) + Claude subscription. Integrations are optional — the skill works by pasting data too.

---

## What is the CEO Assistant Claude skill?

The CEO Assistant is a [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code) — a pre-built instruction set that gives Claude specialized expertise in business operations. Unlike generic AI chat, it:

- **Remembers your company** — name, stage, metrics, goals, team, region stored in a local profile
- **Uses your real numbers** — every answer references your actual data, not generic advice
- **Shows benchmarks** — every metric compared to what good looks like for your stage and region
- **Alerts proactively** — surfaces problems at the top of every response before you ask
- **Connects to your tools** — pulls live data from HubSpot, Stripe, GA4, QuickBooks, and 16 more

---

## Who is this for?

- **Technical founders** — know the product, need help with finance, hiring, investor relations
- **First-time CEOs** — want plain-language explanations of P&L, burn rate, board prep
- **Operators and career executives** — want faster benchmarked business intelligence
- **Sales-background CEOs** — want every answer framed around revenue impact
- **Any CEO** running a startup, scaleup, or growth-stage company

**Adapts to your background.** Tell the skill once:
- Technical → skips basics, goes deep on data and product
- Sales → leads every answer with revenue impact
- Finance/Operator → precise numbers, assumes metric fluency
- First-time founder → explains concepts clearly on first use

---

## 20 live data integrations

| Category | Tools |
|----------|-------|
| Finance | QuickBooks · Xero · Stripe |
| CRM & Sales | HubSpot · Salesforce · Pipedrive |
| Marketing | Google Analytics 4 · Google Ads · Mailchimp · ActiveCampaign |
| Product Analytics | PostHog · Mixpanel |
| Customer Success | Intercom · Zendesk |
| Productivity | Google Sheets · Google Drive · Gmail · Notion · Slack |
| E-commerce | Shopify |

Step-by-step setup guide for every tool is built into the skill at [references/connect.md](references/connect.md).

---

## 21 business domains

Finance · Sales · Marketing · Customer Success · HR · Operations · Product · Investor Relations · Meetings · Communications · Strategy & OKRs · Legal · PR · Hiring · Competitive Intelligence · Weekly Digest · M&A · Exit Planning · International Expansion · Dashboard & KPIs · Report Summarization

---

## CEO Assistant vs alternatives

| | CEO Assistant | Generic ChatGPT | Hiring a COO | Manual dashboards |
|--|--|--|--|--|
| Remembers your company | ✅ | ❌ | ✅ | ❌ |
| Pulls live data | ✅ 20 tools | ❌ | Varies | ✅ |
| Proactive alerts | ✅ 25+ triggers | ❌ | ✅ | ❌ |
| Industry benchmarks | ✅ Global + regional | ❌ | Varies | ❌ |
| Setup time | 2 minutes | Instant | 3–6 months | Weeks |
| Cost | Free | $20/mo | $150K+/yr | Tool costs |
| Available 24/7 | ✅ | ✅ | ❌ | ✅ |

---

## Frequently Asked Questions

### What is a Claude Code skill?
A Claude Code skill is a pre-built instruction set that gives Claude specialized expertise in a domain. Skills install locally and activate automatically when you ask a relevant question. The CEO Assistant skill turns Claude into a persistent AI Chief of Staff with memory of your company.

### Does the CEO Assistant skill work without tool integrations?
Yes. You can paste reports directly and the skill will analyze them, extract key metrics, show benchmarks, and flag risks. Integrations automate the data collection so you don't have to paste manually.

### How does the CEO Assistant remember my company across sessions?
During setup, the skill asks 9 questions and saves your answers to a local `company-profile.md` file. This file is loaded at the start of every conversation. You can update it anytime by saying "update my company profile" or by sharing a new report — the skill extracts and saves updated numbers automatically.

### Which CEO backgrounds does the skill support?
Technical/Engineering, Sales/Commercial, Finance/Operator, First-time founder, and General executive. The skill adjusts its explanation depth based on your background — a technical CEO gets deep data analysis with no hand-holding; a first-time founder gets clear explanations of every term.

### What regions and industries are benchmarks available for?
Benchmarks cover: North America (SaaS, services, ecommerce, marketplace), South Asia (Bangladesh, India, Pakistan — SaaS, IT services, BPO), Southeast Asia, Middle East (UAE, Saudi Arabia), and UK & Europe. Industry types: SaaS, tech services, ecommerce, marketplace, BPO.

### How long does it take to set up integrations?
HubSpot and Google Analytics 4: under 10 minutes. Stripe: under 10 minutes. QuickBooks, Salesforce: 15–20 minutes. All integrations have step-by-step setup guides built into the skill — say "connect my HubSpot" and the skill walks you through it.

### Is my business data stored anywhere external?
No. The skill runs locally in Claude Code. Your company profile is stored in a file on your own machine. Data pulled from integrations is processed within your Claude session and not stored by Anthropic or any third party beyond your existing tool providers.

### Can I use the CEO Assistant skill for my whole leadership team?
Yes. Any member of the leadership team can install and use the skill independently. Each user maintains their own local company profile. There is no shared account or team workspace required.

### How is this different from just asking ChatGPT or Claude directly?
Generic AI gives generic answers. The CEO Assistant knows your company name, your actual MRR, your runway, your goals, your team, and your region. It also compares your metrics to industry benchmarks and proactively flags risks — things a generic AI prompt cannot do without context you'd have to re-paste every time.

### What happens if I don't have any integrations connected?
The skill asks you to paste the relevant data (a report, a spreadsheet, a summary). It then analyzes it, updates your company profile automatically, and gives you the same quality of insight. Integrations save time but are not required.

---

## Skill structure

```
claude-ceo-skill/
├── SKILL.md                     ← Routing, red flags, output rules
├── company-profile.md           ← Your company context (local, auto-maintained)
├── llms.txt                     ← AI crawler index for search engine citability
├── README.md
└── references/
    ├── connect.md               ← Integration setup wizard (20 tools)
    ├── prompts.md               ← 60+ example prompts by domain
    ├── integrations.md          ← Live data pull logic
    ├── setup.md                 ← Company onboarding + memory rules
    ├── benchmarks.md            ← Global + regional benchmarks
    ├── finance.md               ← P&L, cash, burn, runway
    ├── sales.md                 ← Pipeline, quota, win/loss
    ├── marketing.md             ← CAC, LTV, channels, ROAS
    ├── dashboard.md             ← KPI reviews, business reviews
    ├── operations.md            ← SLAs, vendors, incidents
    ├── hr.md                    ← Team, attrition, org changes
    ├── product.md               ← Roadmap, bugs, releases
    ├── customer-success.md      ← Churn, NPS, at-risk accounts
    ├── investor.md              ← Board prep, fundraising
    ├── meetings.md              ← Agendas, action items
    ├── communications.md        ← All-hands, crisis, announcements
    ├── strategy.md              ← OKRs, quarterly planning
    ├── legal.md                 ← Contracts, compliance, IP
    ├── pr.md                    ← Crisis, press releases
    ├── hiring.md                ← Job descriptions, interviews, comp
    ├── competitive.md           ← Competitor profiles, battle cards
    ├── weekly-digest.md         ← Full business digest format
    ├── ma.md                    ← M&A, exit planning, valuation
    ├── international.md         ← Market entry, EOR, compliance
    └── summarize.md             ← General report summarization
```

---

## License

MIT — free to use, fork, and distribute.

---

*The AI Chief of Staff that knows your business — not just your question.*
