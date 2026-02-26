# Project Decision Log
---
<!-- Entries below -->

### 2026-02-26 — Asana Skill Consolidation and Compliance Skill Reorganization
- **Context:** Reviewed three new skill files (asana-project-creation.md, asana-project-setup.md, compliance-marketing.md) against existing skills (asana-process-building.md, compliance-review.md) to determine whether to merge or keep separate.
- **Decision (Asana):** All three Asana files serve distinct purposes and should stay separate: asana-process-building.md (strategic process design), asana-project-setup.md (tactical project execution, all types), and the content of asana-project-creation.md (detailed 9-section campaign task list) was merged into asana-project-setup.md as the "Large Campaign Project — Standard Task List" section. asana-project-creation.md was deleted as it was superseded by the merged v1.2 of project-setup.md.
- **Decision (Compliance):** compliance-marketing.md (writing compliant copy) and compliance-review.md (auditing existing copy) serve different jobs and must stay separate. compliance-marketing.md was reformatted from a single-line blob to proper markdown and updated: (1) added skill header per system conventions, (2) softened the hard testimonial ban to align with the 2022 SEC Marketing Rule (testimonials permitted with full disclosure compliance), (3) added companion skill reference.
- **Routing changes:** CLAUDE.md routing table updated — Asana row split into two (process design vs. project setup); compliance-marketing.md added as a co-load with email-marketing for advisor-voiced content; compliance row updated to "reviewing existing content."
- **Files Updated:** skills/asana-project-setup.md (merged task list, reformatted, v1.2), skills/asana-project-creation.md (deleted), skills/compliance-marketing.md (full rewrite), CLAUDE.md (routing table)

### 2026-02-26 — Dual-Environment Deployment Model Established
- **Context:** Evaluated whether Claude's memory system (corrections.md, preferences.md, auto-updating source files) could function in Claude Projects the same way it does in Claude Code. Determined that Claude Projects have a read-only knowledge base — Claude can read uploaded files but cannot write back to them. Conversations are ephemeral and nothing persists automatically.
- **Decision:** Adopt a two-track deployment model. Claude Code (used by the Marketing Manager) is the maintenance environment with full read/write capability. Claude Projects (used by the team) is a consumption environment where updates require manual intervention.
- **Compensation mechanism:** Added a Session Close Protocol to CLAUDE.md that instructs Claude to surface a copy-paste-ready "Session Learnings Block" at the end of any productive session. This makes it practical to manually propagate corrections and preferences from Project sessions back into the repo.
- **Maintenance workflow:** Marketing Manager reviews Project session outputs, copies learnings into the repo's memory files, and re-uploads changed files to the Project. Weekly batch review recommended.
- **Files Updated:** `CLAUDE.md` (Session Close Protocol section added), `README.md` (Two-track deployment model section added)
