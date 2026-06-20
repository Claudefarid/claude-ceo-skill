# Product & Tech — CEO Guide

Use this when the CEO needs to understand or act on product matters: roadmap status, feature requests, bug escalations, release updates, tech debt, or engineering team health.

---

## Standard output format

**Product Summary — [Period]**

**Headline:** [One sentence: is the product moving forward, stuck, or at risk?]

**Key metrics:**
| Metric | This Period | Last Period | Status |
|--------|-------------|-------------|--------|
| Features shipped | X | X | ✅ / ⚠️ / 🔴 |
| Active bugs (critical) | X | X | ✅ / ⚠️ / 🔴 |
| Uptime / reliability | X% | X% | ✅ / ⚠️ / 🔴 |
| Sprint velocity | X pts | X pts | ✅ / ⚠️ / 🔴 |
| Time to ship (avg) | X days | X days | ✅ / ⚠️ / 🔴 |

**What shipped:** [Top 1–2 features or improvements delivered]

**What's blocked:** [What is stuck and why — no technical jargon]

**Recommended action:** [One CEO-level decision or intervention]

**Next steps:**
1. [Owner] — [Action] — [By when]

---

## How to handle specific product situations

### Roadmap review
Present as 3 time horizons only:
- **Now (this month):** What is being built right now? What will it do for customers?
- **Next (next quarter):** What's planned? What customer problem does it solve?
- **Later (6+ months):** Strategic bets — what are we building toward?

CEO question to ask: Is the roadmap driven by customer needs or internal preferences? If you can't link each item to a customer problem or revenue impact, it needs rethinking.

### Feature request escalation
- Who is asking? (customer, sales team, investor, internal)
- How many customers would benefit? (1, a few, most)
- Revenue at risk if we don't build it? ($X or a named deal)
- Engineering estimate: small (days), medium (weeks), large (months)
- CEO recommendation: prioritize now / add to backlog / decline with rationale

### Bug escalation
Present as:
- **Severity:** Critical (product broken) / High (major feature broken) / Medium / Low
- **Who is affected:** All users / X% of users / specific segment
- **Business impact:** Churn risk / SLA breach / support ticket volume
- **Current status:** Being fixed / workaround available / under investigation
- **ETA to resolve:** [Date or "unknown — escalating"]

CEO should only see Critical and High severity bugs. Others are for the team to manage.

### Release or launch update
- What launched? (plain language description)
- Who gets it and when?
- What does it change for the customer?
- Are there any risks or known issues?
- How will it be communicated? (in-app, email, support docs)

### Tech debt or infrastructure concern
Tech debt = shortcuts taken earlier that slow the team down now.
- What is the issue? (in plain language)
- How much is it slowing the team? (X% of engineering time lost)
- Risk if not addressed: (system outage, security vulnerability, can't scale)
- Investment needed: (X weeks of engineering time)
- CEO decision: schedule now / defer to next quarter / accept the risk

---

## Common product terms — plain language

| Term | What it means |
|------|--------------|
| Sprint | A 1–2 week work cycle where the team commits to delivering specific things |
| Velocity | How much work the team completes per sprint — tracks capacity and pace |
| MVP (Minimum Viable Product) | The simplest version of a feature that delivers real value to customers |
| Tech debt | Code shortcuts that work now but create problems later if not cleaned up |
| Bug | Something that is broken or behaving incorrectly |
| Critical bug | A bug that prevents customers from using the product at all |
| Backlog | The full list of features and fixes not yet started |
| Roadmap | The plan for what product will build and in what order |
| API | A way for two systems to talk to each other (e.g. your product connecting to Stripe) |
| Uptime | % of time the product is available and working for customers |
| Deployment / release | Pushing new code live so customers can use it |
| A/B test | Showing two versions of something to different users to see which performs better |

---

## Red flags to always surface

- A critical bug open for more than 48 hours with no fix timeline
- Engineering velocity dropping more than 20% two sprints in a row
- A feature that was promised to a key customer slipping its delivery date
- Tech debt consuming more than 25% of engineering capacity
- No product releases in 3+ weeks (team may be stuck or blocked)
- A security vulnerability that hasn't been patched

---

## CEO questions worth asking every product review

1. What did we ship this month — and did customers actually use it?
2. What is the team stuck on right now?
3. Is there anything on the roadmap we should kill or defer to free up capacity?
4. Are there any promises made to customers or sales that engineering can't meet?

---

## When to invoke specialist skills

- **Competitor product analysis:** invoke `competitor-profiling` to see what competitors are shipping
- **SEO for product pages:** invoke `seo-audit` to check product landing page performance
- **User research on feature requests:** invoke `customer-research` to validate what customers actually want
