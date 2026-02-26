# SOP Pattern Guide

> **What this file is:** A structural reference derived from real CreativeOne SOPs. Claude should use this as the authoritative pattern when building any new SOP. The rules below were extracted from actual team-produced SOPs — they are conventions, not suggestions.

---

## Header Block

Every SOP begins with a metadata table. This is non-negotiable — no SOP ships without it.

| Field | Format | Notes |
|---|---|---|
| SOP Title | `[Department] — [Category] — [Process Name]` | Use the team's naming convention. Examples: `Marketing Ops — AI — Using the Claude Project`, `Marketing Ops — HubSpot — Monthly Data Cleanup` |
| Owner | Role title (not person's name) | The person accountable for maintaining the SOP |
| Version | `v1.0`, `v1.1`, etc. | Increment minor version for edits, major version for structural rewrites |
| Last Updated | `MM/DD/YYYY` | Date of most recent edit |
| Cadence | Frequency or trigger | Examples: `Monthly`, `As needed`, `Quarterly`, `Event-triggered` |
| Audience | Who will read and execute this SOP | Examples: `Any marketing team member`, `Marketing Operations Manager`, `Marketing Automations Specialist` |
| Reviewed By | Role title of the reviewer/approver | Typically the next level up from the Owner |
| Next Review | `MM/DD/YYYY` | Scheduled date for the next review cycle |

**Layout:** The header block is a 4-column, 4-row table. Row 1 is the title spanning the row. Rows 2–4 pair fields side by side:

```
| SOP Title   | [Full title]              | [Full title]   | [Full title]  |
| Owner       | [Role]                    | Version        | [v#.#]        |
| Last Updated| [Date]                    | Cadence        | [Frequency]   |
| Audience    | [Who]                     | Next Review    | [Date]        |
```

If the SOP is reviewed/approved by someone, add a `Reviewed By` row.

---

## Section Structure

SOPs follow a numbered section pattern. Not every SOP needs every section, but the order is fixed. Do not rearrange.

### Required Sections (every SOP must have these)

1. **Purpose** — Why this SOP exists. 2–3 sentences. First sentence states the problem or need. Second sentence states what following this SOP accomplishes. Avoid generic purpose statements — connect to a real outcome.
2. **Procedure** — The step-by-step process. This is the core of the SOP. See "Procedure Structure" below.
3. **Troubleshooting** — Problem/Solution table covering the most common issues. Minimum 3 rows. See "Troubleshooting Format" below.
4. **Related Resources** — Bulleted list of connected documents, skill files, or tools. Include file paths where relevant.

### Conditional Sections (include when applicable)

- **Scope** — What this SOP covers AND what it does not cover. Use when the process boundary isn't obvious or when people might confuse this SOP's scope with another process. Two paragraphs: first states what's in scope, second states what's explicitly out of scope.
- **What You'll Need / Prerequisites** — Bulleted list of access, tools, knowledge, or time estimates needed before starting. Use when the process requires specific setup or access that the executor might not have by default.
- **Verification / How to Know It's Done** — Checklist of completion criteria. Use when the process has a defined "done" state that needs to be confirmed. Format as a checklist with checkboxes (`☐`).

### Section Order (fixed)

```
1. Purpose
2. Scope (if needed)
3. What You'll Need / Prerequisites (if needed)
4. Procedure
5. Verification — How to Know It's Done (if needed)
6. Troubleshooting
7. Related Resources
```

---

## Procedure Structure

The Procedure section uses **named phases** to group related steps. This is the most distinctive element of the CreativeOne SOP format.

### Phase Pattern

Each phase gets:
- A **phase header** formatted as: `Phase [#] — [Action-Oriented Name]`
- Numbered or bulleted steps underneath
- Callout boxes inserted at high-risk, commonly confused, or high-value moments

### Phase Naming Convention

Phase names are short, action-oriented, and describe what happens in that phase — not what section of the document it is.

**Good phase names:**
- `Phase 1 — Start the Session`
- `Phase 2 — Answer Claude's Questions`
- `Phase 3 — Review the Draft`
- `Phase 4 — Request Corrections`
- `Phase 5 — Request File Updates and Session Learnings`
- `Phase 6 — Send the Session Learnings and Update Files`

**Bad phase names:**
- `Phase 1 — Introduction` (not action-oriented)
- `Phase 2 — Steps` (too generic)
- `Phase 3 — Miscellaneous` (meaningless)

### Step Writing Rules

- Write steps as direct instructions: "Open the Claude Project" not "The user should open the Claude Project"
- One action per step. If a step has an "and" in it, consider splitting it.
- Include the exact platform, list, tool, or field name — never use a generic reference when a specific name exists.
- When a step involves a specific prompt or command, include it verbatim in a callout box labeled `📋 [PROMPT TYPE] — copy and customize` or `📋 [PROMPT TYPE] — use verbatim`.
- After steps that produce output (a draft, a report, a file), include what to do with that output — download it, review it, send it somewhere.

---

## Callout Boxes

Callout boxes are the visual signaling system in CreativeOne SOPs. They break up dense procedure sections and draw attention to critical moments. They are formatted as single-cell tables with an emoji prefix.

### Callout Types

| Type | Emoji | When to use | Example opening |
|---|---|---|---|
| **Tip** | 💡 | Helpful but non-critical guidance. Best practices, time-savers, "nice to know" information. | `💡 Tip: Always work inside the Claude Project — not a general Claude chat.` |
| **Warning** | ⚠️ | Critical step that, if skipped or done wrong, causes a real problem. Data loss, incorrect output, broken process. | `⚠️ Warning: Do not skip this step. If corrections from the session are not logged, they will not carry forward.` |
| **Common Mistake** | ❌ | A specific error the team has seen people make. Describes the mistake and the correct approach. | `❌ Common mistake: Sending vague feedback like 'make it better.' Claude needs to know what specifically is wrong.` |
| **Starter Prompt** | 📋 | A copy-paste-ready prompt or command. Always label whether it should be used verbatim or customized. | `📋 STARTER PROMPT — copy and customize` |

### Callout Placement Rules

- Place callout boxes **immediately after** the step they relate to — not before, not in a separate section.
- Don't cluster multiple callouts back-to-back. If two callouts are needed at the same step, combine them or spread them across sub-steps.
- Every SOP should have **at least 2 callout boxes** in the Procedure section. An SOP with zero callouts is missing visual signaling.
- Don't overuse callouts. If every step has a callout, none of them stand out. Reserve them for genuinely important moments.

---

## Troubleshooting Format

The Troubleshooting section is always a two-column table: `Problem` and `Solution` (or `Fix`).

### Rules

- Minimum 3 rows, maximum 8. If you need more than 8, the process is probably too complex for a single SOP.
- Problems should be described as symptoms the executor would actually experience — not technical root causes. Write from the user's perspective.
- Solutions should be actionable — specific steps to fix the issue, not "contact your manager."
- If a solution involves flagging something for system improvement (e.g., updating a project file), say so explicitly.

**Good problem description:** "Claude's output doesn't match our tone or standards"
**Bad problem description:** "Brand voice file not loaded into context window"

---

## Related Resources Format

Bulleted list. Each item includes:
- The document name (human-readable)
- The file path or location (if it exists in the system)
- A brief description of what it is — one clause, not a sentence

**Example:**
- SOP Skill File — `skills/sop-writing.md` (the rules Claude follows when building SOPs)
- CLAUDE.md — system brain; routing logic, compliance rules, and the full memory protocol
- corrections.md — running log of past corrections and system learnings

---

## Tone and Language

- **Direct and instructional.** SOPs are not persuasive documents — they are reference documents. Write like you're training someone, not selling them.
- **Second person ("you").** "Open the Project" or "Tell Claude what you need" — not "The user opens the Project."
- **Specific over general.** "Post a comment on the Asana task, then ping the Marketing Manager via Microsoft Teams" — not "Notify the relevant parties."
- **No jargon without explanation.** If a term is specific to the team's tools or processes, define it on first use or link to a resource that does.
- **Accessible to any skill level.** A new team member with no prior context should be able to follow the SOP without asking someone for help. That's the bar.

---

## File Output

SOPs are delivered as `.docx` files. Claude produces the downloadable file at the end of the drafting process. The executor downloads, reviews, and stores the final version in the appropriate shared location.

Within the AI system (Claude Project knowledge base or repo), SOPs are referenced and templated in `.md` format for portability and token efficiency.
