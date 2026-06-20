# CEO Assistant — Claude Skill

A Claude skill built for non-technical CEOs. Ask in plain language — get executive-ready summaries, recommendations, and next steps across every major business domain. Also routes to specialist skills when deeper work is needed.

---

## Domains covered

| Domain | What it handles |
|--------|----------------|
| **Finance** | P&L, cash flow, burn rate, budget vs actuals, runway |
| **HR** | Hiring, performance reviews, team announcements, attrition, org changes |
| **Marketing** | Campaigns, leads, CAC, LTV, channel performance, ad spend |
| **Dashboard & KPIs** | Business reviews, metric interpretation, weekly/monthly summaries |
| **Operations** | Process issues, vendor SLAs, incident reports, efficiency |
| **Sales** | Pipeline, deal updates, quota attainment, win/loss, forecasts |
| **Product & Tech** | Roadmap status, bug escalations, release updates, tech debt |
| **Customer Success** | Churn analysis, NPS, at-risk accounts, expansion revenue |
| **Investor Relations** | Investor updates, board prep, fundraising narrative, cap table |
| **Meetings** | Pre-meeting briefs, agendas, action item capture, follow-ups |
| **Communications** | All-hands, crisis comms, customer announcements, partner emails |

---

## Skill routing — specialist integrations

When a task needs more than a summary, the skill routes to specialist tools:

| Need | Routes to |
|------|-----------|
| Competitor analysis | `competitor-profiling` skill |
| SEO & organic traffic | `seo-audit` / `ai-seo` skill |
| Content planning | `content-strategy` skill |
| Customer insight & personas | `customer-research` skill |
| Deep analytics & funnels | `analytics` skill |
| Paid advertising | `marketing-skills:paid-ads` skill |
| Email campaigns | `marketing-skills:email-sequence` skill |
| Lead prospecting | `apollo:prospect` skill |
| Social media content | `marketing-skills:social-content` skill |
| Slide decks & design | `canvas-design` / Canva / Figma |
| Deep research | `deep-research` skill |

---

## How to use

Just describe what you need in plain language — no commands required.

**Finance**
```
Explain this P&L report
How is our cash looking?
What's our runway?
```

**HR**
```
We have an HR situation — one of our managers is underperforming
Help me write a hiring announcement for our new CTO
Summarize the performance review data
```

**Marketing**
```
How did marketing perform this month?
What are our CAC and LTV numbers telling us?
Which channel is bringing in the best leads?
```

**Dashboard**
```
Put together the weekly business review
What does our KPI dashboard mean?
How are we tracking against Q3 targets?
```

**Operations**
```
We had an outage last night — help me write the incident report
Our vendor missed their SLA again — what should I say?
What are our biggest operational risks right now?
```

**Sales**
```
How is sales tracking this quarter?
Which deals need my attention?
What does the pipeline look like for next month?
```

**Product**
```
What did the product team ship this month?
We have a critical bug — what should I know?
Summarize the roadmap for the board
```

**Customer Success**
```
How many customers are at risk of churning?
What is our NPS telling us?
Which accounts should I personally call this month?
```

**Investor Relations**
```
Write the monthly investor update
Prep me for the board meeting
Help me structure the fundraising pitch
```

**Meetings**
```
Prep me for my meeting with [Company] tomorrow
Write an agenda for the quarterly planning session
Capture the action items from this meeting
```

**Communications**
```
Write an all-hands announcement about the restructure
Help me respond to this difficult email
Draft a customer communication about the outage
```

---

## Output style

Every response follows the same CEO-friendly format:
- Headline insight first — no preamble
- Key metrics in a scannable table
- What's working / what needs attention
- One clear recommendation (not a list of options)
- 1–3 specific next steps with owners and dates
- No jargon, no hype language, no made-up numbers

---

## Install

### Option 1 — Claude Code CLI

```bash
claude skills install https://github.com/YOUR_USERNAME/ceo-assistant
```

### Option 2 — Manual install

1. Clone or download this repository
2. Copy the `ceo-assistant/` folder into your Claude skills directory:

```bash
# macOS / Linux
cp -r ceo-assistant ~/.claude/skills/

# Windows
xcopy ceo-assistant %USERPROFILE%\.claude\skills\ceo-assistant\ /E /I
```

3. Restart Claude Code — the skill activates automatically

---

## Skill structure

```
ceo-assistant/
├── SKILL.md                        ← Main skill + routing logic
├── README.md                       ← This file
└── references/
    ├── finance.md                  ← P&L, cash flow, burn rate
    ├── hr.md                       ← Hiring, performance, org changes
    ├── marketing.md                ← Campaigns, leads, CAC, LTV
    ├── dashboard.md                ← KPIs, business reviews
    ├── operations.md               ← Process, vendor, incidents
    ├── sales.md                    ← Pipeline, quota, forecasts
    ├── product.md                  ← Roadmap, bugs, releases
    ├── customer-success.md         ← Churn, NPS, account health
    ├── investor.md                 ← Board, fundraising, updates
    ├── meetings.md                 ← Prep, agendas, action items
    ├── communications.md           ← All-hands, crisis, announcements
    └── summarize.md                ← General report summarization
```

---

## Requirements

- Claude Code (CLI or desktop app)
- No API keys or additional configuration required
- Optional: other Claude skills for deep-dive routing (competitor-profiling, seo-audit, etc.)

---

## License

MIT — free to use, modify, and distribute.
