# Operations — CEO Guide

Use this when the CEO needs to understand or act on operational reports: process performance, vendor issues, delivery metrics, efficiency reports, infrastructure health, supply chain, or cross-team coordination.

---

## Standard output format

**Operations Summary — [Period]**

**Headline:** [One sentence: are operations running smoothly or is something broken?]

**Key metrics:**
| Metric | This Period | Last Period | Status |
|--------|-------------|-------------|--------|
| [Core ops metric — e.g., uptime, delivery rate] | X% | X% | ✅ / ⚠️ / 🔴 |
| [Customer issue resolution time] | X hrs | X hrs | ✅ / ⚠️ / 🔴 |
| [Cost per unit / cost per delivery] | $X | $X | ✅ / ⚠️ / 🔴 |
| [Vendor SLA compliance] | X% | X% | ✅ / ⚠️ / 🔴 |

**What's running well:** [1–2 sentences — what is working reliably]

**Problem requiring CEO attention:** [Be direct — what is broken, slow, or at risk]

**Recommended action:** [One decision or intervention the CEO should make]

**Next steps:**
1. [Owner] — [Action] — [By when]

---

## How to handle specific ops situations

### Incident or outage report
Present as:
- **What happened:** [Plain-language description — no technical jargon]
- **When:** [Start time → resolved time, or still ongoing]
- **Impact:** [How many customers affected, what couldn't they do]
- **Root cause:** [One sentence — what went wrong]
- **Resolution:** [What was done to fix it]
- **Prevention:** [What will stop it from happening again]

CEO takeaway: should this be communicated to customers? Is there a financial or reputational impact?

### Vendor issue
- What did the vendor fail to deliver?
- What is the business impact?
- Options: escalate, switch vendors, or work around it
- Recommendation: [CEO's decision]
- Timeline: how long until resolution

### Process bottleneck
- Where is the slowdown? (team, system, approval step)
- How long has it been happening?
- Quantified impact: [deals delayed, revenue at risk, team hours wasted]
- Recommended fix: [hire, automate, change process, or escalate]

### Cost overrun in operations
- Which ops area is over budget?
- By how much and why?
- Is this a one-time issue or a structural problem?
- Options to address: cut scope, find efficiency, or accept and budget for it
- Recommendation

### Capacity issue
- Is a team, system, or vendor at or near capacity?
- What happens if we don't act? (service degrades, team burns out, revenue is capped)
- Lead time to fix: [how long to hire, upgrade, or scale]
- CEO recommendation: act now or plan for next quarter

---

## Common ops metrics — plain language

| Term | What it means |
|------|--------------|
| SLA (Service Level Agreement) | A promise to deliver something within a set time (e.g., respond to support tickets within 24 hrs) |
| SLA compliance rate | % of the time you're meeting that promise |
| Uptime | % of time a system or service is running without issues. 99.9% = ~9 hrs downtime/year |
| MTTR (Mean Time to Resolve) | Average time to fix a problem after it's detected. Lower = better |
| Throughput | How many units (orders, tickets, deliveries) get processed per period |
| Utilization rate | % of capacity being used. Above 85–90% usually means you're running too hot |
| Error rate | % of outputs that contain defects or failures |

---

## Operational red flags to always surface

- SLA compliance dropping below 95% two months in a row
- A critical vendor dependency with no backup option
- A team running at 90%+ utilization with no relief planned
- An incident that affected customers and wasn't communicated externally
- A manual process that represents a single point of failure (one person who "knows how to do it")
- Operating costs growing faster than revenue

---

## CEO questions worth asking in every ops review

1. Are we able to deliver at current scale? And at 2x?
2. Where are we most dependent on one person, one vendor, or one system?
3. What is the biggest thing slowing the team down right now?
4. What would a customer notice if it broke today?

Use these to prompt the ops team if they're not surfacing problems proactively.

---

## Live data — Zendesk + Slack integration

### Zendesk — SLA and operational health
```
- SLA compliance rate (% of tickets resolved within SLA) — benchmark: >90%
- Critical/P1 tickets open longer than 4 hours → immediate CEO alert
- Ticket volume trend (week over week) — spike = operational incident
- Resolution time by category (technical vs billing vs access)
- Backlog size: tickets open > 72 hours
```

**Red flags from Zendesk operations data:**
- SLA compliance drops below 85% → team capacity or process issue
- P1 tickets open > 4 hours → escalate immediately
- Ticket volume spike >50% vs prior week → potential product incident or outage
- Same issue appearing in multiple tickets → systemic bug or communication gap

### Slack — incident and operations signals
```
Monitor these channels if connected:
- #incidents or #alerts → active operational issues
- #engineering or #devops → deployment issues, outages
- #ops or #operations → vendor, process, or capacity issues
```

**What to pull from Slack:**
- Any message in #incidents from last 24 hours
- Any @here or @channel mentions in ops channels (usually urgent)
- Bot alerts or automated notifications about system status

### Operations summary with live data
```
Operations Pulse — [Date] (Live: Zendesk ✅ Slack ✅)

SLA compliance: X% (benchmark: >90%) ✅/⚠️/🔴
Open P1 tickets: X | Oldest: X hours
Ticket volume: X this week vs X last week (+/-%)
Active incidents: [None / X open in #incidents]
Backlog (>72h): X tickets

🔴 Needs immediate attention: [any P1 or SLA breach]
```

**If not connected:**
> "Connect Zendesk and Slack for live operational data. For now, paste your ops report or incident summary."
