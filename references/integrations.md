# Live Data Integrations — CEO Assistant

This file governs how the skill detects, uses, and falls back on connected data sources. Load this file whenever the CEO asks for live data, a digest, or any report that could be auto-pulled.

---

## Step 1 — Detect what's connected

At the start of any data request, check `company-profile.md` for the `Connected tools` field. Then attempt tool calls to confirm live connectivity. Do this silently — the CEO should not see connection attempts.

| Tool | How to detect | MCP namespace |
|------|--------------|---------------|
| HubSpot | Try `mcp__hubspot__*` tool | `mcp__hubspot__` |
| Google Analytics 4 | Try `mcp__google-analytics__*` tool | `mcp__google-analytics__` |
| QuickBooks | Try `mcp__quickbooks__*` tool | `mcp__quickbooks__` |
| Salesforce | Try `mcp__salesforce__*` tool | `mcp__salesforce__` |
| Mixpanel | Try `mcp__mixpanel__*` tool | `mcp__mixpanel__` |
| Microsoft Clarity | Try `mcp__clarity__*` tool | `mcp__clarity__` |
| Google Drive | Try `mcp__gdrive__*` tool | `mcp__gdrive__` |
| Gmail | Try `mcp__gmail__*` tool | `mcp__gmail__` |

If a tool responds → use it. If it fails or is unavailable → fall back to asking the CEO to paste data.

---

## Step 2 — Pull data by domain

### Finance → QuickBooks

When the CEO asks about finance and QuickBooks is connected:

```
Pull from QuickBooks:
- Profit & Loss (current month + last month)
- Cash on hand (current balance)
- Monthly burn rate (total operating expenses)
- Accounts receivable aging
- Revenue by customer (top 10)
```

Key QuickBooks MCP calls:
- `get_profit_and_loss` — P&L for a date range
- `get_balance_sheet` — assets, liabilities, equity
- `get_cash_flow` — operating/investing/financing
- `get_customers` — customer revenue breakdown

Auto-update in `company-profile.md`: `mrr_or_arr`, `gross_margin`, `cash_on_hand`, `burn_rate`, `runway_months`

---

### Marketing → HubSpot + GA4

When the CEO asks about marketing and HubSpot/GA4 are connected:

**HubSpot pulls:**
```
- Contacts created (last 30 days)
- MQLs and SQLs (by lifecycle stage)
- Email campaign performance (open rate, CTR, unsubscribes)
- Landing page conversions
- Source breakdown (organic, paid, direct, social, referral)
- CAC calculation (marketing spend ÷ new customers)
```

Key HubSpot MCP calls:
- `get_contacts` — new leads with source attribution
- `get_deals` — pipeline and conversion rates
- `get_marketing_emails` — email performance
- `get_forms` — form submission rates
- `search_objects` — filtered by date range and lifecycle stage

**GA4 pulls:**
```
- Total sessions and users (last 30 days vs prior period)
- Traffic by channel (organic, paid, direct, referral, social)
- Top pages by sessions and conversions
- Conversion rate (sessions → goal completions)
- Bounce rate and average session duration
- Geographic breakdown (top countries/cities)
```

Key GA4 MCP calls:
- `run_report` — custom metrics and dimensions for any date range
- `get_realtime_data` — live users on site right now
- Standard dimensions: `sessionDefaultChannelGroup`, `landingPage`, `country`
- Standard metrics: `sessions`, `totalUsers`, `conversions`, `bounceRate`

Auto-update in `company-profile.md`: `leads_per_month`, `cac`, `primary_channel`, `website_visitors`

---

### Sales → HubSpot CRM / Salesforce

When the CEO asks about sales and HubSpot or Salesforce is connected:

**HubSpot CRM pulls:**
```
- Open deals by stage (pipeline breakdown)
- Deals closed this month vs last month
- Win rate (closed won ÷ total closed)
- Average deal size
- Sales cycle length (average days from create to close)
- Rep performance (deals by owner)
- At-risk deals (no activity in 14+ days)
```

Key HubSpot CRM MCP calls:
- `get_deals` with stage filters — pipeline by stage
- `search_objects` with `closedate` filter — closed deals this period
- `get_pipelines` — stage breakdown and conversion rates
- `get_owners` — deals by rep

**Salesforce pulls (if connected instead of HubSpot):**
```
- Opportunity pipeline by stage
- Quota vs actual (from Salesforce reports)
- Forecast by rep and territory
- Win/loss reasons
- Account health scores
```

Auto-update in `company-profile.md`: `pipeline_value`, `win_rate`, `average_deal_size`, `quota_attainment`

---

### Analytics → GA4 + Mixpanel + MS Clarity

**GA4 (full funnel):**
```
- Acquisition funnel: sessions → signups → activations → conversions
- Channel ROI: sessions and conversions per channel
- Content performance: top pages by goal completion
- User journey: most common paths to conversion
```

**Mixpanel (product analytics, if connected):**
```
- Active users (DAU/WAU/MAU)
- Feature adoption rates
- Funnel completion rates (onboarding, activation, feature use)
- Retention cohorts (day 1, day 7, day 30)
- Event-level tracking for key user actions
```

Key Mixpanel pulls:
- `get_funnels` — funnel conversion rates
- `get_retention` — cohort retention tables
- `get_segmentation` — metric breakdowns by user property
- `get_events` — event volume over time

**MS Clarity (UX signals, if connected):**
```
- Pages with highest scroll depth
- Pages with highest rage click rate (frustration signal)
- Dead click rate by page
- Session recordings for specific user segments
- Heatmap data for key landing pages
```

Note: Clarity's API is limited. Primarily useful for identifying UX problem pages, not for revenue metrics.

Auto-update in `company-profile.md`: `website_visitors`, conversion rates, feature adoption notes

---

## Step 3 — Announce what was pulled

After pulling live data, tell the CEO:

> "Pulled live data from [HubSpot + GA4] as of [date/time]. Here's the summary:"

If data is more than 24 hours old, note:
> "Note: HubSpot data last synced [X hours] ago."

---

## Step 4 — Fallback when not connected

If a tool is not connected and the CEO asks for data it would provide:

> "I don't have [QuickBooks] connected for your account. You can:
> 1. Paste your [P&L / sales report / dashboard] here and I'll analyze it instantly
> 2. Say 'how do I connect QuickBooks' and I'll walk you through setup"

Never leave the CEO without a path forward.

---

## Integration setup — what credentials are needed

### HubSpot
- **What you need:** Private App Access Token
- **Where to get it:** HubSpot → Settings → Integrations → Private Apps → Create a private app
- **Scopes needed:** `crm.objects.contacts.read`, `crm.objects.deals.read`, `marketing-email`, `forms`
- **Setup command:**
```bash
claude mcp add hubspot -- npx -y @hubspot/mcp-server
# Then add your token to environment: HUBSPOT_ACCESS_TOKEN=your_token
```

### Google Analytics 4
- **What you need:** GA4 Property ID + Google Service Account credentials
- **Where to get it:** Google Cloud Console → Create Service Account → Enable Analytics Data API → Download JSON key
- **Setup command:**
```bash
claude mcp add google-analytics -- npx -y @modelcontextprotocol/server-google-analytics
# Then set: GA4_PROPERTY_ID=your_property_id
# And: GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json
```

### QuickBooks
- **What you need:** QuickBooks OAuth 2.0 credentials (Client ID + Secret + Refresh Token)
- **Where to get it:** Intuit Developer Portal → Create App → OAuth 2.0 credentials
- **Note:** QuickBooks requires a more complex OAuth flow. Use an existing QuickBooks MCP package or a middleware like Zapier/Make to export to Google Sheets, then connect Google Sheets MCP instead.

### Salesforce
- **What you need:** Salesforce Connected App credentials (Consumer Key + Secret + username + password + security token)
- **Setup:** Use a community Salesforce MCP or export reports to Google Drive and use Google Drive MCP.

### Mixpanel
- **What you need:** Mixpanel Service Account credentials (username + secret)
- **Where to get it:** Mixpanel → Settings → Service Accounts → Create
- **Note:** No official MCP yet. Export data to Google Sheets weekly for now, or use Mixpanel's API via a custom MCP.

---

## Priority integration order

If the CEO is setting up integrations for the first time, recommend this order:

1. **HubSpot** — highest ROI. Covers leads, pipeline, and marketing in one connection.
2. **GA4** — critical for website and funnel data. Easy to set up.
3. **QuickBooks / Xero** — financial data. More setup complexity but unlocks fully automated weekly digest.
4. **Mixpanel** — only if the company has product analytics set up. Powerful for SaaS.
5. **Salesforce** — only if HubSpot is not being used as CRM.
6. **MS Clarity** — low priority. Useful for UX, not for CEO-level reporting.
