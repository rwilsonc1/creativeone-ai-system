# CreativeOne Marketing Operations AI System

> A structured AI system for the CreativeOne Marketing Operations team, built around Claude Code.

## Architecture

```
CLAUDE.md (Brain) → Skills (Execution) → Brands (Context) → Templates (Output) → Memory (Learning)
```

## Directory Structure

```
creativeone-ai-system/
├── CLAUDE.md                      ← System brain — read first every session
├── skills/                        ← How to execute specific task types
├── brands/
│   ├── creativeone/               ← Corporate brand (CreativeOne → Advisors/Prospects)
│   └── advisor/                   ← Advisor voice (Advisor → Consumer/Client)
├── context/                       ← Shared reference docs (compliance, tech stack)
├── templates/
│   └── email-templates/           ← Reusable email structures
└── memory/                        ← Corrections, preferences, project decisions
```

## Getting Started

1. Clone this repo
2. Open the directory in Claude Code
3. Claude reads `CLAUDE.md` first and routes from there

---

## Environment Model: Two-Track Deployment

This system is designed to run in two different environments with different capabilities. Understanding the distinction is important for system maintenance.

### Claude Code (Your Environment)

Claude Code has full read/write access to this repository. This means:
- Claude can directly update `memory/corrections.md` and `memory/preferences.md` during a session
- The Continuous Improvement Protocol (auto-updating source files when corrections occur) works as designed
- You are the primary user of Claude Code — this is where system maintenance happens

### Claude Projects (Team Environment)

Claude Projects have a **read-only knowledge base**. Claude can reference every uploaded file, but cannot write back to them. Conversations are ephemeral — nothing persists from one session to the next unless a human manually updates the files. This means:
- The memory files do not auto-update in Projects
- Corrections and preferences must be manually applied to the repo and re-uploaded to the Project
- The Session Close Protocol (in CLAUDE.md) compensates for this by surfacing copy-paste-ready update blocks at the end of sessions

### Maintenance Workflow

**You are the bridge between the two environments.**

| Environment | Who Uses It | Write Access | System Maintenance |
|---|---|---|---|
| **Claude Code** | You (Marketing Manager) | ✅ Full | Direct — Claude updates files automatically |
| **Claude Projects** | Marketing Ops team | ❌ Read-only | Manual — copy Session Learnings blocks into repo, then re-upload to Project |

**Recommended maintenance cadence:**

1. **After Claude Code sessions:** Files update automatically per the Continuous Improvement Protocol.
2. **After Project sessions (team use):** Claude surfaces a Session Learnings Block. Copy any corrections or preference entries into the appropriate `memory/` files in this repo. Sync updated files back to the Project.
3. **Weekly:** Review the week's Project conversations for anything worth logging. Update and re-upload in batch.
4. **When source files change:** Re-upload the updated file(s) to the Claude Project knowledge base. The old version does not auto-sync.
