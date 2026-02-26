# Skill: Zap Building

> **Trigger:** Building, designing, planning, or optimizing any Zapier workflow (Zap).
> **Context required:** Load `context/asana-sop.md` for MOS standards when the Zap involves Asana. Load relevant system context (HubSpot, Formstack, Fusion) based on the integration target.
> **Governance rule:** All Zaps are owned by Marketing Ops. No team builds Zapier workflows without Marketing Ops approval. This skill produces Zap blueprints and implementation plans — all Zaps go through Marketing Ops for build, testing, and deployment.
> **Companion skill:** For troubleshooting existing broken Zaps, see `skills/zap-troubleshooting.md`.

---

## Philosophy: Automation That Earns Trust

The biggest risk with Zapier isn't a broken Zap — it's a Zap that silently does the wrong thing. A broken Zap fails loudly and gets fixed. A Zap that creates duplicate records, skips data, routes to the wrong portfolio, or burns through task quotas unnoticed erodes trust in the entire automation layer and ultimately in the MOS itself.

Zaps with high reliability share these traits:

1. **Do one job well.** A Zap should have a single, clearly defined purpose. If you can't describe what it does in one sentence, it's trying to do too much.
2. **Fail loudly.** Every Zap should have error handling that surfaces problems before they compound. Silent failures are the most expensive kind.
3. **Validate before acting.** Data coming from external sources (forms, APIs, webhooks) should be checked and formatted before being pushed into Asana, HubSpot, or any system of record.
4. **Minimize task consumption.** Every successfully completed action costs a task. Filters and Paths don't consume tasks — use them aggressively to prevent unnecessary actions from firing.
5. **Be readable by someone who didn't build it.** Descriptive names, renamed steps, Zap descriptions, and documented logic mean anyone on the team can understand, maintain, and troubleshoot the Zap.

**The golden rule: If a Zap breaks at 2am, could another Marketing Ops team member diagnose and fix it using only the Zap's name, description, step labels, and folder location — without calling the person who built it?**

---

## Pre-Flight Checklist

Before building any Zap, answer these:

1. **What is the trigger event?** What specific thing happens in what specific app that should kick off this workflow?
2. **What is the desired outcome?** What should exist, change, or be created when this Zap completes successfully?
3. **What data flows between the systems?** Map every field that needs to move from source to destination. Identify any fields that need transformation (date formats, text splitting, lookups).
4. **What could go wrong?** List the ways this Zap could fail — missing fields, duplicate records, API rate limits, expired auth, unexpected data formats. Each becomes a design consideration.
5. **How often will it fire?** Estimate volume. A Zap that fires 5 times a day has different design needs than one that fires 500 times a day. Volume directly impacts task consumption and plan costs.
6. **Does a similar Zap already exist?** Check the Zapier account for existing Zaps that touch the same apps or serve similar purposes. Duplication wastes tasks and creates conflict.
7. **Can this be done natively instead?** Check if Asana Rules, HubSpot Workflows, or GoHighLevel automations can handle this without Zapier. Use Zapier for cross-system integration, not for things a single app can do internally.

---

## Zapier Platform Reference

### Core Architecture

Every Zap follows the same fundamental structure:

```
Trigger (1 per Zap)
  → Action 1
    → Action 2
      → Action 3
        → ... (up to 100 steps total)
```

- **Trigger:** The event that starts the Zap. One trigger per Zap. Can be a polling trigger (Zapier checks periodically) or an instant/webhook trigger (fires immediately when event occurs).
- **Action:** Something the Zap does — create a record, send a message, update a field, search for data, etc.
- **Task:** Each successfully completed action step consumes one task from the monthly quota. Triggers, Filters, and Paths do NOT consume tasks.

### The Zapier Toolkit

Claude should understand each built-in tool and when to recommend it:

| Tool | What It Does | When to Use | Task Cost |
|---|---|---|---|
| **Filter** | Stops the Zap if conditions aren't met | When you only want the Zap to continue for specific data. Prevents unnecessary downstream actions. | Free (no task consumed) |
| **Paths** | Routes data to different action branches based on conditions | When you need to handle multiple outcomes in one Zap (e.g., different advisor tiers get different treatment). Multiple branches can run in the same Zap run. | Free for the Path step itself; actions within running branches cost tasks |
| **Formatter** | Transforms text, numbers, dates, and utilities | When data from the trigger isn't in the format the action needs. See Formatter section below. | 1 task per Formatter action |
| **Delay** | Pauses the Zap for a set time or until a condition | When timing matters — e.g., wait 24 hours then check status. Minimum delay: 1 minute (as of Jan 2025). | 1 task |
| **Sub-Zap** | Calls another Zap as a reusable component, can return data | When the same set of actions is needed in multiple Zaps. Build once, call from many. Requires a "Return from Sub-Zap" step. | Tasks consumed by actions in the Sub-Zap |
| **Looping** | Repeats action(s) for each item in a list | When processing line items (e.g., multiple products in an order, multiple attendees). Max 500 iterations. Runs in parallel by default. | 1 task per action per loop iteration |
| **Webhooks** | Sends or receives raw HTTP requests | When connecting to APIs without native Zapier integration, or when you need a Zap to be triggered by an external system. | 1 task per webhook action |
| **Code (JavaScript/Python)** | Runs custom code within a Zap | When you need logic that exceeds Zapier's built-in capabilities — complex conditionals, data manipulation, regex parsing, API calls. | 1 task |
| **AI by Zapier** | Uses AI models for text analysis, generation, classification | When you need intelligent processing — sentiment analysis, categorization, summarization, content drafting. | 1 task |
| **Storage** | Key-value data storage within Zapier | When you need to persist data between Zap runs — counters, status flags, deduplication checks. | 1 task per read/write |
| **Tables** | Spreadsheet-style database within Zapier | When you need structured data storage that Zaps can read from and write to — lookup tables, tracking logs, staging data. | Varies |

### Formatter Deep Dive

Formatter is used in nearly every multi-step Zap. The four categories:

**Text transforms:** Capitalize, Lowercase, Titlecase, Uppercase, Truncate, Find & Replace, Split Text, Extract Pattern (regex), Extract Email/URL/Number, Remove HTML, Convert Markdown to HTML, Trim Whitespace, Word Count, Default Value, Pluralize, Super Trim, Convert to ASCII.

**Number transforms:** Perform Math, Format Number, Format Currency, Format Phone, Random Number, Spreadsheet-style formula.

**Date/Time transforms:** Format (reformat date to any style), Add/Subtract Time, Compare Dates (calculate difference between two dates).

**Utilities:** Lookup Table (key-value mapping), Pick from List, Line Itemizer (create/append/prepend), Line-item to Text, Text to Line-item, Import CSV.

**Key Formatter patterns for CreativeOne:**
- **Date formatting** between Fusion (which may output dates in one format) and Asana/HubSpot (which expect another format)
- **Lookup Tables** to map Annuity Sales Team names to Slack tags, Asana portfolio IDs, or HubSpot properties
- **Split Text** to extract first/last name from a full name field
- **Default Value** to provide fallback data when a form field is optional and might be empty
- **Trim Whitespace / Super Trim** to clean form input before it hits the CRM

### Filters vs. Paths: When to Use Which

| Scenario | Use Filter | Use Paths |
|---|---|---|
| You only care about one condition (yes/no gate) | ✅ | |
| You need to handle multiple outcomes differently | | ✅ |
| You want to stop the Zap entirely if conditions aren't met | ✅ | |
| You want different actions based on advisor tier | | ✅ |
| You want a "catch-all / else" branch | | ✅ (use Fallback path) |
| You want to minimize task usage (only actions in matching branches fire) | Either works | ✅ is more flexible |

**Critical Filter/Path logic notes:**
- AND logic: ALL conditions must be true
- OR logic: AT LEAST ONE condition must be true
- With negative conditions (e.g., "does not contain") + AND logic, both must be false for the path to run. Always test with real data.
- If a Path errors, subsequent Paths still run — errors don't cascade across branches
- Filter and Path steps are free (no task consumed). Actions within a running Path branch DO consume tasks.

### Error Handling

Zapier offers three layers of error handling:

**1. Autoreplay (account-wide or per-Zap)**
- Automatically retries errored steps up to 5 times on a backoff schedule (~10.5 hours total)
- Available on Professional, Team, and Enterprise plans
- Per-Zap override options: Always replay, Never replay, Use account setting
- Does NOT send error notifications until the final retry fails
- Does NOT replay Halted (filter-stopped) runs — only Errored runs
- ⚠️ If 95% of a Zap's runs error in the last 7 days, Zapier automatically pauses the Zap

**2. Custom Error Handling (per-step)**
- Add an error handler to any action step (not triggers or Path steps)
- Creates a Success path (normal flow) and Error path (runs only when that step errors)
- Error handler path can access the error message from the failed step for routing/notification
- When error handler runs, the step doesn't count toward the Zap's error ratio
- ⚠️ Enabling custom error handling on a step disables Autoreplay for that Zap
- ⚠️ Cannot manually replay individual Zap runs that have error handlers — must replay entire run

**3. Preventive Design (best approach)**
- Place Filters early to prevent bad data from reaching action steps
- Use Formatter to normalize data before action steps
- Use "Find" search steps before "Create" steps to prevent duplicates
- Set required fields in intake forms so data arrives complete
- Test with real data, not just sample data

### Sub-Zaps

Sub-Zaps are reusable Zap components — build a workflow once, call it from multiple parent Zaps.

**When to use Sub-Zaps:**
- The same sequence of actions appears in 3+ Zaps (DRY principle — Don't Repeat Yourself)
- You want to encapsulate complex logic into a modular, testable unit
- You need to return processed data back to the parent Zap

**Sub-Zap structure:**
```
Parent Zap: Trigger → Actions → Call Sub-Zap (passes data) → Uses returned data → More Actions

Sub-Zap: Start Sub-Zap trigger → Actions → Return from Sub-Zap (sends data back)
```

**Sub-Zap limitations:**
- Every branch in a Sub-Zap with Paths must include a "Return from Sub-Zap" step
- Looping inside Sub-Zaps has constraints — loop actions cannot be added before a Return step. Workaround: use a Path with "Always Run" on both branches; loop on the left, delay + return on the right.
- Sub-Zaps consume tasks for all actions within them
- A Sub-Zap requires a "Return from Sub-Zap" step to send data back; without it, the parent Zap will remain in a Delayed state

---

## CreativeOne Zap Standards

### Naming Convention

Every Zap must follow this naming format:

```
[Source App] → [Destination App] | [What it does] | [Scope/Context]
```

**Examples:**
- `Fusion → Asana | Create Advisor Project from Order | SMAC`
- `Formstack → Asana | Create Event Task from Registration | Events`
- `HubSpot → Asana | Sync Contact Update to Advisor Task | CSM`
- `Asana → Slack | Notify Annuity Team on Status Change | Reporting`
- `Gravity Forms → HubSpot | Create Contact from Website Lead | B2B`

**Why this format works:**
- Immediately shows which systems are connected
- Describes the action in plain language
- Identifies the business area or scope
- Alphabetically sortable by source app
- Searchable by any keyword

### Step Naming

**Rename every step** in every Zap. Default step names like "Create Task in Asana" don't tell you which task or why.

**Format:** `[Action verb] [What] [Context]`

**Examples:**
- ❌ Default: "Create Task in Asana"
- ✅ Renamed: "Create advisor project task from Fusion order"
- ❌ Default: "Find Contact in HubSpot"
- ✅ Renamed: "Look up existing advisor by Header ID"
- ❌ Default: "Filter"
- ✅ Renamed: "Filter: Only proceed if Advisor Tier is Premier or Preferred"
- ❌ Default: "Paths"
- ✅ Renamed: "Route by Annuity Sales Team"

### Zap Description

Every Zap must include a description (Zapier's built-in description field). The description must answer:

1. **What does this Zap do?** (One sentence)
2. **What triggers it?** (Specific event)
3. **What does it create/update/send?** (Specific outcome)
4. **What systems does it touch?** (All apps involved)
5. **Who owns it?** (Marketing Ops team member responsible)
6. **Dependencies or related Zaps** (Does this Zap depend on or feed into another?)
7. **Error handling notes** (What should happen when it fails?)

**Example description:**
```
WHAT: Creates an Asana project from a new Fusion marketing order.
TRIGGER: New order created in Fusion with "Marketing Services" category.
OUTCOME: New Asana project in advisor's portfolio with tasks from template, custom fields populated.
SYSTEMS: Fusion → Zapier → Asana
OWNER: [Marketing Ops Manager Name]
RELATED: Feeds "Asana → Slack | Notify CSM of New Project" Zap
ERRORS: If Asana project creation fails, sends error notification to #mktg-ops-alerts Slack channel. Autoreplay enabled.
```

### Folder Organization

Organize Zaps into folders by business function:

```
📁 SMAC — Advisor Onboarding
📁 SMAC — Order Processing
📁 SMAC — EngageOne
📁 SMAC — Local Spark
📁 Events — Corporate Events
📁 Events — Incentive Trips
📁 Corporate — B2B Marketing
📁 Corporate — Social Media
📁 Ops — Internal Automations
📁 Ops — Reporting
📁 ⚠️ DEPRECATED (do not use)
```

**Folder rules:**
- Every Zap must live in a folder — no Zaps in the root/unfiled area
- Deprecated Zaps are moved to the DEPRECATED folder (turned off) rather than deleted, in case they're needed for reference
- Folder names use consistent format: `[Business Area] — [Function]`

### Documentation Outside Zapier

For complex Zaps (5+ steps, Paths, Sub-Zaps, or Webhooks), maintain documentation in CNET:

**CNET documentation must include:**
- Visual flowchart of the Zap logic (can be created in Lucidchart, Miro, or similar)
- Field mapping table (source field → Formatter transformation → destination field)
- Error handling behavior and escalation path
- Related Asana templates that the Zap creates projects from
- Any API-specific notes (rate limits, authentication refresh schedule)
- Link to the Zap in Zapier

**CNET pages must link to Zapier.** Zapier Zap descriptions must link to CNET. This mirrors the bidirectional linking standard from the Asana SOP.

---

## Zap Building Framework

### Step 1: Map the Data Flow

Before touching Zapier, document the data flow on paper or in a diagram:

```
[Source System] ─── field mapping ───→ [Zapier Processing] ─── field mapping ───→ [Destination System]
```

For each field:
- Source field name and format (e.g., "advisor_name" as text, "order_date" as MM/DD/YYYY)
- Any transformation needed (e.g., split name, reformat date, lookup tier)
- Destination field name and expected format
- Required vs. optional — what happens if the source field is empty?

### Step 2: Design the Logic Flow

Sketch the Zap's logic before building. Use this template:

```
TRIGGER: [App] — [Event]
  │
  ├── FILTER/FORMAT: [Any data validation or formatting needed?]
  │
  ├── SEARCH: [Need to look up existing records first?]
  │
  ├── PATH (if needed): [Multiple outcomes based on conditions?]
  │    ├── Path A: [Condition] → Actions
  │    ├── Path B: [Condition] → Actions
  │    └── Fallback: → Actions
  │
  ├── ACTION(S): [What to create/update/send]
  │
  └── ERROR HANDLING: [What happens if an action fails?]
```

### Step 3: Optimize for Task Efficiency

Tasks are the currency of Zapier. Every action step in a successful run costs one task. Optimization strategies:

**Place Filters as early as possible.** If 60% of trigger events don't need to proceed, a Filter at step 2 prevents steps 3-8 from consuming tasks on irrelevant runs. Filters are free.

**Consolidate actions where possible.** If you're updating multiple fields on the same HubSpot contact, do it in one "Update Contact" action rather than separate actions for each field.

**Use Paths instead of multiple Zaps.** One Zap with Paths that handles 3 scenarios uses fewer total tasks than 3 separate Zaps that each filter for one scenario, because the Filter Zaps still fire their triggers and any pre-filter steps on every run.

**Avoid unnecessary Formatter steps.** If the data is already in the right format, don't add a Formatter "just in case." Each Formatter step costs one task.

**Review high-volume Zaps monthly.** Sort Zaps by task consumption. The top 10 Zaps by task usage should be reviewed for optimization opportunities.

### Step 4: Build the Trigger

**Trigger selection principles:**
- Prefer instant/webhook triggers over polling triggers when available. Instant triggers fire immediately; polling triggers check at intervals (1-15 minutes depending on plan).
- Use the most specific trigger event available. "New Order in Fusion" is better than "New Record in Database" if both are available — the specific trigger reduces false triggers.
- If the trigger app doesn't have a native Zapier integration, use Webhooks by Zapier (Catch Hook) as the trigger and configure the source app to send webhooks.

**Trigger testing:**
- Always test with real data, not just Zapier's sample data. Sample data may not represent edge cases.
- Verify the trigger is firing for the correct events and not picking up unintended data.

### Step 5: Build Validation and Formatting

Immediately after the trigger, add any validation and formatting steps:

1. **Filter** — Stop the Zap if the trigger data doesn't meet criteria (e.g., wrong order type, missing required field, test record)
2. **Formatter** — Transform data that's not in the format downstream actions need
3. **Search** — Look up existing records to prevent duplicates or to enrich the trigger data with additional context

**The validation-first pattern:**
```
Trigger → Filter (stop if invalid) → Formatter (normalize data) → Search (find existing records) → Action (create/update with clean, enriched data)
```

This pattern prevents the most common Zap failures: actions receiving bad data, creating duplicates, or failing on unexpected formats.

### Step 6: Build the Actions

**Action design principles:**

- **One action = one operation.** Each action should do one clear thing. Multi-purpose actions are harder to debug.
- **Map fields intentionally.** Don't map a field just because it's available. Every mapped field should serve a purpose in the destination system.
- **Handle empty fields.** If a source field might be empty, use Formatter's "Default Value" to provide a fallback, or use a Filter to only proceed when the field has data.
- **Search before create.** When creating records (contacts, projects, tasks), always search for existing records first. Use "Find or Create" actions when available to prevent duplicates.
- **Set custom fields in the same action as record creation.** Don't create a record in one step and then update its custom fields in a separate step. Most apps allow you to set all fields during creation.

### Step 7: Build Error Handling

**Every Zap that creates or modifies data in a system of record (Asana, HubSpot) must have error handling.**

**Minimum error handling standard for CreativeOne:**

For simple Zaps (2-3 steps):
- Enable Autoreplay (account-wide or per-Zap)
- Set up Zapier Manager to send Slack notification to #mktg-ops-alerts on final failure

For complex Zaps (4+ steps, Paths, external APIs):
- Add custom error handlers on critical action steps
- Error handler should: (1) send Slack notification with error details, (2) create an Asana task in the Marketing Ops project for investigation
- Include the error message, Zap name, and relevant record identifiers in the notification

For high-volume Zaps (100+ runs/day):
- All of the above, plus:
- Add a daily digest Zap that reports error counts from Zap History
- Set Autoreplay to "Never" for the Zap if errors are likely caused by data issues that Autoreplay won't fix (to conserve tasks)

### Step 8: Test Thoroughly

**Testing protocol:**

1. **Test each step individually** using Zapier's built-in test feature
2. **Test the full Zap end-to-end** with a real (or realistic test) record
3. **Test edge cases:**
   - What happens when an optional field is empty?
   - What happens when the trigger fires with unexpected data?
   - What happens when a search step finds no results?
   - What happens when a search step finds multiple results?
   - What happens when the destination system is temporarily unavailable?
4. **Test Paths** — verify each branch with data that matches its conditions
5. **Verify the output** — check the destination system to confirm records were created/updated correctly with all fields populated

**⚠️ Zapier has no staging environment.** You cannot test changes to production Zaps safely. Best practice: **Clone the Zap before making significant changes.** Test on the clone. When verified, turn off the original, turn on the clone, and move the original to DEPRECATED.

### Step 9: Document and Deploy

Before turning on the Zap:

- [ ] Zap is named following the naming convention
- [ ] Every step is renamed with descriptive labels
- [ ] Zap description is filled out completely
- [ ] Zap is placed in the correct folder
- [ ] Error handling is configured
- [ ] CNET documentation is created (if complex Zap)
- [ ] Zap has been tested with real data end-to-end
- [ ] Any related Asana templates or projects are updated to reflect the new automation
- [ ] Team members who need to know have been notified

### Step 10: Monitor Post-Launch

After deployment:

- **Day 1-3:** Check Zap History daily for errors, unexpected behavior, or higher-than-expected task usage
- **Week 1:** Review error rate. If errors exceed 10%, investigate and fix before Zapier auto-pauses the Zap (95% error rate over 7 days = auto-pause)
- **Week 2-4:** Monitor task consumption. Is it in line with estimates?
- **Ongoing:** Monthly review of all Zaps for task optimization, deprecated Zaps, expired connections

---

## Common Failure Patterns and Fixes

| Failure Pattern | What Happens | Prevention |
|---|---|---|
| **No validation after trigger** | Zap processes every trigger event including junk, test records, and incomplete data → downstream systems get dirty data | Add Filter immediately after trigger. Stop the Zap for events that don't meet criteria. |
| **Missing field crashes action** | A form field is left empty → action step expects data → Zap errors | Use Formatter "Default Value" for optional fields. Use Filter to stop the Zap if required fields are missing. |
| **Duplicate records created** | Zap fires for the same event twice (or doesn't check for existing records) → duplicate contacts, projects, or tasks | Always search before create. Use "Find or Create" actions. Add deduplication logic (e.g., check by Header ID or email). |
| **Date format mismatch** | Source app sends "10/15/2024" but destination expects "2024-10-15" → action fails or creates bad data | Add Formatter Date/Time step between trigger and action. Always specify From Format explicitly. |
| **Expired authentication** | An app connection expires (common with OAuth tokens) → Zap silently stops running | Check connected accounts monthly. Enable Autoreplay to handle transient auth issues. Set up Zapier Manager alerts for connection failures. |
| **API rate limiting** | Zap fires faster than the destination app allows → errors on high-volume runs | Add Delay steps before rate-limited API actions. Use Looping with sequential delays (not parallel) for batch operations. Batch operations where possible. |
| **Task quota exceeded** | Monthly task limit reached → all Zaps pause → work stops flowing | Monitor task usage weekly. Optimize high-volume Zaps. Place Filters early to prevent wasted tasks. Review and turn off unused Zaps. |
| **Path logic error** | AND/OR logic configured incorrectly → data routes to wrong branch or no branch | Test every Path with data that matches each branch's conditions. Be especially careful with negative conditions + AND logic. |
| **Zap auto-paused by Zapier** | 95% error rate over 7 days triggers automatic pause → nobody notices → work stops flowing | Monitor Zap History. Set up Zapier Manager to alert on Zap status changes. Fix root causes rather than just replaying. |
| **Shadow Zaps** | Team member builds an unapproved Zap that conflicts with existing automation → duplicate data, conflicting updates | Governance: only Marketing Ops builds Zaps. Regular audit for unauthorized Zaps. |
| **Sub-Zap missing Return step** | Parent Zap calls Sub-Zap but Sub-Zap doesn't return → parent stays in Delayed state indefinitely | Always include "Return from Sub-Zap" in every branch of a Sub-Zap. Test parent + Sub-Zap together. |
| **Looping overwhelms API** | Loop fires 500 iterations in parallel → destination API gets hammered → rate limits or failures | Use sequential looping (add delay per iteration). Reduce batch sizes. Consider Webhook-based chaining for very large datasets. |
| **Formatter used unnecessarily** | Formatter step added "just in case" when data is already in correct format → wastes 1 task per run | Only add Formatter when transformation is actually needed. Review high-volume Zaps for unnecessary Formatter steps. |

---

## Task Optimization Reference

| Optimization | Estimated Task Savings | Effort |
|---|---|---|
| Place Filter before all actions (stop 50% of runs) | 50% of downstream task cost | Low |
| Consolidate multiple update actions into one | 1 task per consolidated action | Low |
| Replace multiple single-purpose Zaps with one Zap using Paths | Eliminates duplicate trigger processing | Medium |
| Use Sub-Zaps for repeated logic (build once, call from many) | Eliminates duplicated action steps across Zaps | Medium |
| Remove unnecessary Formatter steps on high-volume Zaps | 1 task per removed Formatter per run | Low |
| Turn off deprecated/unused Zaps | Eliminates all tasks from inactive automations | Low |
| Reduce polling frequency (if available) for non-time-sensitive triggers | Fewer trigger checks, fewer runs | Low |
| Use Code by Zapier to replace multi-step logic with one step | Multiple tasks → 1 task | High (requires code) |

**Monthly task review cadence:**
1. Sort Zaps by task consumption in Zapier's Task History
2. Review the top 10 task-consuming Zaps
3. For each: Can Filters be added? Can actions be consolidated? Is the Zap still needed?
4. Document findings and optimizations made

---

## CreativeOne Integration Patterns

These are the most common Zap patterns for CreativeOne's tech stack:

### Fusion → Asana (Order Processing)
```
Trigger: New order in Fusion
→ Filter: Only "Marketing Services" category orders
→ Formatter: Format order date, parse advisor name
→ Search: Find existing advisor portfolio in Asana by Header ID
→ Path A (Project exists): Add task to existing project
→ Path B (New advisor): Create project from template, populate custom fields, add to portfolios
→ Error Handler: Notify #mktg-ops-alerts on failure
```

### Form → Asana (Intake)
```
Trigger: New form submission (Formstack/Gravity Forms/HubSpot)
→ Filter: Required fields are populated
→ Formatter: Normalize name, date, phone
→ Search: Find advisor in Asana by name/Header ID
→ Create Task in Asana: Apply naming convention, set custom fields, assign to CSM
→ Multi-home task to appropriate projects
```

### Form → HubSpot (Lead Capture)
```
Trigger: New form submission (website)
→ Filter: Email is not blank, not a test submission
→ Formatter: Trim whitespace, titlecase name
→ Search: Find existing contact in HubSpot by email
→ Path A (Exists): Update contact properties
→ Path B (New): Create contact with properties, add to list
```

### Asana → Slack (Notifications)
```
Trigger: Task updated in Asana (custom field change)
→ Filter: Status field changed to "At Risk" or "Off Track"
→ Formatter: Build Slack message with task name, project, assignee
→ Action: Send Slack message to appropriate channel
```

### Event Registration Processing
```
Trigger: New registration form submission
→ Formatter: Parse event ID, advisor name, registration details
→ Search: Find event project in Asana by CS Event ID
→ Create Task: Registration task in event project with naming convention
→ Search: Find contact in HubSpot
→ Update Contact: Add event registration property
→ Error Handler: Log failures to Ops tracking sheet
```

---

## Zap Blueprint Output Format

When Claude helps design a Zap, deliver the blueprint in this format:

```
## Zap Blueprint: [Name following naming convention]

### Purpose
[One sentence: what this Zap does and why]

### Trigger
- App: [App name]
- Event: [Specific trigger event]
- Frequency estimate: [How often this will fire]

### Data Flow
| Source Field | Transformation | Destination Field | Required? |
|---|---|---|---|
| [field] | [none / formatter action] | [field] | [yes/no] |

### Logic Flow
[Step-by-step with step numbers, named descriptively]

Step 1 — Trigger: [Description]
Step 2 — Filter: [Condition — what stops the Zap]
Step 3 — Formatter: [What's being transformed]
Step 4 — Search: [What's being looked up and where]
Step 5 — Path A: [Condition] → Step 5a, 5b...
Step 5 — Path B: [Condition] → Step 5a, 5b...
Step 6 — Action: [What's being created/updated]

### Error Handling
- Autoreplay: [On/Off and why]
- Custom error handlers: [Which steps and what they do]
- Notification: [Where errors are reported]

### Task Estimate
- Actions per run: [X]
- Estimated runs per day/week/month: [X]
- Estimated monthly task consumption: [X]
- Optimization notes: [Any ways to reduce]

### Testing Plan
- Test case 1: [Normal scenario]
- Test case 2: [Edge case — missing data]
- Test case 3: [Edge case — duplicate record]
- Test case 4: [Each Path branch]

### Dependencies
- Related Zaps: [Any Zaps this feeds or depends on]
- Asana templates: [If creating projects from templates]
- Connected accounts: [Which Zapier connections are needed]

### Deployment Checklist
- [ ] Naming convention applied
- [ ] All steps renamed
- [ ] Description completed
- [ ] Folder assigned
- [ ] Error handling configured
- [ ] CNET documentation created
- [ ] Tested end-to-end with real data
- [ ] Marketing Ops approved
```

---

## Governance Reminders

These are non-negotiable:

| Rule | Reason |
|---|---|
| Only Marketing Ops builds Zaps | Prevents conflicting automations, maintains single source of truth for workflow logic |
| All Zaps must be named, described, and foldered | Maintainability — anyone should be able to understand and troubleshoot any Zap |
| Clone before editing production Zaps | No staging environment exists. Cloning prevents accidental breaks to live workflows |
| Test with real data before going live | Sample data doesn't represent edge cases. Real data does. |
| Expired connections must be checked monthly | Silent connection failures = Zaps silently stop = work stops flowing |
| Task usage reviewed monthly | Prevents surprise overages and identifies optimization opportunities |
| Deprecated Zaps moved to folder (not deleted) | Preserves history and logic for reference. Can be reactivated if needed. |
| Complex Zaps documented in CNET | The Zap itself is the "what." CNET documentation is the "why" and "how." |
| Error notifications go to a shared channel | Not to an individual. If the individual is out, errors must still get seen. |

---

## Updating This File

When new Zapier features ship, new integration patterns are established, or corrections are identified:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
3. Note any new patterns, task optimization discoveries, or failure modes in `memory/preferences.md`.
4. If the Asana SOP changes in ways that affect Zap design (new custom fields, new portfolio structure, new naming conventions), update the CreativeOne Integration Patterns section.
5. Zapier's feature set evolves rapidly — check for new built-in tools (Agents, Canvas, new Formatter transforms) that might replace current workarounds.
