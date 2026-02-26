# Skill: Data Analysis

> **Trigger:** Any request involving data interpretation, reporting, dashboard design, analytics troubleshooting, KPI definition, data hygiene, UTM tracking, or performance measurement across CreativeOne's marketing operations.
> **Context required:** Load relevant platform-specific context as needed — `skills/email-marketing.md` for email KPIs, `skills/zap-building.md` for automation metrics, `context/asana-sop.md` for project data.
> **Governance rule:** Marketing Ops owns the analytics stack. All dashboard builds, tracking implementations, and data hygiene processes go through Marketing Ops.
> **Compliance note:** No advisor-facing reports or dashboards should use promissory language about outcomes. Apply the same compliance standards from client-facing content to any data visualizations or reports shared externally.

---

## Philosophy: Data That Drives Decisions, Not Just Dashboards

The purpose of data analysis at CreativeOne is not to produce charts. It's to answer questions that lead to better decisions. Every metric, dashboard, and report should pass a simple test: **"What will someone do differently because of this information?"** If the answer is nothing, the metric is noise.

**Core principles:**

1. **Measure what matters, not what's easy.** Vanity metrics (impressions, follower counts, raw page views) look good in presentations but rarely drive action. Focus on KPIs that connect directly to business outcomes — advisor engagement, event attendance, lead conversion, content that moves advisors through the relationship lifecycle.

2. **Context makes data useful.** A number without context is meaningless. "500 clicks" means nothing. "500 clicks, up 23% from last month, with a 4.2% conversion rate against our 3% target" is actionable. Always provide comparison points: previous period, target/benchmark, segment breakdown.

3. **Clean data is a prerequisite, not a bonus.** Every analysis is only as good as the data feeding it. Dirty CRM data, inconsistent UTM tagging, broken tracking — these don't just create bad reports, they create bad decisions based on bad reports. Data hygiene is an ongoing operational practice, not a quarterly cleanup project.

4. **The right tool for the right question.** GA4 answers "what's happening on our website." GSC answers "how are we appearing in search." HubSpot answers "how are contacts engaging with our marketing." Looker Studio answers "how do we tell the story across all of these." Clarity answers "what are users actually doing on the page." Each tool has a lane. Use the right one.

5. **Dashboards are for monitoring; analysis is for understanding.** A dashboard tells you something changed. Analysis tells you why it changed and what to do about it. Don't confuse the two. Build dashboards for ongoing monitoring, then do actual analysis when the dashboard signals something worth investigating.

---

## CreativeOne Analytics Stack

Each tool in the stack serves a distinct purpose. Understanding what each one does — and what it doesn't — prevents asking the wrong tool the wrong question.

### Google Analytics 4 (GA4)

**What it answers:** How users find, navigate, and convert on CreativeOne's websites. User behavior, traffic sources, engagement patterns, conversion paths.

**Key concepts:**
- **Event-based model.** Everything in GA4 is an event — page views, clicks, scrolls, form submissions, video plays. This replaces UA's session/pageview model with richer behavioral data.
- **Key Events (conversions).** Any event can be marked as a Key Event. These are the actions that matter most to the business — form submissions, resource downloads, event registrations, contact requests. Mark these intentionally; don't track everything as a conversion.
- **Enhanced Measurement.** Auto-tracks page views, scrolls, outbound clicks, site search, video engagement, and file downloads without code. Verify these are enabled and relevant.
- **Explorations.** GA4's power user tool. Funnel analysis, path exploration, segment comparisons, cohort analysis. Use Explorations when standard reports don't answer the question.
- **Audiences.** Group users by behavior (e.g., visited pricing page but didn't convert, engaged with 3+ pages, returned within 7 days). Useful for remarketing and behavioral analysis.
- **Data retention.** Set to 14 months (maximum). Default is 2 months — if this hasn't been changed, historical Exploration data is limited.
- **Reporting identity.** Blended (recommended for most complete view), Observed, or Device-based. This affects how GA4 stitches user journeys across sessions and devices.

**Best practices for CreativeOne:**
- Track Key Events for: form submissions (advisor inquiries, event registrations, resource requests), CTA clicks (schedule a call, learn more, contact us), and resource downloads.
- Use GTM for all custom event tracking. Don't implement tracking directly in website code — GTM provides a management layer that Marketing Ops controls.
- Exclude internal traffic by IP address in Data Stream settings.
- Add payment gateway domains (if applicable) to the referral exclusion list to prevent attribution being stolen by redirect-based payment flows.
- Connect GA4 to Looker Studio for dashboard visualization. GA4's native reporting is functional but limited for stakeholder-facing presentations.

**Common GA4 analysis patterns:**
- **Traffic source performance:** Reports → Acquisition → Traffic acquisition. Filter by Session source/medium. Compare periods.
- **Landing page effectiveness:** Reports → Engagement → Pages and screens. Sort by conversions and engagement rate.
- **Conversion funnel:** Explore → Funnel exploration. Define steps (e.g., landing page → CTA click → form submission → thank you page).
- **Content engagement:** Reports → Engagement → Events. Filter by custom content events. Identify which content types drive the most engagement.
- **User journey:** Explore → Path exploration. Start from a specific page or event. See where users go next and where they drop off.

### Google Search Console (GSC)

**What it answers:** How CreativeOne's websites appear in Google Search. Which queries drive impressions and clicks, which pages rank, technical indexing health, Core Web Vitals.

**Key concepts:**
- **Four core metrics:** Clicks, Impressions, CTR (click-through rate), Average Position. These form the foundation of all search performance analysis.
- **Pre-click vs. post-click:** GSC shows what happens BEFORE someone visits the site (search visibility). GA4 shows what happens AFTER they arrive. They're complementary, not duplicative.
- **Data limitations:** GSC shows up to 1,000 queries. Rare/privacy-protected queries are hidden. Data has a 2-3 day delay. Historical data limited to 16 months.
- **AI-powered configuration (2025).** Natural language prompts can now configure Performance report filters and comparisons — e.g., "show queries where clicks are flat but impressions are rising."

**Best practices for CreativeOne:**
- Monitor weekly for search performance trends. Look for drops in clicks or impressions that might signal indexing issues or algorithm changes.
- Identify "quick win" opportunities: pages ranking positions 4-10 with high impressions but low CTR. These are candidates for title/meta description optimization or content enrichment.
- Watch for keyword cannibalization: two pages splitting impressions across similar queries. Consolidate or differentiate intent.
- Connect GSC to Looker Studio for combined search + site behavior dashboards.
- Cross-reference GSC data with GA4 organic traffic to understand the full search-to-conversion journey.

**Common GSC analysis patterns:**
- **Branded vs. non-branded performance:** Filter queries containing brand name vs. those that don't. Non-branded growth indicates improving organic discoverability.
- **Rising queries with low CTR:** High impressions, low clicks = opportunity to improve search snippets (title tags, meta descriptions).
- **Page-level performance:** Pages tab → sort by impressions or clicks. Identify top-performing content and underperforming pages that should be doing better.
- **Indexing health:** Pages → Page indexing. Monitor "Not indexed" reasons. Fix crawl errors, noindex tags, or redirect issues.
- **Core Web Vitals:** Experience → Core Web Vitals. Mobile and desktop separately. Prioritize fixing "Poor" URLs that affect search rankings.

### HubSpot (CRM & Email Analytics)

**What it answers:** Contact engagement, email campaign performance, lifecycle stage progression, lead scoring, list health, and marketing attribution within the CRM.

**Key concepts:**
- **Contact-centric data.** HubSpot's strength is tying marketing activity back to individual contacts and companies. Unlike GA4 (anonymous sessions), HubSpot knows WHO did WHAT.
- **Lifecycle stages.** Subscriber → Lead → Marketing Qualified Lead → Sales Qualified Lead → Opportunity → Customer → Evangelist. Track how marketing moves contacts through these stages.
- **Attribution reporting.** HubSpot tracks which marketing touchpoints (emails, pages, forms) contributed to conversions. Multi-touch attribution models available on higher tiers.
- **Custom reports.** Build reports combining contact properties, engagement data, deals, and marketing activities. Use the report builder for cross-object analysis.
- **Dashboards.** Create role-specific dashboards — executive summary, email performance, advisor engagement, event marketing.

**Best practices for CreativeOne:**
- Define and enforce property standards. Standardize how contact types, advisor tiers, product interests, and engagement levels are recorded.
- Use HubSpot's built-in duplicate management tool regularly. Duplicates inflate list counts, distort analytics, and cause double-sends.
- Monitor email health metrics: deliverability rate, bounce rate, unsubscribe rate, spam complaint rate. These affect sender reputation.
- Build engagement-based lists (opened last 11 emails vs. never opened) to segment active from unengaged contacts.
- Set up progressive profiling on forms to gather additional data over time without overwhelming contacts upfront.

**Common HubSpot analysis patterns:**
- **Email campaign performance:** Marketing → Email → select campaign. Review open rate, click rate, unsubscribe rate. Compare against historical benchmarks.
- **Contact lifecycle movement:** Reports → Custom report → Contact lifecycle stage changes over time. Identify bottlenecks.
- **List health audit:** Marketing → Email → Health tab. Review deliverability, bounce rate, engagement trends.
- **Source attribution:** Reports → Attribution. Which channels/touchpoints drive the most conversions?
- **Advisor engagement scoring:** Build custom reports using contact properties + activity data to identify most/least engaged advisors.

### Looker Studio

**What it answers:** The unified story across all data sources. Looker Studio is the visualization and reporting layer that combines GA4, GSC, HubSpot, and other data into stakeholder-ready dashboards.

**Key concepts:**
- **Data sources.** Native connectors for GA4, GSC, Google Sheets, BigQuery. Third-party connectors (Supermetrics, etc.) for HubSpot, social platforms, and other tools.
- **Data blending.** Combine metrics from different sources using a common key (e.g., date, page URL, campaign name). Enables cross-platform analysis in a single view.
- **Calculated fields.** Create custom metrics (e.g., conversion rate = conversions / sessions × 100) directly in Looker Studio.
- **Interactive controls.** Date range pickers, dropdown filters, search boxes. Let users explore data without separate reports for every segment.
- **Parameters.** Let users input values that affect calculations — budget targets, goal thresholds, scenario modeling.

**Dashboard design best practices:**
- **Structure for the audience.** Executive dashboards: 5-7 KPIs max, trend lines, goal progress. Manager dashboards: channel-level metrics, campaign comparisons, conversion rates. Specialist dashboards: granular detail, filterable by segment.
- **Visual hierarchy.** Top-level KPIs at the top (scorecards). Supporting trends below (line charts). Detail at the bottom (tables). Users should get the headline in 5 seconds.
- **Chart type selection.** Line charts for trends over time. Bar charts for comparisons between categories. Scorecards for single KPIs. Tables for detailed data. Pie/donut charts sparingly and only for composition (parts of a whole). Avoid 3D charts, dual-axis charts, and anything that requires explanation to read.
- **Consistent design language.** One font family. Consistent color palette (brand colors for positive metrics, muted colors for neutral, red/orange for alerts). Aligned elements. Whitespace between sections.
- **Always include:** Date range, "last updated" timestamp, data source labels, comparison periods (vs. previous period or vs. target).
- **Performance.** Keep dashboards under 25 queries. Use page navigation to split dense dashboards into focused sections. Avoid auto-refresh faster than your data actually updates.

### Microsoft Clarity

**What it answers:** What users actually DO on the page. Heatmaps, scroll maps, session recordings, and behavioral signals that reveal UX issues invisible in aggregate analytics.

**Key concepts:**
- **Heatmaps.** Click heatmaps show where users click (including rage clicks and dead clicks). Scroll heatmaps show how far users scroll.
- **Session recordings.** Watch real user sessions to see navigation patterns, hesitation, confusion, and abandonment.
- **Behavioral signals.** Rage clicks (rapid repeated clicks indicating frustration), dead clicks (clicks on non-interactive elements), excessive scrolling, quick backs (user arrived and immediately returned to search).
- **Smart tags.** AI-powered identification of sessions with notable behaviors — useful for filtering recordings to the most instructive ones.
- **Integration with GA4.** Clarity can be connected to GA4 to see heatmap and recording data alongside analytics.

**Best practices for CreativeOne:**
- Use Clarity for qualitative validation of quantitative findings. If GA4 shows high bounce rate on a landing page, Clarity recordings reveal WHY.
- Review heatmaps on key conversion pages (event registration, contact forms, resource downloads) to verify CTAs are visible and clicked.
- Check scroll depth on long-form content pages. If users aren't reaching the CTA at the bottom, move it higher or add mid-page CTAs.
- Look for rage clicks on navigation elements or buttons that might indicate broken links or confusing UI.
- Clarity is free and privacy-compliant — there's no reason not to have it running on all CreativeOne web properties.

### Google Tag Manager (GTM)

**What it answers:** GTM doesn't answer questions directly — it's the infrastructure layer that enables clean, manageable tracking across GA4 and other platforms.

**Key concepts:**
- **Tags, triggers, variables.** Tags fire data to platforms (GA4 event tag). Triggers define when tags fire (page load, button click, form submission). Variables carry the data (page URL, click text, form field values).
- **Container versioning.** Every publish creates a version. Roll back if a new tag breaks something.
- **Preview mode.** Test tags before publishing. See which tags fire on which events without affecting production data.
- **Debug View.** GA4's companion to GTM preview mode. Confirms events are reaching GA4 with correct parameters.

**Best practices for CreativeOne:**
- ALL custom tracking should go through GTM. No hardcoded analytics scripts on the website.
- Use a naming convention for tags: `[Platform] - [Event Type] - [Description]` (e.g., "GA4 - Event - Form Submission - Contact Us")
- Test every new tag in Preview mode before publishing. Verify in GA4 Debug View.
- Document what each tag tracks and why. Maintain a tag inventory — lost institutional knowledge about what tags do is a real problem.
- Set up trigger groups for complex conditions (e.g., fire only when user is on a specific page AND clicks a specific button AND is not internal traffic).

---

## Data Hygiene Standards

Clean data is the foundation. Without it, every dashboard lies and every analysis misleads.

### HubSpot CRM Hygiene

| Practice | Frequency | Owner |
|---|---|---|
| Duplicate scan and merge | Monthly | Marketing Ops |
| Bounce/unsubscribe list cleanup | Monthly | Marketing Ops |
| Unengaged contact review | Quarterly | Marketing Ops |
| Custom property audit (overlap, unused) | Quarterly | Marketing Ops |
| Contact lifecycle stage accuracy check | Quarterly | Marketing Ops + Sales |
| Data entry standards review | Semi-annually | Marketing Ops |

**Unengaged contact rules of thumb:**
- Never opened a marketing email → flag for review
- Hasn't opened the last 11 emails → likely unengaged
- Previously engaged but hasn't opened the last 16 emails → unengaged

**Property governance:**
- Maintain a property dictionary documenting every custom property: name, type, purpose, who uses it, and where it's referenced in workflows/reports.
- Before creating a new property, check if an existing one already captures the same data. Overlapping properties are a top cause of dirty data.
- Use property validation rules (Settings → Properties → Rules) to enforce data formats at entry.
- Designate a data steward (Marketing Ops Manager or delegate) who approves new properties and audits existing ones.

### UTM Tracking Standards

UTM consistency is the single highest-leverage data hygiene practice for marketing attribution. Inconsistent UTMs fragment your analytics and make it impossible to accurately measure channel performance.

**The five parameters:**
- `utm_source` — WHERE the traffic comes from (platform/sender). Examples: `hubspot`, `facebook`, `linkedin`, `newsletter`, `google`
- `utm_medium` — HOW the traffic arrives (marketing channel type). Examples: `email`, `social`, `cpc`, `referral`, `organic`
- `utm_campaign` — WHICH specific campaign. Examples: `2026-q1-incentive-trip`, `advisor-onboarding-series`, `feb-newsletter`
- `utm_content` — WHAT variation (for A/B testing or differentiating links within the same campaign). Examples: `cta-button`, `header-link`, `image-banner`
- `utm_term` — Search keywords (primarily for paid search). Examples: `life-insurance-quotes`, `annuity-rates`

**CreativeOne UTM naming convention:**

| Rule | Standard | Example |
|---|---|---|
| Case | Always lowercase | `facebook` not `Facebook` |
| Word separator | Hyphens | `incentive-trip` not `incentive_trip` or `incentive trip` |
| Source names | Full platform name, no abbreviations | `facebook` not `fb`, `linkedin` not `li` |
| Medium names | Match GA4 default channel definitions | `email`, `social`, `cpc`, `referral` |
| Campaign names | Format: `yyyy-qq-campaign-name` or `yyyy-mm-campaign-name` | `2026-q1-incentive-trip-maui` |
| No special characters | Avoid `!`, `@`, `#`, `$`, etc. | — |
| No spaces | Hyphens only | — |

**Critical rules:**
- **Never use UTMs on internal links.** UTMs on links within your own website overwrite the original traffic source attribution, creating false sessions and misleading data.
- **Always test UTM-tagged URLs before launch.** Click the link in an incognito browser and verify it loads correctly and the parameters appear in GA4 real-time reporting.
- **Maintain a UTM log.** A shared spreadsheet documenting every UTM-tagged URL created: full URL, each parameter value, campaign purpose, launch date, creator. This is the system of record for campaign tracking.
- **Three parameters minimum.** Every external marketing link should have at least `utm_source`, `utm_medium`, and `utm_campaign`. Missing any of these creates gaps in attribution.

**Channel UTM matrix for CreativeOne:**

| Channel | utm_source | utm_medium |
|---|---|---|
| HubSpot marketing emails | `hubspot` | `email` |
| EngageOne (Snappy Kraken) emails | `engageone` | `email` |
| Facebook organic posts | `facebook` | `social` |
| Facebook paid ads | `facebook` | `cpc` |
| LinkedIn organic posts | `linkedin` | `social` |
| LinkedIn paid ads | `linkedin` | `cpc` |
| Google paid search | `google` | `cpc` |
| Partner referrals | `[partner-name]` | `referral` |
| Direct mail with QR code | `direct-mail` | `offline` |
| Event signage/collateral | `event-collateral` | `offline` |

### GA4 Data Quality

- **Exclude internal traffic.** Configure IP filters in Admin → Data Streams → Configure tag settings → Define internal traffic.
- **Filter out bot/spam traffic.** Enable bot filtering in Admin → Data Streams settings.
- **Verify Enhanced Measurement events.** Admin → Data Streams → Enhanced Measurement. Toggle off events you don't need (reduces noise).
- **Check referral exclusions.** Add payment gateways and any third-party redirect domains to prevent them from stealing attribution.
- **Monitor (not set) and (direct) / (none) traffic.** High percentages of these indicate tracking gaps or missing UTMs. Investigate and fix the source.

---

## KPI Framework for CreativeOne

KPIs should be organized in a hierarchy: strategic outcomes at the top, diagnostic metrics in the middle, operational indicators at the bottom. Each level answers a different question for a different audience.

### Tier 1: Strategic KPIs (Leadership View)

These answer: "Is marketing driving business results?"

| KPI | Definition | Source | Target Setting |
|---|---|---|---|
| Advisor engagement rate | % of active advisors engaging with marketing content (email, events, resources) in a given period | HubSpot + event data | Set baseline, then improve quarter-over-quarter |
| Event attendance rate | Registrations → actual attendees for incentive trips, recruiting events, appreciation events | Registration system + Asana | Historical comparison by event type |
| Marketing qualified leads (MQLs) | New prospects meeting defined criteria for sales follow-up | HubSpot lifecycle stage | Monthly target based on pipeline needs |
| Email program health | Composite: deliverability, open rate trend, unsubscribe rate, engagement rate | HubSpot | Industry benchmarks for financial services email |
| Website conversion rate | Key Event completions / total sessions | GA4 | Baseline + improvement target |

### Tier 2: Diagnostic KPIs (Manager View)

These answer: "Which channels and campaigns are performing, and where are the issues?"

| KPI | Definition | Source |
|---|---|---|
| Traffic by channel | Sessions segmented by organic, email, social, referral, direct, paid | GA4 |
| Email open rate by campaign type | Open rates segmented by newsletter, event promo, nurture sequence, one-off | HubSpot |
| Email click-through rate | Unique clicks / delivered emails | HubSpot |
| Landing page conversion rate | Key Events / page sessions, per landing page | GA4 |
| Search visibility (impressions + position) | Total impressions and average position for target query categories | GSC |
| EngageOne program engagement | Advisor-level engagement with white-labeled nurture content | Snappy Kraken reporting |
| Social engagement rate | (Likes + comments + shares + clicks) / impressions per platform | Native platform analytics |
| Bounce rate by landing page | Single-session visits / total sessions per page | GA4 |

### Tier 3: Operational Metrics (Specialist View)

These answer: "Are the systems running correctly and efficiently?"

| Metric | Definition | Source |
|---|---|---|
| Email deliverability rate | Delivered / sent emails | HubSpot |
| Email bounce rate (hard + soft) | Bounced / sent emails | HubSpot |
| Spam complaint rate | Spam reports / delivered emails | HubSpot |
| Unsubscribe rate | Unsubscribes / delivered emails | HubSpot |
| Crawl errors | Pages with indexing errors | GSC |
| Core Web Vitals scores | LCP, INP, CLS for mobile and desktop | GSC + Clarity |
| Tag firing accuracy | % of tags firing correctly vs. expected | GTM Preview + GA4 Debug |
| Zapier task usage | Tasks consumed vs. plan limit | Zapier dashboard |
| HubSpot contact count | Total contacts vs. plan limit; marketing vs. non-marketing contacts | HubSpot |

### Metrics to Avoid (Vanity Metrics)

These are frequently reported but rarely actionable. Don't build dashboards around them:

- **Raw page views** without engagement context (time on page, scroll depth, conversions)
- **Social media follower count** without engagement rate
- **Total email list size** without segmentation by engagement level
- **Impressions** alone without CTR or conversion context
- **"Leads generated"** without qualification criteria

---

## Reporting Cadence

| Frequency | Report | Audience | Format | Content |
|---|---|---|---|---|
| **Weekly** | Marketing pulse | Marketing team | Slack/email summary | Email sends + performance, active campaigns, website traffic trend, any alerts or issues |
| **Monthly** | Marketing performance report | Leadership + marketing | Looker Studio dashboard + commentary | Full KPI review across all tiers, month-over-month trends, goal progress, key insights and recommendations |
| **Quarterly** | Strategic marketing review | Leadership | Presentation + dashboard | Quarter performance vs. goals, channel ROI, program effectiveness (EngageOne, Local Spark, events), strategic recommendations for next quarter |
| **Post-event** | Event marketing report | Leadership + event team | One-page summary | Registration → attendance conversion, marketing channel contribution, engagement during event, follow-up actions |
| **Post-campaign** | Campaign performance report | Marketing team | Dashboard or document | Campaign-specific KPIs, A/B test results, lessons learned, recommendations |
| **Ad-hoc** | Investigation/analysis | Varies | Document or presentation | Deep-dive into a specific question (e.g., "Why did organic traffic drop 15% in February?") |

### What Good Commentary Looks Like

A dashboard without commentary is just decoration. Every report shared with stakeholders should include:

1. **What happened.** State the facts. "Email open rates dropped from 28% to 22% this month."
2. **Why it happened (hypothesis).** Offer an informed explanation. "This coincides with our shift to more promotional subject lines and a 15% increase in send frequency."
3. **What it means.** Connect to business impact. "Lower engagement may indicate list fatigue in our weekly newsletter segment."
4. **What we're doing about it.** Recommend next steps. "We're testing subject line personalization next month and reducing newsletter frequency from weekly to biweekly for the lowest-engagement segment."

---

## Common Analysis Workflows

### "Why did website traffic change?"

1. **Confirm the change is real.** Check date range. Check for tracking issues (was GTM updated? Did a tag break?). Rule out seasonal patterns.
2. **Identify which channel changed.** GA4 → Acquisition → Traffic acquisition. Compare periods. Is it organic, paid, email, social, direct, or referral?
3. **Drill into the channel.**
   - Organic: Check GSC for impression/click/position changes. Look for algorithm updates. Check for indexing issues.
   - Email: Check HubSpot for recent send volumes and click rates.
   - Social: Check platform analytics for post performance and reach changes.
   - Direct: High direct traffic can mask other channels with missing UTMs. Audit recent campaigns for UTM compliance.
   - Referral: Check for new or lost referral sources.
4. **Check page-level impact.** GA4 → Engagement → Pages and screens. Which pages gained or lost traffic? Is it sitewide or concentrated?
5. **Form a hypothesis and test it.** Cross-reference findings across tools. Validate with Clarity recordings if behavior changed.

### "How did our email campaign perform?"

1. **Pull campaign metrics from HubSpot.** Open rate, click rate, CTR, unsubscribe rate, bounce rate.
2. **Compare to benchmarks.** Compare against your own historical averages AND industry benchmarks for financial services email.
3. **Segment performance.** Break down by list segment, advisor tier, or engagement level. Overall averages hide important variation.
4. **Track post-click behavior in GA4.** Use UTM parameters to filter GA4 traffic to email campaign visitors. What did they do after clicking? Did they convert?
5. **Identify actionable insights.** Which links got the most clicks? Which segments performed best/worst? What can be tested next?

### "Which content is driving results?"

1. **Start with conversions, not traffic.** GA4 → Explore → Free form exploration. Dimension: Page path. Metric: Key Events. Sort by conversions descending.
2. **Layer in engagement.** Add metrics: engagement rate, average engagement time, scroll events. High-converting pages with low engagement may have forms above the fold. High-engagement pages with low conversion may need better CTAs.
3. **Check search performance.** GSC → Pages tab. Which content pages are ranking? What queries bring them traffic?
4. **Review user behavior.** Clarity heatmaps and recordings on top content pages. Are users engaging with the content or just bouncing?
5. **Map content to the advisor journey.** Which content serves awareness (attracting new advisors), consideration (evaluating CreativeOne), and decision (ready to onboard)?

### "Is our SEO improving?"

1. **GSC Performance report.** Compare current period to previous period (28 days vs. previous 28 days, or quarter vs. quarter).
2. **Track four metrics together.** Impressions (visibility), Clicks (traffic), CTR (relevance of snippets), Position (ranking strength). All four together tell the story; any one alone can be misleading.
3. **Segment branded vs. non-branded.** Filter queries containing/not containing brand name. Branded queries measure brand awareness. Non-branded queries measure organic discoverability.
4. **Identify quick wins.** Pages at positions 4-10 with high impressions = content enrichment or internal linking could push them to page 1.
5. **Monitor technical health.** Indexing status, Core Web Vitals, mobile usability. Technical issues can silently erode search performance.

---

## Dashboard Templates for CreativeOne

### Executive Dashboard (Monthly/Quarterly)

**Purpose:** Give leadership a 60-second view of marketing health.

**Components:**
- Scorecard row: 5 strategic KPIs with period-over-period comparison and goal indicators
- Trend line: Website sessions over time (12-month view)
- Channel breakdown: Traffic and conversions by channel (bar chart)
- Email health: Open rate and click rate trends (line chart)
- Event marketing: Upcoming events with registration progress (table)

### Email Performance Dashboard

**Purpose:** Monitor email program health and campaign performance.

**Components:**
- Scorecard row: Deliverability rate, average open rate, average click rate, unsubscribe rate
- Campaign table: Recent campaigns with open/click/unsubscribe per campaign (sortable)
- Trend lines: Open rate and click rate over time (12-month view)
- List health: Active vs. unengaged contacts (pie chart)
- A/B test results: Most recent test results with winner highlighted

### SEO & Search Dashboard

**Purpose:** Track organic search visibility and website health.

**Components:**
- Scorecard row: Total clicks, total impressions, average CTR, average position (vs. previous period)
- Trend lines: Clicks and impressions over time (16-month view)
- Top queries table: Top 20 queries by clicks, with impressions, CTR, position
- Top pages table: Top 20 pages by clicks, with impressions, CTR, position
- Quick wins table: Pages at positions 4-10 with highest impressions
- Core Web Vitals: Mobile and desktop pass rates

### Event Marketing Dashboard

**Purpose:** Track marketing lifecycle for each event from announcement through follow-up.

**Components:**
- Event summary: Name, date, type, registration goal, current registrations (scorecard)
- Registration funnel: Email sent → opened → clicked → registered → attended (funnel chart)
- Channel attribution: Which marketing channels drove registrations (bar chart)
- Registration timeline: Registrations over time since announcement (line chart)
- Engagement: Post-event survey responses, follow-up email engagement (table)

---

## Analysis Output Format

When Claude provides data analysis guidance or frameworks, structure the output as:

```
## Analysis Request: [What question are we answering?]

### Data Sources Needed
- [Tool] → [Specific report/section] → [Metrics]

### Analysis Steps
1. [Step with specific instructions for which tool, which report, which filters]
2. [Next step...]

### What to Look For
- [Specific patterns, thresholds, or comparisons that would indicate an issue or opportunity]

### Recommended Visualizations
- [Chart type] for [what it shows]

### Reporting Recommendation
- [Who should see this, in what format, at what frequency]

### Caveats / Data Quality Notes
- [Any known data quality issues, tracking gaps, or limitations that might affect this analysis]
```

---

## Updating This File

When new tools are added to the stack, analysis patterns are refined, or KPI definitions change:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
3. If a new dashboard template is developed, add it to the Dashboard Templates section.
4. If new UTM standards are established, update the Channel UTM Matrix.
5. If KPI targets are set or revised, update the KPI Framework section.
