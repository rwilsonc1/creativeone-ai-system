# Tech Stack Reference

> This file provides platform details, integrations, and known quirks for the CreativeOne marketing tech stack.
> Referenced by: Any skill involving platform-specific work.
> Updates: When a new integration, quirk, or platform detail is discovered, update this file AND log in `memory/corrections.md`.

---

## Core Platforms

### HubSpot
- **Role:** CRM, email marketing, workflows, data management
- **Primary users:** Marketing Operations Manager, Marketing Manager
- **Key functions we use:**
  - Contact and company management
  - Email creation and sending
  - Marketing workflows (automation)
  - Lists (active and static)
  - Forms and landing pages
  - Reporting and dashboards
- **Integrations:** Connected to Zapier for cross-platform automations
- **Known quirks:**
  - *(Add discovered quirks here as they come up)*

### Asana
- **Role:** Project management, task management, team workload tracking
- **Primary users:** Entire Marketing Operations team
- **Key functions we use:**
  - Projects (Waterfall-style, with Agile when appropriate)
  - Tasks, subtasks, dependencies
  - Custom fields and templates
  - Workload view for team capacity
  - Native automations (rules)
  - Zapier-powered automations
- **Integrations:** Connected to Zapier; native automations used alongside Zaps
- **Known quirks:**
  - *(Add discovered quirks here as they come up)*

### GoHighLevel
- **Role:** Marketing automation platform
- **Primary users:** Marketing Automations Specialist
- **Key functions we use:**
  - Marketing automation workflows
  - Funnel/pipeline management
- **Integrations:** Connected to Zapier
- **Known quirks:**
  - *(Add discovered quirks here as they come up)*

### Zapier
- **Role:** Integration and automation layer between platforms
- **Primary users:** Marketing Manager, Marketing Operations Manager
- **Key functions we use:**
  - Zaps connecting HubSpot, Asana, GoHighLevel, and other tools
  - Multi-step Zaps with filters, formatters, and paths
  - Error monitoring and troubleshooting
- **Common Zap patterns:**
  - *(Document recurring Zap patterns here as they're built)*
- **Known pain points:**
  - Broken connections are a frequent issue
  - Debugging failed Zaps is a recurring task
  - *(Add specific recurring issues here)*

---

## Content & Client-Facing Platforms

### Snappy Kraken (EngageOne)
- **Role:** White-labeled advisor content and nurture platform
- **What it provides advisors:**
  - Email nurture sequences
  - Social media content
  - Timely communications about real-world events affecting finances
- **Managed by:** Marketing Communications Specialist
- **Key notes:**
  - This is a white-labeled service — advisors see it as "EngageOne," not Snappy Kraken
  - Content must comply with all compliance guidelines

### WhiteSpark (Local Spark)
- **Role:** White-labeled citation building and business listing management
- **What it provides advisors:**
  - Citation building across platforms
  - Business listing accuracy management
- **Key notes:**
  - This is a white-labeled service — advisors see it as "Local Spark," not WhiteSpark

---

## Analytics & Tracking

### Google Analytics 4 (GA4)
- **Role:** Web analytics
- **Growth area:** Team is actively deepening GA4 knowledge
- **Known quirks:**
  - *(Add discovered quirks here)*

### Google Tag Manager (GTM)
- **Role:** Tag management and tracking implementation
- **Growth area:** Team is actively building GTM capabilities
- **Known quirks:**
  - *(Add discovered quirks here)*

### Google Search Console (GSC)
- **Role:** Search performance and indexing monitoring
- **Growth area:** Team is improving GSC utilization
- **Known quirks:**
  - *(Add discovered quirks here)*

### Looker Studio
- **Role:** Data visualization and dashboards
- **Growth area:** Team is building stronger dashboard practices
- **Known quirks:**
  - *(Add discovered quirks here)*

### Microsoft Clarity
- **Role:** Heatmaps and session recordings
- **Known quirks:**
  - *(Add discovered quirks here)*

---

## Infrastructure

### Cloudflare
- **Role:** DNS, security, performance
- **Known quirks:**
  - *(Add discovered quirks here)*

---

## Documentation Tools

### Scribe
- **Role:** Visual SOP/process documentation
- **How we use it:** Scribe captures step-by-step visual walkthroughs. These are paired with written SOPs for comprehensive process documentation.
- **Key notes:**
  - Scribe walkthroughs supplement written SOPs — they don't replace them
  - The SOP skill file defines how written SOPs and Scribe walkthroughs work together

---

## Integration Map

A high-level view of how platforms connect:

```
HubSpot ←→ Zapier ←→ Asana
              ↕
         GoHighLevel

Snappy Kraken (EngageOne)    → Advisor-facing (managed separately)
WhiteSpark (Local Spark)     → Advisor-facing (managed separately)

GA4 + GTM + GSC + Clarity    → Analytics layer (feeds into Looker Studio)
```

---

## Updating This File

When a new tool, integration, platform quirk, or workaround is discovered:

1. Add it to the appropriate section above.
2. Log the change in `memory/corrections.md` with date and context.
