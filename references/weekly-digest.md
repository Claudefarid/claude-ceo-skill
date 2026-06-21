# CEO Weekly Digest

Use this when the CEO says "give me my weekly digest", "weekly summary", "how did the week go", "what's the state of the business", or any variation of a full cross-domain business summary.

The Weekly Digest is the CEO's single most important recurring output — a complete picture of the business in under 5 minutes of reading.

---

## How to generate the Weekly Digest

1. Load `company-profile.md` for current metrics and goals
2. **Auto-pull from connected tools** (check `references/integrations.md`):
   - QuickBooks → cash, burn, runway, gross margin
   - HubSpot → leads, pipeline, deals closed, win rate
   - GA4 → sessions, conversions, top channels
   - Mixpanel → DAU/MAU, retention, activation
3. If tools are connected: generate digest from live data — do NOT ask the CEO to paste anything
4. If tools are NOT connected: say "I can pull this automatically if you connect HubSpot, GA4, or QuickBooks. For now, share any reports and I'll compile the digest."
5. Run the red flag check across ALL domains before writing
6. Generate the digest using the format below

**Data source line** — always show at the top of the digest:
> *Data sources: QuickBooks ✅ | HubSpot ✅ | GA4 ✅ | Mixpanel ⚠️ (not connected) | Manual inputs: [list any]*

---

## Weekly Digest format

---

# [Company Name] — Weekly Business Digest
**Week ending [Date]**
*Prepared for CEO*

---

## 🔴 Alerts This Week
*Only show if red flags triggered. Remove this section if none.*

- 🔴 **[Alert name]:** [One sentence. Recommended action.]
- ⚠️ **[Warning name]:** [One sentence. What to watch.]

---

## Executive Summary
*3 sentences max. Overall business health, biggest win, biggest concern.*

[One sentence on overall momentum — are we accelerating, holding steady, or slowing?]
[One sentence on the biggest positive signal this week.]
[One sentence on the biggest risk or concern.]

---

## Finance
| Metric | This Week / Month | vs Last | Benchmark | Status |
|--------|-------------------|---------|-----------|--------|
| Revenue (MRR/ARR) | $X | +/-% | $X (target) | ✅/⚠️/🔴 |
| Cash on Hand | $X | — | — | ✅/⚠️/🔴 |
| Burn Rate | $X/mo | +/-% | — | ✅/⚠️/🔴 |
| Runway | X months | — | >12 mo = safe | ✅/⚠️/🔴 |

**Insight:** [One sentence — what the finance numbers mean for the business right now]

---

## Sales
| Metric | This Week | vs Last | Status |
|--------|-----------|---------|--------|
| New Revenue Closed | $X | +/-% | ✅/⚠️/🔴 |
| Pipeline Value | $X | +/-% | ✅/⚠️/🔴 |
| Quota Attainment | X% | — | ✅/⚠️/🔴 |
| Deals Closed | X | — | ✅/⚠️/🔴 |

**Top deal this week:** [Name, value, status]
**Biggest risk:** [Deal or trend at risk]

---

## Marketing
| Metric | This Week | vs Last | Status |
|--------|-----------|---------|--------|
| Leads Generated | X | +/-% | ✅/⚠️/🔴 |
| Best Channel | [Channel] | — | — |
| CAC | $X | +/-% | ✅/⚠️/🔴 |

**Insight:** [One sentence — what the marketing numbers are telling us]

---

## Customer Success
| Metric | This Week | vs Last | Status |
|--------|-----------|---------|--------|
| Churn Rate | X% | +/-% | ✅/⚠️/🔴 |
| NPS | X | +/-% | ✅/⚠️/🔴 |
| At-Risk Accounts | X | — | ✅/⚠️/🔴 |

**Needs CEO attention:** [Account name or issue that needs personal intervention, if any]

---

## Product & Operations
**Shipped this week:** [Top 1–2 things delivered]
**Blocked or at risk:** [What's stuck]
**Ops status:** [Any incidents, vendor issues, or SLA concerns]

---

## Team & HR
**Headcount:** [X] employees | [X] open roles
**This week:** [Notable hire, departure, or team update]
**Watch:** [Any team health concern]

---

## OKR Progress (Quarter to date)
| Objective | Progress | On Track? |
|-----------|----------|-----------|
| [Obj 1] | X% | ✅/⚠️/🔴 |
| [Obj 2] | X% | ✅/⚠️/🔴 |
| [Obj 3] | X% | ✅/⚠️/🔴 |

---

## CEO Priorities — Next 7 Days
*The 3 highest-leverage things the CEO should personally focus on.*

1. **[Priority]** — [Why it matters this week] — [Owner if not CEO]
2. **[Priority]** — [Why it matters this week] — [Owner if not CEO]
3. **[Priority]** — [Why it matters this week] — [Owner if not CEO]

---

## Decisions Needed This Week
*Only include items that require a CEO decision.*

- [Decision] — [Context in one sentence] — [Deadline]
- [Decision] — [Context in one sentence] — [Deadline]

---

## One Thing to Watch
*The single biggest risk or opportunity over the next 30 days that the CEO should have on their radar.*

[2–3 sentences. Specific, forward-looking, actionable.]

---

*Next digest: [Date of next week]*
*To update your company profile: say "update my company profile"*

---

## Weekly Digest rules

- **Never pad.** If a section has no news, write "No changes this week" and move on.
- **Always show benchmarks** for key metrics — load `references/benchmarks.md`
- **Prioritize alerts.** If there are red flags, they go first — the CEO should see problems before summaries.
- **CEO priorities must be specific.** "Focus on sales" is not useful. "Call the 3 at-risk enterprise accounts before Thursday" is.
- **Decisions section is only for real decisions** — not tasks, not updates. Only include something here if the CEO must choose.
- **Keep the full digest under 600 words** of prose. Tables don't count toward this limit.

---

## Monthly variant — Monthly Business Review

When the CEO asks for a monthly review, use the same format but:
- Replace "This Week" with "This Month"
- Add a "Month in Review" narrative paragraph (5–6 sentences, honest assessment)
- Add a "Next Month Plan" section with the top 5 priorities
- Include a trend line for key metrics (3-month view where available)
- Include a "What We Learned" section — what assumptions were tested, what changed?
