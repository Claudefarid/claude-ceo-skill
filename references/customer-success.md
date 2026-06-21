# Customer Success — CEO Guide

Use this when the CEO needs to understand or act on customer health: churn reports, NPS scores, account expansion, retention risk, customer complaints, or support performance.

---

## Standard output format

**Customer Success Summary — [Period]**

**Headline:** [One sentence: are customers happy, at risk, or leaving?]

**Key metrics:**
| Metric | This Period | Last Period | Status |
|--------|-------------|-------------|--------|
| Churn Rate | X% | X% | ✅ / ⚠️ / 🔴 |
| Net Revenue Retention (NRR) | X% | X% | ✅ / ⚠️ / 🔴 |
| NPS Score | X | X | ✅ / ⚠️ / 🔴 |
| Customers at Risk | X | X | ✅ / ⚠️ / 🔴 |
| Support Tickets (open) | X | X | ✅ / ⚠️ / 🔴 |
| Avg Resolution Time | X hrs | X hrs | ✅ / ⚠️ / 🔴 |
| Expansion Revenue | $X | $X | ✅ / ⚠️ / 🔴 |

**Biggest at-risk account:** [Name, ARR value, what the risk is]

**Biggest opportunity:** [Account with expansion potential or strong health signal]

**Recommended action:** [One clear CEO decision]

**Next steps:**
1. [Owner] — [Action] — [By when]

---

## How to handle specific CS situations

### Churn analysis
- How many customers cancelled? What ARR was lost?
- Why did they leave? (top 3 reasons — from exit interviews or support tickets)
- Was this preventable? (yes / no / partially)
- Pattern: is churn concentrated in a specific segment, plan, or time cohort?
- CEO recommendation: what changes to prevent this pattern repeating?

### At-risk account alert
Present as:
- **Account:** [Name, industry, ARR]
- **Risk signal:** [Low usage / complaint / non-renewal signal / executive contact went dark]
- **Days until renewal:** [X days]
- **Recommended intervention:** [CS outreach / executive call / product fix / discount offer]
- **CEO involvement needed?** Yes / No

### NPS results
- **Score:** [X] — Excellent (70+) / Good (50–69) / Needs work (30–49) / Problem (below 30)
- **Promoters (9–10):** What are they saying? Can we get case studies or referrals?
- **Detractors (0–6):** What are they saying? What's the common complaint?
- **Action:** What one thing would move the needle most based on this feedback?

### Expansion revenue opportunity
- Which customers are using the product heavily and might upgrade?
- Which customers have grown (more employees, more revenue) and are due for a tier review?
- What is the potential expansion ARR if we reach out to the top 10 accounts?
- Recommended outreach: who reaches out, what they say, by when

### Support volume spike
- What caused the spike? (new release, outage, billing issue, feature confusion)
- How many customers are affected?
- What is the resolution path?
- Does this need a proactive customer communication?

---

## Common CS metrics — plain language

| Term | What it means |
|------|--------------|
| Churn Rate | % of customers who cancelled in a given period. Lower is always better |
| Gross Churn | Revenue lost from cancellations only |
| Net Revenue Retention (NRR) | Revenue retained + expansion, minus churn. Above 100% means growth from existing customers |
| NPS (Net Promoter Score) | Survey score (0–100) measuring how likely customers are to recommend you |
| CSAT | Customer satisfaction rating after a specific interaction |
| Health Score | A composite score (usage + engagement + support tickets + NPS) that predicts churn risk |
| At-Risk Account | A customer showing signs they may cancel (low usage, open complaints, missed check-ins) |
| Expansion Revenue | Additional revenue from existing customers (upgrades, add-ons, seat growth) |
| Logo Churn | Number of customers lost (not just revenue) |
| Time to Value (TTV) | How long it takes a new customer to get their first meaningful result from the product |
| Onboarding Completion | % of new customers who complete the setup/onboarding process |

---

## Customer health score — simple framework

If no formal health score exists, assess accounts across 3 signals:

| Signal | Healthy | At Risk |
|--------|---------|---------|
| Product usage | Weekly active, using core features | Logged in rarely or not at all |
| Engagement | Responds to CS, attends QBRs | Goes dark, ignores outreach |
| Support | Few tickets, resolved quickly | Many open tickets, frustrated tone |

Any account that scores "At Risk" on 2 out of 3 signals needs immediate intervention.

---

## Red flags to always surface

- Churn rate above 3% monthly (36% annually) — existential for most businesses
- NRR below 90% — you're shrinking from your existing customer base
- NPS below 30 — customers are not happy and may be talking to competitors
- A customer representing more than 10% of revenue showing at-risk signals
- Support ticket volume growing faster than customer count
- Average resolution time exceeding your SLA commitment

---

## CEO questions for every CS review

1. Are we retaining the customers we worked hardest to win?
2. Which at-risk accounts need my personal involvement this month?
3. Are there customers ready to expand who we haven't reached out to?
4. What is the single biggest complaint we keep hearing — and what are we doing about it?

---

## When to invoke specialist skills

- **Understand why customers churn:** invoke `customer-research` for deeper qualitative analysis
- **Email campaigns to at-risk accounts:** invoke `marketing-skills:email-sequence`
- **Build re-engagement campaigns:** invoke `marketing-skills:churn-prevention`

---

## Live data — Intercom + Zendesk integration

When Intercom or Zendesk is connected, pull customer health data automatically.

### Intercom — what to pull
```
- Open conversations (count + average age in hours)
- Median first response time vs SLA target
- CSAT score (last 30 days)
- Conversations tagged as churn risk, billing issue, or bug report
- Users who have explicitly mentioned cancelling or switching
- New conversations opened this week vs last week
```

### Zendesk — what to pull
```
- Open tickets by priority: Critical / High / Normal / Low
- Average first reply time vs SLA (breached vs on track)
- Average resolution time (this month vs last month)
- CSAT score (last 30 days) — benchmark: >85% is good
- Tickets by category: billing, technical, feature request, complaint
- SLA breached tickets requiring CEO awareness
```

### Customer success summary with live data
```
Customer Health Pulse — [Date] (Live: Intercom ✅ / Zendesk ✅)

Support volume: X open conversations | X new this week (+/-%)
Response time: Xh median (SLA: Xh) ✅/⚠️/🔴
CSAT: X% (benchmark: >85%) ✅/⚠️/🔴
Churn signals: X conversations flagged as at-risk
Critical tickets: X overdue SLA breaches

🔴 Needs CEO attention: [account name + issue if any]
```

**Auto-update in company-profile.md:** `nps_score`, `at_risk_accounts`, support SLA status

**If not connected:**
> "Connect Intercom or Zendesk to get live customer health data. For now, paste your support report and I'll analyze it."
