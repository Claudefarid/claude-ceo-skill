# CEO Assistant — Company Setup Guide

This file runs the first time the CEO uses the skill, or when they say "set up my company profile", "update my profile", or "reset company context".

---

## When to run setup

Run the guided setup when:
- No `company-profile.md` exists yet
- The CEO says "set up my profile", "update company info", or "start fresh"
- Key fields in `company-profile.md` are empty or marked `[not set]`

If a profile already exists, load it silently at the start of every conversation — do not ask these questions again.

---

## Guided setup flow

Tell the CEO:

> "Before we start, let me capture a few details about your company so I can give you answers that are specific to your situation rather than generic advice. This takes about 2 minutes and I'll remember it for every future conversation."

Then ask these questions **one at a time**. Wait for each answer before asking the next.

---

### Question 1 — Company basics
> "What is your company name, and what does it do in one sentence?"

Capture: `company_name`, `one_line_description`

---

### Question 2 — Industry and stage
> "What industry are you in, and which stage best describes the business right now?"
> - Pre-revenue (building, not yet selling)
> - Early stage (under $500K ARR, finding product-market fit)
> - Growth stage ($500K–$5M ARR, scaling what works)
> - Scale stage ($5M+ ARR, optimizing and expanding)

Capture: `industry`, `stage`

---

### Question 3 — Key metrics
> "What are your current key numbers? Share whatever you have — revenue, team size, customers, runway. Even rough numbers help."

Capture: `mrr_or_arr`, `team_size`, `customer_count`, `runway_months`, `burn_rate`

---

### Question 4 — Top goals
> "What are your top 2–3 goals for the next 90 days?"

Capture: `current_goals[]`

---

### Question 5 — Direct reports
> "Who are your direct reports? Just names and roles is fine."

Capture: `direct_reports[]`

---

### Question 6 — Biggest challenge
> "What is the single biggest challenge or risk you're facing right now?"

Capture: `current_challenge`

---

## After setup

1. Save all answers to `company-profile.md` using the template in that file
2. Confirm with the CEO:

> "Got it. I've saved your company profile. From now on I'll use this context to give you answers specific to [Company Name]. You can update any of this at any time by saying 'update my company profile'."

3. Proceed with whatever the CEO originally asked for.

---

## Auto-update rules

After processing any report or data the CEO shares, silently update the relevant fields in `company-profile.md`:

| If CEO shares | Update these fields |
|---|---|
| Finance report | `mrr_or_arr`, `burn_rate`, `runway_months`, `cash_on_hand` |
| Sales report | `customer_count`, `pipeline_value`, `quota_attainment` |
| HR update | `team_size`, `open_roles`, `attrition_rate` |
| Marketing report | `leads_per_month`, `cac` |
| Customer success report | `churn_rate`, `nps_score` |

Do not announce the update — just save it. If a number has changed significantly (>15%), note it briefly: "I've updated your ARR in your company profile from $X to $Y."
