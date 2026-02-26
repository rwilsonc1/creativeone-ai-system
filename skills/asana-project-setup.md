# CreativeOne Asana Project Setup Guide

## Workspace Information

- **Workspace Name**: CreativeOne
- **Workspace ID**: 116266473211825
- **Team**: SMAC (GID: 638838561646744)
- **Portfolio**: SMAC > Creative (GID: 1210322193819767)

---

## Naming Conventions

### Color Dot System

All projects and tasks must begin with the correct color dot based on project type:

| Dot | Type | Usage |
|-----|------|-------|
| 🔴 | Premier Advisor | Advisor-facing client projects — Premier tier |
| 🟠 | Preferred Advisor | Advisor-facing client projects — Preferred tier |
| 🟢 | Core Advisor | Advisor-facing client projects — Core tier |
| 🔵 | Blueprint Advisor | Advisor-facing client projects — Blueprint tier |
| 🟣 | Corporate / Internal | CreativeOne internal marketing & content projects |
| 🟡 | Corporate Events | Company-wide events and incentive trips |

> Tiers are assigned by the Sales team. If a tier is missing, CSM should contact Sales to update in Fusion.

---

### Project Naming Formats

**Corporate Internal Projects:**
```
🟣 [Content/Campaign Name] | [Descriptor] | [Month Year]
```
```
🟣 Referral Playbook | Design & Distribution | March 2026
```

**Corporate Events:**
```
🟡 Event [ID] | [Location/Name] | [Event Name] | [Date]
```
```
🟡 Event 3411 | Munich | Incentive Trip 2026 | June 12th
```

**Advisor Projects:**
```
[Dot] ARE-#### | [Advisor Name] | [Project/Campaign Name]
```
```
🔴 ARE-20034 | Clayton Alexander | Ascent Plan (Radio) Lead Gen Campaign
🟠 ARE-19960 | Trevor Phibbs | Custom VSL Campaign
```

---

### Task Naming Formats

**Corporate Internal Tasks:**
```
🟣 [Deliverable Type] | [Task Description] | [Project Name]
```
```
🟣 Email | Schedule Existing Advisor Email | Referral Playbook
```

**Corporate Event Tasks:**
```
🟡 [Deliverable Type] | [Location/Event Identifier] | [Event Name]
```
```
🟡 Final Docs Box | Munich | Incentive Trip 2026
```

**Advisor Tasks:**
```
[Dot] [Task Description] | [Advisor Name] | [Campaign/Project Name]
```
```
🔴 Primary Compliance Task | Clayton Alexander | Ascent Plan Lead Gen Campaign
🟠 Write Main Video Copy | Trevor Phibbs | Custom VSL Campaign
```

---

## Critical Rules

### Task Creation Order

**CRITICAL**: Tasks must be created in **REVERSE ORDER** within each section.

- Create the **LAST** task in the section **FIRST**
- Create the **FIRST** task in the section **LAST**
- This ensures tasks stack correctly — newest tasks appear at the bottom, so the first task ends up at the top

### Workflow Process

1. **User creates all sections manually** in the Asana UI before any tasks are created (sections cannot be created via API)
2. Claude retrieves section IDs using `asana_get_project_sections`
3. Claude creates tasks in **reverse order** within each section
4. Claude works through sections **bottom to top** (last section first)
5. User confirms before moving to the next section

---

## Standard Project Structure

Every project begins with a logistics section regardless of project type. Subsequent sections vary based on scope. The section name for the first section varies by project — use judgment based on context (common names: "Project Logistics", "Project Setup").

### Universal First Section — Project Logistics

*(Applies to all project types: advisor campaigns, corporate/internal, lead gen, content, etc.)*

This section is always first and contains the foundational setup tasks that must be completed before execution begins. The **Project Lead** owns these tasks — this role varies by project type (CSM, account manager, campaign lead, etc.).

**Tasks (create in reverse order):**
1. Write Project Brief
2. Write Project Brief *(second pass / updated version if needed — omit if single-pass)*
3. Kick Off *(Internal team kickoff only)*
4. Set Timeline and Owners

**Task Details:**

**Write Project Brief**
- Owner: Project Lead
- Purpose: Documents campaign goals, target audience, key deliverables, scope, and success criteria. This is the source of truth for all execution. Work cannot begin without a complete brief per Asana SOP.
- Must be completed before any copy, design, or buildout work begins.
- Link the brief in the task description and/or the project Overview tab.

**Kick Off**
- Owner: Project Lead
- Purpose: Internal team alignment meeting. Reviews the project brief, confirms scope, assigns owners, surfaces questions, and aligns on timeline before execution starts.
- This is an internal kickoff only — not client-facing unless explicitly noted.

**Set Timeline and Owners**
- Owner: Project Lead
- Purpose: Establishes due dates for each section/phase and confirms the assigned owner for every task in the project. A task without an owner and due date is not schedulable work per Asana SOP.
- Complete after kickoff so timeline is informed by team discussion.

---

## Standard Section Flow by Project Type

Sections after the logistics section vary by project type. The consistent pattern across all project types is:

```
[Work Section] → [Review Section for that work]
```

Copy and design are always separated — never mixed into the same section. Each has its own dedicated review section immediately following it.

### Lead Gen / Campaign Projects
1. Project Logistics
2. Copy & Review
3. Design & Review
4. Lead Gen Build Out *(or "Buildout")*
5. Build Out Review
6. Final Approvals
7. Maintenance

### Content / Playbook Projects
1. Design Phase I
2. Copy Phase I
3. Copy Phase II *(if paid/cold traffic in scope)*
4. Design Phase II *(if ad creative in scope)*
5. Media *(if video in scope)*
6. Marketing Operations

### Large Campaign Projects (e.g., multi-asset, multi-channel)
1. Project Logistics
2. Content & Copy Development
3. Copy & Content Review
4. Design & Production
5. Design Review
6. Buildout
7. Buildout Review
8. Launch & Promotion
9. Optimization & Maintenance

---

## Large Campaign Project — Standard Task List

The section structure for large advisor campaign projects is fixed. Use this task list as the starting template, then adjust tasks based on scope (e.g., remove video tasks if video is not in scope).

> ⚠️ **Build order:** Work through sections **bottom to top** (Section 9 first, Section 1 last). Within each section, create tasks in **reverse order** (last task first). This ensures tasks stack correctly in Asana.

### Section 1: Project Logistics
1. Write Project Brief
2. Write Project Brief *(second pass — omit if single-pass)*
3. Kick Off *(internal team only)*
4. Set Timeline and Owners

### Section 2: Content & Copy Development
1. Landing Page Copy
2. Video Script Finalization
3. Decision Checklist Copy
4. Email Sequence: Checklist Series
5. Email Sequence: Review Request Series
6. Article 1: [Topic]
7. Article 2: [Topic]
8. Article 3: [Topic]
9. Email Sequence: Database Campaigns
10. Email Sequence: Pre/Post Appointment

### Section 3: Copy & Content Review
1. Internal Copy Review (all assets)
2. Internal Copy Revisions
3. QA Review — Copy
4. QA Edits — Copy
5. Package Copy for Compliance
6. Compliance Edits — Copy
7. Copy Compliance Approved

### Section 4: Design & Production
1. Landing Page Design (Figma mockup → final)
2. Decision Checklist Design (PDF layout)
3. Video Production (shoot with [Name])
4. Video Editing & B-roll
5. Email Template Design

### Section 5: Design Review
1. Internal Design Review
2. Internal Design Revisions
3. QA Review — Design
4. QA Edits — Design
5. Package Design for Compliance
6. Compliance Edits — Design
7. Design Compliance Approved

### Section 6: Website & Technical Buildout
1. Landing Page Build (HubSpot/GHL)
2. Form Setup & Integrations
3. Video Hosting & Embedding
4. Article Publishing (SEO optimization)
5. Email Automation Setup (all sequences)
6. Calendar/Scheduling Integration

### Section 7: Buildout Review
1. QA Review — Landing Page & Forms
2. QA Edits — Landing Page
3. QA Review — Email Sequences
4. QA Edits — Email Automation
5. Package All Final Assets for Compliance
6. Compliance Review — Built Assets
7. Compliance Edits — Built Assets
8. Final Compliance Approved

### Section 8: Launch & Promotion
1. Google Ads Setup *(if applicable)*
2. YouTube Video Publishing *(if applicable)*
3. Final Client Review
4. Campaign Go-Live Checklist
5. Campaign Documentation & Handoff

### Section 9: Optimization & Maintenance
1. Week 1 Performance Review
2. Ongoing Monitoring & SEO Optimization

### Customizing the Template

Adjust tasks based on actual project scope:

| If this deliverable is NOT in scope... | Remove these tasks |
|---|---|
| Video | Video Script Finalization, Video Production, Video Editing & B-roll, Video Hosting & Embedding, YouTube Video Publishing |
| Articles | Article 1, 2, 3, Article Publishing |
| Google Ads | Google Ads Setup |
| Decision Checklist | Decision Checklist Copy, Decision Checklist Design |

Always maintain the section structure and review flow (copy review → design review → buildout review) regardless of scope.

---

## Task Description Standards

Every task description should give the owner everything they need to execute and know when they're done — without having to ask questions or hunt for context.

### What to Include (when relevant)

**Definition of Done**
Clearly state what "complete" looks like for this specific task. Don't leave it open to interpretation.
> Example: "Script is approved by CSM, formatted in the standard template, and saved to the shared drive with correct naming convention."

**Expected Turnaround / Duration**
Note the expected time to complete or the SLA window if one applies.
> Example: "2-day turnaround per SLA for Preferred tier advisors."

**Dependencies or Blockers**
If the task cannot start until something else is finished, call it out explicitly. Set the dependency in Asana AND note it in the description.
> Example: "Cannot begin until Copy Compliance Approved task is marked complete."

**Links to Briefs, References, or Prior Versions**
Include links to the project brief, creative brief, intake form, prior versions of the asset, brand guidelines, or any CNET workflow documentation relevant to this task.
> Example: "Refer to project brief linked in Overview tab. Prior version: [link]."

---

### Description Complexity — Match the Task

Not every task needs the same depth. Write the description to match what the owner actually needs to execute.

**Detailed / Instructional** — Use when the task involves a decision tree, a conditional workflow, or a handoff that could easily go wrong without guidance. Tell the owner exactly what to do, what to check, and what NOT to do until this is complete.
> *Example: "Verify Google Business Ownership" — includes intake form review instructions, two conditional paths (claim vs. confirm manager access), and a hard stop before the next task can proceed.*

**Standard / Contextual** — Use when the task is clear but benefits from knowing what "done" looks like, what it unlocks, or what to reference.
> *Example: "Send the advisor the templated email with instructions for how to add CreativeOne as a manager on their Google Business Profile. Do NOT mark complete until access is verified. Derek cannot submit to Whitespark until this step is done."*

**Simple / Directive** — Use when the task is straightforward and the deliverables just need to be listed clearly. Subtasks can carry the detail.
> *Example: "Write headline, benefit bullets, form copy, and credibility elements for GHL landing page."*

---

### When Claude Should Write a Description

Claude only writes task descriptions when there is **meaningful context to add** — not by default on every task.

Write a description when:
- The task has a non-obvious definition of done
- There is a conditional workflow or decision point the owner needs to navigate
- There are hard stops or dependencies that must be called out
- Specific instructions, links, or references are known and relevant
- The task is a key handoff point (compliance packaging, client review, kickoff, etc.)
- Subtasks exist and the parent description should orient the owner to the full scope

Skip the description when:
- The task name is fully self-explanatory and no additional context is available
- The task is a simple status or milestone marker
- No brief, reference, or dependency information has been provided

---

### Standard Review Section Task Sequence

Every review section — whether for copy, design, or buildout — follows this consistent task sequence:

1. Internal Review / Revisions
2. QA Review
3. QA Edits
4. Package for Compliance
5. Compliance Edits
6. Compliance Approved

> Not every project requires compliance steps. Include or omit based on project scope.

---

## Key People

| Role | Name | GID |
|------|------|-----|
| Approver / Reviewer (Corporate) | Perry Boles | 638841289035848 |
| Lead Designer | Schuyler | *(look up via typeahead)* |

**Perry Boles** should be assigned to all review, approval, and final review tasks on corporate/internal projects.

---

## API Function Reference

### Key Functions
- `asana_list_workspaces` — Get workspace ID
- `asana_create_project` — Create new project (requires team GID)
- `asana_get_project_sections` — Get section IDs after user creates them
- `asana_create_task` — Create individual task (requires project_id + section_id)
- `asana_typeahead_search` — Look up users by name

### Task Creation Parameters
```javascript
{
  name: "[Dot] Deliverable | Client Name | Project Name",
  project_id: "project_gid",
  section_id: "section_gid",
  assignee: "user_gid",   // Only when owner is known
  notes: "Task description"
}
```

---

## Common Pitfalls to Avoid

❌ **DON'T**:
- Mix copy and design tasks into the same section
- Skip the project logistics section
- Create tasks without an owner and due date (they are not schedulable work)
- Create tasks in forward order — they'll appear reversed in Asana
- Try to create sections via API — not supported
- Start execution work before the project brief is complete

✅ **DO**:
- Always match the color dot to the correct advisor tier or project type
- Create tasks in reverse order within every section
- Work through sections bottom to top when building via API
- Keep copy, design, and buildout in separate sections with paired review sections
- Confirm project brief is written before kickoff
- Remind user to manually assign Schuyler to design tasks on corporate projects
- Add the project to the appropriate portfolio after creation

---

## Quick Reference Checklist

Before starting project creation:
- [ ] Confirm project/content name
- [ ] Confirm color dot (advisor tier or corporate/internal)
- [ ] Confirm ARE number (advisor projects)
- [ ] Confirm project lead / owner
- [ ] Confirm which phases/sections are in scope
- [ ] Confirm if compliance review steps are required

During project creation:
- [ ] Create project shell first
- [ ] User adds custom fields manually
- [ ] User creates all sections in Asana UI
- [ ] Retrieve section IDs via `asana_get_project_sections`
- [ ] Create tasks section by section, bottom to top
- [ ] Create tasks within each section in reverse order (last task first)
- [ ] Assign Perry Boles to all review/approval tasks (corporate projects)
- [ ] Add overview text to project Overview tab
- [ ] Add project to appropriate portfolio

---

**Last Updated**: February 2026
**Version**: 1.2
**Reference Projects**:
- 🔴 ARE-20081 | Clayton Alexander | IHC Pension Freeze Campaign (GID: 1213230551292200)
- 🔴 Clayton Alexander | Ascent Plan Lead Gen Campaign (GID: 1213073361715900)
- 🟣 Referral Playbook | CreativeOne Marketing
