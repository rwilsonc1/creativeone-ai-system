# Example SOP: Using the Claude Project

> **Why this example exists:** This is a real, team-approved SOP converted to markdown for use as a reference template. Claude should study the structure, tone, callout placement, and level of detail when building new SOPs.

---

| SOP Title | Marketing Ops — AI — Using the Claude Project |||
|---|---|---|---|
| Owner | Marketing Operations Manager | Version | v1.0 |
| Last Updated | 02/26/2026 | Audience | Any marketing team member |
| Reviewed By | Marketing Manager | Next Review | 06/01/2026 |

---

## 1. Purpose

The CreativeOne Claude Project is a customized AI assistant built specifically for this marketing team. Unlike a general AI chatbot, it knows our tech stack, our brand voice, our compliance rules, and our processes — because all of that context has been built into it. The quality of what it produces depends almost entirely on how clearly you ask.

This SOP gives any team member the knowledge to use the Project confidently: what it can do, how to prompt it well, and how to close a session properly so the system keeps improving over time.

## 2. What the Project Knows

Before you open a chat, it helps to understand what context the Project has access to. This is what makes it different from a standard Claude chat.

| What's built in | What that means for you |
|---|---|
| Skill files for every task type | Claude knows how to build SOPs, emails, Zaps, SLAs, Asana projects, compliance reviews, and data analyses — using CreativeOne's specific standards, not generic best practices. |
| CreativeOne brand voice | Claude writes in the correct tone for every context — formal and advisor-focused for B2B content, compliance-safe for advisor-to-client content, clear and direct for internal docs. |
| Compliance rules | For any content written as or for an advisor to their clients, Claude automatically applies the correct compliance constraints without being asked. |
| Tech stack details | Claude knows we use HubSpot, Asana, Zapier, GoHighLevel, Microsoft Teams, and the rest of the stack — so platform-specific steps and references are accurate. |
| Memory files | Claude checks past corrections and preferences at the start of every session, so mistakes from previous sessions don't repeat. |

## 3. Accessing the Project

1. Go to claude.ai and sign in with your Anthropic account.
2. In the left sidebar, locate the CreativeOne Marketing Ops Project under Projects.
3. Click the Project to open it, then click New conversation to start a fresh session.

> ⚠️ **Warning:** Always use the Claude Project — not a general Claude.ai chat or a new project. The context files that make outputs accurate only exist inside this Project. A general chat will produce generic output that won't match our standards.

> 💡 **Tip:** Each conversation inside the Project is independent — Claude does not remember what was said in a previous conversation. Always include the relevant context in your current message. The memory files handle long-term learning, but within-session context is on you.

## 4. How to Prompt Well

The Project is only as good as the instructions it receives. These are the five principles that consistently produce the best outputs:

| Principle | What it means in practice |
|---|---|
| Be specific, not vague | The more context you give, the less Claude has to assume — and the less you have to correct. Name the platform, the role, the list, the criteria. |
| Tell Claude who the content is for | "From CreativeOne to advisors" vs. "from an advisor to their clients" triggers completely different brand voices and compliance rules. Always state the audience. |
| Let Claude ask questions first | For any complex task, add the phrase "ask me clarifying questions before writing anything." This prevents a full draft built on wrong assumptions. |
| Corrections are instructions | If something is wrong, say exactly what is wrong and what the correct information is. Vague feedback ("make it better") produces vague edits. |
| Always close the session | At the end of every productive session, run the Session Close prompt. This is what keeps the system improving over time. |

### Anatomy of a Good Prompt

Most strong prompts share the same structure. You don't need all four parts every time, but the more you include, the less back-and-forth you'll need:

| Part | What it does | Example |
|---|---|---|
| Task | Tells Claude what to build | I need to build an SOP for... |
| Audience / direction | Tells Claude who the content is for and who it's from | This is content from CreativeOne to advisors / This is written as an advisor to their clients |
| Context | Fills in the specifics Claude can't know on its own | The person executing this is the Marketing Automations Specialist. The list is called 'Unengaged Contacts | Active.' |
| Instructions | Shapes how Claude approaches the work | Ask me clarifying questions before writing anything. / Keep it under one page. |

## 5. Compliance — What You Need to Know

Compliance rules apply to content written as or for advisors communicating with their clients or prospects. They do not apply to internal content or CreativeOne B2B marketing. Claude applies these rules automatically — but you need to tell it clearly who the content is for.

| Content type | Compliance behavior |
|---|---|
| ✅ CreativeOne → Advisors/Prospects | No compliance rules apply. Claude uses full brand voice from the CreativeOne brand files. |
| ⚠️ Advisor → Consumer/Client | Compliance rules always apply. No promissory language, no outcome guarantees. Claude will flag issues automatically. |
| 📋 Internal (SOPs, process docs, Asana) | No compliance rules apply. Claude uses clear internal tone. |

> ❌ **Common mistake:** Not stating the audience. If you ask Claude to "write an email about annuities" without saying whether it's from CreativeOne to advisors or from an advisor to clients, Claude will make a judgment call — and it may be the wrong one. Always state the direction.

## 6. Starter Prompts by Task Type

Use these as starting points. Replace the bracketed sections with your specifics. The prompt structure is designed to give Claude the minimum it needs to either start — or ask the right clarifying questions.

### ✉️ Marketing Email

**When to use + key info to include:**
Use when you need to write or edit a marketing email in HubSpot. Always specify who it's from (CreativeOne or an advisor) and who it's to (advisors, clients, prospects). For advisor-to-client emails, name the vertical (annuity, life, wealth, securities). Include any key message, CTA, or deadline if you have one.

> 📋 **Starter prompt:**
> I need to write a marketing email. This email is from [CreativeOne / advisor name] to [advisors / clients / prospects]. The goal is [describe the goal]. [If advisor-to-client: The vertical is [annuity / life / wealth / securities].] Key message: [describe]. CTA: [describe]. Please review the relevant skill and brand files, then ask clarifying questions before writing.

### 📋 Standard Operating Procedure (SOP)

**When to use + key info to include:**
Use when you need to document a repeatable process. Name the process and who executes it. Mention any tools, platforms, or lists involved. If you are not the person who executes the process, loop them in before answering Claude's questions.

> 📋 **Starter prompt:**
> I need to build an SOP for [describe the process]. The person who will execute this is the [role]. Please review the relevant skill and project files, then ask me clarifying questions before writing anything.

### 🤝 Service Level Agreement (SLA)

**When to use + key info to include:**
Use when you need to define turnaround times and responsibilities between two teams or roles. Identify who is the service provider and who is the requester. Have an idea of the services to be covered and any known turnaround targets. SLAs are two-way — Claude will ask about both sides' responsibilities.

> 📋 **Starter prompt:**
> I need to build an SLA between [provider team/role] and [requester team/role]. The services to be covered are [describe]. I have [some / no] data on current turnaround times. Please review the SLA skill file and ask clarifying questions before writing.

### 📌 Asana Project or Workflow

**When to use + key info to include:**
Use when you need to build, restructure, or template a project or process in Asana. Describe the workflow: what triggers it, who is involved, what the phases are. Mention if you want native Asana automations, Zapier-powered automations, or both. Note if this is a one-off project or a repeating template.

> 📋 **Starter prompt:**
> I need to build [a project / a template / a workflow] in Asana for [describe the process]. The team members involved are [roles]. It [is / is not] a recurring process. I [want / do not want] automations built in. Automation type: [native Asana / Zapier / both]. Please review the Asana skill file and ask clarifying questions before building.

### ⚡ Build a New Zap

**When to use + key info to include:**
Use when you need to create a new automation connecting two or more platforms. Name the trigger platform and the action platform(s). Describe what the automation should do in plain language before worrying about technical steps. Mention any filters, conditions, or branching logic if you know of any.

> 📋 **Starter prompt:**
> I need to build a new Zap. The trigger is [describe trigger + platform]. The action(s) should [describe what should happen] in [platform(s)]. Conditions or filters: [describe, or 'none that I know of']. Please review the Zap building skill file and ask clarifying questions before mapping the steps.

### 🔧 Troubleshoot a Broken Zap

**When to use + key info to include:**
Use when a Zap has failed or is producing unexpected results. Share the Zap name and which step is failing. Copy the error message from Zapier's task history if you can find it. Describe what the Zap is supposed to do vs. what it is actually doing.

> 📋 **Starter prompt:**
> I have a broken Zap that needs troubleshooting. The Zap is called [Zap name]. The step that is failing is [Step # / step name]. Error message: [paste error, or 'not visible']. What it should do: [describe]. What it's actually doing: [describe]. Please review the Zap troubleshooting skill file and help me diagnose the issue.

### ✅ Compliance Review

**When to use + key info to include:**
Use when you have a piece of content that needs to be reviewed against compliance rules before it goes out. Paste the content directly into the message. Specify whether the content is advisor-to-client or CreativeOne-to-advisor — this determines which rules apply. Name the vertical if it's advisor-to-client content.

> 📋 **Starter prompt:**
> Please review the following content for compliance. This content is [from an advisor to their clients / from CreativeOne to advisors]. [If advisor-to-client: The vertical is [annuity / life / wealth / securities].]
>
> [Paste content here]

### 📊 Data Analysis or Dashboards

**When to use + key info to include:**
Use when you need help interpreting data, defining KPIs, or building a report or dashboard. Describe the question you are trying to answer — not just the chart you want. Name the platform(s) where the data lives. Note who the audience for the output is.

> 📋 **Starter prompt:**
> I need help with [a data analysis / a dashboard / interpreting metrics]. The question I'm trying to answer is: [describe]. The data lives in [platform(s)]. The audience for this output is [team / leadership / other]. Please review the data analysis skill file and ask clarifying questions before building.

## 7. Closing a Session — Always Do This

At the end of any productive session — one where Claude produced a draft, you provided corrections, or you gave Claude new information about our processes or tools — run the Session Close prompt. This is what keeps the system improving.

If you skip this step, corrections made in your session stay in the chat and disappear. The next person who uses the Project may run into the exact same issue you just fixed.

> 📋 **SESSION CLOSE PROMPT — use verbatim:**
> Please review the relevant skill files and my CLAUDE.md file and any other project files that would need to be updated with the new information you learned during this session — if applicable.

Claude will produce a formatted Session Learnings block. Copy it and send it as a Microsoft Teams message to the Marketing Manager. The Marketing Manager reviews the learnings and manually updates the relevant project files.

> 💡 **Tip:** Claude cannot write to the project files directly — only humans can do that. The Session Learnings block is formatted to make manual updates as fast as possible. Think of it as handing off a set of clean, copy-paste-ready notes.

## 8. Troubleshooting

| Problem | Fix |
|---|---|
| Claude's output doesn't match our tone or standards | Make sure you're working inside the Claude Project, not a general chat. General chats don't have access to the brand, skill, or memory files. If you're already in the Project, add more context about the audience and content type. |
| Claude used the wrong platform name, list name, or tool | Correct it explicitly: "The list is called X, not Y — fix throughout." Then flag it in the Session Learnings block so the project files get updated. |
| Claude wrote advisor-to-client content without compliance rules applied | You likely didn't specify the audience direction. Always tell Claude explicitly: "This is from an advisor to their clients." That phrase triggers compliance mode. |
| The output is too generic — it doesn't feel like it's built for CreativeOne | Add more specifics to your prompt: the exact role, exact tool, exact list name, exact criteria. Specificity is the single biggest driver of output quality. |
| Claude asked clarifying questions but I wasn't sure how to answer one | Answer as best you can, and tell Claude what you're uncertain about. It will work with partial information and flag what still needs to be defined. You can also ask Claude: "What would you recommend as a default for this?" |
| I'm not sure if my task is covered by the Project | When in doubt, describe what you need in plain language and ask Claude: "Is this something you can help with using the CreativeOne Project?" Claude will tell you what it can do and what it needs from you. |

## 9. Quick Reference — What to Always Include

| Task type | Must-include in your prompt |
|---|---|
| Any email | Who it's from + who it's to + goal + CTA |
| Advisor-to-client email | Vertical (annuity / life / wealth / securities) |
| SOP | Process name + who executes it + tools/lists involved |
| SLA | Provider team + requester team + services covered |
| Asana project/template | Workflow phases + roles involved + automation type |
| New Zap | Trigger platform + action platform + what it should do |
| Zap troubleshooting | Zap name + failing step + error message + expected vs. actual behavior |
| Compliance review | Content + audience direction + vertical (if advisor-to-client) |
| Data/dashboard | The question to answer + data platform + audience for the output |

## 10. Related Resources

- SOP: Building SOPs Using the Claude Project — step-by-step guide for the SOP-specific workflow
- CLAUDE.md — the system brain; full routing logic, compliance rules, and memory protocol
- `skills/` folder — individual skill files for each task type (sop-writing.md, email-marketing.md, etc.)
- `memory/corrections.md` — running log of past corrections; review if outputs seem off
- `memory/preferences.md` — running log of team preferences that shape Claude's defaults
