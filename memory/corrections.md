# Corrections Log
---
<!-- Entries below -->

### 2026-02-26 — Team uses Microsoft Teams, not Slack
- **Context:** While building the Monthly HubSpot Data Cleanup SOP, an initial draft referenced Slack as the team communication tool. The Marketing Manager corrected this — the team uses Microsoft Teams, and all team members have access to it.
- **Learning:** Never reference Slack in any output. All team communication, notifications, and stakeholder pings happen in Microsoft Teams. When SOPs or processes include a "notify the team" or "send summary" step, always reference Microsoft Teams.
- **Files Updated:** context/tech-stack.md, skills/sop-writing.md, CLAUDE.md

### 2026-02-26 — SOP completion summaries are posted to Asana tasks
- **Context:** Same SOP session. The initial draft directed the executor to send a completion summary via a messaging tool. The correct method is posting a comment on the relevant monthly Asana task, then notifying via Microsoft Teams.
- **Learning:** For recurring operational SOPs, the completion summary should be documented as a comment on the associated Asana task. A Teams ping to the Marketing Operations Manager follows. Do not default to a standalone message as the primary record.
- **Files Updated:** skills/sop-writing.md

### 2026-02-26 — HubSpot unengaged contact lists and criteria confirmed
- **Context:** While building the Monthly HubSpot Data Cleanup SOP, placeholder logic was used for the unengaged contact threshold. The Marketing Manager provided the actual list names and criteria.
- **Learning:** CreativeOne's unengaged contact threshold uses two criteria (OR logic): (1) Last marketing email open date has not been updated in the last 300 days, OR (2) Marketing emails clicked has not been updated in the last 365 days. Two active lists exist in HubSpot for this:
  - "Unengaged Contacts | Active" — general unengaged population
  - "Unengaged Contracted Advisors" — subset of above; contacts who are currently contracted with CreativeOne AND meet the unengaged criteria. These require elevated care — do not suppress or delete without notifying the Marketing Operations Manager first.
- **Files Updated:** context/tech-stack.md (HubSpot section)
