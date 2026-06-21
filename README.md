# CEO Assistant — AI Chief of Staff for Claude Code

**An AI-powered Chief of Staff for any CEO.** Connects to HubSpot, Stripe, GA4, QuickBooks, Salesforce, Notion, Slack, and 14 more tools. Covers 21 business domains. Alerts on 25+ red flags. Adapts to your background — technical founder, first-time CEO, or seasoned executive.

Install in Claude Code. Ask in plain language. Get executive-ready answers in seconds.

```bash
claude skills install https://github.com/Claudefarid/claude-ceo-skill
```

---

## What is the CEO Assistant Claude Skill?

The CEO Assistant is a [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code) that acts as a persistent AI Chief of Staff. It remembers your company — metrics, goals, team, stage — and uses that context in every answer. It connects to your live business tools so you never have to paste a spreadsheet again.

Unlike generic AI chatbots, the CEO Assistant:
- Knows your company by name and uses your real numbers
- Shows industry benchmarks alongside every metric
- Proactively alerts you to problems before you ask
- Walks you through connecting your tools step by step
- Adapts how it explains things based on your professional background

---

## Who is this for?

- **Technical founders** who know their product but need help with finance, HR, and investor relations
- **First-time CEOs** who want plain-language explanations of P&L, burn rate, and board prep
- **Operators and career executives** who want faster access to benchmarked business intelligence
- **Sales-background CEOs** who want every answer framed around revenue impact
- **Any CEO** running a startup, scaleup, or growth-stage company

---

## Install the CEO Assistant Skill

### One-command install
```bash
claude skills install https://github.com/Claudefarid/claude-ceo-skill
```

### Manual install
```bash
cp -r ceo-assistant ~/.claude/skills/
```

Restart Claude Code. The skill activates automatically on any CEO-related request.

---

## Key Features

### 1. Company memory that persists across sessions
Set up once in 2 minutes. The skill remembers your company name, revenue stage, key metrics, goals, team, and region. Every answer uses your real context — not generic advice.

### 2. Live data from 20 business tools
Connect HubSpot, GA4, Stripe, QuickBooks, Salesforce, Pipedrive, Notion, Slack, Zendesk, PostHog, and more. The skill pulls live data automatically — no copy-pasting reports.

### 3. Proactive red flag alerts
25+ danger patterns monitored across finance, sales, marketing, HR, operations, and M&A. Problems surface at the top of every response before you have to ask.

### 4. Industry benchmarks on every metric
Every number you share gets a benchmark: your number vs what good looks like for your stage and region. Always shows ✅ ⚠️ 🔴 status.

### 5. 21 business domains in one skill
Finance · Sales · Marketing · Customer Success · HR · Operations · Product · Investor Relations · Meetings · Communications · Strategy & OKRs · Legal · PR · Hiring · Competitive Intelligence · Weekly Digest · M&A · Exit Planning · International Expansion · Dashboard & KPIs · Report Summarization

### 6. Adapts to your CEO background
Tell the skill your background once — technical, sales, finance, first-time founder, or general executive. It adjusts explanation depth in every response automatically.

### 7. Regional benchmarks for global CEOs
Built-in benchmarks for North America, South Asia (Bangladesh, India, Pakistan), Southeast Asia, Middle East (UAE, Saudi Arabia), and UK & Europe.

### 8. In-skill integration setup wizard
Say "connect my HubSpot" or "set up GA4" — the skill walks you through the full connection process step by step, inside the conversation.

---

## What can I ask the CEO Assistant?

```
give me my weekly business digest
explain this P&L report to me
how is sales tracking this quarter?
which customers are most at risk?
help me hire a VP of Sales
prep me for the board meeting
we received an acquisition offer — what do I do?
connect my HubSpot
how do we expand to the UAE?
write an all-hands about the restructure
what's our runway and should I be worried?
who are our biggest competitors and how do we beat them?
```

---

## Live Data Integrations

| Category | Connected Tools |
|----------|----------------|
| **Finance** | QuickBooks · Xero · Stripe |
| **CRM & Sales** | HubSpot · Salesforce · Pipedrive |
| **Marketing** | Google Analytics 4 · Google Ads · Mailchimp · ActiveCampaign |
| **Product Analytics** | PostHog · Mixpanel |
| **Customer Success** | Intercom · Zendesk |
| **Productivity** | Google Sheets · Google Drive · Gmail · Notion · Slack |
| **E-commerce** | Shopify |

Each integration has a step-by-step setup guide built into the skill. No external documentation needed.

---

## Example — Weekly Business Digest (with live data)

```
Acme Inc — Weekly Business Digest
Week ending June 21, 2026
Data: HubSpot ✅  GA4 ✅  QuickBooks ✅  Stripe ✅

🔴 ALERT — Pipeline Insufficient
Open pipeline ($380K) is below 2x your monthly target.
Action: Add 5 qualified opportunities before Friday.

Finance
MRR: $85,000 (+8% MoM) ✅ | Cash: $1.2M | Runway: 14 months ⚠️
Benchmark (Growth SaaS): Runway >18mo = safe. Start planning next raise.

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

## Example — Finance Report Explanation

```
CEO: explain this month's P&L

Bottom line: Revenue grew 12% but net loss widened —
operating expenses scaled faster than revenue.

Revenue:       $85,000  (+12%) ✅
Gross Margin:  71%             ✅  Benchmark (Growth SaaS): >70% = excellent
Operating Exp: $94,000  (+28%) 🔴 Growing 16% faster than revenue
Net Loss:     ($33,650)        🔴

What needs attention:
OpEx jumped $21K — driven by 3 new hires in May.
If revenue doesn't catch up within 60 days, runway
shortens below 12 months.

Action: Freeze non-essential hiring. Review top 3
expense lines with CFO by end of week.
```

---

## Frequently Asked Questions

### What is a Claude Code skill?
A Claude Code skill is a pre-built instruction set that gives Claude specialized expertise in a domain. Skills are installed locally and activate automatically when you ask a relevant question. The CEO Assistant skill turns Claude into a persistent AI Chief of Staff with memory of your company.

### Do I need to pay for this skill?
No. The skill itself is free and open source. You need a Claude Code subscription (Anthropic) to use it.

### Does the skill work without integrations?
Yes. Without integrations, you paste reports and the skill analyzes them. With integrations connected, data is pulled automatically.

### How does the skill remember my company?
During first setup, the skill asks 9 questions and saves your answers to a local `company-profile.md` file. This file is read at the start of every conversation. You can update it anytime by saying "update my company profile".

### What CEO backgrounds does the skill support?
Technical/Engineering · Sales/Commercial · Finance/Operator · First-time founder · General executive. The skill adapts its explanation depth based on your background.

### Which integrations are easiest to set up?
HubSpot and Google Analytics 4 are the fastest — both take under 10 minutes. Stripe is also straightforward. QuickBooks and Salesforce take 15–20 minutes.

### Is my data stored anywhere?
No. The skill runs locally in Claude Code. Your company profile is stored in a local file on your machine. Data pulled from integrations is processed in your Claude session and not stored externally.

### Can I use this for my team — not just the CEO?
Yes. Anyone on the leadership team can install and use the skill. Each user maintains their own company profile.

---

## Red Flag Alerts — What Gets Monitored

| Domain | Alert Triggers |
|--------|---------------|
| Finance | Runway < 6 months · Burn escalating >20% MoM · Gross margin below benchmark · Revenue declining 2+ months |
| Sales | Team quota attainment < 60% · Pipeline < 2x target · Win rate < 20% · No deals closed in 30 days |
| Customer Success | Monthly churn > 3% · NRR < 90% · NPS < 20 · Key account (>20% ARR) at risk |
| HR | Annual attrition > 25% · Critical role open 60+ days · Multiple departures same team |
| Operations | SLA compliance < 90% · Critical bug open 48+ hours · Vendor concentration > 50% |
| Marketing | CAC exceeds LTV · Paid ROAS < 1x · Lead volume declining 3+ months |
| M&A | LOI exclusivity > 60 days · Earn-out tied to metrics CEO won't control · Revenue concentration risk |

---

## Skill Structure

```
claude-ceo-skill/
├── SKILL.md                     ← Routing, red flags, output rules
├── company-profile.md           ← Your company context (local, auto-maintained)
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

## Requirements

- Claude Code (CLI or desktop app)
- Claude subscription (Anthropic)
- Integrations are optional — the skill works without them

## License

MIT — free to use, fork, and distribute.

---

*Built for founders and executives who want AI that knows their business, not just their question.*
