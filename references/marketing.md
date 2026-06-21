# Marketing Reports — CEO Guide

Use this when the CEO needs to understand or act on marketing performance: campaign results, lead generation, channel performance, CAC, LTV, content metrics, brand awareness, or paid advertising spend.

---

## Standard output format

**Marketing Summary — [Period]**

**Headline:** [One sentence: is marketing performing, struggling, or at an inflection point?]

**Key metrics:**
| Metric | This Period | Last Period | Change |
|--------|-------------|-------------|--------|
| Total Leads Generated | X | X | +/-% |
| MQLs (Marketing Qualified Leads) | X | X | +/-% |
| CAC (Cost to Acquire a Customer) | $X | $X | +/-% |
| Marketing Spend | $X | $X | +/-% |
| Website Visitors | X | X | +/-% |
| Email Open Rate | X% | X% | +/-% |
| Conversion Rate (lead → customer) | X% | X% | +/-% |

**Best performing channel:** [Channel name + why it's working]

**Underperforming area:** [What's not working and why it matters]

**Recommended action:** [One decision the CEO should make]

**Next steps:**
1. [Owner] — [Action] — [By when]

---

## How to read key marketing metrics

### CAC (Customer Acquisition Cost)
- **Formula:** Total Marketing Spend ÷ New Customers Acquired
- **What it means:** How much it costs to win one customer
- **CEO rule:** CAC should be less than 1/3 of LTV. If CAC is rising and LTV is flat, the business is becoming less efficient.

### LTV (Lifetime Value)
- **Formula:** Average Revenue per Customer × Average Customer Lifespan
- **What it means:** How much revenue one customer generates over their relationship with you
- **CEO rule:** LTV:CAC ratio should be at least 3:1. Below that, growth is expensive and unsustainable.

### MQL (Marketing Qualified Lead)
- A lead that marketing has decided is worth passing to sales
- **CEO question:** What % of MQLs are converting to customers? If low, either marketing is sending bad leads or sales can't close them.

### Conversion Rate
- Measures how many people took the desired action (signed up, purchased, booked a call)
- Even small improvements matter: going from 2% to 3% conversion is a 50% increase in output from the same traffic.

### ROAS (Return on Ad Spend)
- **Formula:** Revenue Generated from Ads ÷ Ad Spend
- **What it means:** For every $1 spent on ads, how much revenue came back?
- **CEO rule of thumb:** ROAS below 2x on direct-response campaigns is usually a problem.

---

## Channel-specific guidance

### Paid Ads (Meta, Google, LinkedIn)
- Report spend, clicks, conversions, and cost per conversion
- Flag any campaign where CPC (cost per click) is rising without a corresponding increase in conversions
- Key question: Are we getting cheaper or more expensive customers over time?

### Email Marketing
- Open rate and click rate are engagement signals, not revenue signals
- What matters: how many emails led to a demo, trial, or purchase?
- Healthy benchmarks (B2B SaaS): 25–35% open rate, 3–5% click rate

### Content / SEO
- Traffic is a vanity metric unless it converts
- Report: organic sessions, top 5 landing pages, and how many leads came from organic search
- Flag any page losing significant traffic — it may indicate a ranking drop

### Social Media
- Reach and impressions are awareness metrics, not revenue metrics
- What matters for the CEO: did social activity generate leads or pipeline?

---

## Red flags to always surface

- CAC increasing month-over-month while LTV is flat or declining
- Marketing spend increasing but lead volume not growing proportionally
- A single channel generating more than 60% of leads (dangerous dependency)
- Email deliverability issues (spam rates rising, open rates dropping sharply)
- Paid campaigns with ROAS below 1x (losing money on ads)

---

## When the CEO gets a marketing report

1. Identify the top 3 KPIs (usually leads, CAC, and one channel metric)
2. Compare to last period and to target
3. Highlight one thing that's working and one thing that isn't
4. Give a budget or strategy recommendation based on the data
5. Never relay every campaign result — summarize and surface what requires a decision

---

## Live data — HubSpot + GA4 integration

When HubSpot and/or GA4 MCPs are connected, pull data automatically before presenting any marketing summary.

### HubSpot — what to pull
```
- New contacts created (last 30 days vs prior 30 days)
- Contacts by lifecycle stage: subscriber → lead → MQL → SQL → customer
- Email campaigns sent this month: open rate, CTR, unsubscribe rate
- Form submissions by landing page
- Lead source breakdown (organic search, paid, social, direct, referral, email)
- New deals created from marketing-sourced leads
```

**HubSpot MCP calls:**
- `search_objects(objectType: "contacts", filterGroups: [{filters: [{propertyName: "createdate", operator: "BETWEEN", value: ...}]}])`
- `get_marketing_emails` — email performance
- `search_objects(objectType: "deals", properties: ["dealstage", "hs_analytics_source"])`

### GA4 — what to pull
```
- Sessions and users: this month vs last month
- Sessions by channel: organic, paid, direct, social, referral, email
- Top 5 landing pages by sessions
- Top 5 converting pages (by goal completion)
- Conversion rate: sessions → key goal (signup, demo request, purchase)
- Geographic data: top 5 countries by sessions
```

**GA4 MCP calls:**
- `run_report(property: "properties/YOUR_ID", dateRanges: [...], metrics: [{name: "sessions"}, {name: "totalUsers"}, {name: "conversions"}], dimensions: [{name: "sessionDefaultChannelGroup"}])`

### Combined marketing summary with live data
Present as:
```
Marketing Pulse — [Date] (Live data from HubSpot + GA4)

Traffic: X sessions (+/-% vs last month) | Top channel: [Channel]
Leads: X new contacts | MQLs: X | SQL conversion: X%
Email: X% open rate | X% CTR (benchmark: 22% open, 3% CTR)
Top converting page: [Page] at X%
CAC this month: $X (HubSpot spend ÷ new customers)
```

**Auto-update in company-profile.md:**
- `leads_per_month`, `cac`, `primary_channel`, `website_visitors`

**If not connected:**
> "Connect HubSpot and GA4 to get this automatically. For now, paste your marketing report and I'll analyze it."
