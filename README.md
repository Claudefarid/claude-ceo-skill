# CEO Assistant — Claude Skill

A Claude skill built for non-technical CEOs. Ask in plain language — get personalized, executive-ready answers across every major business domain. Connects to your live tools (HubSpot, GA4, QuickBooks) for automatic data pulling. No more pasting spreadsheets.

---

## Install

```bash
claude skills install https://github.com/digitalmarketerswadhin-droid/ceo-assistant
```

Restart Claude Code. The skill activates automatically.

---

## What it does

Ask anything — the skill handles it:

```
give me my weekly digest
how is sales tracking this quarter?
explain this P&L report
we have a critical bug — what should I know?
prep me for the board meeting
help me hire a VP of Sales
who are our biggest competitors and how do we beat them?
we received an acquisition offer — what do I do first?
we want to expand to the UAE — where do I start?
connect my HubSpot
```

---

## Example output — Weekly Digest (with HubSpot + GA4 connected)

```
Acme Inc — Weekly Business Digest
Week ending June 21, 2026 | Data: HubSpot ✅ GA4 ✅ QuickBooks ✅

🔴 ALERT — Pipeline Insufficient
Open pipeline ($380K) is below 2x your monthly target ($500K).
Recommended action: Sales team to add 5 qualified opportunities by Friday.

Executive Summary
Revenue is growing but pipeline is thin going into Q3. Marketing is
performing well — CAC improved 18% this month. The critical focus
for the next 7 days is pipeline building, not closing.

Finance
MRR: $85,000 (+8% MoM) ✅ | Cash: $1.2M | Runway: 14 months ⚠️
Burn: $86K/mo | Gross Margin: 71% ✅

Sales
Closed this week: $42,000 | Pipeline: $380,000 ⚠️
Win rate: 28% ✅ | Avg deal: $14,200 | Quota attainment: 84% ✅

Marketing (live from GA4 + HubSpot)
Sessions: 12,400 (+15%) | Leads: 87 (+22%) | CAC: $1,240 ✅
Top channel: Organic search (42% of leads)

CEO Priorities — Next 7 Days
1. Pipeline review call with sales team — Thursday
2. Call the 3 at-risk enterprise accounts personally
3. Approve Q3 marketing budget increase for organic content
```

---

## Example output — Finance Report

```
User: explain this month's P&L

Finance Summary — May 2026

Bottom line: Revenue grew 12% but net loss widened — operating
expenses scaled faster than revenue. Not a crisis, but needs attention.

Key numbers:
Revenue:       $85,000   (+12% vs last month) ✅
Gross Profit:  $60,350   (71% margin)         ✅
Operating Exp: $94,000   (+28% vs last month) 🔴
Net Loss:     ($33,650)  (worse than -$24K)   🔴
Cash on Hand:  $1.2M     | Runway: 14 months  ⚠️

Benchmark (Growth stage SaaS): Gross margin >70% is excellent.
Operating expense growth outpacing revenue growth by 16% is a warning sign.

What needs attention:
OpEx jumped $21K this month. Biggest driver: new hires (3 added in
May). This is expected but needs to normalize — revenue growth must
catch up within 60 days or runway shortens to <12 months.

Recommended action:
Freeze non-essential hiring for 60 days. Review the 3 largest
non-headcount expense lines with your CFO by end of week.

Next steps:
1. CFO — Pull expense breakdown by category — by Wednesday
2. CEO — Decision on Q3 hiring plan — by Friday
```

---

## Example output — Hiring

```
User: help me hire a VP of Sales

Hiring Summary — VP of Sales

Why you're hiring: Scale revenue from $1M to $5M ARR
Urgency: This quarter
Type: New role (first dedicated sales leader)

Compensation benchmark (Growth stage, USD):
Base: $160–$220K | OTE: $220–$300K | Equity: 0.1–0.25%

90-day outcomes this person must deliver:
1. Inherit and close current pipeline within 30 days
2. Build repeatable sales process and playbook by day 60
3. Hit first month's quota independently by day 90

Interview process I recommend:
Stage 1: 45-min CEO call — career narrative + past results in numbers
Stage 2: Work sample — "Here's our pipeline. Build your 90-day plan."
Stage 3: Panel with head of marketing and a senior AE

Red flags to watch for:
- Can't give revenue numbers for their last role
- References only come from people they managed
- Has never stayed at a company more than 18 months

Recommended action: Post the role today. Set a 30-day deadline
to make an offer — VP of Sales searches that drag past 45 days
usually result in a mis-hire.
```

---

## Features

### Company memory
One-time setup saves your company name, stage, metrics, and goals. Every answer uses your real numbers — not generic advice. Updates automatically when you share new reports.

### Proactive red flag alerts
25+ danger patterns monitored. Problems surface at the top of every response before you have to ask.

| Area | Examples |
|------|---------|
| Finance | Runway < 6 months, burn escalating, margin below benchmark |
| Sales | Quota < 60%, pipeline too thin, win rate < 20% |
| Customer Success | Churn > 3%, NRR < 90%, NPS < 20 |
| HR | Attrition > 25%, critical role open 60+ days |
| Operations | SLA < 90%, critical bug open 48+ hrs |
| Marketing | CAC > LTV, ROAS < 1x, leads declining 3 months |
| M&A | LOI exclusivity > 60 days, earn-out risk |

### Industry benchmarks on every metric
Every number you share gets a benchmark alongside it. You always know if your number is good, concerning, or critical — without having to ask.

### 19 business domains
Finance · Sales · Marketing · Customer Success · HR · Operations · Product · Investor Relations · Meetings · Communications · Strategy & OKRs · Legal · PR · Hiring · Competitive Intelligence · Weekly Digest · M&A · International Expansion · Dashboard & KPIs

### Regional benchmarks
Built-in benchmarks for: North America (SaaS/Services/Ecommerce) · South Asia (Bangladesh, India, Pakistan) · Southeast Asia (Singapore, Vietnam, Philippines) · Middle East (UAE, Saudi Arabia) · UK & Europe

### Live data integrations
Connect once — no more pasting reports:

| Tool | What it pulls automatically |
|------|-----------------------------|
| HubSpot | Pipeline, leads, deals, email performance |
| Google Analytics 4 | Traffic, conversions, channel breakdown |
| QuickBooks / Xero | P&L, cash, burn rate, runway |
| Salesforce | Pipeline, quota, forecasts |
| Mixpanel | User activity, retention, activation funnels |

Say **"connect my HubSpot"** or **"how do I connect GA4"** — the skill walks you through setup step by step.

---

## 60+ things you can ask

**Finance:** explain this P&L · how much runway do we have · why is gross margin dropping · walk me through this cash flow

**Sales:** give me a pipeline review · why are we losing deals · which deals are at risk · our win rate dropped — what do I look at

**Marketing:** how are our channels performing · why is CAC going up · which channel drives the best leads · summarize this marketing report

**Customers:** which accounts are at risk · our NPS dropped — what do I do · explain net revenue retention · which customers should I call this week

**Weekly digest:** give me my weekly digest · what's the state of the business · what should I focus on this week

**Hiring:** help me hire a VP of Sales · what should I pay a Head of Marketing · write a job description · how much equity should I offer

**M&A:** we received an acquisition offer — what do I do · what is our company worth · what does an LOI mean · what will buyers look at in due diligence

**International:** we want to expand to UAE · should we enter India or Southeast Asia first · what does it take to hire in Bangladesh

**Competitive:** who are our biggest competitors · how do we win against [competitor] · build me a battle card

---

## Setup

### First run
After installing, just say "set up my company profile". The skill asks 8 questions (2 minutes) and remembers your answers forever.

### Connect your tools
Say "what integrations are available" — the skill walks you through connecting HubSpot, GA4, QuickBooks, and others step by step inside the conversation.

### Requirements
- Claude Code (CLI or desktop app) — free to install
- No API keys required to start
- Integrations optional but recommended for live data

---

## File structure

```
ceo-assistant/
├── SKILL.md                     ← Skill logic, routing, red flags
├── company-profile.md           ← Your company context (auto-maintained)
├── README.md
└── references/
    ├── connect.md               ← Step-by-step integration setup wizard
    ├── prompts.md               ← 60+ example prompts by domain
    ├── setup.md                 ← Company onboarding + memory rules
    ├── integrations.md          ← Live data pull logic (HubSpot, GA4, etc.)
    ├── benchmarks.md            ← Global + regional industry benchmarks
    ├── finance.md
    ├── sales.md
    ├── marketing.md
    ├── dashboard.md
    ├── operations.md
    ├── hr.md
    ├── product.md
    ├── customer-success.md
    ├── investor.md
    ├── meetings.md
    ├── communications.md
    ├── strategy.md
    ├── legal.md
    ├── pr.md
    ├── hiring.md
    ├── competitive.md
    ├── weekly-digest.md
    ├── ma.md
    ├── international.md
    └── summarize.md
```

---

## License

MIT — free to use, modify, and distribute.
