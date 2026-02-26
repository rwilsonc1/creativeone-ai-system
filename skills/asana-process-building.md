# Skill: Asana Process Building

> **Trigger:** Building, restructuring, or troubleshooting any workflow, project structure, template, automation rule, or portfolio configuration in Asana.
> **Context required:** Load `context/asana-sop.md` for the full Marketing Operating System (MOS) standards.
> **Governance rule:** All structural changes to Asana (templates, custom fields, rules, portfolio architecture) are owned by Marketing Ops. This skill produces recommendations and blueprints — implementation goes through the Marketing Ops change control process.
> **Reference SOP:** The CreativeOne Asana SOP is the governing document. This skill helps Claude apply it correctly when building new processes.

---

## Philosophy: Build for the Person Who Isn't in the Room

The most common failure mode in Asana isn't a bad project structure — it's a good one that only the person who built it understands. Processes must be self-documenting, meaning anyone on the team should be able to open a project, understand what's happening, and know what to do next without asking another person.

Processes with high adoption share these traits:

1. **Obvious at a glance.** Naming conventions, color dots, sections, and custom fields should tell the story before anyone clicks into a task.
2. **Automation-backed.** Anything a human can forget, a rule should handle. Manual steps that enforce the system are the first thing teams skip under pressure.
3. **Scalable by design.** If a process works for 10 advisors but breaks at 50, it wasn't ready. Build for 3x your current load.
4. **Connected to the hierarchy.** Every task should trace upward: task → project → portfolio → strategic priority. Orphan work is invisible work.
5. **Documented outside Asana.** The process lives in Asana; the *how and why* live in CNET. Both must link to each other.

**The golden rule: If a new team member can't look at a project and know what to do, who owns it, and where it stands — the process isn't done yet.**

---

## Pre-Flight Checklist

Before building anything in Asana, answer these:

1. **What problem does this process solve?** Not "what does it do" — what breaks, gets missed, or takes too long without it?
2. **Who are the roles involved?** Map every person/team who touches the work from intake to completion. Each role becomes either a task owner, a contributor, or a stakeholder.
3. **What triggers this process?** Where does the work come from? (Form submission, Fusion order, manual creation, Zapier trigger, recurring schedule)
4. **What does "done" look like?** Define the deliverable(s) and the exit criteria. If you can't describe "done" in one sentence, the scope is too broad.
5. **Does a similar process already exist?** Check existing templates and projects before building new. Duplication is the enemy of governance.
6. **What systems are involved?** Identify every tool the process touches (HubSpot, Fusion, Formstack, Google Drive, etc.) — these become integration points.
7. **How will this be reported on?** If leadership or stakeholders need visibility, the portfolio, custom field, and dashboard requirements must be designed in from the start, not bolted on later.

---

## CreativeOne Asana Hierarchy

Understanding the hierarchy is critical. Every building decision should reinforce it, not work around it.

```
Organization (CreativeOne)
  └── Teams (SMAC, Corporate Marketing, etc.)
        └── Portfolios (Top-Level → Sub-Portfolios → Advisor Portfolios)
              └── Projects (defined bodies of work with owner + timeline)
                    └── Sections (phases/stages within a project)
                          └── Tasks (single units of actionable work)
                                └── Subtasks (smaller steps within a task)
```

### Key Hierarchy Principles

**Portfolios = Reporting views.** Portfolios exist for visibility, not execution. They group projects so that different audiences (CSMs, team leads, sales leaders, executives) can see the work relevant to them.

**Projects = Execution containers.** One project = one defined body of work with a clear owner, timeline, and outcome. Projects are where tasks live and work gets done.

**Tasks = The atomic unit of work.** A task is one action, one owner, one due date. If it doesn't have all three, it's not schedulable work.

**Multi-homing = Same work, multiple views.** Projects live in multiple portfolios. Tasks live in multiple projects. The work exists once but is visible everywhere it needs to be. Never duplicate — always multi-home.

---

## Building Blocks: What to Build and When

### When to Build a New Template

Build a template when:
- A process will repeat 3+ times with substantially the same structure
- Multiple people will execute the same workflow and consistency matters
- The process has defined stages, handoffs, or quality gates
- Onboarding new team members to the process is a known need

Do NOT build a template when:
- The process is still being figured out (build it as a live project first, then templatize after 2-3 successful runs)
- It's a one-time initiative with no repeating pattern
- The process is so simple it's just 2-3 tasks (use a task template instead)

### When to Build a New Project

Build a project when:
- There is a defined scope of work with a beginning and an end
- Multiple tasks and/or multiple people are involved
- The work needs to be tracked, reported on, or reviewed as a unit
- It supports an advisor engagement, event, campaign, or program

### When to Build a Rule (Native Asana Automation)

Build a rule when:
- The same manual action happens every time a condition is met (task assigned → add to project; field changes → move to section; task completed → notify someone)
- Enforcement of a standard depends on human memory (rules don't forget)
- Routing, assignment, or status updates follow a predictable pattern

Do NOT build a rule when:
- The logic requires data from outside Asana (use Zapier instead)
- The condition involves complex branching logic that exceeds Asana's trigger/action model
- The rule would conflict with an existing rule on the same project

> ⚠️ **Rule limit awareness:** Asana has a 50-rule limit per project. For complex workflows, consider splitting into multiple linked projects within a portfolio, or offloading some logic to Zapier.

### When to Build a Zap (Zapier)

Build a Zap when:
- Data needs to flow between Asana and another system (HubSpot, Fusion, Formstack, etc.)
- The trigger originates outside Asana (form submission, CRM event, order creation)
- Multi-step logic requires conditional branching beyond Asana's native rules
- You need to create projects from templates automatically based on external events

> ⚠️ **Governance rule:** No team builds Zapier workflows without Marketing Ops approval. All Zaps must be documented and owned by Marketing Ops.

### When to Build a Custom Field

Build a custom field when:
- The data enables filtering, reporting, or automation that doesn't currently exist
- The data needs to be consistent across projects (e.g., Advisor Tier, Annuity Sales Team)
- A dashboard or portfolio view requires the data point to function

Do NOT build a custom field when:
- The information can live in the task description (not everything needs to be structured data)
- A similar field already exists (check first — proliferation breaks reporting)
- Only one team needs it and it won't be used in reporting or automation

> ⚠️ **Governance rule:** Only Marketing Ops can add, modify, or deprecate custom fields. New field requests require a business justification, proposed name/values, intended use, and impact assessment.

---

## Project Building Framework

When building a new project or template, follow this framework:

### Step 1: Map the Workflow

Before touching Asana, document the workflow on paper or in a document:

1. **List every step** from trigger to "done" — include decision points and handoffs
2. **Identify owners** for each step — who does this?
3. **Identify dependencies** — what has to happen before this step can start?
4. **Identify inputs and outputs** — what does each step need to begin, and what does it produce?
5. **Identify where things typically go wrong** — these become your execution pause points and quality gates

### Step 2: Design the Section Structure

Sections in Asana represent stages or phases. They should reflect how work actually moves, not just a category system.

**Effective section design patterns:**

| Pattern | When to Use | Example |
|---|---|---|
| **Sequential stages** | Work flows through defined phases in order | Intake → In Progress → Review → Approved → Complete |
| **Functional ownership** | Different teams own different sections | Copy → Design → Build → QA → Launch |
| **Status-based (Kanban)** | Work is pulled through stages by the team | Backlog → To Do → In Progress → In Review → Done |
| **Deliverable-based** | Project contains distinct deliverables | Emails → Social Posts → Landing Page → Print Materials |

**Section naming rules:**
- Use clear, action-oriented or stage-oriented names
- Keep names short (2-4 words)
- Sections should be mutually exclusive — a task should only logically belong in one section at a time
- If using sequential stages, the order must match the actual workflow left-to-right (Board view) or top-to-bottom (List view)

### Step 3: Build the Tasks

For each step in your workflow map, create a task that follows MOS standards:

**Every task must have:**
1. **Clear title** — describes the output and includes contextual identifiers (color dot, ARE #, advisor name as applicable)
2. **Assigned owner** — one person accountable
3. **Due date** — no date = not schedulable
4. **Task description** — includes definition of done, links to SOPs/briefs, expected duration
5. **Dependencies** — set blocking/dependent relationships for any task that requires a predecessor

**Task title format for advisor work:**
```
[Color Dot] [Deliverable] | [Advisor/Entity Name] | [Context]
```
Examples:
- 🔴 Email Copy | James Smith | Lead Generation Campaign
- 🟣 Registration Invite | Munich Incentive Trip | June 2026

**Task title format for internal/corporate work:**
```
[Color Dot] [Deliverable] | [Project/Event Name] | [Date/Context]
```

### Step 4: Set Dependencies and Handoffs

Dependencies turn a list of tasks into a workflow. Apply the Task Handoff & Next-Stage Routing Standard:

- Every task that produces output consumed by another task must have a **blocking dependency** set
- When a contributor completes their task, they must:
  1. Confirm their deliverable meets the definition of done
  2. Mark their task complete
  3. Route work to the next owner (via assignment change, status field change, section move, or next-task creation)
  4. Tag the next owner with a comment confirming the deliverable is ready

> ❌ **Anti-pattern:** Completing a task without routing to the next stage. Work must never sit in a "Done" state if additional stages are required.

### Step 5: Configure Custom Fields

Apply the required custom fields per the MOS:

**Required for all advisor projects:**
- Assignee
- Due Date
- Estimated Time
- Advisor Tier (Premier | Preferred | Core | Blueprint)
- Annuity Sales Team
- Advisor Header ID

**Common operational fields:**
- Status (On Track | At Risk | Off Track | On Hold | Complete)
- Priority (P1 Critical | P2 High | P3 Standard | P4 Low)
- Deliverable Type (for reporting and cycle time tracking)
- Rush (Yes/No — for measuring planning discipline)

### Step 6: Build Rules and Automation

Design rules to enforce the workflow, not just to save clicks. The best rules are invisible to the user — they enforce standards that humans would otherwise forget.

**High-value rule patterns for CreativeOne:**

| Trigger | Action | Purpose |
|---|---|---|
| Task assigned to [person] | Add task to [person's HQ project] | Individual workload visibility via multi-homing |
| Custom field [Annuity Team] changes | Add project to [team portfolio] | Automated portfolio routing |
| Task moved to [section] | Change custom field status | Status tracking without manual field updates |
| Task completed | Add comment notifying next owner | Handoff enforcement |
| Task becomes overdue | Change status to "At Risk" + notify project owner | Proactive risk surfacing |
| Form submitted | Create task with default fields populated | Standardized intake |

**Rule design principles:**
- One rule should do one thing clearly. Avoid stacking too many actions in a single rule (harder to debug)
- Name rules descriptively: "When assigned to Sarah → Add to Sarah's Design HQ" not "Rule 14"
- Document every rule's purpose — either in a comment at the top of the project or in CNET
- Test rules with a dummy task before going live
- Monitor for conflicts — two rules firing on the same trigger can produce unpredictable results

### Step 7: Configure Multi-Homing

Multi-homing is the single most powerful feature in CreativeOne's Asana setup. It eliminates duplication while providing multiple views of the same work.

**Standard multi-homing pattern for advisor projects:**

```
Task: 🔴 Design Assets | James Smith | Brand Kit
  ├── Lives in: James Smith Advisor Project (CSM sees all advisor work)
  ├── Lives in: Sarah's Design HQ (Designer sees all their assigned work)
  └── Lives in: Creative Team Project (Creative lead sees all design work)

Project: 🔴 ARE-12345 | James Smith | Lead Generation Campaign
  ├── Lives in: James Smith | 123456 (Advisor Portfolio)
  ├── Lives in: Websites (Functional Sub-Portfolio)
  ├── Lives in: Frank's Team (Annuity Sales Team Portfolio)
  └── Lives in: SMAC (Top-Level Portfolio)
```

**Multi-homing principles:**
- **Always multi-home, never duplicate.** The task or project exists once. It appears in multiple containers. Updates propagate everywhere automatically.
- **Design views for the audience.** CSMs need the advisor view. Team leads need the functional view. Sales leaders need the team view. Leadership needs the strategic view. Multi-homing serves them all from a single source.
- **Custom fields must be organization-level.** If a custom field is project-level, it won't carry across multi-homed contexts. Use organization-level fields for any data that needs to be visible in multiple projects.
- **Watch for rule conflicts.** When a task is multi-homed, rules from ALL projects it belongs to may fire. Design rules with this in mind to avoid duplicate actions.

### Step 8: Build the Intake

Every process needs a defined front door. Intake determines how work enters the system.

**CreativeOne intake sources:**
- Fusion Orders → Zapier → Asana (automated project creation)
- Formstack/Gravity Forms/HubSpot Forms → Zapier → Asana (automated task or project creation)
- Asana Forms → Asana (native task creation)
- Manual creation (should be the exception, not the rule)

**Intake design requirements:**
- Every intake form must have: clear instructions, field validation, required vs. optional field designation, confirmation message with next steps
- Automated intake must populate: project title (with naming convention), required custom fields, default owner, portfolio assignment
- The **Definition of Ready (DOR)** standard must be enforceable at intake. If required fields are missing, the project or task should be flagged as blocked, not started.

### Step 9: Link to CNET Documentation

**This is a required step, not optional.**

Every Asana template must link to its CNET workflow SOP. Every CNET workflow SOP must link to its Asana template. This bidirectional linking ensures teams can move between execution (Asana) and reference documentation (CNET).

**Linking format in Asana:**
- Add the CNET SOP link in the project description/overview section
- Add links to relevant SOPs in task descriptions where execution instructions are needed

**Linking format in CNET:**
- Reference the Asana template name and location
- Include screenshots of the expected Asana project structure

### Step 10: Design Reporting and Dashboards

Before launching the process, define how it will be measured. Reference the MOS dashboard requirements:

- What metrics does this process need to feed? (Cycle time? SLA compliance? Throughput? Rework rate?)
- What custom fields power those metrics?
- What portfolio view does this process appear in?
- Who consumes the reporting? (CSMs, team leads, sales leaders, leadership)

> 💡 **Design reporting into the process from the start.** Bolting on reporting after launch always means missing data, inconsistent fields, and unreliable dashboards.

---

## Template Design Standards

When converting a proven process into a reusable template:

### Template Must Include
- **Defined sections** matching the workflow stages
- **Pre-built tasks** with titles, descriptions, and default assignees (using role placeholders if assignee varies)
- **Due date offsets** relative to project start date (e.g., "5 days after project start")
- **Dependencies** pre-set between tasks
- **Required custom fields** pre-attached
- **Execution pause points** built in — tasks that cannot start until prerequisites are confirmed (e.g., "Confirm Brief Complete" blocking all execution tasks)
- **Project overview** with SOP links and context instructions
- **Rules** embedded in the template (these activate automatically when the template is used)

### Template Naming Convention
```
[Team/Function] — [Process Name] — Template
```
Examples:
- Creative — Brand Guidelines Package — Template
- Events — Corporate Event Marketing — Template
- Ops — Email Campaign Production — Template

### Template Maintenance Cadence
- **Quarterly review** by Marketing Ops + process owner
- **Immediate update** when a workflow SOP changes
- **Deprecation** of outdated templates (archive, don't delete — some projects may still reference them)

---

## Revision Protocol

When the process requires revisions to deliverables, the Revision Task Protocol from the MOS applies:

**Critical rule:** Comments are NOT revision requests. Revisions are schedulable work.

**Revision task format:**
```
REVISION | [Deliverable] | [Advisor/Entity] | [Version] | [Date]
```
Example: `REVISION | Radio Script | John Smith | V2 | March 1`

**Revision task must include:**
- Assigned owner and due date
- Description answering: What changed? Why? What does "done" look like? Timeline impact?
- Linked/attached original deliverable + marked-up feedback
- Escalation note if revision represents scope creep

**Enforcement:** Team members should create a revision task rather than executing revision requests made via comments alone.

---

## Common Failure Patterns and Fixes

| Failure Pattern | What Happens | Fix |
|---|---|---|
| **Overengineering on day one** | Complex setup → user fatigue → poor adoption. People stop using it. | Start with the minimum viable process. Run it 2-3 times. Then add complexity based on what's actually needed. |
| **Building Asana to match a broken process** | Asana faithfully reproduces a workflow that doesn't work. Garbage in, garbage out. | Map and fix the process first. Then build it in Asana. Asana should improve your process, not just digitize it. |
| **Custom field proliferation** | Too many fields → team ignores them → data quality collapses → reporting fails. | Fewer fields, filled consistently, beats many fields filled sporadically. Every field must justify its existence through reporting or automation. |
| **Tasks without owners or dates** | Unschedulable work that clutters the system and erodes trust. People stop checking Asana because it's full of noise. | Enforce the MOS standard: no owner + no date = not real work. Treat unowned tasks as backlog, not active commitments. |
| **Duplicate projects instead of multi-homing** | Same work tracked in two places → conflicting updates → nobody knows which is current. | Delete the duplicate. Multi-home the original. One source of truth, multiple views. |
| **Rules that conflict** | Two rules fire on the same trigger → unpredictable results → team loses trust in automation. | Audit rules regularly. Document every rule's purpose. Test with dummy tasks before going live. |
| **Shadow processes in email/Teams** | Work happens outside Asana → invisible to reporting → capacity planning breaks → leadership is surprised by missed deadlines. | Pull context into Asana task comments. If the conversation matters, it belongs in the task. "If it's not in Asana, it's not real work." |
| **Templates never updated** | Workflow evolves but template is frozen → new projects launch with outdated structure → team works around the template instead of from it. | Quarterly template review. Immediate update when SOPs change. Templates are living documents. |
| **No execution pause enforcement** | Work starts before requirements are complete → rework, scope creep, delays. | Build execution pause into templates via dependencies. Prerequisite tasks must be completed before downstream work unblocks. |
| **Reporting bolted on after launch** | Custom fields added retroactively → historical data is missing → dashboards show incomplete picture → leadership doesn't trust the data. | Design reporting into the process from step 1. Define metrics, fields, and portfolio views before building. |

---

## Process Building Output Format

When Claude helps build an Asana process, deliver the blueprint in this format:

```
## Asana Process Blueprint: [Process Name]

### Problem Statement
[What breaks, gets missed, or takes too long without this process?]

### Trigger / Intake
[How does this work enter the system?]

### Roles Involved
| Role | Responsibility |
|---|---|
| [Role] | [What they do in this process] |

### Workflow Map
[Step-by-step workflow with owners and dependencies]

Step 1: [Task Name] → Owner: [Role] → Depends on: [None / Prior step]
Step 2: [Task Name] → Owner: [Role] → Depends on: Step 1
...

### Asana Structure

**Project Type:** [New project per instance / Ongoing single project / Template-based]
**Sections:**
1. [Section Name] — [Purpose]
2. [Section Name] — [Purpose]
...

**Custom Fields Required:**
| Field Name | Type | Values | Purpose |
|---|---|---|---|
| [Field] | [Dropdown/Text/Number/Date] | [Values] | [What it enables] |

**Rules / Automation:**
| Trigger | Action | Purpose |
|---|---|---|
| [Trigger] | [Action] | [Why] |

**Multi-Homing Plan:**
- Task multi-homing: [Where tasks should also appear]
- Project multi-homing: [Which portfolios this project should live in]

### Intake Requirements
[What the form/Zap must capture, required fields, what triggers creation]

### Reporting
[What metrics this process feeds, what dashboards it appears in]

### CNET Documentation Needed
[What SOPs need to be written/linked]

### Execution Pause Points
[Where work should stop if requirements aren't met]

### Change Control Note
[Submit to Marketing Ops via change control process for implementation]
```

---

## Scalability Checklist

Before finalizing any process, verify it passes the scalability test:

- [ ] **3x load test:** Would this process still work if volume tripled? If not, identify the bottleneck now.
- [ ] **New team member test:** Could a new hire follow this process with only the Asana project + linked CNET SOP, without asking a colleague? If not, add clarity.
- [ ] **Reporting integrity:** Are all custom fields that feed dashboards required (not optional)? Optional fields create incomplete data.
- [ ] **Automation resilience:** If a Zap breaks or a rule misfires, does the team know? Build in monitoring (Zapier error alerts, Asana rule audit schedule).
- [ ] **Multi-homing completeness:** Does every stakeholder group have a view that shows them what they need? CSMs, team leads, sales, leadership.
- [ ] **Template readiness:** If this process will repeat, is a template built with all standards embedded (sections, tasks, fields, rules, dependencies, SOP links)?
- [ ] **Naming convention compliance:** Do all projects, tasks, and portfolios follow MOS naming conventions?
- [ ] **Change control documented:** Is the process blueprint submitted to Marketing Ops for review before implementation?

---

## Quick Reference: MOS Standards That Apply to Every Build

These are non-negotiable standards from the Asana SOP that apply to every process Claude helps build:

| Standard | Rule |
|---|---|
| Task hygiene | Every task must have: clear title, assigned owner, due date, description with definition of done |
| Naming convention (advisors) | `[Color Dot] ARE-#### \| Advisor Name \| Project Type` |
| Naming convention (events) | `[Color Dot] Event #### \| Location \| Event Name \| Date` |
| Color dots | 🔴 Premier, 🟠 Preferred, 🟢 Core, 🔵 Blueprint, 🟣 Corporate Events, 🟡 Corporate Projects |
| Portfolio assignment | Every advisor project must live in: Advisor Portfolio + Functional Sub-Portfolio + Annuity Team Portfolio + Top-Level Portfolio |
| Custom field governance | Only Marketing Ops adds/modifies/deprecates custom fields |
| Template requirement | All repeatable work must use templates |
| CNET linking | Bidirectional: Asana → CNET and CNET → Asana |
| Revision protocol | Revisions are tasks, not comments. Format: `REVISION \| [Deliverable] \| [Name] \| [Version] \| [Date]` |
| Execution pause | Work cannot start without complete intake. Blockers must be documented and escalated. |
| Handoff routing | Completing your portion ≠ work is done. Route to next stage explicitly. |
| Source of truth | "If it's not in Asana, it's not real work." |

---

## Updating This File

When Asana SOP standards change, new patterns emerge, or corrections are identified:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
3. If the Asana SOP document (`context/asana-sop.md`) has been updated, reconcile this skill file to match.
4. Note any new rule patterns, multi-homing strategies, or failure modes discovered during builds in `memory/preferences.md`.
