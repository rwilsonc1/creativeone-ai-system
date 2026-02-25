# Advisor Brand Directory

Voice and context for content written **as an advisor** to their clients and prospects (consumers).

**All content from this directory is subject to compliance rules in `context/compliance-guidelines.md`.**

## Layered Architecture

```
voice-foundation.md          ← Always loaded (universal advisor voice)
    ↓
verticals/[vertical].md      ← Layered on (topic-specific adjustments)
    ↓
individual/[advisor].md       ← Layered on if exists (personal overrides)
```

## File Map

| File | Purpose |
|---|---|
| `voice-foundation.md` | Universal advisor voice — tone, do/don't, anti-patterns |
| `audience.md` | Consumer/client audience profile (retirees, pre-retirees) |
| `positioning.md` | General advisor-to-consumer positioning framework |
| `verticals/annuity.md` | Annuity-specific voice and compliance adjustments |
| `verticals/life.md` | Life insurance-specific voice and compliance adjustments |
| `verticals/wealth.md` | Wealth management-specific voice and compliance adjustments |
| `verticals/securities.md` | Securities-specific voice and compliance adjustments |
| `individual/_TEMPLATE.md` | Template for creating individual advisor profiles |
| `assets.md` | Accumulated examples and references |
| `learnings.md` | Corrections and patterns discovered through use |
