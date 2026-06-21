# Connecting Your Tools — In-Skill Setup Guide

Use this when the CEO says "connect my HubSpot", "set up GA4", "how do I connect QuickBooks", "what integrations are available", or "how do I get live data".

This is the in-skill setup wizard. Walk the CEO through connecting their tools step by step — inside this conversation.

---

## Start here — what's available

When the CEO asks about integrations, first show them this:

> "Here are the tools you can connect to get live data in your weekly digest and reports — no more pasting spreadsheets:
>
> **Finance & Revenue**
> | Tool | What it unlocks |
> |------|----------------|
> | **QuickBooks** | P&L, cash, burn rate, runway, expenses |
> | **Xero** | P&L, cash flow, invoices, payroll |
> | **Stripe** | MRR, ARR, churn, new revenue, failed payments |
>
> **CRM & Sales**
> | Tool | What it unlocks |
> |------|----------------|
> | **HubSpot** | Pipeline, deals, leads, email performance, CAC |
> | **Salesforce** | Pipeline, quota, win/loss, forecasts |
> | **Pipedrive** | Deals, pipeline stages, activity, revenue forecast |
>
> **Marketing & Analytics**
> | Tool | What it unlocks |
> |------|----------------|
> | **Google Analytics 4** | Traffic, conversions, channel breakdown |
> | **Google Ads** | Spend, ROAS, conversions, cost per lead |
> | **Mailchimp** | Email open rate, CTR, list growth, unsubscribes |
> | **ActiveCampaign** | Email performance, automations, list health |
>
> **Product & User Analytics**
> | Tool | What it unlocks |
> |------|----------------|
> | **PostHog** | Events, funnels, retention, feature flags |
> | **Mixpanel** | DAU/MAU, funnels, cohort retention |
>
> **Customer Success & Support**
> | Tool | What it unlocks |
> |------|----------------|
> | **Intercom** | Conversations, CSAT, response times, churn signals |
> | **Zendesk** | Ticket volume, resolution time, CSAT, SLA compliance |
>
> **Productivity & Data**
> | Tool | What it unlocks |
> |------|----------------|
> | **Google Sheets** | Any dashboard or report you maintain in Sheets |
> | **Google Drive** | Reports, board decks, financial exports stored in Drive |
> | **Gmail** | Weekly reports emailed to you, investor updates |
> | **Notion** | OKR trackers, team wikis, project status |
> | **Slack** | Team pulse, key channel summaries |
>
> **E-commerce**
> | Tool | What it unlocks |
> |------|----------------|
> | **Shopify** | Revenue, orders, AOV, conversion rate, refunds |
>
> Which would you like to connect first? I recommend starting with **HubSpot** or **GA4** — both are 5 minutes to set up."

---

## HubSpot — Setup walkthrough

**Time to set up: 5–10 minutes**
**What you'll get:** Live pipeline, deals, leads, email performance pulled automatically

### Step 1 — Create a HubSpot Private App

Tell the CEO:
> "We need a HubSpot Private App token. Here's how to get it:
>
> 1. Log into HubSpot
> 2. Click **Settings** (gear icon, top right)
> 3. Go to **Integrations → Private Apps**
> 4. Click **Create a private app**
> 5. Name it: `CEO Assistant`
> 6. Go to the **Scopes** tab and enable:
>    - `crm.objects.contacts.read`
>    - `crm.objects.deals.read`
>    - `crm.objects.companies.read`
>    - `marketing-email` (read)
>    - `forms` (read)
> 7. Click **Create app**
> 8. Copy the **Access Token** — it starts with `pat-`
>
> Paste the token here and I'll give you the exact setup command."

### Step 2 — Install the MCP

Once the CEO shares their token, give them this command:

```bash
claude mcp add hubspot \
  -e HUBSPOT_ACCESS_TOKEN=pat-YOUR-TOKEN-HERE \
  -- npx -y @hubspot/mcp-server
```

Tell them:
> "Open your Terminal app (search 'Terminal' on Mac), paste this command with your actual token, and press Enter. It installs in about 30 seconds."

### Step 3 — Restart and verify

> "Restart Claude Code after running the command. Then come back and say 'check my HubSpot connection' — I'll confirm it's working and pull your first live pipeline data."

### Verify connection

When the CEO says "check my HubSpot connection", attempt:
- `mcp__hubspot__get_deals` or `mcp__hubspot__search_objects`

If it responds: ✅ "HubSpot is connected. Here's your current pipeline:" → pull and show pipeline data
If it fails: "The connection didn't work. Let's troubleshoot — did you restart Claude Code after running the command?"

---

## Google Analytics 4 — Setup walkthrough

**Time to set up: 10–15 minutes**
**What you'll get:** Live traffic, conversions, channel performance, top pages

### Step 1 — Create a Google Cloud Service Account

Tell the CEO:
> "GA4 needs a service account to connect securely. Here's how:
>
> 1. Go to **console.cloud.google.com**
> 2. Create a new project (or use an existing one) — name it `CEO Assistant`
> 3. Search for **'Google Analytics Data API'** and click **Enable**
> 4. Go to **IAM & Admin → Service Accounts**
> 5. Click **Create Service Account**
>    - Name: `ceo-assistant`
>    - Click **Create and Continue**
>    - Skip the optional steps, click **Done**
> 6. Click on the service account you just created
> 7. Go to **Keys → Add Key → Create new key → JSON**
> 8. Download the JSON file — save it somewhere safe (e.g. Desktop)"

### Step 2 — Add service account to GA4

> "Now add it to your GA4 property:
>
> 1. Go to **analytics.google.com**
> 2. Click **Admin** (gear icon)
> 3. Under **Property**, click **Property access management**
> 4. Click **+** to add a user
> 5. Enter the service account email (it's in the JSON file, looks like `ceo-assistant@your-project.iam.gserviceaccount.com`)
> 6. Set role to **Viewer**
> 7. Click **Add**"

### Step 3 — Find your GA4 Property ID

> "In GA4, go to **Admin → Property Settings** — your Property ID is a number like `123456789`. Copy it."

### Step 4 — Install the MCP

Once you have the JSON file path and Property ID:

```bash
claude mcp add google-analytics \
  -e GA4_PROPERTY_ID=YOUR_PROPERTY_ID \
  -e GOOGLE_APPLICATION_CREDENTIALS=/path/to/your-service-account.json \
  -- npx -y @modelcontextprotocol/server-google-analytics
```

> "Replace `YOUR_PROPERTY_ID` with the number from Step 3, and `/path/to/your-service-account.json` with the actual path to the JSON file you downloaded (e.g. `/Users/yourname/Desktop/ceo-assistant-abc123.json`)."

### Step 5 — Restart and verify

> "Restart Claude Code, then say 'check my GA4 connection'. I'll pull your last 30 days of traffic data to confirm it's working."

---

## QuickBooks — Setup walkthrough

**Time to set up: 15–20 minutes**
**What you'll get:** Live P&L, cash on hand, burn rate, runway**

Note: QuickBooks uses OAuth 2.0 which is more complex. The easiest path for most CEOs:

**Option A — Google Sheets bridge (recommended, 5 min)**
> "The easiest way to connect QuickBooks is to export your P&L monthly to Google Drive, then I'll read it automatically from there. Here's how:
>
> 1. In QuickBooks: **Reports → Profit & Loss → Export → Google Sheets**
> 2. Connect Google Drive MCP (see below)
> 3. Tell me your Google Drive folder name — I'll find and read the latest export automatically"

**Option B — Direct QuickBooks MCP (15–20 min, more technical)**

```bash
# First install the QuickBooks MCP
claude mcp add quickbooks \
  -e QB_CLIENT_ID=YOUR_CLIENT_ID \
  -e QB_CLIENT_SECRET=YOUR_CLIENT_SECRET \
  -e QB_REFRESH_TOKEN=YOUR_REFRESH_TOKEN \
  -e QB_REALM_ID=YOUR_COMPANY_ID \
  -- npx -y quickbooks-mcp-server
```

> "To get these credentials:
> 1. Go to **developer.intuit.com**
> 2. Create an app → OAuth 2.0
> 3. Get Client ID and Secret from the app dashboard
> 4. Complete OAuth flow to get your Refresh Token
>
> This is more technical — if you want the quick path, use Option A."

---

## Google Drive — Setup walkthrough

**Time to set up: 5 minutes**
**What you'll get:** Automatic reading of reports, dashboards, board decks stored in Drive**

```bash
claude mcp add gdrive \
  -e GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json \
  -- npx -y @modelcontextprotocol/server-gdrive
```

> "Use the same service account JSON you created for GA4 — or create a new one. Make sure the service account has access to your shared Drive folders."

---

## Salesforce — Setup walkthrough

**Time to set up: 15–20 minutes**
**What you'll get:** Live pipeline, quota attainment, win/loss data**

```bash
claude mcp add salesforce \
  -e SF_USERNAME=your@email.com \
  -e SF_PASSWORD=yourpassword \
  -e SF_SECURITY_TOKEN=yourtoken \
  -e SF_LOGIN_URL=https://login.salesforce.com \
  -- npx -y salesforce-mcp-server
```

> "To get your Security Token: Salesforce → Settings → My Personal Information → Reset My Security Token. It will be emailed to you."

---

## Checking what's connected

When the CEO says "what's connected" or "check my integrations":

Try each tool silently, then report:
```
Your connected tools:
✅ HubSpot — pipeline and marketing data live
✅ GA4 — website analytics live
⚠️ QuickBooks — not connected (use Google Drive bridge or set up direct)
⚠️ Salesforce — not connected
⚠️ Mixpanel — not connected (no MCP available yet — export to Sheets)
⚠️ MS Clarity — not connected (API too limited for CEO reporting)

Say "connect [tool name]" to set up any of these.
```

---

## Troubleshooting

**"The command didn't work"**
> "Try this — copy the command exactly, including the quotes. Make sure you replaced the placeholder values (YOUR_TOKEN etc) with your actual credentials. If you see a permission error, run: `sudo npm install -g npx` first."

**"It says the MCP is connected but data isn't showing"**
> "Restart Claude Code fully (quit and reopen). Then say 'check my [tool] connection' again."

**"I don't have Terminal / I'm not technical"**
> "That's fine — the Google Sheets bridge works without any commands. Export your reports to a Google Sheet, connect Google Drive (one command), and I'll read them automatically. Want me to walk you through that instead?"

**"I'm getting an authentication error"**
> "Your token may have expired or the scopes may be wrong. Go back to HubSpot/Google Cloud and regenerate the token with the permissions listed in the setup steps. Then re-run the install command with the new token."

---

## Stripe — Setup walkthrough

**Time: 5 minutes | What you get: Live MRR, ARR, churn, new revenue, failed payments**

### Step 1 — Get Stripe API key
> "1. Log into Stripe dashboard
> 2. Go to **Developers → API keys**
> 3. Copy your **Secret key** (starts with `sk_live_`)
> 4. ⚠️ Never share this key publicly — it has full account access"

### Step 2 — Install
```bash
claude mcp add stripe \
  -e STRIPE_SECRET_KEY=sk_live_YOUR_KEY \
  -- npx -y @stripe/mcp-server-stripe
```

### What it pulls automatically
- MRR and ARR (current + trend)
- New subscriptions this month
- Churned subscriptions (cancelled)
- Failed payments and recovery rate
- Revenue by plan/product
- Top customers by revenue

---

## Xero — Setup walkthrough

**Time: 10 minutes | What you get: P&L, cash flow, invoices, expenses**

### Step 1 — Create Xero App
> "1. Go to **developer.xero.com**
> 2. Click **New App**
> 3. Name it `CEO Assistant`, select **Web app**
> 4. Redirect URI: `http://localhost:3000/callback`
> 5. Copy **Client ID** and **Client Secret**"

### Step 2 — Install
```bash
claude mcp add xero \
  -e XERO_CLIENT_ID=YOUR_CLIENT_ID \
  -e XERO_CLIENT_SECRET=YOUR_CLIENT_SECRET \
  -- npx -y xero-mcp-server
```

### What it pulls automatically
- Profit & Loss (current month + YTD)
- Balance sheet (cash, assets, liabilities)
- Aged receivables (overdue invoices)
- Expense breakdown by category
- Cash flow statement

---

## Pipedrive — Setup walkthrough

**Time: 5 minutes | What you get: Pipeline, deals, activity, revenue forecast**

### Step 1 — Get API token
> "1. Log into Pipedrive
> 2. Go to **Settings → Personal preferences → API**
> 3. Copy your **Personal API token**"

### Step 2 — Install
```bash
claude mcp add pipedrive \
  -e PIPEDRIVE_API_TOKEN=YOUR_TOKEN \
  -- npx -y pipedrive-mcp-server
```

### What it pulls automatically
- Open deals by stage
- Deals closed this month vs target
- Win rate and average deal size
- Overdue activities (calls, emails not completed)
- Revenue forecast (weighted pipeline)

---

## Mailchimp — Setup walkthrough

**Time: 5 minutes | What you get: Email open rates, CTR, list growth, campaign performance**

### Step 1 — Get API key
> "1. Log into Mailchimp
> 2. Go to **Account → Extras → API keys**
> 3. Click **Create A Key**
> 4. Copy the key"

### Step 2 — Find your data center
> "Look at your Mailchimp URL — it shows `us1`, `us6`, `eu1` etc. That's your data center."

### Step 3 — Install
```bash
claude mcp add mailchimp \
  -e MAILCHIMP_API_KEY=YOUR_KEY \
  -e MAILCHIMP_DATA_CENTER=us1 \
  -- npx -y mailchimp-mcp-server
```

### What it pulls automatically
- Last 5 campaign performance (open rate, CTR, unsubscribes)
- List growth (new subscribers vs unsubscribes)
- Best performing subject lines
- Audience health (engagement rate)

---

## ActiveCampaign — Setup walkthrough

**Time: 5 minutes | What you get: Email performance, automation health, contact activity**

### Step 1 — Get API credentials
> "1. Log into ActiveCampaign
> 2. Go to **Settings → Developer**
> 3. Copy your **API URL** and **API Key**"

### Step 2 — Install
```bash
claude mcp add activecampaign \
  -e AC_API_URL=https://youraccountname.api-us1.com \
  -e AC_API_KEY=YOUR_KEY \
  -- npx -y activecampaign-mcp-server
```

### What it pulls automatically
- Active automations and their performance
- Campaign open and click rates
- Contact list health (active vs unengaged)
- Deal pipeline (if using CRM features)

---

## Google Ads — Setup walkthrough

**Time: 10 minutes | What you get: Spend, ROAS, clicks, conversions, cost per lead**

### Step 1 — Get credentials
> "Use the same Service Account you created for GA4 (or create a new one):
> 1. Go to **Google Cloud Console → IAM → Service Accounts**
> 2. Enable the **Google Ads API** for your project
> 3. In Google Ads: **Tools → API Center → Link service account**"

### Step 2 — Find your Customer ID
> "In Google Ads, your Customer ID is the 10-digit number at the top right (xxx-xxx-xxxx format)."

### Step 3 — Install
```bash
claude mcp add google-ads \
  -e GOOGLE_ADS_CUSTOMER_ID=YOUR_CUSTOMER_ID \
  -e GOOGLE_ADS_DEVELOPER_TOKEN=YOUR_DEV_TOKEN \
  -e GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json \
  -- npx -y google-ads-mcp-server
```

### What it pulls automatically
- Total spend (this month vs last month)
- ROAS by campaign
- Cost per conversion by campaign
- Top performing and worst performing ads
- Budget utilization

---

## PostHog — Setup walkthrough

**Time: 5 minutes | What you get: User events, funnels, retention, feature adoption**

### Step 1 — Get API key
> "1. Log into PostHog
> 2. Go to **Project Settings → Project API Key**
> 3. Copy the key (starts with `phx_`)"

### Step 2 — Find your host
> "If using PostHog Cloud: `https://app.posthog.com`
> If self-hosted: your own domain (e.g. `https://posthog.yourcompany.com`)"

### Step 3 — Install
```bash
claude mcp add posthog \
  -e POSTHOG_API_KEY=phx_YOUR_KEY \
  -e POSTHOG_HOST=https://app.posthog.com \
  -- npx -y posthog-mcp-server
```

### What it pulls automatically
- DAU / WAU / MAU
- Funnel completion rates (signup → activation → retention)
- Feature flag adoption
- Top events by volume
- Cohort retention (day 1, 7, 30)
- Session recordings count by page

---

## Intercom — Setup walkthrough

**Time: 5 minutes | What you get: Support conversations, CSAT, response times, at-risk users**

### Step 1 — Get Access Token
> "1. Log into Intercom
> 2. Go to **Settings → Integrations → Developer Hub**
> 3. Create a new app or use existing
> 4. Go to **Authentication → Access Token**
> 5. Copy the token"

### Step 2 — Install
```bash
claude mcp add intercom \
  -e INTERCOM_ACCESS_TOKEN=YOUR_TOKEN \
  -- npx -y intercom-mcp-server
```

### What it pulls automatically
- Open conversation count and age
- Median first response time (vs SLA)
- CSAT score (current month)
- Conversations by tag (bug reports, billing, churn risk)
- Users who explicitly said they're cancelling
- New conversations opened this week

---

## Zendesk — Setup walkthrough

**Time: 5 minutes | What you get: Ticket volume, resolution time, CSAT, SLA compliance**

### Step 1 — Get API credentials
> "1. Log into Zendesk
> 2. Go to **Admin → Apps and Integrations → Zendesk API**
> 3. Enable Token Access
> 4. Click **Add API token** and copy it"

### Step 2 — Install
```bash
claude mcp add zendesk \
  -e ZENDESK_SUBDOMAIN=yourcompany \
  -e ZENDESK_EMAIL=your@email.com \
  -e ZENDESK_API_TOKEN=YOUR_TOKEN \
  -- npx -y zendesk-mcp-server
```

### What it pulls automatically
- Open tickets by priority (Critical / High / Normal)
- Average first reply time vs SLA target
- Average resolution time
- CSAT score (last 30 days)
- Tickets by category (billing, technical, feature request)
- Overdue SLA tickets (needs CEO attention)

---

## Google Sheets — Setup walkthrough

**Time: 5 minutes | What you get: Any dashboard or tracker you maintain in Sheets**

The most flexible integration — if you track anything in Google Sheets (KPI dashboards, OKR trackers, sales pipelines), this reads it automatically.

### Step 1 — Set up (uses same Google credentials as GA4)
```bash
claude mcp add google-sheets \
  -e GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json \
  -- npx -y @modelcontextprotocol/server-google-sheets
```

### Step 2 — Share your Sheets with the service account
> "For each Sheet you want me to read:
> 1. Open the Google Sheet
> 2. Click **Share**
> 3. Add the service account email as **Viewer**
>    (it's in your JSON file, looks like `ceo-assistant@project.iam.gserviceaccount.com`)"

### What it pulls automatically
- Any spreadsheet you've shared with it
- Reads tables, dashboards, and structured data
- Perfect for: KPI trackers, weekly metrics sheets, financial models, OKR trackers

> **Tip:** Name your sheet tabs clearly — "Finance", "Sales Pipeline", "OKRs" — so I can find the right data quickly.

---

## Gmail — Setup walkthrough

**Time: 10 minutes | What you get: Weekly reports sent to you, investor updates, customer escalations**

Many teams send weekly/monthly reports via email. This reads those automatically for your digest.

### Step 1 — Create OAuth credentials
> "1. Go to **console.cloud.google.com**
> 2. Enable the **Gmail API**
> 3. Go to **OAuth consent screen** → set up (Internal, if G Suite)
> 4. Go to **Credentials → Create Credentials → OAuth Client ID**
> 5. Type: Desktop app
> 6. Download the JSON credentials file"

### Step 2 — Install
```bash
claude mcp add gmail \
  -e GOOGLE_CREDENTIALS_PATH=/path/to/oauth-credentials.json \
  -- npx -y @modelcontextprotocol/server-gmail
```

### What it searches for automatically
- Emails with "weekly report", "monthly update", "sales summary", "board update" in subject
- Emails from your direct reports
- Investor updates sent in the last 7 days
- Customer escalations flagged to you

---

## Google Drive — Setup walkthrough

**Time: 5 minutes | What you get: Board decks, finance reports, any file stored in Drive**

### Step 1 — Install (uses same service account as GA4)
```bash
claude mcp add gdrive \
  -e GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json \
  -- npx -y @modelcontextprotocol/server-gdrive
```

### Step 2 — Share folders
> "Share your key folders with the service account email:
> - Finance Reports
> - Board Decks
> - Sales Reports
> - Marketing Reports"

### What it reads automatically
- Most recently modified files in shared folders
- PDFs, Google Docs, Google Sheets, Slides
- Searches by filename and content

---

## Notion — Setup walkthrough

**Time: 5 minutes | What you get: OKR pages, project status, team wikis, meeting notes**

### Step 1 — Create a Notion integration
> "1. Go to **notion.so/my-integrations**
> 2. Click **New integration**
> 3. Name it `CEO Assistant`
> 4. Copy the **Internal Integration Token**"

### Step 2 — Share pages with the integration
> "For each Notion page you want me to access:
> 1. Open the page
> 2. Click **Share** (top right)
> 3. Click **Invite** → search for `CEO Assistant`
> 4. Add as **Can view**"

### Step 3 — Install
```bash
claude mcp add notion \
  -e NOTION_API_KEY=secret_YOUR_TOKEN \
  -- npx -y @modelcontextprotocol/server-notion
```

### What it reads automatically
- OKR database (progress, owners, status)
- Project tracker (status of key initiatives)
- Meeting notes (last 7 days)
- Any page or database you've shared

---

## Slack — Setup walkthrough

**Time: 10 minutes | What you get: Key channel summaries, team pulse, important messages**

### Step 1 — Create a Slack App
> "1. Go to **api.slack.com/apps**
> 2. Click **Create New App → From scratch**
> 3. Name it `CEO Assistant`, select your workspace
> 4. Go to **OAuth & Permissions → Scopes → Bot Token Scopes**
> 5. Add these scopes: `channels:read`, `channels:history`, `users:read`
> 6. Click **Install to Workspace**
> 7. Copy the **Bot User OAuth Token** (starts with `xoxb-`)"

### Step 2 — Install
```bash
claude mcp add slack \
  -e SLACK_BOT_TOKEN=xoxb_YOUR_TOKEN \
  -- npx -y @modelcontextprotocol/server-slack
```

### What it reads automatically
- Recent messages in channels you specify (e.g. #general, #sales, #engineering)
- Threads with high reaction counts (important discussions)
- Messages from key team members in the last 48 hours
- Incident or alert channels for operational issues

> **CEO use case:** Say "summarize #engineering from this week" or "what's the team talking about in #sales?"

---

## Shopify — Setup walkthrough

**Time: 5 minutes | What you get: Revenue, orders, AOV, conversion rate, refunds, top products**

### Step 1 — Create a Custom App
> "1. Log into Shopify Admin
> 2. Go to **Settings → Apps and sales channels → Develop apps**
> 3. Click **Create an app**
> 4. Name it `CEO Assistant`
> 5. Go to **API credentials → Configure Admin API scopes**
> 6. Enable: `read_orders`, `read_products`, `read_analytics`, `read_customers`
> 7. Click **Install app**
> 8. Copy the **Admin API access token**"

### Step 2 — Find your store domain
> "Your store domain is `yourstore.myshopify.com` (find it in Settings → Store details)"

### Step 3 — Install
```bash
claude mcp add shopify \
  -e SHOPIFY_ACCESS_TOKEN=shpat_YOUR_TOKEN \
  -e SHOPIFY_SHOP_DOMAIN=yourstore.myshopify.com \
  -- npx -y shopify-mcp-server
```

### What it pulls automatically
- Total revenue (today, this week, this month vs last)
- Order count and average order value (AOV)
- Conversion rate (sessions → purchases)
- Top 10 products by revenue
- Refund rate (returns as % of orders)
- New vs returning customer ratio
- Cart abandonment rate

---

## Checking all connections

When the CEO says "what's connected", "check my integrations", or "what tools do you have access to":

Try each tool silently, then show a status board:

```
Your Connected Tools — [Date]

FINANCE
✅ Stripe — MRR and revenue data live
✅ QuickBooks — P&L and cash data live
⚠️ Xero — not connected

SALES & CRM
✅ HubSpot — pipeline and leads live
⚠️ Salesforce — not connected
⚠️ Pipedrive — not connected

MARKETING
✅ Google Analytics 4 — traffic data live
⚠️ Google Ads — not connected
⚠️ Mailchimp — not connected

PRODUCT & ANALYTICS
⚠️ PostHog — not connected
⚠️ Mixpanel — not connected (no MCP yet)

CUSTOMER SUCCESS
⚠️ Intercom — not connected
⚠️ Zendesk — not connected

PRODUCTIVITY
✅ Google Sheets — dashboard access live
✅ Notion — OKR and project pages live
⚠️ Slack — not connected
⚠️ Gmail — not connected

E-COMMERCE
⚠️ Shopify — not connected

Say "connect [tool name]" for step-by-step setup of any tool above.
```

