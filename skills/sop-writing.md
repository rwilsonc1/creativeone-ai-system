# Skill: SOP Writing

> **Trigger:** Creating or improving a Standard Operating Procedure.
> **Tools:** Written SOPs (markdown/document) + Scribe (visual walkthroughs)
> **Brand context required:** No — SOPs use internal tone (clear, accessible, jargon-free).

---

## Philosophy: SOPs That People Actually Use

Most SOPs fail not because the information is wrong but because nobody reads them. The single most important measure of an SOP's quality is **adoption** — does the team actually reach for it when they need to do the task?

SOPs with high adoption share these traits:

1. **Short enough to not be intimidating.** If it looks like a wall of text, people skip it.
2. **Visual enough to scan.** People should be able to glance at it and orient themselves.
3. **Clear enough for any skill level.** The reader shouldn't need to ask someone to understand the SOP.
4. **Structured as a story.** It follows a logical narrative: why this matters → what you need → what you do → how you know it worked.
5. **Actionable from step 1.** No long preambles. Get to the procedure quickly.

**The golden rule: If someone can't follow this SOP start-to-finish without asking another person for help, it isn't done yet.**

---

## Pre-Flight Checklist

Before writing any SOP, answer these:

1. **What task does this SOP cover?** Define the exact scope. One SOP = one process. If it covers two distinct processes, split it into two SOPs.
2. **Who is the audience?** New employee? Experienced team member? Cross-department? This determines the level of detail and terminology.
3. **What format fits best?** (See Format Selection below)
4. **Does a Scribe walkthrough already exist or need to be created?** Scribe walkthroughs pair with written SOPs — they don't replace them.
5. **Check `memory/corrections.md` and `memory/preferences.md`** for SOP-specific learnings.

---

## Format Selection

Choose the right format for the task. Not every SOP needs the same structure.

| Format | Best For | Example |
|---|---|---|
| **Step-by-step** | Linear processes with a clear start and end. Most common format. | "How to send a marketing email in HubSpot" |
| **Checklist** | Tasks where the user already knows the process but needs to verify nothing was missed. | "Pre-send email quality check" |
| **Decision tree / flowchart** | Processes with branching outcomes or conditional logic. | "How to troubleshoot a failed Zap" |
| **Hierarchical** | Complex multi-phase processes with sub-tasks under each phase. | "Event marketing project setup (full lifecycle)" |

**Default to step-by-step** unless the task clearly calls for another format.

---

## SOP Structure

Every SOP follows this structure. Sections marked *(optional)* can be omitted for simple, short procedures.

### 1. Header Block

| Field | Description |
|---|---|
| **Title** | Clear, specific, action-oriented. Use the format: "How to [Action] in [Platform/Context]" |
| **Last Updated** | Date of most recent revision |
| **Owner** | Person responsible for maintaining this SOP |
| **Version** | Version number (v1.0, v1.1, etc.) |

### 2. Purpose — *Why this matters* (2–3 sentences max)

Answer: **Why does this SOP exist? What does it protect against or enable?**

This is the "story hook." It connects the reader to the reason this matters. Don't just say "this SOP covers X process." Say what goes wrong without it, or what success looks like when it's followed.

**Good example:**
> "This SOP ensures that every HubSpot marketing email goes through a consistent quality check before sending. Skipping these steps has led to emails going to wrong lists, broken personalization tokens, and missing CTAs — all of which hurt engagement and reflect poorly on our team."

**Bad example:**
> "This document outlines the procedure for quality checking emails."

### 3. Scope — *What this covers and what it doesn't* (2–3 sentences)

Be specific about boundaries. If there's a related SOP that covers adjacent work, link to it.

### 4. What You'll Need *(optional)*

A quick-reference list of tools, access, credentials, or prerequisites needed before starting. Use a simple bulleted list or a small table.

### 5. The Procedure — *The steps*

This is the core. Follow these writing rules:

**Structure rules:**
- **One step = one action.** If a step has "and" in it, consider splitting it into two steps.
- **Start every step with a verb.** "Click," "Open," "Navigate," "Enter," "Select," "Verify."
- **Number all steps.** Even if there are sub-steps, use numbered hierarchy (1, 1a, 1b, 2, 3...).
- **Keep steps short.** One to two sentences per step. If a step needs more explanation, add a "Note" or "Tip" callout beneath it.

**Language rules:**
- **Active voice only.** "Click the Send button" not "The Send button should be clicked."
- **Use consistent terminology.** If you call it a "workflow" in step 1, don't call it an "automation" in step 5.
- **Define jargon on first use.** If a term might be unfamiliar to any reader, explain it in parentheses the first time it appears.
- **Be literal.** "Click the blue 'Save' button in the top right corner" not "Save your work."

**Visual rules:**
- **Add a Scribe link or screenshot at key decision points.** Not every step needs a visual — but anywhere the user might hesitate or get lost, add one.
- **Use callout boxes for warnings, tips, and common mistakes.** Visually distinguish these from regular steps so they stand out at a glance.
- **Bold key UI elements.** When referencing buttons, menu items, or field names, bold them so readers can scan.

**Callout types:**

> ⚠️ **Warning:** Use for steps where a mistake could cause real damage (data loss, wrong list, irreversible action).

> 💡 **Tip:** Use for helpful shortcuts or best practices that aren't strictly required.

> ❌ **Common mistake:** Use for errors that people frequently make at this step.

### 6. Verification — *How you know it worked*

One to three checkpoints that confirm the procedure was completed successfully. This closes the loop and gives the reader confidence they did it right.

### 7. Troubleshooting *(optional)*

A short FAQ-style section for common issues. Format: **Problem → Solution.** Only include if there are known recurring issues.

### 8. Related Resources *(optional)*

Links to related SOPs, Scribe walkthroughs, external documentation, or team contacts.

---

## Length Guidelines

SOPs should be as short as possible while still being complete. Here are targets:

| Process Complexity | Target Length | Guideline |
|---|---|---|
| Simple (5–10 steps) | 1 page | Header + Purpose + Steps + Verification. No need for Scope or Troubleshooting. |
| Medium (10–20 steps) | 1–2 pages | Full structure. Include Scope and What You'll Need. |
| Complex (20+ steps) | 2–3 pages max | If it exceeds 3 pages, break it into multiple SOPs covering sub-processes. Link them together. |

**If an SOP feels too long, it probably covers too much.** Split it.

---

## Pairing SOPs with Scribe Walkthroughs

Scribe captures step-by-step visual walkthroughs with annotated screenshots. Here's how to pair them with written SOPs effectively:

| Element | Written SOP | Scribe Walkthrough |
|---|---|---|
| **Purpose** | Explains the why, context, and decision-making | Shows the exact clicks and screens |
| **Best for** | Reference, policy, edge cases, troubleshooting | First-time execution, visual learners, training |
| **Limitation** | Can be hard to follow in UI-heavy tasks without visuals | Doesn't capture why, warnings, or decision context well |

**How to pair them:**
1. Create the written SOP first (it forces you to think through the logic and edge cases).
2. Record the Scribe walkthrough by following the SOP steps.
3. Embed the Scribe link in the written SOP at the top of the Procedure section.
4. In the Scribe, add a link back to the written SOP for context and troubleshooting.

**Format for embedding:**
> 📹 **Visual Walkthrough:** [View Scribe Walkthrough →](link)
> *(Follow along with the visual guide while referencing the steps below for context and troubleshooting.)*

---

## Adoption Best Practices

Writing the SOP is only half the job. Getting people to actually use it:

1. **Involve the person who does the task.** If you're writing an SOP for someone else's process, interview them first. They'll know the edge cases and gotchas that make the difference between a usable SOP and a theoretical one.
2. **Test it with someone unfamiliar.** Have someone who hasn't done the task follow the SOP. If they get stuck, the SOP has a gap.
3. **Store them where people already work.** Link SOPs from Asana tasks, pin them in relevant channels, or embed Scribe links in project templates. Don't rely on people remembering to go look for them.
4. **Keep them alive.** Review SOPs when the process changes. Add a calendar reminder for a quarterly review of all active SOPs.
5. **Make them visually inviting.** A well-formatted SOP with clear headers, callout boxes, and white space gets read. A wall of text doesn't.

---

## SOP Naming Convention

Use a consistent naming pattern so SOPs are easy to find and organize:

**Pattern:** `[Department] - [Process Category] - [Specific Task]`

**Examples:**
- `Marketing Ops - Email - Pre-Send Quality Check`
- `Marketing Ops - Asana - Creating a New Event Project`
- `Marketing Ops - Zapier - Troubleshooting a Failed Zap`
- `Marketing Comms - EngageOne - Adding a New Advisor`

---

## Quality Check — Before Finalizing

- [ ] Title is clear and action-oriented
- [ ] Purpose section explains *why this matters* (not just what it covers)
- [ ] Every step starts with a verb and contains one action
- [ ] Jargon is defined on first use
- [ ] Key UI elements are bolded
- [ ] Warning/tip callouts are used at high-risk or confusing steps
- [ ] Verification section confirms how to know it worked
- [ ] Scribe walkthrough is linked (if applicable)
- [ ] Someone unfamiliar with the task could follow this without asking for help
- [ ] Length is within the guidelines for the complexity level

---

## Updating This File

When SOP-specific corrections or new patterns are discovered:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
