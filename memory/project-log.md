# Project Decision Log
---
<!-- Entries below -->

### 2026-02-26 — Dual-Environment Deployment Model Established
- **Context:** Evaluated whether Claude's memory system (corrections.md, preferences.md, auto-updating source files) could function in Claude Projects the same way it does in Claude Code. Determined that Claude Projects have a read-only knowledge base — Claude can read uploaded files but cannot write back to them. Conversations are ephemeral and nothing persists automatically.
- **Decision:** Adopt a two-track deployment model. Claude Code (used by the Marketing Manager) is the maintenance environment with full read/write capability. Claude Projects (used by the team) is a consumption environment where updates require manual intervention.
- **Compensation mechanism:** Added a Session Close Protocol to CLAUDE.md that instructs Claude to surface a copy-paste-ready "Session Learnings Block" at the end of any productive session. This makes it practical to manually propagate corrections and preferences from Project sessions back into the repo.
- **Maintenance workflow:** Marketing Manager reviews Project session outputs, copies learnings into the repo's memory files, and re-uploads changed files to the Project. Weekly batch review recommended.
- **Files Updated:** `CLAUDE.md` (Session Close Protocol section added), `README.md` (Two-track deployment model section added)
