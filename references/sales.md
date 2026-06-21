# Sales — CEO Guide

Use this when the CEO needs to understand or act on sales performance: pipeline reviews, deal updates, quota attainment, win/loss analysis, forecast accuracy, rep performance, or sales team health.

---

## Standard output format

**Sales Summary — [Period]**

**Headline:** [One sentence: is sales on track, behind, or ahead?]

**Key metrics:**
| Metric | This Period | Target | Attainment |
|--------|-------------|--------|------------|
| New Revenue Closed | $X | $X | X% |
| Pipeline Value (total open deals) | $X | $X | ✅ / ⚠️ / 🔴 |
| New Qualified Opportunities | X | X | ✅ / ⚠️ / 🔴 |
| Win Rate | X% | X% | ✅ / ⚠️ / 🔴 |
| Average Deal Size | $X | $X | ✅ / ⚠️ / 🔴 |
| Sales Cycle Length | X days | X days | ✅ / ⚠️ / 🔴 |
| Quota Attainment (team) | X% | 100% | ✅ / ⚠️ / 🔴 |

**Biggest win this period:** [Deal name, value, why it matters]

**Biggest risk:** [Deal or trend that could hurt next month's number]

**Recommended action:** [One decision the CEO should make]

**Next steps:**
1. [Owner] — [Action] — [By when]

---

## How to handle specific sales situations

### Pipeline review
- How much total pipeline exists? Is it enough to hit next quarter's target?
  - Rule of thumb: pipeline should be 3–4x the quarterly revenue target
- Which deals are most likely to close? (Weighted by probability)
- Which deals are stuck? (No activity in 2+ weeks)
- What's the single biggest deal and what does it need to move forward?

### Deal update
Present as:
- **Deal:** [Company name, deal value]
- **Stage:** [Where it is in the sales process]
- **Decision maker:** [Who needs to say yes]
- **Status:** On track / At risk / Stalled
- **Next step:** [Specific action, owner, date]
- **CEO support needed?** Yes / No — [If yes, what exactly]

### Quota attainment review
- Overall team attainment (% of quota achieved)
- Individual rep breakdown:
  - Top performers: [names, attainment %]
  - On track: [names, attainment %]
  - Behind: [names, attainment %, and why]
- Pattern: is underperformance in one rep, or systemic across the team?

### Win/Loss analysis
- **Win rate:** % of deals closed won vs total closed (won + lost)
- **Why we won:** [Top 2–3 reasons — product, price, relationship, speed]
- **Why we lost:** [Top 2–3 reasons — competitor, price, timing, wrong fit]
- **Pattern:** Is there a competitor we keep losing to? A deal size we consistently win at?
- **CEO recommendation:** What should change in our approach or positioning?

### Sales forecast
- What is the team committing to close this month/quarter?
- What is the upside scenario (if everything goes right)?
- What is the downside scenario (if 1–2 deals slip)?
- How does this compare to last period's forecast accuracy?
- CEO action: is there a gap between forecast and target that needs to be addressed now?

---

## Common sales terms — plain language

| Term | What it means |
|------|--------------|
| Pipeline | All open deals in various stages of the sales process |
| Qualified Opportunity | A deal that has been confirmed to have budget, authority, need, and timeline |
| MQL → SQL | Marketing Qualified Lead converted to Sales Qualified Lead (sales accepted it) |
| Win Rate | % of deals you win out of all deals that reached a decision point |
| Sales Cycle | Average number of days from first contact to closed deal |
| ACV (Annual Contract Value) | Average yearly value of a customer deal |
| ARR (Annual Recurring Revenue) | Total annualized subscription revenue |
| Churn | Customers who cancelled — reduces ARR |
| Expansion Revenue | Existing customers buying more — grows ARR without new sales |
| NRR (Net Revenue Retention) | If above 100%, you're growing even accounting for churn |
| Closed Won | Deal was signed — revenue |
| Closed Lost | Deal was lost to competitor or no decision |
| Slippage | A deal that was expected to close but moved to a future period |

---

## Red flags to always surface

- Team quota attainment below 70% two months in a row
- Pipeline coverage below 2.5x the monthly target
- Win rate declining without a clear explanation
- Average deal size shrinking (may indicate going downmarket)
- A single rep carrying more than 40% of revenue (key person risk)
- Deals consistently slipping to next month (forecast is unreliable)
- Sales cycle lengthening without a change in deal size

---

## CEO questions for every sales review

1. Are we on track for the quarter? If not, what's the gap and can we close it?
2. Which deals need CEO involvement to move forward?
3. Is the pipeline healthy enough to hit next quarter's number?
4. Are there any early warning signs in this month's data that will show up in revenue 60 days from now?

---

## Live data — HubSpot CRM / Salesforce integration

When HubSpot CRM or Salesforce MCP is connected, pull pipeline data automatically.

### HubSpot CRM — what to pull
```
- Open deals by stage (full pipeline breakdown)
- Deals closed this month: closed won vs closed lost
- Win rate: closed won ÷ (closed won + closed lost)
- Average deal size (last 90 days)
- Average sales cycle (days from create to close)
- Deals with no activity in 14+ days (stalled deals)
- Pipeline by owner (rep performance)
- New deals created this month
```

**HubSpot MCP calls:**
- `get_pipelines` — stage breakdown with deal counts and values
- `search_objects(objectType: "deals", filterGroups: [{filters: [{propertyName: "closedate", operator: "BETWEEN"}, {propertyName: "dealstage", operator: "EQ", value: "closedwon"}]}])`
- `search_objects` with `hs_lastmodifieddate` to find stalled deals

### Salesforce — what to pull
```
- Opportunity pipeline by stage and amount
- Closed won this month vs quota
- Forecast by rep
- Win/loss reason breakdown
- Account engagement scores
```

### Live sales summary format
```
Sales Pulse — [Date] (Live data from HubSpot CRM)

Pipeline: $X across X deals | Weighted: $X
Closed this month: $X vs $X target (X% attainment)
Win rate: X% | Avg deal: $X | Avg cycle: X days
Stalled deals: X (no activity 14+ days) — needs follow-up
Best rep: [Name] at $X closed | Needs support: [Name] at $X

🔴 Alerts: [any triggered by live data]
```

**Auto-update in company-profile.md:**
- `pipeline_value`, `win_rate`, `average_deal_size`, `quota_attainment`

**If not connected:**
> "Connect HubSpot CRM or Salesforce to pull pipeline data automatically. For now, paste your pipeline report and I'll analyze it."
