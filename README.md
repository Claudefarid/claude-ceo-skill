# CEO Assistant — Claude Skill

A Claude skill built for non-technical CEOs. Ask in plain language — get personalized, executive-ready answers across every major business domain. The skill remembers your company, shows industry benchmarks, alerts you to problems before you ask, and routes to specialist tools when deeper work is needed.

---

## What makes it different

- **Remembers your company** — one-time setup saves your metrics, goals, team, and stage. Every answer uses your real numbers, not generic advice.
- **Industry benchmarks on every metric** — always shows "your number vs what good looks like" with ✅ ⚠️ 🔴 status
- **Proactive red flag alerts** — 20+ danger patterns monitored across all domains. Problems surface at the top of every response.
- **17 business domains** — covers everything a CEO deals with
- **Routes to specialist skills** — hands off to deeper tools when the task needs more than a summary

---

## Domains covered

| Domain | What it handles |
|--------|----------------|
| **Finance** | P&L, cash flow, burn rate, budget vs actuals, runway |
| **HR** | Performance reviews, team updates, attrition, org changes |
| **Marketing** | Campaigns, leads, CAC, LTV, channel performance, ad spend |
| **Dashboard & KPIs** | Business reviews, metric interpretation, weekly/monthly summaries |
| **Operations** | Process issues, vendor SLAs, incident reports, efficiency |
| **Sales** | Pipeline, deal updates, quota attainment, win/loss, forecasts |
| **Product & Tech** | Roadmap status, bug escalations, release updates, tech debt |
| **Customer Success** | Churn analysis, NPS, at-risk accounts, expansion revenue |
| **Investor Relations** | Investor updates, board prep, fundraising narrative, cap table |
| **Meetings** | Pre-meeting briefs, agendas, action item capture, follow-ups |
| **Communications** | All-hands, crisis comms, customer announcements, partner emails |
| **Strategy & OKRs** | OKR setting/grading, quarterly planning, decision frameworks |
| **Legal & Compliance** | Contract red flags, employment law, IP, GDPR/HIPAA basics |
| **PR & Media** | Crisis response, press releases, interview prep, reputation |
| **Weekly Digest** | Full cross-domain business summary in one command |
| **Hiring Playbook** | Job descriptions, interview frameworks, compensation, onboarding |
| **Competitive Intelligence** | Competitor profiles, win/loss analysis, battle cards, positioning |

---

## Red flag alerts (auto-triggered)

The skill monitors 20+ critical patterns and surfaces alerts before summaries:

**Finance:** Runway < 6 months · Burn escalating · Margin below benchmark · Revenue contracting

**Sales:** Quota attainment < 60% · Pipeline < 2x target · Win rate < 20% · No deals in 30 days

**Customer Success:** Churn > 3% · NRR < 90% · NPS < 20 · Key account at risk

**HR:** Attrition > 25% · Critical role open 60+ days · Multiple departures same team

**Operations:** SLA < 90% · Critical bug open 48+ hrs · Vendor concentration risk

**Marketing:** CAC > LTV · Paid ROAS < 1x · Lead volume declining 3+ months

---

## Specialist skill routing

When a task needs more than a summary, the skill routes to:

| Need | Routes to |
|------|-----------|
| Competitor deep-dive | `competitor-profiling` |
| SEO & organic traffic | `seo-audit` / `ai-seo` |
| Content planning | `content-strategy` |
| Customer research | `customer-research` |
| Analytics & funnels | `analytics` |
| Paid advertising | `marketing-skills:paid-ads` |
| Email campaigns | `marketing-skills:email-sequence` |
| Lead prospecting | `apollo:prospect` |
| Social content | `marketing-skills:social-content` |
| Slide decks | `canvas-design` / Canva |
| Deep research | `deep-research` |

---

## How to use

Just speak naturally — no commands needed.

```
give me my weekly digest
how is sales tracking this quarter?
explain this P&L report
we have a critical bug — what should I know?
prep me for the board meeting
write an all-hands about the restructure
review this contract
help me set our Q3 OKRs
who are our biggest competitors and how do we beat them?
help me hire a VP of Sales
how are our customers doing?
what does this dashboard mean?
update my company profile
```

---

## Install

```bash
claude skills install https://github.com/digitalmarketerswadhin-droid/ceo-assistant
```

### Manual install

```bash
cp -r ceo-assistant ~/.claude/skills/
```

Restart Claude Code — skill activates automatically.

---

## Skill structure

```
ceo-assistant/
├── SKILL.md                        ← Main skill + routing + red flags
├── company-profile.md              ← Your company context (auto-maintained)
├── README.md
└── references/
    ├── setup.md                    ← Guided company setup + auto-update rules
    ├── benchmarks.md               ← Industry benchmarks by stage and type
    ├── finance.md
    ├── hr.md
    ├── marketing.md
    ├── dashboard.md
    ├── operations.md
    ├── sales.md
    ├── product.md
    ├── customer-success.md
    ├── investor.md
    ├── meetings.md
    ├── communications.md
    ├── strategy.md
    ├── legal.md
    ├── pr.md
    ├── weekly-digest.md            ← Full business digest format
    ├── hiring.md                   ← Hiring playbook
    ├── competitive.md              ← Competitive intelligence
    └── summarize.md
```

---

## Requirements

- Claude Code (CLI or desktop app)
- No API keys or extra configuration required

## License

MIT
