# Skill Health Check

## When the CEO says: "check skill health", "is everything working", "run health check", "test the skill", "verify setup", "what's working"

Run a full diagnostic and report results. This helps new users confirm the skill is working correctly and identify what needs to be set up.

---

## Health check sequence

Run silently, then report all results at once.

### 1. Company profile check
- Read `company-profile.md`
- Check if core fields are populated: `company_name`, `stage`, `mrr_or_arr`, `runway_months`, `current_goals`

**Result format:**
```
Company Profile: ✅ Complete / ⚠️ Partial ([X] of 9 fields set) / 🔴 Empty
```

### 2. Integration check
Try each MCP tool silently:

| Tool | MCP namespace to test |
|------|-----------------------|
| HubSpot | `mcp__hubspot__*` |
| GA4 | `mcp__google-analytics__*` |
| Stripe | `mcp__stripe__*` |
| QuickBooks | `mcp__quickbooks__*` |
| Salesforce | `mcp__salesforce__*` |
| Google Drive | `mcp__gdrive__*` |
| Gmail | `mcp__gmail__*` |
| Notion | `mcp__notion__*` |
| Slack | `mcp__slack__*` |
| Google Sheets | `mcp__google-sheets__*` |

**Result format:**
```
Integrations:
✅ HubSpot — connected
✅ GA4 — connected
⚠️ Stripe — not connected (run: claude mcp add stripe ...)
⚠️ QuickBooks — not connected
⚠️ [rest] — not connected
```

### 3. Reference files check
Confirm key reference files are readable:
- `references/finance.md`
- `references/sales.md`
- `references/weekly-digest.md`
- `references/benchmarks.md`

**Result format:**
```
Reference Files: ✅ All 29 files accessible
```

### 4. Benchmark coverage check
Check `company-profile.md` for `primary_region` and `stage` — confirm benchmarks exist for their combination.

**Result format:**
```
Benchmarks: ✅ [Stage] [Region] benchmarks available
```

---

## Full health report format

```
CEO Assistant — Health Check
[Date]

COMPANY PROFILE
✅ Complete — [Company Name], [Stage], [Region]
Last updated: [date or "never"]

LIVE INTEGRATIONS (X of 20 connected)
✅ HubSpot — pipeline and marketing data live
✅ GA4 — website analytics live
⚠️ Stripe — not connected
⚠️ QuickBooks — not connected
[... rest]

SKILL FILES
✅ All 29 reference files accessible

BENCHMARKS
✅ [Stage] [Region] benchmarks available

OVERALL STATUS: ✅ Ready / ⚠️ Partial / 🔴 Setup needed

RECOMMENDED NEXT STEP:
[One specific action based on the biggest gap found]

---
Having issues? Open an issue at:
github.com/Claudefarid/claude-ceo-skill/issues
```

---

## After health check

If status is 🔴 or ⚠️:
- If profile is empty → run guided setup from `references/setup.md`
- If no integrations → offer to start with connect wizard from `references/connect.md`
- If reference files missing → tell CEO to reinstall: `claude skills install https://github.com/Claudefarid/claude-ceo-skill`

If status is ✅:
- Say: "Everything looks good. Say 'give me my weekly digest' to see it all in action."
