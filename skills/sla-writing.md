# Skill: SLA Writing

> **Trigger:** Creating or revising a Service Level Agreement between teams, departments, or for a managed program/service.
> **Context:** Most SLAs written here will be **internal** — between the Marketing Ops team and other departments, or between Marketing Ops and stakeholders requesting work. Some may be **program SLAs** defining service standards for managed programs like EngageOne or Local Spark.
> **Brand context required:** No — SLAs use internal operational tone (clear, precise, collaborative).

---

## Philosophy: SLAs That Protect Both Sides

An SLA is not a weapon. It's a handshake that's been written down.

The best SLAs do three things:

1. **Set expectations before frustration occurs.** Without an SLA, "ASAP" means something different to every person. An SLA replaces ambiguity with clarity — and clarity prevents conflict.
2. **Protect the providing team's capacity.** A well-written SLA doesn't just promise fast turnaround; it defines what the requesting party must provide and when, so the providing team can deliver quality work on time.
3. **Create a shared language for accountability.** When both sides agree on what "done" looks like, how long it should take, and what happens when things slip, the conversation shifts from blame to problem-solving.

**The golden rule: An SLA should be realistic enough to hit consistently, specific enough to measure objectively, and fair enough that both sides would sign it voluntarily.**

---

## When to Write an SLA

Not every internal arrangement needs an SLA. Use one when:

- **Recurring requests** come from the same team/stakeholder and turnaround expectations are unclear or frequently misaligned.
- **A program or service** is being offered to internal or external users (EngageOne, Local Spark, marketing request intake, etc.) and you need to define what's included and how fast.
- **Cross-departmental work** depends on inputs from both sides — and delays from either side cause downstream problems.
- **Accountability gaps exist.** If the same friction point keeps showing up (late requests, unclear priorities, missed deadlines), an SLA formalizes the fix.

Don't write an SLA for one-off projects, ad hoc favors, or work that doesn't repeat.

---

## Pre-Flight Checklist

Before drafting any SLA, resolve these:

1. **Who is the provider?** (The team delivering the service — likely your Marketing Ops team)
2. **Who is the requester/recipient?** (The team or stakeholders receiving the service)
3. **What is being provided?** Define the specific services covered — and what's explicitly out of scope.
4. **What does each side need from the other?** SLAs are two-way. The provider commits to turnaround and quality; the requester commits to complete briefs, timely feedback, and using the right intake process.
5. **What data exists on current performance?** Set targets based on actual capacity, not aspirational goals. If you don't have data, start with conservative targets and adjust after 90 days.
6. **Check `memory/corrections.md` and `memory/preferences.md`** for SLA-specific learnings.

---

## SLA Structure

Every SLA follows this structure. Sections marked *(optional)* can be omitted for simple agreements.

### 1. Header Block

| Field | Description |
|---|---|
| **Title** | Clear, specific. Format: "[Provider Team] SLA for [Service/Recipient]" |
| **Effective Date** | When this SLA takes effect |
| **Review Date** | When this SLA will be formally reviewed (quarterly recommended) |
| **Owner** | Person responsible for maintaining and enforcing this SLA |
| **Version** | Version number (v1.0, v1.1, etc.) |
| **Stakeholders** | Names and roles of key contacts on both sides |

### 2. Purpose — *Why this SLA exists* (2–4 sentences)

This isn't boilerplate. Write it in plain language so anyone reading understands the problem this SLA solves and the outcome it creates.

**Good example:**
> "This SLA defines the service standards between the Marketing Operations team and the Sales department for marketing asset requests. It establishes clear turnaround times by priority level, defines what constitutes a complete request, and creates accountability on both sides so that requests are fulfilled on time and at quality."

**Bad example:**
> "This document outlines the service level agreement between Marketing and Sales."

### 3. Scope of Services

Two parts — what's **included** and what's **excluded**. Both are equally important. Scope creep is the most common SLA failure mode.

**Structure:**

**Services Covered:**
- List each specific service (e.g., "Marketing email creation in HubSpot," "Social media post creation," "Asana project setup for events")
- Be granular. "Marketing support" is too vague. "Creation and scheduling of marketing emails in HubSpot based on approved copy and creative" is specific.

**Services NOT Covered:**
- List exclusions explicitly (e.g., "Strategy development," "Content writing — copy must be provided by requester," "Paid media management")
- This section prevents scope creep and protects the team from undefined work sneaking in.

**Operating Hours:**
- Define when the team is available (e.g., "Monday–Friday, 8:00 AM – 5:00 PM ET")
- Clarify that SLA timers run on **business hours only** unless stated otherwise

### 4. Request Process — *How to submit work*

This is where most SLAs fail in practice. If the intake process isn't clear, requests come in through Slack DMs, hallway conversations, and "quick favors" — and SLA timers never start.

**Define:**
- **Where to submit:** The exact intake method (e.g., Asana form, specific Asana project, email to a shared inbox). One channel, enforced.
- **What a complete request includes:** List the required fields. Incomplete requests don't start the SLA clock.
- **When the clock starts:** "SLA turnaround begins when a complete request is received through the approved intake channel during operating hours. Requests submitted after 5 PM ET will be treated as received the following business day."

> ⚠️ **Critical:** Requests submitted outside the approved process (Slack messages, verbal asks, emails to personal inboxes) are not governed by this SLA. This isn't bureaucracy — it's how the team manages workload, tracks requests, and ensures nothing falls through cracks.

### 5. Priority Tiers & Turnaround Times

This is the core of the SLA. Define priority levels with clear criteria so there's no ambiguity about which tier a request falls into.

**Priority Matrix Template:**

| Priority | Criteria | Acknowledgment | Turnaround (Completion) |
|---|---|---|---|
| 🔴 **P1 — Critical** | Business-critical, time-sensitive, significant revenue/reputation impact. Examples: broken automation affecting live campaigns, urgent compliance-required communication. | Within 2 business hours | 1 business day |
| 🟠 **P2 — High** | Important with a firm deadline. Examples: event email with a hard send date, time-sensitive announcement. | Within 4 business hours | 3 business days |
| 🟡 **P3 — Standard** | Routine work with a reasonable timeline. Examples: regular marketing email, social post batch, Asana project setup. | Within 1 business day | 5 business days |
| 🟢 **P4 — Low** | Nice-to-have, no firm deadline. Examples: process improvement request, template update, exploratory project. | Within 2 business days | 10 business days or as scheduled |

**Important distinctions:**

- **Acknowledgment ≠ Completion.** Acknowledgment means the provider has received the request, confirmed it's complete, and assigned it a priority. It does not mean the work has started.
- **Turnaround = business days from acknowledgment to delivery of first draft/completion.** Define clearly whether this means "first draft delivered" or "final asset delivered." In most cases, it should mean first draft — revision cycles are separate.
- **Rush requests** that need turnaround faster than their priority tier allows should be flagged explicitly, require approval from the provider team lead, and may result in deprioritization of other work. Document this.

**Adjusting the default numbers:**

The numbers above are starting points. Calibrate based on:
- Your team's actual capacity and current workload
- Historical data (how long do these requests actually take?)
- Stakeholder expectations (what turnaround do they need to do their jobs?)

Start conservative. It's easier to tighten SLAs later than to loosen them after setting aggressive targets you can't hit.

### 6. Requester Responsibilities — *What we need from you*

This section is what makes an SLA fair rather than one-sided. The provider's ability to hit turnaround targets depends on the requester holding up their end.

**Common requester responsibilities:**

- **Submit complete requests.** All required fields filled in. Incomplete requests will be returned for completion, and the SLA clock resets when the complete request is resubmitted.
- **Provide assets on time.** If the request requires copy, images, approvals, or other inputs from the requester, include due dates for those inputs. Delays in providing assets extend the turnaround by the same number of business days.
- **Use the approved intake process.** Requests outside the system aren't tracked and aren't covered.
- **Provide timely feedback.** Define a feedback turnaround (e.g., "Requester will provide feedback on first drafts within 2 business days"). If feedback is late, the completion deadline shifts accordingly.
- **Respect priority definitions.** Not everything is P1. If requesters consistently over-prioritize, address it in the quarterly review.

### 7. Escalation Procedures

Define what happens when things go off track — on either side.

**Provider misses SLA:**
1. Automatic notification to provider team lead when SLA is at 80% of turnaround time with no update.
2. If SLA is breached, provider team lead reviews the cause and communicates a revised timeline within 4 business hours.
3. Repeated breaches (3+ in a quarter) trigger a process review in the next quarterly SLA review.

**Requester causes delay:**
1. Provider notifies requester that missing inputs are blocking the request. SLA clock pauses.
2. If inputs are not received within 2 business days of notification, the request is moved to "On Hold" status and the requester is notified.
3. SLA clock restarts when complete inputs are received.

**Disputes on priority:**
- If the requester and provider disagree on priority assignment, escalate to [defined escalation contact — typically the provider team lead and the requester's manager] for resolution within 1 business day.

### 8. Metrics & Reporting *(optional but recommended)*

Define what gets measured and how it's reported. Keep it simple — two to four metrics that matter.

**Recommended metrics:**

| Metric | Definition | Target |
|---|---|---|
| **SLA Compliance Rate** | % of requests completed within the defined turnaround for their priority tier | 90%+ |
| **Acknowledgment Compliance** | % of requests acknowledged within the defined acknowledgment window | 95%+ |
| **Request Completeness Rate** | % of requests submitted with all required information on first submission | Track to improve |
| **Average Turnaround by Priority** | Actual average turnaround vs. the SLA target, broken out by priority tier | At or below target |

**Reporting cadence:** Monthly summary shared with stakeholders. Quarterly deep-dive review with both sides to adjust targets, address patterns, and refine the process.

> 💡 **Avoid the "watermelon effect."** This is when all metrics look green from the provider's perspective, but the requester's experience is actually poor. Include qualitative feedback (even a simple quarterly pulse check) alongside quantitative metrics to catch this.

### 9. Revision & Review

- **Quarterly review:** Both sides meet to review SLA performance, discuss friction points, and propose adjustments.
- **Trigger-based revisions:** If team capacity changes significantly (new hire, departure, new program launch), the SLA should be reviewed and adjusted within 30 days.
- **Version control:** Every revision gets a new version number and an updated effective date. Keep a changelog.

---

## SLA Types for Marketing Ops

Here are the most common SLA types you'll write, with context for each:

### Internal Request SLA (Marketing Ops ↔ Other Departments)

The most common type. Defines turnaround times for marketing requests from Sales, Recruiting, Leadership, etc.

**Key design choices:**
- Use Asana as the intake system — forms feed into a request project, auto-assign based on type.
- Priority is assigned by the provider (Marketing Ops), not the requester. Requesters can flag urgency, but the provider triages.
- Build in a "revision cycle" definition — first draft is within SLA; revisions restart a shorter mini-SLA (e.g., 2 business days per revision round).

### Program SLA (Marketing Ops ↔ Program Users)

For managed programs like EngageOne or Local Spark. Defines what users can expect when they enroll, what's included in the service, and how support requests are handled.

**Key design choices:**
- Service descriptions need to be very specific (what's included in the program vs. what requires separate work).
- Turnaround times may be tied to vendor timelines (Snappy Kraken, WhiteSpark) — build in buffer.
- Support request process should be separate from the general marketing request intake.

### Team SLA (Within Marketing Ops)

Internal to your team. Defines how work flows between the Marketing Operations Manager, Marketing Automations Specialist, and Marketing Communications Specialist.

**Key design choices:**
- Lighter-weight than a cross-departmental SLA. Can be a one-page agreement.
- Focus on handoff points: when work moves from one team member to another, what's the expected turnaround for the next step?
- Enforce through Asana task assignments and due dates rather than a formal document.

---

## Writing Rules

### Language
- **Be specific, not vague.** "Within a reasonable timeframe" is unenforceable. "Within 3 business days" is clear.
- **Use "must" and "will" for commitments.** "The provider will acknowledge all P1 requests within 2 business hours." Not "should" or "aims to."
- **Use "business days" and "business hours" consistently.** Define them once and reference them throughout.
- **Define jargon.** If the SLA uses terms like "complete request," "acknowledgment," or "first draft," define exactly what those mean in the Scope or Definitions section.

### Tone
- **Collaborative, not adversarial.** The SLA should read like two teams agreeing on how to work well together, not like a legal threat.
- **Practical.** Skip the legalese. Write it so anyone on either team can read it and understand their responsibilities in five minutes.

### Length
- **One to three pages** for most internal SLAs. If it's longer, it's probably trying to cover too many services in one document — split it.
- **Use tables** for priority tiers, metrics, and turnaround times. Tables are scannable and reduce ambiguity.

---

## Common Mistakes to Avoid

| Mistake | Why It Fails | Fix |
|---|---|---|
| Setting turnaround times based on aspirational goals instead of actual capacity | You'll miss SLAs constantly, eroding trust | Base targets on real performance data. Start conservative, tighten over time. |
| One-sided SLA (all obligations on the provider, none on the requester) | Requesters submit incomplete briefs, give late feedback, bypass the process — and blame the provider for missed deadlines | Include a Requester Responsibilities section with specific, measurable commitments. |
| No intake process enforcement | Requests come in through Slack, hallways, and emails — SLA timers never start, work falls through cracks | Define one intake channel. State clearly that requests outside the channel are not covered. |
| Confusing acknowledgment with completion | Requesters expect the work to be done when they get a "received" confirmation | Define both terms explicitly. Acknowledgment = we got it and prioritized it. Completion = deliverable is ready. |
| Not distinguishing first draft from final delivery | Turnaround expectations are misaligned when revisions are needed | Define SLA turnaround as "first draft delivery." Revision cycles are a separate, shorter SLA. |
| No review cadence | The SLA becomes outdated as team capacity, tools, and processes change | Build in quarterly reviews. Treat the SLA as a living document. |
| Too many metrics | Tracking 10+ KPIs dilutes focus and creates reporting overhead | Two to four metrics. Focus on the ones that directly impact the requester's experience and the provider's workload. |

---

## Quality Check — Before Finalizing

- [ ] Purpose section explains why this SLA exists in plain language
- [ ] Scope clearly lists what's covered AND what's excluded
- [ ] Request intake process is defined with one clear channel
- [ ] "Complete request" is defined with specific required fields
- [ ] Priority tiers have clear, objective criteria (not subjective)
- [ ] Both acknowledgment and turnaround/completion times are specified per priority
- [ ] Requester responsibilities are documented (not just provider obligations)
- [ ] Escalation procedures cover both provider delays AND requester delays
- [ ] Turnaround targets are based on actual capacity, not aspirational goals
- [ ] Review cadence is defined (quarterly recommended)
- [ ] Document is under 3 pages and uses tables for key reference data
- [ ] Both sides would willingly sign this

---

## Updating This File

When SLA-specific corrections or new patterns are discovered:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
