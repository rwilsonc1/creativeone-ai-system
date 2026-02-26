# Skill: Zap Troubleshooting

> **Trigger:** Debugging, diagnosing, or fixing a broken, errored, paused, or misbehaving Zapier workflow (Zap).
> **Context required:** Load `skills/zap-building.md` for reference on how CreativeOne Zaps should be structured, named, and documented.
> **Governance rule:** All Zap troubleshooting and fixes are owned by Marketing Ops. Fixes to production Zaps follow the clone-fix-deploy protocol described below.
> **Companion skill:** For building new Zaps from scratch, see `skills/zap-building.md`.

---

## Philosophy: Diagnose Before You Touch

The most expensive troubleshooting mistake isn't failing to find the problem — it's changing something in a live Zap without understanding what broke, and making it worse. Every production Zap is processing real advisor data, real orders, real event registrations. Changing a live Zap without a diagnosis is like performing surgery without an X-ray.

**The troubleshooting mindset:**

1. **Understand the symptom first.** What is happening? What should be happening? When did it start? How many runs are affected? Get the full picture before touching anything.
2. **Read the error, then read it again.** Zapier's error messages and HTTP status codes tell you most of what you need to know — if you actually read them. Don't guess when the answer is in the logs.
3. **Clone before editing.** Zapier has no version control and no staging environment. Editing a Zap turns it off automatically. Clone first, diagnose on the clone, apply the fix to the original, then turn it back on.
4. **Fix the root cause, not the symptom.** Replaying a failed run might clear the error, but if the underlying data issue or logic flaw still exists, it'll fail again tomorrow.
5. **Recover the data.** After fixing the Zap, identify any runs that were missed, errored, or held during the outage and replay them. Data gaps are worse than Zap downtime.

---

## Triage Framework

When a Zap issue is reported or discovered, follow this diagnostic sequence. Don't skip steps.

### Step 1: Identify the Symptom

Classify the problem into one of these categories:

| Symptom | What You're Seeing |
|---|---|
| **Zap not running** | No runs appear in Zap History at all. Trigger events are happening in the source app but the Zap isn't firing. |
| **Zap erroring** | Runs appear in Zap History with "Stopped / Errored" status. Some or all runs are failing. |
| **Zap held** | Runs appear with "Holding" status. The Zap triggered but actions aren't completing. |
| **Zap running slow** | Runs are completing but with significant delays. Data appears in the destination late. |
| **Zap creating bad data** | Runs complete "successfully" but the data in the destination is wrong — duplicates, missing fields, incorrect values, wrong format. |
| **Zap stuck in a loop** | The same trigger fires repeatedly, consuming tasks rapidly. Task usage spikes. |
| **Zap auto-paused** | Zapier turned the Zap off automatically. It needs manual intervention to restart. |

### Step 2: Check the Basics

Before diving deep, eliminate the obvious causes:

- [ ] **Is the Zap turned on?** Open the Zap editor. Check the toggle in the top left. Editing a Zap turns it off automatically — someone may have made an edit and forgotten to turn it back on.
- [ ] **Is the Zapier account in good standing?** Check for task limit warnings, payment issues, or plan restrictions. All Zaps pause when the account hits its task limit.
- [ ] **Is the app connection active?** Go to the Zap editor → trigger/action step → Account tab. Look for "needs reconnect" warnings. OAuth tokens expire, passwords change, API keys get revoked.
- [ ] **Is there a platform outage?** Check [status.zapier.com](https://status.zapier.com) for Zapier-side issues. Check the status page of the connected app (Asana, HubSpot, Fusion, etc.) for their-side issues.
- [ ] **Was the Zap recently edited?** Check Zap History for when the last successful run occurred. If it was working before a recent edit, the edit likely introduced the problem.

### Step 3: Read the Error

Go to Zap History and find the failed run(s):

1. **Filter by status:** Use the status dropdown to show only errored, held, or stopped runs.
2. **Open a failed run.** Click into it to see the full step-by-step execution.
3. **Find the failed step.** Scroll down to find the step with the red "Stopped" icon.
4. **Read the error message.** The error message tells you what went wrong. It usually includes an HTTP status code and a description from the connected app.
5. **Check the Troubleshoot tab.** Zapier's AI-powered troubleshooter will generate step-by-step instructions. These are often helpful for common errors.
6. **Check the Logs tab (HTTP log).** For deeper diagnosis, the HTTP log shows the raw request Zapier sent and the raw response the app returned. This reveals the exact data that was sent and the exact error the app gave back.
7. **Compare input vs. output.** For each step, Zapier shows what data went IN and what came OUT. Comparing these is one of the most powerful debugging techniques — it reveals where data gets lost, transformed incorrectly, or rejected.

### Step 4: Classify the Root Cause

Based on what you found in Steps 1-3, classify into one of these root cause categories:

| Root Cause Category | Indicators |
|---|---|
| **Authentication / Connection** | 401 errors, "needs reconnect" warnings, expired tokens |
| **Data / Field issue** | 400/422 errors, missing required fields, format mismatches, empty values where data expected |
| **Permission issue** | 403 errors, "forbidden" messages, user doesn't have access |
| **Record not found** | 404 errors, search steps returning no results, wrong ID being passed |
| **Rate limiting** | 429 errors, "too many requests," Zap running during high-volume periods |
| **Server / App outage** | 500/502/503 errors, app status page showing issues, errors occurring across multiple Zaps using the same app |
| **Timeout** | 504 errors, large data payloads, complex operations exceeding the timeout window |
| **Logic / Configuration** | Zap running but producing wrong results — Path conditions wrong, Filter too broad/narrow, wrong field mapped, static value instead of dynamic |
| **Account / Plan** | Task limit reached, payment issue, plan doesn't support feature being used |
| **Zap design flaw** | Loop detected, no dedup logic, trigger too broad, missing validation |

### Step 5: Fix and Recover

Follow the fix protocol for the specific root cause (see sections below), then:

1. **Replay failed runs.** After the fix is applied and verified, go to Zap History and replay any errored runs that should have completed. You have 60 days from the original trigger event to replay.
2. **Check for data gaps.** Were any runs missed entirely (trigger didn't fire) vs. errored (trigger fired but action failed)? Missed runs won't appear in Zap History — you'll need to check the source app for records created during the outage window and process them manually or via Zapier Transfer.
3. **Monitor post-fix.** Watch the Zap for 24-48 hours after applying a fix. Confirm errors don't recur.

---

## Clone-Fix-Deploy Protocol

**This is the standard protocol for fixing production Zaps at CreativeOne. Follow it every time.**

```
1. CLONE: Duplicate the broken Zap (My Zaps → dropdown → Duplicate)
2. DIAGNOSE: Open the clone. Review the errored step. Read error messages and HTTP logs.
3. FIX: Make changes to the clone. Test each changed step.
4. VERIFY: Run an end-to-end test on the clone with real or realistic data.
5. APPLY: Go back to the ORIGINAL Zap. Apply the same fix. (Note: editing turns the Zap off.)
6. PUBLISH: Turn the original Zap back on.
7. REPLAY: Go to Zap History. Replay any failed runs from the outage period.
8. CLEAN UP: Turn off (or delete) the clone. Move to DEPRECATED folder if keeping for reference.
9. DOCUMENT: Note what broke, what fixed it, and any preventive measures in the Zap description or CNET documentation.
```

**Why this protocol matters:**
- Editing a Zap turns it off automatically, creating additional downtime
- Zapier has no undo/rollback — if your fix makes things worse, the clone is your safety net
- The clone lets you test without affecting production data
- The replay step ensures no data falls through the cracks

**When to skip cloning (and go direct):**
- The fix is a simple reconnection of an expired app account (Account tab → Reconnect)
- The Zap is already paused/off and the fix is trivially obvious (typo in a field, wrong dropdown selected)
- Time-critical Zaps where minutes of additional downtime are unacceptable — fix directly, but be careful

---

## HTTP Status Code Reference

When a Zap step fails, the error usually includes an HTTP status code. Here's what each means and what to do:

### 4xx Errors (Client-Side — Usually Fixable by You)

| Code | Name | What It Means | Likely Cause in Zapier | Fix |
|---|---|---|---|---|
| **400** | Bad Request | The app couldn't understand what Zapier sent | Missing required field, wrong data type (e.g., text sent to a date field), malformed data, invalid characters | Check field mappings. Verify data types match what the app expects. Use Formatter to fix data before the action step. |
| **401** | Unauthorized | Zapier can't authenticate with the app | Expired OAuth token, changed password, revoked API key, wrong account connected | Reconnect the app account: Zap editor → affected step → Account tab → Reconnect. |
| **403** | Forbidden | Zapier authenticated but doesn't have permission | The connected account lacks permission for this specific action. Common with CRM admin-only operations. | Check the app account's permissions and role. You may need admin-level access. Contact the app's account owner if needed. |
| **404** | Not Found | The record or resource Zapier is looking for doesn't exist | Wrong ID passed, record was deleted, searching wrong environment/object, URL changed | Check that the ID being passed from the trigger/previous step is correct. Verify the record exists in the app. Check if a Search step is returning the wrong result. |
| **409** | Conflict | The record is being modified by something else at the same time | Another user, another Zap, or the app itself is updating the same record concurrently | Add a short Delay before the action step. Check for duplicate Zaps hitting the same record. |
| **415** | Unsupported Media Type | Wrong file format sent | Action expected one file type but received another | Check file handling. Verify the source file type matches what the action accepts. |
| **422** | Unprocessable Entity | Data is in the right format but has an issue | Correct type but invalid value — e.g., email field gets "john@" (missing domain), phone field gets letters, enum field gets a value not in the allowed list | Check the specific field value against the app's requirements. Look for typos, truncation, or unexpected special characters. |
| **429** | Too Many Requests | Zapier is hitting the app's API rate limit | Too many Zap runs firing too quickly, multiple Zaps hitting the same app simultaneously, high-volume looping | Add Delay steps. Reduce concurrency. Stagger Zap trigger times. Check the app's API rate limit documentation. |

### 5xx Errors (Server-Side — Usually Not Your Fault)

| Code | Name | What It Means | What to Do |
|---|---|---|---|
| **500** | Internal Server Error | The app's server failed | Check the app's status page. If there's an outage, wait for it to resolve. If the error is on the trigger, the Zap will catch up on the next successful poll. If on an action, replay failed runs after the outage clears. |
| **502** | Bad Gateway | The app's server received an invalid response from an upstream server | Same as 500. Usually transient. Autoreplay often resolves these automatically. |
| **503** | Service Unavailable | The app's server is temporarily overloaded or in maintenance | Same as 500. Check for scheduled maintenance windows. |
| **504** | Gateway Timeout | The request took too long | Large data payload, complex operation, slow app. Break large operations into smaller batches. Reduce the amount of data being processed per run. |

### Special Zapier Statuses

| Status | What It Means | What to Do |
|---|---|---|
| **Stopped / Errored** | An action step failed with an error | Diagnose using the error message and HTTP code. Fix and replay. |
| **Stopped / Halted** | A Filter or Path stopped the run because conditions weren't met | This is expected behavior — the Filter/Path is working as designed. If runs are being halted that shouldn't be, check your filter/path conditions. |
| **Holding** | The run triggered but actions are paused | Check for: disconnected app, task limit reached, payment issue, flood protection (100+ runs triggered at once), premium app on wrong plan. |
| **Waiting / Scheduled** | The run is in a Delay step or scheduled for Autoreplay | If Autoreplay: wait for the retry. If Delay: normal behavior. |
| **Playing** | The run is currently executing | Normal — it's in progress. If it stays in "Playing" for an unusually long time, the app may be responding slowly. |

---

## Symptom-Based Troubleshooting Guide

### "The Zap isn't triggering at all"

**No runs appear in Zap History. Events are happening in the source app but the Zap doesn't fire.**

Diagnostic path:

1. **Is the Zap on?** Check the toggle. Editing turns it off.
2. **Is the connection active?** Check Account tab on the trigger step. Reconnect if needed.
3. **Is the trigger type correct?** If it's a polling trigger (clock icon), Zapier checks at intervals (1-15 min depending on plan). Be patient and confirm enough time has passed. If it's an instant/webhook trigger (lightning bolt icon), the source app must be configured to send webhooks to Zapier's URL.
4. **Is the trigger pointed at the right data?** Check the Configure tab. Verify the correct workspace, list, sheet, folder, or object is selected. Common mistake: trigger pointed at a test environment instead of production.
5. **Are trigger conditions too restrictive?** If the trigger has filter options, verify they're not excluding the events you expect.
6. **Is this a deduplication issue?** Zapier deduplicates triggers by unique ID. If the trigger item was previously seen (even during testing), it won't fire again. Create a genuinely new record to test.
7. **Did the items exist before the Zap was turned on?** Most triggers only fire for NEW items created AFTER the Zap is activated. They don't retroactively process older data.
8. **Turn it off and back on.** Sometimes forces a connection refresh and re-establishes the trigger.

### "The Zap is erroring on most/all runs"

**Runs appear but most or all have Stopped/Errored status.**

Diagnostic path:

1. **Check the error ratio.** If 95% of runs in the last 7 days are erroring AND the Zap has run 20+ times, Zapier will auto-pause it. (Team plans get 24-hour grace period; Enterprise gets 72 hours.)
2. **Is it the same error every time?** Open 3-5 errored runs. If the same step fails with the same error message, it's a systemic issue (broken connection, wrong field mapping, changed API).
3. **Is it intermittent?** If some runs succeed and others fail, compare the data between succeeding and failing runs. The difference reveals the edge case — usually an empty field, unexpected format, or record-not-found.
4. **When did it start?** Filter Zap History by date. Find the last successful run. What changed between the last success and the first failure? Common causes: app connection expired, someone edited the Zap, the source app changed its API/data structure, a custom field was renamed.
5. **Check the HTTP status code.** Use the reference table above to classify and fix.

### "The Zap is creating duplicate records"

**Runs complete successfully but the destination has duplicate contacts, tasks, or projects.**

Diagnostic path:

1. **Is there a Search step before the Create step?** If not, add one. Always search for existing records before creating new ones.
2. **Is the trigger firing multiple times for the same event?** Check Zap History — are there multiple runs with identical trigger data? Causes: webhook misconfiguration (source app sending the same event twice), trigger set to "New or Updated" when it should be "New" only, Zap loop.
3. **Are multiple Zaps processing the same trigger?** Search your Zap list for other Zaps using the same trigger app and event. Two Zaps with the same trigger both create records = duplicates.
4. **Is there a static test value in a field?** During testing, you might have typed a static value instead of mapping a dynamic field. This creates the same record every run instead of using the trigger data.
5. **Is Autoreplay creating duplicates?** If a step times out (504) but the app actually processed the request before timing out, Autoreplay will retry it — creating a second record. For Zaps prone to timeout duplication, consider disabling Autoreplay and adding custom error handling instead.

### "The Zap ran but data is wrong or missing"

**Records are created/updated but fields are empty, formatted incorrectly, or have the wrong values.**

Diagnostic path:

1. **Compare input vs. output on each step.** In the Zap run detail, check what data went into each step and what came out. Find where the data is correct and where it becomes wrong — that's the problem step.
2. **Are empty fields coming from the trigger?** If the source form/app allows optional fields, those fields arrive as blank in Zapier. If the action step requires them, it may silently accept blank or use a default value you didn't intend.
3. **Is a Formatter step misconfigured?** Check Formatter steps for: wrong From Format on date conversions, wrong Segment Index on Split Text, incorrect Lookup Table mappings, regex patterns that don't match.
4. **Is the wrong field mapped?** In multi-step Zaps, it's easy to map a field from the wrong step. Verify that each mapped field is pulling from the intended step (check the step label in the field mapping dropdown).
5. **Did the source app change its field names or structure?** APIs evolve. If the source app renamed a field or changed its format, Zapier may be receiving different data than expected. Re-test the trigger to see current field names and values.

### "The Zap is running slowly"

**Runs complete but arrive late in the destination system.**

Diagnostic path:

1. **Polling vs. instant trigger?** Polling triggers check at intervals: every 1 minute (Enterprise), 2 minutes (Team), 5 minutes (Professional), 15 minutes (Free). If you need faster, switch to a webhook/instant trigger if available.
2. **Are there Delay steps?** Check for intentional delays in the Zap that might have been set too long.
3. **Is the Zap being throttled?** Zapier throttles Zaps that receive many webhook triggers simultaneously. Check the [Webhooks rate limits documentation](https://help.zapier.com/hc/en-us/articles/8496241726989) for current limits.
4. **Is a Sub-Zap waiting for a return?** If the Zap calls a Sub-Zap that doesn't return promptly (or at all), the parent Zap sits in "Delayed" state.
5. **Is the destination app slow?** If the app's API is responding slowly (visible in HTTP logs as long response times), Zapier must wait. Nothing you can do on the Zapier side except potentially add error handling for timeouts.

### "The Zap was auto-paused by Zapier"

**The Zap was running and is now turned off. You didn't turn it off.**

Diagnostic path:

1. **Check the error ratio.** Zapier auto-pauses Zaps that error 95% of the time over the last 7 days (with 20+ runs). Open Zap History and review the errors.
2. **Was the task limit reached?** If the account hit its monthly task limit, ALL Zaps pause. Check task usage in the dashboard.
3. **Was the app connection revoked?** Some apps revoke Zapier's access after a period of inactivity or when the user changes their password.
4. **Is there a payment issue?** Expired billing information pauses all Zaps.

**To restart:**
- Fix the root cause first (errors, connection, billing)
- Turn the Zap back on
- Replay any missed/errored runs from the outage period
- Monitor for 24-48 hours to confirm stability

**Advanced option:** On Team/Enterprise plans, you can enable "Error ratio override" in the Zap's advanced settings to prevent auto-pause. Use this cautiously and only when you're actively monitoring — it lets a broken Zap keep running (and keep erroring).

### "The Zap is stuck in a loop"

**The same trigger fires over and over. Task usage spikes. The destination fills with duplicate records.**

Diagnostic path:

1. **Is the Zap's action triggering its own trigger?** Classic loop: Trigger is "New Spreadsheet Row" and Action is "Create Spreadsheet Row" in the same sheet. The created row triggers the Zap again, which creates another row, which triggers again... Fix: Use a different trigger, add a Filter to exclude rows created by Zapier (e.g., mark Zapier-created rows with a flag field), or use separate sheets for trigger and action.
2. **Are two Zaps triggering each other?** Zap A creates something that triggers Zap B, which creates something that triggers Zap A. Map the circular dependency and break it with a Filter or by changing the trigger.
3. **Is a Webhook chaining back to itself?** Webhook-based loops can be intentional (for large dataset processing) but must have a termination condition. If the counter/condition is missing or broken, the loop runs forever.

**Emergency stop:** Turn the Zap off immediately. Then diagnose. Check task usage to assess damage.

---

## Connection and Authentication Troubleshooting

Connection issues are the single most common cause of Zap failures. Here's the systematic approach:

### Symptoms
- 401 Unauthorized errors
- "Needs reconnect" warning in the Zap editor
- Zap suddenly stops running with no code changes
- "Authentication credentials were missing or incorrect" error messages

### Common Causes
- **OAuth token expired.** Most OAuth connections last 30-90 days. Some apps (like Google) may revoke tokens more frequently.
- **Password changed.** If the user whose credentials connect the app changed their password, the connection breaks.
- **API key rotated or revoked.** Common when security teams rotate keys on a schedule.
- **Account permissions changed.** The connected user had permissions downgraded or was removed from the team/workspace.
- **Connected to wrong account.** The Zap was built with a test account and never switched to production.
- **App updated its API/authentication method.** The app deprecated the auth method Zapier was using.

### Fix Protocol
1. Go to Zap editor → affected step → Account tab
2. Click "Reconnect" on the existing connection
3. Re-authorize with the correct credentials and permissions
4. Test the step to confirm the connection works
5. If reconnecting doesn't work: disconnect the account entirely, then connect a fresh account
6. Turn the Zap back on
7. Replay any failed runs

### Prevention
- **Monthly connection health check.** Go to [zapier.com/app/connections](https://zapier.com/app/connections) and review all connected accounts. Look for any warnings.
- **Use service accounts where possible.** Don't connect apps using a personal user account that might get deactivated. Use a shared/service account designated for integrations.
- **Set up Zapier Manager alerts.** Create a Zap using Zapier Manager that notifies #mktg-ops-alerts when any Zap encounters a connection error.

---

## Data Issue Troubleshooting

### Empty or Missing Fields

**The trigger sends data but one or more fields arrive empty in the action step.**

Causes:
- The field is optional in the source app and the user didn't fill it in
- The field name changed in the source app (Zapier still maps to the old name)
- The field is on a different object/record that the trigger doesn't include
- The trigger type doesn't include that field (e.g., "New Contact" may not include custom properties — "Updated Contact" might)

Fixes:
- Add a Filter after the trigger: "Only continue if [field] exists"
- Add a Formatter "Default Value" step to provide a fallback for empty fields
- Change to a trigger type that includes the needed fields
- Use a Search step to look up the full record with all fields after the trigger

### Date/Time Format Mismatches

**The most common data transformation error in Zapier.**

The problem: App A sends "10/15/2024" but App B expects "2024-10-15T00:00:00Z". Zapier tries to send it as-is. App B rejects it (400 error) or misinterprets it.

Fixes:
- Add a Formatter → Date/Time → Format step between trigger and action
- Set the "From Format" explicitly — don't rely on Zapier's auto-detection for ambiguous formats (is "01/02/2024" January 2 or February 1?)
- Set the "To Format" to match what the destination app expects
- Set timezones explicitly if the apps are in different zones

Common CreativeOne date patterns:
- Fusion → Asana: May need MM/DD/YYYY to YYYY-MM-DD conversion
- HubSpot → anywhere: HubSpot uses Unix timestamps (milliseconds) for many date properties. Use Formatter to convert.
- Form submissions → anywhere: Form dates arrive as user-typed text. Always format before passing downstream.

### Field Type Mismatches

**Sending the wrong data type to a field.**

Common examples:
- Text sent to a number field (or vice versa)
- A text value sent to a dropdown/enum field that doesn't match any allowed option
- A name sent where an ID is expected (dropdown fields expect IDs, not display names)
- Boolean (true/false) sent as text "true" instead of actual boolean

Fixes:
- For dropdown/ID fields: Use the "Custom" tab in field mapping to pass a dynamic ID from a previous step instead of selecting a static dropdown option
- For number fields: Use Formatter → Numbers → Format Number to strip non-numeric characters
- For boolean fields: Use Formatter → Utilities → Lookup Table to map text values to true/false
- For fields expecting IDs: Add a Search step first to look up the record and get its ID, then pass the ID to the action

---

## Escalation Guide

Not every issue is solvable within Zapier. Here's when and how to escalate:

### Escalate Within the Team
- **To Marketing Ops Manager:** Any Zap that's been down for more than 4 hours, affects advisor-facing processes, or where you've followed the diagnostic path above and can't identify the root cause.
- **Include in your escalation:** Zap name, link to Zap, symptom, error message, HTTP status code, what you've already tried, number of affected runs, and which system/process is impacted.

### Escalate to Zapier Support
- **When:** The error appears to be on Zapier's platform side (not the connected app), Autoreplay isn't working as expected, you see a "Zap has diverged too much" error, or the issue persists after reconnecting and rebuilding the step.
- **How:** Contact Zapier Support via the Help menu. Include: Zap ID, specific run IDs that are failing, screenshots of the error and HTTP logs, and steps you've already taken.

### Escalate to the Connected App's Support
- **When:** 500-series errors that persist beyond a reasonable outage window, 403 errors that aren't resolved by reconnecting, the app's API changed (new fields, deprecated endpoints, changed authentication), or the app's status page confirms a known issue.
- **Include:** The exact error message and HTTP response body from Zapier's logs, the action Zapier was trying to perform, timestamps of the failures.

### Escalate to Zapier Community
- **When:** You've encountered an unusual edge case, need a creative workaround, or want to confirm whether something is a known limitation.
- **Where:** [community.zapier.com](https://community.zapier.com)
- **Best practice:** Search first — most common issues have existing threads with solutions.

---

## Post-Incident Checklist

After resolving any Zap incident that caused downtime or data issues:

- [ ] **Root cause documented.** What actually broke and why?
- [ ] **All failed runs replayed.** Check Zap History for any remaining errored/held runs in the outage window.
- [ ] **Data gaps checked.** Were any trigger events missed entirely (not just errored)? These won't be in Zap History. Check the source app for records created during the outage.
- [ ] **Duplicate data cleaned.** If Autoreplay or manual replays created duplicates in the destination, clean them up.
- [ ] **Preventive measures identified.** What could prevent this from happening again? Add validation, error handling, connection monitoring, or alerts.
- [ ] **Zap description updated.** Add a note about the incident and fix to the Zap's description for future reference.
- [ ] **CNET documentation updated.** For complex Zaps, update the CNET page with lessons learned.
- [ ] **Team notified.** If the outage affected any CSMs, advisors, or downstream processes, notify the relevant people that it's resolved and what (if anything) they need to do.

---

## Quick-Reference Diagnostic Cheat Sheet

**Use this for rapid triage. Match the symptom to the first diagnostic action.**

| What You're Seeing | First Thing to Check |
|---|---|
| Zap not triggering at all | Is the Zap on? Is the connection active? |
| 401 error | Reconnect the app account |
| 400 error | Check field mappings — wrong data type or missing required field |
| 403 error | Check account permissions in the connected app |
| 404 error | Verify the record/resource exists. Check the ID being passed. |
| 422 error | Field value is wrong format — check for typos, invalid characters, or values not in allowed list |
| 429 error | Rate limiting — add Delay steps, reduce concurrency |
| 500/502/503 error | App server issue — check app status page, wait, then replay |
| 504 error | Timeout — reduce payload size, simplify the operation |
| Runs show "Holding" status | Check: task limit, app connection, payment, flood protection |
| Runs show "Scheduled" status | Autoreplay is retrying — wait for it (up to 5 attempts over ~10.5 hours) |
| Zap turned itself off | 95% error rate for 7+ days. Fix root cause, then re-enable. |
| Duplicate records in destination | Add Search step before Create. Check for loop or duplicate Zaps. |
| Empty fields in destination | Check if source field is optional. Add Filter or Default Value. |
| Wrong date format | Add Formatter Date/Time step with explicit From Format and To Format |
| Task usage spiking | Check for loop. Check for Zap firing on unintended trigger events. Place Filters earlier. |
| Dropdown field rejected the value | Pass the record ID (via Custom tab), not the display name |
| "Zap has diverged too much" | Zap was significantly edited after a run errored. Cannot replay that run — must re-process manually. |

---

## Monitoring and Prevention

The best troubleshooting happens before something breaks. CreativeOne's monitoring standards:

### Automated Monitoring (Set Up Once)

| Monitor | How | Alert Destination |
|---|---|---|
| Zap errors | Zapier Manager → trigger on "Zap run errored" → send Slack message | #mktg-ops-alerts |
| Zap turned off | Zapier Manager → trigger on "Zap turned off" → send Slack message | #mktg-ops-alerts |
| Connection expired | Monthly manual check of [zapier.com/app/connections](https://zapier.com/app/connections) | Calendar reminder |
| Task usage approaching limit | Zapier's built-in task usage notifications (email + in-app) | Account owner email |
| High error rate | Weekly review of Zap History filtered by errors | Ops team meeting |

### Manual Review Cadence

| Frequency | What to Check |
|---|---|
| **Daily** (during active incidents) | Zap History for the affected Zap(s). Confirm fix is holding. |
| **Weekly** | Quick scan of Zap History for any new errors across all Zaps. Review task usage trend. |
| **Monthly** | Full connection health check. Review top 10 Zaps by task consumption. Turn off any unused Zaps. Verify all active Zaps are in correct folders with descriptions. |
| **Quarterly** | Audit all Zaps against naming convention and documentation standards. Review DEPRECATED folder for Zaps that can be permanently deleted. Test error handling and alerting by intentionally triggering a test error. |

---

## Updating This File

When new error patterns are encountered, Zapier ships new diagnostic tools, or resolution procedures change:

1. Update the relevant section above.
2. Log the change in `memory/corrections.md`.
3. Add newly discovered error patterns to the Symptom-Based Troubleshooting Guide.
4. If a new common failure mode is identified, add it to the Quick-Reference Diagnostic Cheat Sheet.
5. Update `skills/zap-building.md` if the root cause reveals a design flaw that should be prevented in future Zap builds (add to the Common Failure Patterns table there).
