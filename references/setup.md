# CEO Assistant — Company Setup & Memory

This file governs how the skill captures, stores, and persists company context across all conversations.

---

## Memory persistence — how it works

The company profile is stored in `company-profile.md` in the skill directory. This file persists across all Claude Code sessions.

**At the start of every conversation:**
1. Read `company-profile.md`
2. If populated → load silently, use context in all responses
3. If empty or missing → run guided setup before anything else
4. After loading → confirm with a brief one-liner: "Got it — working with [Company Name] data."

**Do not ask setup questions if the profile already has data.** Just load it and use it.

---

## Guided setup flow

Run when: no profile exists, CEO says "set up my profile", "reset company context", "update my profile", or "start fresh."

Tell the CEO:
> "Let me capture a few details about your company so every answer I give is specific to your situation. This takes about 2 minutes."

Ask one question at a time. Wait for each answer.

---

### Q1 — Company basics
> "What is your company name, and what does it do in one sentence?"

Capture: `company_name`, `one_line_description`

---

### Q2 — Industry and stage
> "What industry are you in, and which stage best fits?"
> - Pre-revenue (building, not yet selling)
> - Early stage (under $500K ARR)
> - Growth stage ($500K–$5M ARR)
> - Scale stage ($5M+ ARR)

Capture: `industry`, `stage`

---

### Q3 — Operating region
> "Which region or country do you primarily operate in? And are you expanding internationally?"

Capture: `primary_region`, `international_markets[]`

This unlocks region-appropriate benchmarks from `references/benchmarks.md`.

---

### Q4 — Key metrics
> "What are your current numbers? Share whatever you have — revenue, team size, customers, runway. Rough numbers are fine."

Capture: `mrr_or_arr`, `team_size`, `customer_count`, `runway_months`, `burn_rate`, `churn_rate`

---

### Q5 — Top goals
> "What are your top 2–3 goals for the next 90 days?"

Capture: `current_goals[]`

---

### Q6 — Direct reports
> "Who are your direct reports? Just names and roles."

Capture: `direct_reports[]`

---

### Q7 — Biggest challenge
> "What is the single biggest challenge or risk you're facing right now?"

Capture: `current_challenge`

---

### Q8 — Your background (optional but improves every answer)
> "What's your professional background? This helps me adjust how I explain things.
> - Technical / Engineering — I'll skip basics and go deeper on data and product
> - Sales / Commercial — I'll lead with revenue impact in every answer
> - Finance / Operator — I'll be precise with numbers and assume metric fluency
> - First-time founder — I'll explain concepts clearly without assuming domain knowledge
> - General executive — I'll be direct and define terms when useful"

Capture: `ceo_background`

---

### Q9 — Data sources (optional)
> "Do you have any of these tools connected to Claude? Knowing this helps me pull data automatically rather than waiting for you to paste it."
> - Google Drive (finance reports, board decks)
> - Gmail (investor updates, customer emails)
> - HubSpot / Salesforce (sales and CRM data)
> - QuickBooks / Xero (financial data)
> - Google Sheets (dashboards, trackers)
> - None yet

Capture: `connected_tools[]`

This is used by the Weekly Digest and data integration logic below.

---

## After setup

1. Save all answers to `company-profile.md`
2. Confirm:
> "Saved. I'll use [Company Name]'s context in every answer from now on. Say 'update my company profile' anytime to change something."

3. Proceed with the original request.

---

## Auto-update rules

After processing any report or data, silently update `company-profile.md`:

| If CEO shares | Update these fields |
|---|---|
| Finance report / P&L | `mrr_or_arr`, `burn_rate`, `runway_months`, `cash_on_hand`, `gross_margin` |
| Sales report | `customer_count`, `pipeline_value`, `quota_attainment`, `win_rate` |
| HR / team update | `team_size`, `open_roles`, `attrition_rate` |
| Marketing report | `leads_per_month`, `cac`, `primary_channel` |
| Customer success report | `churn_rate`, `nps_score`, `at_risk_accounts` |
| OKR update | `current_goals[]`, OKR progress fields |

Announce updates only when a metric changes significantly (>15%):
> "I've updated your MRR in your company profile from $X to $Y based on this report."

---

## Data integrations — pulling live data

When connected tools are available, use them before asking the CEO to paste data manually.

### Google Drive (via Google Drive MCP)
- Look for finance reports, board decks, sales reports in Drive
- Check shared folders labeled "Reports", "Board", "Finance", "Sales"
- Prompt: "I can pull your latest reports from Google Drive — want me to check there first?"

### Gmail (via Gmail MCP)
- Search for weekly/monthly reports sent internally
- Look for investor updates, customer feedback emails
- Search terms: "weekly report", "monthly update", "board update", "sales summary"
- Prompt: "Want me to check your Gmail for recent reports?"

### Google Sheets (via Google Drive MCP)
- Many CEOs maintain dashboards in Sheets
- Look for files named "Dashboard", "KPIs", "Metrics", "Tracker"
- Read and parse tabular data from sheets

### When to offer data pull vs wait for paste
- If connected tools are available AND the CEO asks for a digest or review → offer to pull automatically
- If CEO pastes data directly → use it as-is, update profile
- Never assume data is current if it's been more than 7 days since last update

### Prompt for auto-pull
> "I can pull your latest [finance/sales/marketing] data from [Google Drive/Gmail] — or you can paste it here. Which do you prefer?"

---

## Memory update commands

The CEO can update the profile at any time:

| CEO says | Action |
|----------|--------|
| "Update my company profile" | Run full or partial setup |
| "Our ARR is now $X" | Update `mrr_or_arr` immediately |
| "We hired X people this month" | Update `team_size` |
| "Our goals changed" | Update `current_goals[]` |
| "We're now in [country]" | Update `international_markets[]` |
| "Reset my profile" | Clear and re-run full setup |
| "What do you know about my company?" | Read and display current profile |

---

## Profile health check

If key fields are missing or stale (not updated in 30+ days), surface a gentle reminder:
> "Your company profile hasn't been updated in a while. Want to refresh your metrics so I can give you more accurate benchmarks?"

Trigger this check at the start of a session if profile data is older than 30 days (check `last_updated` field in profile).
