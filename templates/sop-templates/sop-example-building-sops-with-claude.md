# Example SOP: Building SOPs Using the Claude Project

> **Why this example exists:** This is a real, team-approved SOP converted to markdown for use as a reference template. Claude should study the phased procedure structure, callout placement, correction examples, and session close workflow when building new SOPs.

---

| SOP Title | Marketing Ops — AI — Building SOPs Using the Claude Project |||
|---|---|---|---|
| Owner | Marketing Operations Manager | Version | v1.0 |
| Last Updated | 02/26/2026 | Cadence | As needed — any time an SOP is required |
| Audience | Any marketing team member | Next Review | 06/01/2026 |

---

## 1. Purpose

This SOP exists because the quality of what the Claude Project produces is directly tied to how well you use it. Without a consistent approach — reading the right files first, asking the right questions upfront, and closing the loop with a Session Learnings block — outputs require more revision, corrections get lost, and the system doesn't improve over time.

When this process is followed, every SOP the team produces starts from shared knowledge, gets refined through real feedback, and leaves the system smarter than it was before.

## 2. Scope

This SOP covers the end-to-end process for using the Claude Project to produce a new SOP — from the initial prompt through file updates and session close. It applies to any team member who needs to build an SOP using the AI system.

This SOP does not cover: building other content types (emails, Zaps, Asana projects), using Claude for compliance reviews, or making manual edits to project files outside of a Claude session.

## 3. What You'll Need

- Access to the CreativeOne Claude Project (claude.ai — same login as your Anthropic account)
- A clear idea of the process you need to document — at minimum, the task name and who performs it
- Microsoft Teams — to send the Session Learnings block to the Marketing Manager at the end
- Approximately 30–60 minutes for a standard SOP (more for complex, multi-phase processes)

## 4. Procedure

### Phase 1 — Start the Session

1. Open the Claude Project in claude.ai and start a new conversation.

> 💡 **Tip:** Always work inside the Claude Project — not a general Claude chat. The Project has access to all the skill files, brand files, and memory files that make outputs accurate and consistent.

2. Tell Claude what you need. Use this prompt structure as your starting point — replace the bracketed sections with your specifics:

> 📋 **STARTER PROMPT — copy and customize:**
> I need to build an SOP for [describe the process]. The person who will execute this is [role]. Please review the relevant skill and project files first, then ask me any clarifying questions you need before writing anything.

### Phase 2 — Answer Claude's Questions

Claude will ask clarifying questions before writing anything. This is intentional — answer them as specifically as you can. The more precise your answers, the less revision the draft will need.

Common questions Claude will ask:

- Which specific tasks does this SOP cover?
- Who is the primary person executing this process?
- What tools, platforms, or lists are involved?
- Are there any thresholds, criteria, or definitions the SOP needs to use?
- Does an Asana task or recurring template already exist for this process?

> 💡 **Tip:** The instruction to "ask clarifying questions before writing" is important. It stops Claude from producing a draft based on assumptions. The questions it asks are what shape the final output.

> ⚠️ **Warning:** If you are not the person who executes the process being documented, loop in whoever does before answering. They will know the edge cases, platform quirks, and real criteria that make the difference between a theoretical SOP and one that actually gets used.

### Phase 3 — Review the Draft

Claude will produce a full SOP draft as a downloadable .docx file. Download it and review it against the following:

| ✓ | Task |
|---|---|
| ☐ | Every step reflects how the process actually works — not a general best practice |
| ☐ | Platform names, list names, and tool names are correct (e.g., Microsoft Teams, not Slack) |
| ☐ | Thresholds, criteria, and defined terms are accurate (e.g., exact day counts, exact list names) |
| ☐ | The completion/handoff step directs the executor to post a comment on the Asana task, then ping the relevant manager via Microsoft Teams |
| ☐ | Callout boxes (warnings, tips, common mistakes) are placed at genuinely high-risk or confusing steps |
| ☐ | The SOP could be followed by any team member without needing to ask someone for help |

### Phase 4 — Request Corrections

If anything in the draft is wrong or needs adjustment, tell Claude directly in the chat. Be specific — the more precise the correction, the cleaner the edit.

Examples of effective correction prompts:

- "We use Microsoft Teams, not Slack. Update every reference."
- "The list name is 'Unengaged Contacts | Active' — not the name you used."
- "The threshold is 300 days, not 6 months. Fix that throughout."
- "Add a warning callout at Step 3 — people often skip the log step."

> ❌ **Common mistake:** Sending vague feedback like "make it better" or "simplify this." Claude needs to know what specifically is wrong and what the correct information is. Vague feedback produces vague edits.

Repeat the review-and-correction cycle until the SOP is accurate. Claude will produce an updated .docx for each round of changes.

### Phase 5 — Request File Updates and Session Learnings

Once the SOP is finalized, prompt Claude to review whether any corrections or new information from the session should be reflected in the project files. This is what keeps the system improving — corrections made in one session get baked into future outputs automatically.

Use this prompt exactly:

> 📋 **SESSION CLOSE PROMPT — use verbatim:**
> Please review the SOP skill and my CLAUDE.md file and any other necessary files that would need to be updated with the new information you learned — if applicable. Then send the Session Learnings block directly to me via Microsoft Teams message.

Claude will:
- Identify which project files need updating
- Produce a formatted Session Learnings block
- Present the block as a ready-to-paste Microsoft Teams message addressed to you

> ⚠️ **Warning:** Do not skip this step. If corrections from the session are not logged, they will not carry forward. The next person who builds an SOP in this Project may run into the same issues you just corrected.

### Phase 6 — Send the Session Learnings and Update Files

1. Copy the Session Learnings block that Claude produces.
2. Send it as a Microsoft Teams message to the Marketing Manager.
3. The Marketing Manager will review the learnings and manually update the relevant project files — or delegate that update.

> 💡 **Tip:** Claude cannot write directly to the project files in Claude Projects — all file updates require a human to paste the content in manually. The Session Learnings block is formatted specifically to make that as fast as possible.

## 5. Verification — How to Know It's Done

- ☐ The finalized SOP .docx has been downloaded and saved to the appropriate shared location
- ☐ Every step in the SOP reflects actual process — not placeholder or assumed information
- ☐ The Session Learnings block has been sent to the Marketing Manager via Microsoft Teams
- ☐ If any project files needed updating, that work has been handed off to the Marketing Manager

## 6. Troubleshooting

| Problem | Solution |
|---|---|
| Claude skipped the clarifying questions and went straight to writing | This can happen if the initial prompt was too complete. Start a new session and include the instruction: "Ask me clarifying questions before writing anything." That phrase is the trigger. |
| The SOP draft contains incorrect platform names, tool names, or list names | Correct them explicitly in the chat (e.g., "The list is called X, not Y — fix throughout"). Then flag it in the Session Learnings block so the project files get updated and it doesn't happen again. |
| Claude produced a very generic SOP that doesn't reflect our actual process | The clarifying questions phase was likely skipped or answered too broadly. Go back and provide more specific answers — exact list names, day thresholds, role names, tool names. The more specific, the better the output. |
| The downloaded .docx looks different than expected (formatting issues) | Open in Microsoft Word rather than Google Docs — Word renders the formatting correctly. Google Docs may show slight inconsistencies with table borders or spacing. |
| I'm not sure whether a correction is a one-time fix or a permanent system rule | Ask Claude directly: "Should this be a permanent rule in [file name], or was this a one-time adjustment?" Claude will help you decide before logging anything. |

## 7. Related Resources

- SOP Skill File — `skills/sop-writing.md` (the rules Claude follows when building SOPs)
- CLAUDE.md — system brain; routing logic, compliance rules, and the full memory protocol
- `memory/corrections.md` — running log of past corrections and system learnings
- `memory/preferences.md` — running log of team preferences that shape Claude's outputs
- Example SOP: Marketing Ops — HubSpot — Monthly Data Cleanup (reference for expected output quality)
