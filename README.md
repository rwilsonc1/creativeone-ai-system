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
