# Connecting Your Tools — In-Skill Setup Guide

Use this when the CEO says "connect my HubSpot", "set up GA4", "how do I connect QuickBooks", "what integrations are available", or "how do I get live data".

This is the in-skill setup wizard. Walk the CEO through connecting their tools step by step — inside this conversation.

---

## Start here — what's available

When the CEO asks about integrations, first show them this:

> "Here are the tools you can connect to get live data in your weekly digest and reports — no more pasting spreadsheets:
>
> | Tool | What it unlocks |
> |------|----------------|
> | **HubSpot** | Live pipeline, leads, email performance, CAC |
> | **Google Analytics 4** | Live traffic, conversions, channel breakdown |
> | **QuickBooks / Xero** | Live cash, burn, runway, gross margin |
> | **Salesforce** | Live pipeline, quota, win/loss |
> | **Mixpanel** | Live user activity, retention, activation |
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
