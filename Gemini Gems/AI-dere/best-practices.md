# ServiceNow Developer Best Practices

## A practical checklist of habits and patterns that keep your apps performant, supportable, upgrade-safe, and secure.

## 1. General Platform Mindset

**Configure first, customize second.** Use OOTB features (tables, UI policies, Flow Designer actions, ACLs, app frameworks) before writing code.
**Design for upgrades.** Avoid modifying core records directly. Prefer extension points (script includes, UI actions, Business Rules with conditions, scoped apps).
**Keep it simple.** Small, composable scripts beat monoliths. If a requirement feels complex, re-evaluate the data model or process first.
**Document intent.** Explain _why_ a pattern exists, not just _what_ it does.

---

## 2. Data Modeling & Table Design

**Start with the schema.** Good table design reduces most scripting.
**Prefer references over strings.** Reference fields enable integrity, dot-walking, reporting, and indexing.
**Don’t over-extend core tables.** Extending is fine, but avoid hijacking core behavior. If in doubt, create a new table in your scope.
**Index intentionally.**
Index fields used in high-volume filters, joins, or reports.
Revisit indexes when performance issues appear.
**Use dictionary overrides carefully.** Overrides are powerful but easy to forget during upgrades.

---

## 3. Server-Side Scripting (Script Includes, Business Rules, Fix Scripts)

### 3.1 Style & Structure

**Test First in Background Scripts** Concepts should be tested first in a background script before creating script includes or other types of integrations
**Use Script Includes for reusable logic.** Avoid duplicating code in BRs, Flows, or UI actions.
**Follow ES5 compatibility unless proven otherwise.** Many server contexts still expect ES5.
**Encapsulate utilities.** Create “Utils” Script Includes (e.g., `MyAppUtils`) for common tasks.
**Minimize global scope usage.** Keep everything scoped; avoid `global` unless required.

### 3.2 Business Rules

**Use the right type:**
_Before_ BRs for validation / setting values.
_After_ BRs for side effects / triggers.
_Async_ BRs for non-blocking work.
**Guard with tight conditions.** Ensure BRs don’t run unnecessarily.
**Avoid heavy work in synchronous BRs.** Move long operations to async BRs, scheduled jobs, or Flow Designer.

### 3.3 GlideRecord Best Practices

**Query narrowly.**
Add `addQuery` / `addEncodedQuery` early.
Use `setLimit()` whenever possible.
**Use `get()` when you expect one record.**
**Avoid nested queries in loops.** Batch or prefetch instead.
**Prefer `GlideAggregate` for counting/summing.**
**Use `GlideDateTime` for date comparisons.** Avoid string compares for dates/times.
**Check for nulls and types.** Don’t assume fields exist or contain valid data.

---

## 4. Performance & Scale

**Assume “large data” is coming.** Write like your table will get millions of rows.
**Batch long operations.**
Split big arrays into chunks.
Use background scripts / Scheduled Jobs / Flow subflows.
**Use caching where safe.**
Example: `GlideCache` or scoped equivalents for frequently used lookups.
**Avoid synchronous external calls.**
Prefer IntegrationHub actions or async REST patterns.
**Measure before optimizing.**
Use Script Debugger, transaction logs, and timing via `gs.info()`.

---

## 5. Security

**Never trust client input.** Re-validate server-side.
**Use ACLs, not UI conditions, for real security.**
**Least privilege.**
Create specific roles for your app.
Don’t depend on `admin` unless unavoidable.
**Sanitize data for HTML.** Escape user content before rendering in UI/notifications.
**Protect secrets.**
Use **Credential Records** or **Encrypted fields**, not plain text properties.
**Validate integration payloads.**
Confirm required keys + types.
Reject or log unexpected structures.

---

## 6. Client-Side Scripting (Catalog Client Scripts, UI Scripts)

**Keep the client light.** UI behavior only; business logic belongs server-side.
**Use `g_form` responsibly.** Avoid heavy loops over huge field sets.
**Throttle expensive operations.**
Debounce onChange calls that fetch data.
**Use GlideAjax for server data**, and:
Return small payloads.
Handle errors/timeouts.
Avoid huge JSON blobs that can crash modals.

---

## 7. Flow Designer & Automation

**Prefer Flow Designer for orchestration; Script Includes for business logic.**
**Use subflows for reuse.** Keep flows small and readable.
**Name inputs/outputs clearly.** Avoid “var1/var2.”
**Guard triggers.** Make conditions tight to reduce noisy executions.
**Be explicit in stage/state setting**, especially on catalog items, tasks, and custom process tables.

---

## 8. Updates, Source Control, and Deployment

**Use scoped apps.** Keep customizations in your application scope.
**Keep Update Sets clean.**
One logical feature per update set.
Don’t mix unrelated changes.
**Commit early, commit often (Source Control).**
Use branches for features.
Use PRs for review where possible.
**Never develop directly in prod.**
Dev → Test → UAT → Prod with promotion gates.
**Verify collisions and conflicts.**
Resolve before promotions and commits.

---

## 9. Testing & Debugging

**Create test data templates.** Repeatable input reduces guesswork.
**Use ATF for critical paths.**
Catalog workflows
ACL protections
UI actions
Integrations (mock endpoints)
**Log intentionally.**
Use structured `gs.info()` with prefixes.
Remove noisy logging before release.
**Reproduce in sub-prod.** Don’t debug in prod unless it’s a controlled emergency.

---

## 10. UI / UX Practices

**Use UI Policies for simple form logic**, not scripts.
**Avoid DOM hacking where possible.**
**Keep list/form layouts consistent.**
**Make defaults safe.** Prevent accidental destructive actions.

---

## 11. Integrations

**Define contracts up front.**
Use JSON schemas or OpenAPI specs for payloads.
**Idempotency matters.**
External systems retry; your API should not double-create.
**Handle partial failures.**
Log the reason.
Store “last successful sync” timestamps.
**Normalize inbound data.**
Map/validate in a Script Include or Transform Map.
**Prefer event-driven patterns** for high volume (Events, queues, Kafka, etc.).

---

## 12. Documentation & Maintainability

**JSDoc your Script Includes.**
Document params, return types, and examples.
**Comment decisions, not trivia.**
Explain _why_ something is async, cached, or conditional.
**Create README pages per app.**
Purpose, tables, roles, flows, integrations, deployment notes.
**Use consistent naming.**
`MyAppThingUtils`, `MyAppConstants`, `MyApp_<feature>`.

---

## 13. Validation & Troubleshooting Before Making Changes

ServiceNow is highly interconnected. A “small” change can ripple into ACLs, flows, integrations, notifications, reporting, SLAs, and upgrades. Before introducing new scripts, flows, data fixes, or record updates, validate your assumptions and troubleshoot the root cause.

### 13.1 Validate the Problem _Before_ You Solve It

**Reproduce first.** Never fix something you can’t reliably reproduce.
**Confirm scope and impact.**
Who is affected?
How often?
Which tables, roles, and processes are involved?
**Check if it’s already OOTB behavior.**
Look for existing properties, plugins, UI policies, or flows that already solve it.
**Verify data is actually wrong.**
Many “bugs” are mis-modeled fields, bad references, or stale integration mappings.

### 13.2 Troubleshoot Systematically

**Start from the surface, then go deep:**
UI behavior (UI Policies, Client Scripts, UI Actions)
Server logic (Business Rules, Script Includes)
Automation (Flows/Subflows, Scheduled Jobs)
Security (ACLs, roles)
Data model (dictionary, references, indexes)
Integrations (Transform Maps, REST, MID, ECC Queue)
**Use built-in debugging tools:**
Script Debugger
Flow “Executions” & “Context” records
System Logs (`gs.info`, `gs.warn`, `gs.error`)
Transaction / slow query logs
Integration error tables / ECC Queue
**Look for _why_ it happened, not just _where_.**
If a field is blank, identify who/what last touched it and why.

### 13.3 Validate Logic With Safe Tests

**Test in isolation.**
Run Script Include methods in Background Scripts first.
Use small representative datasets.
**Use “dry-run” flags for data fixes.**
Log intended updates without committing, then flip to commit mode.
**Confirm edge cases explicitly:**
Null values
Missing references
Timezone/date boundaries
Duplicate records
Race conditions / concurrent updates

### 13.4 Check Existing Automation and Side Effects

Before changing a record or field value, check:
**Business Rules** on insert/update/delete
**Flows/Subflows** triggered by changes
**Notifications** and **Events**
**SLAs** or **Schedules**
**Integrations** that treat changes as signals
**Reporting/PA indicators** relying on those fields
Rule of thumb:
If you don’t know what will fire, you’re not ready to change it.

### 13.5 Validate Security Implications

**Confirm ACL behavior before assuming a bug.**
**Test with a real end-user role**, not admin.
**Check field-level ACLs** if values appear blank only for some users.

### 13.6 Don’t Patch Symptoms With Code

If the issue is **bad data**, fix the integration or transform.
If the issue is **schema mismatch**, change the table/fields.
If the issue is **OOTB config**, adjust config first.
**Add scripts last**, only when config can’t solve it cleanly.

### 13.7 Record Change Best Practices (Manual or Scripted)

**Prefer non-destructive updates.**
Set new fields instead of overwriting originals when possible.
**Keep a rollback path.**
Snapshot affected sys_ids.
Export before mass changes.
Log old values in fix scripts.
**Use batched updates for large volumes.**
`setLimit()`, pagination, or job chunking.
**Avoid updating records “just because.”**
Every update triggers audits, BRs, flows, and sometimes integrations.

### 13.8 Pre-Change Checklist (“Pause Before You Push”)

[ ] I can reproduce the problem.
[ ] I verified it’s not a role/ACL/UI-policy issue.
[ ] I checked existing BRs/Flows/Notifications on the table.
[ ] I tested logic safely with small data or dry-run mode.
[ ] I identified edge cases and validated expected behavior.
[ ] I know what will trigger from my change.
[ ] I have a rollback plan if needed.
[ ] I’m fixing the root cause, not just a symptom.

---

## 14. Final “Before You Ship” Checklist

[ ] No core record edits without override/extension.
[ ] All BRs/Flows have tight conditions.
[ ] No heavy work in synchronous contexts.
[ ] Queries are indexed or limited.
[ ] ACLs cover all sensitive tables/fields.
[ ] Secrets stored safely.
[ ] Root cause confirmed with evidence.
[ ] Fix tested via dry-run or isolated script tests.
[ ] Side effects (BRs/flows/ACLs/integrations) reviewed.
[ ] Rollback/export plan ready for any data updates.
[ ] ATF or repeatable test plan exists.
[ ] Update set or git commit is focused and clean.
[ ] README / inline docs updated.
[ ] Tested upgrade-safe (no hard dependencies on internal/private APIs).
