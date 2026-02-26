# Skill: RACI Framework

> **Trigger:** Defining roles, responsibilities, or accountability for a process, project, or SOP. Also load when a process blueprint or SOP needs a responsibility matrix or when role confusion/ownership gaps are the core problem to solve.
> **Context required:** None — this is a standalone reference framework. Load relevant brand/skill files based on what the RACI is supporting (e.g., load `skills/asana-process-building.md` if the RACI is for an Asana process, `skills/sop-writing.md` if for an SOP).
> **Output:** A RACI table with R, A, C, I assigned by role for each major task, phase, or decision in the process.

---

## What RACI Is

RACI is a responsibility assignment framework used to define who does what on any given task, project, or decision. It prevents the most common breakdowns in team execution: unclear ownership, decision bottlenecks, people doing work that isn't theirs, and people being surprised by outcomes they should have known about.

RACI stands for:

| Letter | Role | Plain Language |
|---|---|---|
| **R** | **Responsible** | The person who does the work |
| **A** | **Accountable** | The person who owns the outcome |
| **C** | **Consulted** | People whose input is needed before or during the work |
| **I** | **Informed** | People who need to know what happened, but aren't involved in doing it |

---

## The Four Roles — In Detail

### R — Responsible
The person (or people) who actually execute the task. They do the work, manage the details, and respond to questions about progress.

- There can be **more than one** Responsible person on a task
- Responsible doesn't mean they make the final call — that's Accountable
- Think of Responsible as: *"Who has their hands on this?"*

**Example at CreativeOne:** A copywriter is Responsible for writing an email campaign. A designer is Responsible for producing the visual assets. Both are Responsible for their piece — neither is Accountable for the campaign as a whole.

---

### A — Accountable
The single person who ultimately owns the outcome. They delegate to the Responsible parties, review the work, and sign off that it meets the standard. The buck stops with them.

- **Only one Accountable person per task or deliverable** — this is the golden rule
- They don't always do the work, but they answer for it if something goes wrong
- Think of Accountable as: *"Who has to answer for this if it doesn't get done?"*

**Example at CreativeOne:** The CSM is Accountable for the advisor project. The Marketing Ops Manager is Accountable for the automation backbone. The Marketing Manager is Accountable for the overall SOP being accurate and followed.

---

### C — Consulted
People whose expertise or perspective is needed before the work moves forward. This is **two-way communication** — they give input that shapes decisions.

- Consulted parties are actively involved, not just observing
- Their feedback should be incorporated before the work is finalized
- Think of Consulted as: *"Who do we need to talk to before this is done?"*

**Example at CreativeOne:** The Marketing Ops Manager is Consulted before any new template or workflow is built. A CSM might be Consulted when a deliverable requires advisor-specific context the creative team doesn't have.

---

### I — Informed
People who need to be kept in the loop on progress or decisions but don't need to be involved in the work itself. This is **one-way communication** — updates go to them, but they don't have to respond or approve.

- Informed parties don't block progress
- They receive updates at defined points (completion, key milestones, escalations)
- Think of Informed as: *"Who needs to know this happened?"*

**Example at CreativeOne:** Leadership is Informed of project status through dashboards and portfolio reports. Annuity sales team leads are Informed of advisor project health through weekly CSM reports.

---

## The Golden Rules

1. **Every task must have at least one R.** If no one is Responsible, the work won't happen.
2. **Every task must have exactly one A.** If there's more than one Accountable, there's actually none — everyone defers to everyone else.
3. **R and A can be the same person.** This is common when a team member owns their own work end-to-end. The key is that accountability is still explicitly assigned.
4. **C and I are not required for every task.** Don't over-assign these — it creates noise and notification fatigue.
5. **Consulted is two-way. Informed is one-way.** This distinction matters. If someone's feedback would block or change the work, they're Consulted. If they just need to know the outcome, they're Informed.

---

## Common Misuses to Avoid

| Mistake | Why It's a Problem |
|---|---|
| Multiple Accountable on one task | Nobody actually owns it — everyone waits for someone else to decide |
| Confusing Responsible and Accountable | "I did my part" and "I own the outcome" are different obligations |
| Over-assigning Consulted | Too many consultations slow work down without adding proportional value |
| Using Informed as a CYA move | Adding people to Informed just to "cover yourself" creates noise and dilutes real accountability |
| Skipping Informed entirely | People get surprised, escalate unnecessarily, or duplicate work |

---

## RACI Variations Worth Knowing

| Variant | What It Adds | When It's Useful |
|---|---|---|
| **RASCI** | Adds **S = Support** — people who assist the Responsible party without full ownership | Useful when there's meaningful execution support that isn't quite Responsible |
| **DACI** | Replaces R/A with **D = Driver** and **A = Approver** | Better for decision-making processes than task execution |
| **CAIRO** | Adds **O = Out-of-loop** | Explicitly documents who is NOT involved — useful for governance clarity |

---

## How RACI Shows Up in Practice

RACI isn't typically written into every task — that would be excessive. It's most useful at two levels:

**1. Role-level RACI (for SOPs and governance docs)**
Define who is R, A, C, I for each major function or process. This is what the Asana SOP needs — a clear statement of which role holds accountability vs. responsibility for each system/process area.

**2. Task-level RACI (for complex projects or handoffs)**
On high-stakes or cross-functional deliverables, RACI is applied task by task to prevent handoff failures. The Asana SOP's Task Handoff Standard essentially operationalizes this.

---

## RACI Applied to Asana SOP Contexts

Here's how the four roles map to how the team already talks about work:

| Current SOP Language | RACI Translation |
|---|---|
| "Marketing Ops owns X" | Marketing Ops is **Accountable** for X |
| "Team members complete assigned tasks" | Task owners are **Responsible** |
| "Marketing Ops reviews impact before approving" | Marketing Ops is **Consulted** |
| "Leadership uses dashboards for visibility" | Leadership is **Informed** |
| "CSM is responsible for the advisor relationship" | CSM is **Accountable** for advisor project outcomes |
| "Contributors can be added for collaboration" | Contributors are **Responsible** (shared) or **Consulted** |
| "Stakeholders are tagged for visibility" | Stakeholders are **Informed** |
