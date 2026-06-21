# Dashboard & KPI Reviews — CEO Guide

Use this when the CEO needs to interpret a business dashboard, understand what KPIs mean, prepare a weekly or monthly business review, or turn raw metrics into an executive-ready summary.

---

## Standard business review format

**Business Review — [Week/Month/Quarter ending Date]**

**Executive summary:** [2–3 sentences: how is the overall business performing? improving, stable, or under pressure?]

---

### Finance
| KPI | Actual | Target | Status |
|-----|--------|--------|--------|
| Revenue | $X | $X | ✅ / ⚠️ / 🔴 |
| Gross Margin | X% | X% | ✅ / ⚠️ / 🔴 |
| Cash on Hand | $X | — | — |
| Burn Rate | $X/mo | — | — |

### Sales
| KPI | Actual | Target | Status |
|-----|--------|--------|--------|
| New Customers | X | X | ✅ / ⚠️ / 🔴 |
| Pipeline Value | $X | $X | ✅ / ⚠️ / 🔴 |
| Quota Attainment | X% | 100% | ✅ / ⚠️ / 🔴 |

### Marketing
| KPI | Actual | Target | Status |
|-----|--------|--------|--------|
| Leads Generated | X | X | ✅ / ⚠️ / 🔴 |
| CAC | $X | $X | ✅ / ⚠️ / 🔴 |

### Operations / Product
| KPI | Actual | Target | Status |
|-----|--------|--------|--------|
| [Key ops metric] | X | X | ✅ / ⚠️ / 🔴 |
| [Key product metric] | X | X | ✅ / ⚠️ / 🔴 |

---

**Wins this period:**
1. [Specific win with a number if possible]
2. [Second win]

**Risks & issues:**
1. [Risk — owner — mitigation plan]
2. [Risk — owner — mitigation plan]

**Priorities for next [week/month]:**
1. [Priority 1]
2. [Priority 2]
3. [Priority 3]

---

## Status indicators — when to use each

| Symbol | Meaning |
|--------|---------|
| ✅ | On track — at or above target |
| ⚠️ | Watch — within 10% below target or trending the wrong way |
| 🔴 | Off track — more than 10% below target or requires CEO decision |

Only flag 🔴 items in the executive summary. ✅ items don't need explanation.

---

## How to interpret a dashboard the CEO receives

**Step 1: Find the headline number.** What is the single most important metric on this dashboard? (Usually revenue, active users, or pipeline.)

**Step 2: Compare to baseline.** Is this number up or down vs last week/month/quarter? By how much?

**Step 3: Look for the outlier.** What is the one metric that moved the most — positively or negatively?

**Step 4: Ask "so what?"** What does this movement mean for a business decision?

**Step 5: Summarize in 3 sentences:**
- What the dashboard shows overall
- What the most important signal is
- What the CEO should do (or not do) based on it

---

## Common KPIs by department — plain language definitions

### Revenue metrics
- **MRR (Monthly Recurring Revenue):** Predictable subscription revenue per month
- **ARR (Annual Recurring Revenue):** MRR × 12 — your annualized subscription base
- **Churn Rate:** % of customers who cancelled this month — lower is better
- **Net Revenue Retention (NRR):** If NRR > 100%, existing customers are growing in value even after churn
- **ACV (Average Contract Value):** Average annual value of a customer contract

### Growth metrics
- **MoM Growth:** Month-over-month percentage change
- **YoY Growth:** Year-over-year percentage change — more meaningful for seasonal businesses
- **Growth Rate:** How fast the business is expanding — compare to industry benchmark

### Efficiency metrics
- **Payback Period:** How many months until you recover the cost of acquiring a customer
- **Magic Number:** Measures how efficiently sales & marketing spend converts to new ARR (above 0.75 is healthy)
- **Rule of 40:** Revenue growth rate + profit margin should be ≥ 40% for a healthy SaaS business

### Customer metrics
- **DAU / MAU (Daily/Monthly Active Users):** How many users engage regularly
- **NPS (Net Promoter Score):** Customer satisfaction score (0–100). Above 50 is excellent; below 20 is a problem
- **CSAT (Customer Satisfaction):** Post-interaction satisfaction rating

---

## Building a CEO dashboard (if the CEO doesn't have one)

Recommend tracking these 10 metrics, updated weekly:

1. Revenue (MRR or weekly revenue)
2. Cash on hand
3. Runway (months)
4. New customers this week/month
5. Churn rate
6. Open pipeline value
7. Leads generated
8. CAC
9. Headcount (and open roles)
10. One product/ops health metric (uptime, delivery rate, etc.)

Keep it on one page. Color-code status. CEO reviews in under 10 minutes.

---

## Live data — GA4 + Mixpanel + MS Clarity integration

When analytics tools are connected, pull data automatically for any dashboard or KPI review.

### GA4 — core business metrics
```
Pull for every dashboard review:
- Sessions and users (MTD vs prior month)
- Channel breakdown (organic, paid, direct, social, referral)
- Conversion rate (sessions → primary goal)
- Top 10 pages by sessions and conversions
- Geographic performance (top 5 countries)
- Device split (desktop vs mobile vs tablet)
```

**Interpreting GA4 data for a non-technical CEO:**
- Sessions dropping → top of funnel problem (SEO, paid, or brand awareness)
- Sessions stable but conversions dropping → landing page or offer problem
- Mobile sessions high but conversions low → mobile UX issue (check MS Clarity)
- One channel down sharply → algorithm change, budget cut, or technical issue

### Mixpanel — product and user behavior metrics
```
Pull when available:
- DAU / WAU / MAU (daily, weekly, monthly active users)
- DAU/MAU ratio (engagement — good is >20%, great is >50%)
- Core funnel: signup → activation → retained user
- Feature adoption: % of users who used key feature at least once
- Retention by cohort: what % of users from month X are still active in month X+3
- Churned users: did they stop using a specific feature before leaving?
```

**CEO interpretation guide:**
- DAU/MAU < 10% → low engagement — users signed up but aren't coming back
- Activation rate < 40% → onboarding problem — users don't reach their "aha moment"
- Day 7 retention < 20% → product-market fit concern for most SaaS products
- Feature with <10% adoption → either bad UX, undiscovered, or not valued

### MS Clarity — UX signal metrics
```
Pull when available:
- Pages with highest rage click rate (users clicking something expecting it to work)
- Pages with highest dead click rate (clicks going nowhere)
- Average scroll depth per page
- Session recordings for users who dropped off key funnels
```

**CEO interpretation guide:**
- Rage clicks on pricing page → confusing pricing or CTA not working
- Low scroll depth on landing page → headline not compelling enough
- High dead clicks on mobile → navigation or button placement issue

### Full connected dashboard output format
```
Dashboard Pulse — [Date]
Data sources: GA4 ✅ | Mixpanel ✅ | HubSpot ✅ | QuickBooks ✅ | Clarity ⚠️ (not connected)

TRAFFIC (GA4)
Sessions: X (+/-% vs last month) | Users: X
Top channel: [Channel] at X% of traffic
Conversion rate: X% (benchmark: X%)

PRODUCT (Mixpanel)
MAU: X | DAU/MAU: X% (benchmark: >20%)
Activation rate: X% | Day-30 retention: X%

UX SIGNALS (Clarity)
[Not connected — connect for heatmap and rage click data]

PIPELINE (HubSpot)
Open pipeline: $X | Deals stalled: X

FINANCE (QuickBooks)
Cash: $X | Runway: X months | Burn: $X/mo
```
