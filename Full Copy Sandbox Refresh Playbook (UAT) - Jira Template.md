# Jira template — Full Copy refresh

Each refresh is **one User Story with sub-tasks**: seven phase sub-tasks plus one sub-task per integration, created from this template (by cloning a template Story or with a Jira Automation rule). The checklists below are copied from the Playbook tab; when the playbook changes, update this tab and the template Story or automation rule in the same change.

## Ticket structure

| # | Summary | Type | Assignee (role) | Due (relative to Day 0) | Playbook section |
| --- | --- | --- | --- | --- | --- |
| — | Sandbox refresh — \[Sandbox name\] — \[YYYY-MM-DD\] | Story | Refresh Lead | UAT sign-off date | All |
| 1 | Pre-refresh: plan, communicate, back up | Sub-task | Refresh Lead | T-1 | 4 |
| 2 | Export UAT-only users | Sub-task | UAT Coordinator | T-2 | 7 |
| 3 | Execute refresh and activate | Sub-task | Salesforce Admin | Day 0 | 5 |
| 4 | Post-refresh: secure org and re-point endpoints | Sub-task | Admin / Developer | Activation + 1 day | 6 A–C |
| 5 | Recreate UAT-only users and UAT state | Sub-task | UAT Coordinator | After sub-task 4 | 6 D, 7 |
| 6 | Validate managed packages | Sub-task | Package owner | After sub-task 4 | 6 E, 8 |
| 6.x | Reconnect \[Integration\] — **one per integration** | Sub-task | Integration owner | After sub-task 4 | 9 |
| 7 | Validation, sign-off, "ready for UAT" notice | Sub-task | Refresh Lead | UAT open date | 10 |

**Conventions:** label the Story and every sub-task `sandbox-refresh` and `uat-[sandbox name]`; number sub-task summaries (`01 …`, `06.1 …`) so they sort in execution order. Sub-tasks can't have children in Jira, so each integration gets its own sibling sub-task (6.x). Link sub-task 4 as **blocks** 5, 6 and every 6.x, and those as **block** 7, so nobody reconnects an integration before endpoints are re-pointed.

## Story description

```markdown
**Sandbox:** [Sandbox name] (Full Copy, UAT)
**Refresh date (Day 0):** [YYYY-MM-DD]
**Target UAT open date:** [YYYY-MM-DD]
**Refresh Lead:** [Name]   **Backup:** [Name]
**Playbook:** [link to Full Copy Sandbox Refresh Playbook]

**After activation (fill in):**
- New Org ID: [00D…]
- Activation date/time: [ ]
- Production package versions captured: [link/attachment]

**Deviations from playbook:** [none / describe]
```

## Task descriptions

**Sub-task 1 — Pre-refresh: plan, communicate, back up**

```markdown
- [ ] Confirm date with business and release manager; no UAT cycle in flight
- [ ] Confirm 29-day refresh interval has elapsed
- [ ] Send "Refresh announced" notice to testers and all integration owners
- [ ] Announce code freeze from [date/time]
- [ ] Retrieve sandbox-only metadata to Git branch [branch]
- [ ] Export UAT test data sets (SFDMU) to [location]
- [ ] Record Named Credentials, Remote Sites, custom settings/metadata endpoints
- [ ] Record ECA / Connected App keys and callback URLs
- [ ] Note vendor-side sandbox registrations (packages)
- [ ] Confirm SandboxPostCopy class is current in production
- [ ] Decide Auto Activate vs manual activation
- [ ] Go / no-go recorded on the Story
```

**Sub-task 2 — Export UAT-only users**

```markdown
UAT-only users are DELETED by the refresh and cannot be recovered afterwards.
- [ ] Run UAT-only user export query; attach file to this ticket
- [ ] Export PermissionSetAssignment and UserPackageLicense for those users
- [ ] Export Contact/Account keys for Experience Cloud users
- [ ] Record user count: [n]
```

**Sub-task 3 — Execute refresh and activate**

```markdown
- [ ] Click Refresh; record start time
- [ ] Send "Refresh in progress" notice; confirm integrations paused (6.x sub-tasks)
- [ ] Monitor status; log delays here
- [ ] Refresh Lead approves activation; Activate
- [ ] Record new Org ID and activation time on the Story
- [ ] Confirm SandboxPostCopy ran successfully
```

**Sub-task 4 — Post-refresh: secure org and re-point endpoints**

```markdown
A. Secure access
- [ ] Admin login with sandbox username
- [ ] Remove .invalid from refresh-team emails only
- [ ] Review SSO / My Domain settings
- [ ] Freeze users who must not access UAT
B. Block unintended outbound activity
- [ ] Email deliverability = System email only
- [ ] Abort/reschedule scheduled and Apex jobs with callouts
- [ ] Review flows/triggers calling production endpoints
- [ ] Run data masking (if required)
C. Re-point configuration
- [ ] Named / External Credentials to test endpoints
- [ ] Remote Site, CSP Trusted Sites, CORS
- [ ] Custom settings / metadata with endpoints, keys, org IDs
- [ ] ECA / Connected App credentials shared securely with owners
- [ ] Outbound messages, Platform Event / CDC subscribers
- [ ] Experience Cloud URLs and domains
```

**Sub-task 5 — Recreate UAT-only users and UAT state**

```markdown
- [ ] Map Profile / Role / Permission Set by Name (not Id)
- [ ] Load users from sub-task 2 export (suffix convention: [.uat])
- [ ] Assign permission sets, PSGs, package licenses
- [ ] Reload UAT test data (SFDMU)
- [ ] Re-deploy in-flight release metadata from Git
- [ ] Re-authenticate CI/CD against the new sandbox
- [ ] Reconcile: recreated [n] = exported [n]
```

**Sub-task 6 — Validate managed packages**

```markdown
- [ ] Validate each managed package opens without license errors
- [ ] Package versions match production list captured on the Story
- [ ] Re-register sandbox Org ID with vendors where required
- [ ] Re-enable scheduled jobs needed for UAT once all 6.x sub-tasks are done
```

**Sub-task 6.x — Reconnect \[Integration\]** (one per integration) — summary: `06.[n] Reconnect [Integration] to [Sandbox]`, assignee = integration owner from playbook section 9.

```markdown
- [ ] Notified of refresh date (T-10)
- [ ] Integration paused before Day 0
- [ ] Received new Org ID / credentials via secure channel
- [ ] Re-pointed to non-production target
- [ ] Test transaction succeeded: [record Id / log ref]
```

**Sub-task 7 — Validation, sign-off, ready for UAT**

```markdown
- [ ] Admin and sample UAT-only users log in (incl. SSO)
- [ ] Key apps, record pages, Experience sites load
- [ ] No outbound email/callout reached production
- [ ] CI/CD validation deploy succeeds
- [ ] Business-critical process 1: [ ]
- [ ] Business-critical process 2: [ ]
- [ ] Sign-off: Refresh Lead, Admin, UAT Coordinator
- [ ] Send "Ready for UAT" notice
- [ ] Add row to playbook refresh log
```

*Pasting into Jira: if the `- [ ]` lines don't convert to checkboxes, type `[]` followed by a space at the start of a line to create an action item ([Atlassian markdown shortcuts](https://support.atlassian.com/jira-software-cloud/docs/markdown-and-keyboard-shortcuts/)).*
