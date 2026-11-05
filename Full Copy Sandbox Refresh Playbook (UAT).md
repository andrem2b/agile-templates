# Full Copy Sandbox Refresh Playbook (UAT)

Nov 5, 2026 · @Andrea

## 1. Purpose and scope

This playbook is the single checklist the team follows to take the **\[Sandbox name\]** Full Copy sandbox from "refresh requested" back to a working UAT environment. Execute the steps in the order listed; do not open the sandbox to UAT testers until section 10 sign-off is complete.

| Item | Value |
| --- | --- |
| Production org | \[Org name\] — Org ID \[00D…\] |
| Sandbox name / type | \[e.g. UAT\] — Full Copy |
| Sandbox purpose | UAT environment for business testing before production releases |
| Sandbox template | \[Template name, or "none — all objects"\] |
| Refresh interval | Full Copy can be refreshed once every 29 days |
| Playbook owner | \[Name / role\] |
| Last refresh executed | \[Date\] by \[Name\] |

**In scope:** pre-refresh preparation, the refresh itself, post-refresh configuration, integration re-pointing, UAT-only user recreation, validation and sign-off.

**Out of scope:** Partial/Developer sandbox refreshes, production deployments, and release-specific test plans (link them from section 10 instead).

**How to use this document:** duplicate it per refresh (or keep a dated copy), tick the checkboxes as you go, and record the executor and timestamp next to each completed step. Any deviation goes in the refresh log in section 11.

**Executing a refresh:** open a Jira Story with sub-tasks from the template in Jira template; this playbook stays the reference, Jira tracks the run.

## 2. Roles and responsibilities

One person is the **Refresh Lead** and owns the go/no-go call at each phase; everyone else executes the steps assigned to their role. Fill names before every refresh — people change between cycles.

| Role | Responsibilities | Name | Backup |
| --- | --- | --- | --- |
| Refresh Lead | Schedules the refresh, runs this checklist, sends all communications, signs off | \[Name\] | \[Name\] |
| Salesforce Admin | Activation, email deliverability, users, permission sets, scheduled jobs, org settings | \[Name\] | \[Name\] |
| Salesforce Developer / DevOps | Named Credentials, External Client Apps / Connected Apps, custom settings & metadata endpoints, CI/CD auth | \[Name\] | \[Name\] |
| Integration owners | Re-point their system to the refreshed sandbox and confirm connectivity (see section 9) | See section 9 | — |
| Package / AppExchange owner | Validates managed packages and vendor-side sandbox registrations (see section 8) | \[Name\] | \[Name\] |
| UAT Coordinator | Recreates UAT-only users, notifies testers, confirms UAT readiness | \[Name\] | \[Name\] |
| Security / Data Privacy | Approves data masking scope and access for non-employees | \[Name\] | \[Name\] |

*Tip: production data lands in the sandbox. If the sandbox is accessed by people who should not see production PII, Data Mask (or an equivalent) must run before access is opened — the Security role approves this.*

## 3. Timeline: before, during, after

The refresh runs in three phases separated by three gates; testers get access only after the last one. Dates are relative to refresh day (Day 0); fill in actual dates for each cycle.

&#91;embedded content: refresh timeline · 3 phases, 3 gates\]

| Milestone | Planned date | Actual date | Owner |
| --- | --- | --- | --- |
| Refresh announced (T-10) | \[ \] | \[ \] | Refresh Lead |
| UAT-only state backed up (T-2) | \[ \] | \[ \] | Admin / UAT Coordinator |
| Go / no-go (T-1) | \[ \] | \[ \] | Refresh Lead |
| Refresh started (Day 0) | \[ \] | \[ \] | Admin |
| Activated | \[ \] | \[ \] | Refresh Lead |
| Integrations reconnected | \[ \] | \[ \] | Integration owners |
| UAT sign-off | \[ \] | \[ \] | Refresh Lead |

## 4. Pre-refresh checklist (T-10 to T-1 business days)

Everything that exists only in the sandbox is lost on refresh, so this phase is about **backing up UAT-only state and warning everyone who depends on the sandbox**. Nothing here is optional.

**Plan and communicate**

- [ ] Confirm the refresh date with the business and release manager; check no UAT cycle or release is in flight.
- [ ] Confirm the 29-day Full Copy refresh interval has elapsed and the sandbox license is available.
- [ ] Send the "Refresh announced" notice (template in section 10) to UAT testers and every integration contact in section 9.
- [ ] Agree a code freeze: no deployments to the sandbox from \[date/time\] until the refresh completes.

**Back up UAT-only state**

- [ ] Export UAT-only users (see section 7) and store the export in \[location\].
- [ ] Retrieve any sandbox-only metadata not yet in source control (`sf project retrieve start`) and commit it to a branch — anything not in Git or production is lost.
- [ ] Export UAT test data sets that must be reloaded (e.g. SFDMU export) to \[location\].
- [ ] Record current sandbox-specific values: Named Credential / External Credential endpoints, Remote Site Settings, custom metadata and custom settings holding URLs, keys or org IDs.
- [ ] Record External Client App / Connected App consumer keys and callback URLs used by integrations against this sandbox.
- [ ] Note vendor-side sandbox registrations for managed packages that require them (section 8).

**Prepare the refresh**

- [ ] Decide whether to use **Auto Activate** or manual activation (manual gives a window to prepare before the old copy is replaced).
- [ ] Confirm the `SandboxPostCopy` Apex class (if used) is deployed in **production** and up to date — it runs from the production code base.
- [ ] Confirm sandbox template / object selection and history settings.
- [ ] Go / no-go by Refresh Lead.

## 5. During-refresh checklist (Day 0 until activation)

A Full Copy refresh can take from several hours to several days depending on data volume; the sandbox stays usable until activation, so **treat it as read-only from the moment refresh starts**.

- [ ] Click **Refresh** in Setup > Sandboxes; record start time and the requesting user.
- [ ] Send the "Refresh in progress" notice (section 10) — testers stop work, integrations stop writing to the sandbox.
- [ ] Integration owners pause or disable jobs that target the sandbox (middleware schedules, inbound webhooks, ETL) per section 9.
- [ ] Monitor status in Setup > Sandboxes; log any delay.
- [ ] When status is **Ready to activate** (manual activation): confirm with the Refresh Lead, then **Activate**. Activation deletes the old copy and its data permanently.
- [ ] Record activation time and the new sandbox Org ID (it changes on every refresh).
- [ ] Confirm `SandboxPostCopy` ran successfully (check Apex Jobs / debug logs or the email notification).

## 6. Post-refresh checklist (in execution order)

Run the steps **top to bottom**: each step group depends on the previous one, and integrations are re-enabled only after the org is safe (step C). Steps marked *automatable* are candidates for the `SandboxPostCopy` class or a post-refresh script.

**A. Secure access (first hour)**

- [ ] Log in with the admin's sandbox username (`user@domain.com.[sandboxname]`).
- [ ] Fix email addresses for the refresh team: user emails are copied with `.invalid` appended; remove it only for users who need sandbox emails. *Automatable*
- [ ] Review SSO / My Domain settings for the sandbox (SAML entity ID and IdP config may need sandbox-specific values).
- [ ] Freeze or deactivate production users who must not access UAT, per policy.

**B. Protect against unintended outbound activity**

- [ ] Confirm **Email Deliverability** is "System email only"; switch to "All email" only after step C and only if UAT requires it.
- [ ] Review Setup > Scheduled Jobs and Apex Jobs; abort or reschedule jobs that would call external systems.
- [ ] Review active Flows / triggers with callouts or outbound messages pointing to production endpoints.
- [ ] Run data masking (Data Mask or equivalent) if non-employees will access the sandbox.

**C. Re-point configuration to non-production endpoints**

- [ ] Update Named Credentials / External Credentials to sandbox or test endpoints (values recorded in section 4). *Automatable*
- [ ] Update Remote Site Settings, CSP Trusted Sites, and CORS entries.
- [ ] Update custom settings / custom metadata holding endpoints, API keys or org IDs. *Automatable*
- [ ] Re-issue or re-confirm External Client App / Connected App credentials and callback URLs; share new consumer keys with integration owners securely.
- [ ] Update Outbound Message endpoints and Platform Event / CDC subscriber configuration.
- [ ] Update Experience Cloud site URLs and custom domains, if used.

**D. Restore UAT-specific state**

- [ ] Recreate UAT-only users (section 7).
- [ ] Assign UAT-only permission sets, permission set groups and package licenses (section 8).
- [ ] Reload UAT test data sets (e.g. SFDMU import).
- [ ] Re-deploy sandbox-only metadata still in flight for the current release (from the Git branch).
- [ ] Re-authenticate CI/CD (e.g. GitHub Actions / DevOps Center) against the new sandbox.

**E. Reconnect integrations and packages**

- [ ] Validate managed packages and vendor-side registrations (section 8).
- [ ] Notify each integration owner in section 9 that the sandbox is ready; they reconnect and confirm a test transaction.
- [ ] Re-enable scheduled jobs needed for UAT.

**F. Validate and hand over**

- [ ] Execute smoke tests and sign-off (section 10).
- [ ] Send the "Sandbox ready for UAT" notice.

## 7. UAT-only users: export and recreate

> **Important:** a refresh replaces the sandbox with a copy of production. **Users that exist only in this UAT sandbox are deleted by the refresh and are not recoverable afterwards.** They must be exported *before* the refresh (section 4) and recreated *after* it (section 6, step D).

**Who counts as a UAT-only user:** \[e.g. external testers, vendor consultants, test personas, integration test users, Experience Cloud test community users\]. Maintain the current list in \[location / link\].

**Export (before refresh)**

1. Run the export query / report: `SELECT Username, FirstName, LastName, Email, Alias, ProfileId, Profile.Name, UserRoleId, UserRole.Name, FederationIdentifier, TimeZoneSidKey, LocaleSidKey, LanguageLocaleKey, EmailEncodingKey, IsActive FROM User WHERE [criteria identifying UAT-only users]`
2. Export their permission set, permission set group and package license assignments (`PermissionSetAssignment`, `UserPackageLicense`).
3. For Experience Cloud users, export the related Contact / Account keys.
4. Store the files in \[location\]; record row counts here: \[n users\].

**Recreate (after refresh)**

1. Map Profile, Role and Permission Set names to the new IDs (IDs can differ; always join on **Name / DeveloperName**, never on Id).
2. Load users with \[Data Loader / SFDMU / script name\]; usernames must stay globally unique — keep the agreed suffix convention (\[e.g. `.uat`\]).
3. Assign permission sets, permission set groups and package licenses.
4. Trigger password reset / welcome emails only after email deliverability is set appropriately.
5. Reconcile: recreated count = exported count; log exceptions.

**Owner:** \[UAT Coordinator\]. **Known limitations:** \[e.g. record ownership of UAT test data, licence availability — sandbox license counts mirror production\].

## 8. What is available after the refresh

After activation the sandbox is a **point-in-time copy of production**: metadata, data, managed packages and licensing all match production as of the refresh start. Anything that was newer or different in UAT is gone and must be re-applied.

**What you get vs. what you lose**

| Area | State after refresh | Action needed |
| --- | --- | --- |
| Metadata & code | Matches production | Re-deploy in-flight release work from Git |
| Data | Full copy of production (per template) | Mask if required; reload UAT test sets |
| Managed packages | **Same packages and versions as production** | Re-install any newer version being UAT-tested |
| Licensing (user, feature, package) | **Matches production**; if out of sync use Setup > Company Information > *Match Production Licenses* | Re-assign package licenses to recreated UAT-only users |
| Users | Production users only, emails suffixed `.invalid` | Recreate UAT-only users (section 7) |
| Org ID / instance | **New Org ID**, possibly new instance | Update anything keyed on Org ID (vendor registrations, integrations) |
| Credentials & endpoints | Copied from production (point to production!) | Re-point in section 6, step C |

**Managed package inventory**

For each package, state the production version so testers know exactly what they are testing against, and whether the vendor needs a sandbox-side action.

| Package (namespace) | Production version | Licensing model | Post-refresh action | Vendor / owner contact |
| --- | --- | --- | --- | --- |
| \[Package name\] (\[ns\]) | \[x.y\] | \[Site-wide / per-user\] | \[e.g. none / re-register sandbox Org ID / re-enter API key\] | \[Name, email\] |
| \[Package name\] (\[ns\]) | \[x.y\] | \[ \] | \[ \] | \[ \] |
| \[Package name\] (\[ns\]) | \[x.y\] | \[ \] | \[ \] | \[ \] |

*Tip: pull the current list from Setup > Installed Packages in production on the refresh day (or `sf package installed list --target-org prod`) and paste the versions here, so the table is an exact record of what the refresh delivered.*

## 9. Integrations inventory and contacts

Every system that reads from or writes to this sandbox is listed here with a named owner who is **notified before the refresh and again when the sandbox is ready**. After refresh, all credentials and endpoints are production copies, so no integration is re-enabled until its owner confirms it points at a non-production target.

| Integration | Direction | Mechanism / auth | Salesforce config to update | Owner team | Contact (name, email, channel) | Status |
| --- | --- | --- | --- | --- | --- | --- |
| \[e.g. HubSpot\] | \[Bi-directional\] | \[Managed package / OAuth\] | \[Package settings, connected user\] | \[Marketing Ops\] | \[Name, email, #channel\] | Not notified |
| \[e.g. Workato recipes\] | \[Inbound / outbound\] | \[External Client App, JWT\] | \[ECA, Named Credential\] | \[Integration team\] | \[Name, email\] | Not notified |
| \[e.g. ERP / Billing\] | \[Inbound\] | \[REST API, integration user\] | \[Integration user, permission set\] | \[Finance IT\] | \[Name, email\] | Not notified |
| \[e.g. E-signature\] | \[Outbound\] | \[Managed package\] | \[Package API key, callback URL\] | \[Vendor / Sales Ops\] | \[Name, email\] | Not notified |
| \[Integration\] | \[ \] | \[ \] | \[ \] | \[ \] | \[ \] | Not notified |

**Per-integration post-refresh steps** (one line each, kept with the owner):

- &#91;Integration\]: \[e.g. regenerate certificate / re-authorize connected user / update sandbox Org ID in middleware connection\]
- &#91;Integration\]: \[ \]

*Update the Status column through the refresh: Notified (section 4) → Paused (section 5) → Reconnected → Verified (section 6, step E).*

## 10. Validation, sign-off and communications

The sandbox is handed to UAT only when every smoke test below passes and the Refresh Lead signs off.

**Smoke tests**

- [ ] Admin and a sample of UAT-only users can log in (including SSO, if used).
- [ ] Key record pages, Lightning apps and Experience Cloud sites load.
- [ ] Each managed package opens without license errors (section 8).
- [ ] Each integration completes one test transaction against a **non-production** target (section 9).
- [ ] No outbound email or callout reached a production recipient or system (check email logs / integration logs).
- [ ] CI/CD pipeline can validate a deployment against the sandbox.
- [ ] &#91;Business-critical process 1, e.g. create opportunity → quote → e-signature\]
- [ ] &#91;Business-critical process 2\]

**Sign-off**

| Role | Name | Date | Notes |
| --- | --- | --- | --- |
| Refresh Lead | \[ \] | \[ \] | \[ \] |
| Salesforce Admin | \[ \] | \[ \] | \[ \] |
| UAT Coordinator | \[ \] | \[ \] | \[ \] |

**Communication templates**

1. **Refresh announced (T-10)** — *Subject: \[Sandbox\] Full Copy refresh on \[date\].* The UAT sandbox will be refreshed from production on \[date/time\]. All sandbox-only data, users and configuration will be lost. Please export anything you need by \[date\] and pause integrations at \[time\]. Contact: \[Refresh Lead\].
2. **Refresh in progress (Day 0)** — *Subject: \[Sandbox\] refresh started — do not use.* The refresh has started. Stop testing and keep integrations paused until you receive the "ready" notice.
3. **Ready for integration reconnection** — *Subject: \[Sandbox\] ready for integration setup.* New Org ID: \[00D…\]. Please reconnect \[integration\] using \[credentials shared via secure channel\] and confirm a test transaction by \[time\].
4. **Ready for UAT** — *Subject: \[Sandbox\] available for UAT.* The sandbox now matches production as of \[date\] (packages and licensing included). UAT-only users have been recreated; reset your password via \[link\]. Known issues: \[list\].

## 11. Refresh log and references

**Refresh log** (newest first)

| Refresh date | Executed by | New Org ID | Duration | Deviations / issues |
| --- | --- | --- | --- | --- |
| \[YYYY-MM-DD\] | \[Name\] | \[00D…\] | \[hh\] | \[ \] |

**Salesforce references**

- [Sandbox Setup Considerations](https://help.salesforce.com/s/articleView?language=en_US&id=sf.data_sandbox_implementation_tips.htm&type=5)
- [Create, Refresh and Delete Sandboxes — considerations](https://help.salesforce.com/s/articleView?language=en_US&id=data_sandbox_create_refresh_delete.htm&type=0)
- [User email addresses appended with ".invalid" after refresh](https://help.salesforce.com/s/articleView?id=000386507&language=en_US&type=1)
- [Summer '26: changes to email verification and password reset after sandbox refresh](https://help.salesforce.com/s/articleView?id=005390303&language=en_US&type=1)
- [SSO SAML settings behavior during sandbox refresh](https://help.salesforce.com/s/articleView?id=000385851&language=en_US&type=1)
- [Sandbox licenses and storage limits by type](https://help.salesforce.com/s/articleView?language=en_US&id=sf.data_sandbox_environments.htm&type=5)
- [Licenses or features missing in sandbox (Match Production Licenses)](https://help.salesforce.com/s/articleView?id=000386961&language=en_US&type=1)
- [SandboxPostCopy interface — Apex Reference](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_interface_System_SandboxPostCopy.htm)

**Internal references:** \[link to UAT-only user list\] · \[link to integration runbooks\] · \[link to SFDMU seed data config\] · \[link to Git repo / branch strategy\]
