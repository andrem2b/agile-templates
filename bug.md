# Ticket Type: Bug

## Relation to other tickets:

- Bugs can stand alone or be linked to User Stories, Tasks, or Epics.
- Bugs should be linked to the original User Story/Task if the bug was introduced during recent development work.
- Critical bugs may block User Stories or Epics from being completed.

## Purpose:

- Represents an issue, defect, or problem in the existing code or feature.
- Documents unexpected behavior that deviates from requirements or expected functionality.
- Tracks the resolution of problems discovered during development, testing, or production use.

## Roles & Accountability (RACI):

| Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-----------|----------|
| Development Team | Team Lead | Solution Architect | Project Manager<br>Product Owner<br>Business Analyst |

**Definitions:**
- **Responsible**: Investigates and fixes the bug
- **Accountable**: Ensures the bug is resolved and verified
- **Consulted**: Provides technical guidance on complex issues
- **Informed**: Kept up-to-date on critical bugs and resolution status

## Mandatory Content:

- **Descriptive title** following the format: `[Component/Feature] - [Brief Description]`
  - Example: "Opportunity Page - Save Button Not Working on Mobile"
  - Good: "Contact Record - Validation Rule Blocking Valid Data"
  - Bad: "Button broken" or "Error on page"
- **Clear steps to reproduce the bug** - Must be specific and replicable
- **Expected behavior** - What should happen
- **Actual behavior** - What actually happens
- **Environment details** - Where the bug occurs (org, browser, user profile, etc.)
- **Visual proof** - Screenshots or screen recordings demonstrating the issue
- **Severity** - Impact level of the bug
- **Priority** - Urgency of the fix

## Optional Content:

- **Workaround** - Temporary solution while bug is being fixed
- **Root cause analysis** - Technical explanation (filled by developer after investigation)
- **Fix summary** - Brief description of how the bug was resolved

## Dismissible Content:

- Speculative causes unless relevant and documented as assumptions
- Proposed solutions (unless specifically requested by the team)

## Integration to Other Tools:

- Needs a PR/Branch for fixes
- Must reference the code commit where the bug was addressed
- Is part of a release
- Should link to the original User Story/Task if the bug was introduced during recent work
- Should link to related test cases for regression prevention

---

## 📋 BUG TEMPLATE (Copy this into Jira Description)

```
**Title Format:** [Component/Feature] - [Brief Description]

---

## 💡 Summary

**Short description of the observed behavior:**
[Clear, concise description explaining the running user and functional area of the app]

**NOTE TO DEVELOPERS:** Don't propose a solution in the description. Explanations of the testing done when reporting the bug can be included in the comments.

---

## 🖥️ Environment

**Org/Environment:**
- [ ] Production
- [ ] Full Sandbox
- [ ] Partial Sandbox
- [ ] Developer Sandbox
- [ ] Scratch Org

**Running User/Profile:** [Username or Profile experiencing the issue]

**Browser & Version:** [e.g., Chrome 120, Safari 17, Firefox 115]

**Device:**
- [ ] Desktop
- [ ] Mobile
- [ ] Tablet

**Salesforce Experience:**
- [ ] Lightning Experience
- [ ] Classic
- [ ] Mobile App

**Package Version:** [If using managed packages]

**Date/Time Observed:** [When did this bug occur?]

---

## 📸 Visual Proof

**Screenshot:** [Link to Screenshot]

**Video (Optional):** [Link to Video]

*Visual proof is critical for reproducing and understanding the bug*

---

## 🔄 Steps to Reproduce

**Precondition:**
- [Prerequisite 1 - e.g., "User must have Sales Rep profile"]
- [Prerequisite 2 - e.g., "At least one Opportunity must exist"]

**Steps:**
1. [Action 1 - e.g., "Navigate to Opportunity record page"]
2. [Action 2 - e.g., "Click Edit button"]
3. [Action 3 - e.g., "Change Stage to Closed Won"]
4. [Action 4 - e.g., "Click Save"]

---

## ✅ Expected Result

**What should happen:**
[Expected outcome after following the steps]

Example: "The Opportunity should save successfully and display a success message."

---

## 🐛 Actual Result

**What actually happens:**
[Observed outcome after following the steps]

Example: "An error message appears: 'Unable to save record. Contact your administrator.' The Opportunity is not saved."

---

## 🔴 Severity & Priority

**Severity:**
- [ ] **Critical** - System down, data loss, security vulnerability, no workaround
- [ ] **High** - Major functionality broken, significant impact to users, workaround is complex
- [ ] **Medium** - Feature partially broken, workaround exists, moderate impact
- [ ] **Low** - Minor issue, cosmetic problem, minimal impact

**Priority:**
- [ ] **P0 (Blocker)** - Stops all work, must fix immediately (production down)
- [ ] **P1 (High)** - Fix in current sprint (critical functionality broken)
- [ ] **P2 (Medium)** - Fix in next sprint (important but not critical)
- [ ] **P3 (Low)** - Fix when time permits (nice to have)

---

## 📊 Impact Assessment

**Number of Users Affected:**
- [ ] Single user
- [ ] < 10 users
- [ ] < 100 users
- [ ] All users
- [ ] Specific profile/group: [specify]

**Business Impact:**
[How does this affect business operations? Revenue impact? Customer-facing?]

**Data Impact:**
- [ ] No data impact
- [ ] Data at risk
- [ ] Data corrupted/incorrect
- [ ] Data loss occurred

**Frequency:**
- [ ] Always (100% reproducible)
- [ ] Frequently (>75% of the time)
- [ ] Sometimes (25-75% of the time)
- [ ] Rarely (<25% of the time)

---

## ⚙️ Salesforce Context

**Impacted Salesforce Objects:**
-
-

**Impacted Users/Profiles:**
-
-

**Related Functionality:**
- [ ] Apex Code
- [ ] Flow/Process Builder
- [ ] Validation Rules
- [ ] Lightning Web Component
- [ ] Aura Component
- [ ] Visualforce Page
- [ ] Custom Settings/Metadata
- [ ] Integration/API
- [ ] Reports/Dashboards
- [ ] Other: [specify]

---

## 🔄 Regression Information

**Is this a regression?**
- [ ] Yes - This worked before and now it's broken
- [ ] No - This has never worked correctly
- [ ] Unknown

**If regression, when did it break?**
- Last working date/release: [specify]
- Related deployment/release: [link to release ticket]

**Related User Story/Task:**
[Link to the User Story or Task that may have introduced this bug]

---

## 🛠️ Workaround (Optional)

**Is there a workaround?**
- [ ] Yes
- [ ] No

**Workaround Description:**
[If yes, describe the temporary solution users can use while the bug is being fixed]

---

## 🔗 Dependencies & Related Items

**Blocks:** [List User Stories/Tasks blocked by this bug]
-
-

**Related Bugs:** [Link similar or related bugs]
-
-

**Related Test Cases:** [Link to test cases that should have caught this]
-
-

---

## 🔍 Root Cause (To be filled by Developer)

**Root Cause:**
[Technical explanation of what caused the bug - filled after investigation]

**Components Affected:**
-
-

---

## ✔️ Fix Summary (To be filled by Developer)

**Fix Description:**
[Brief description of how the bug was resolved]

**Code Changes:**
- PR/Branch: [link]
- Commit: [link]

**Regression Test Added:**
- [ ] Yes - Test case created/updated: [link]
- [ ] No - Covered by existing tests

---

## 📋 Definition of Done

- [ ] Bug reproduced and root cause identified
- [ ] Fix implemented and code reviewed
- [ ] Unit tests added/updated (for code fixes)
- [ ] Deployed to QA/UAT environment
- [ ] Bug verified as fixed by QA/reporter
- [ ] Regression test documented
- [ ] Deployed to production (for production bugs)
- [ ] Stakeholders notified of resolution

---

## 📎 Linked Items

- Epic: [Link to parent Epic if applicable]
- User Story/Task: [Link to original work item]
- Release: [Link to Release where bug will be fixed]
- Test Case: [Link to test case]
```

---

## Tips for Creating Effective Bug Reports:

1. **Be specific**: "Save button doesn't work" is vague; "Save button on Opportunity page returns error 'FIELD_CUSTOM_VALIDATION_EXCEPTION' when Amount is over $1M" is specific
2. **Include exact error messages**: Copy and paste the full error text, including any error codes
3. **Provide context**: Who, what, when, where - the more details, the faster the fix
4. **Make it reproducible**: Steps should be clear enough that anyone can follow them
5. **Attach visuals**: Screenshots and screen recordings are worth a thousand words
6. **Don't assume the cause**: Describe what you observe, not what you think is wrong
7. **Include workarounds**: If you've found a way around the bug, share it
8. **Link related items**: Connect bugs to the work that may have introduced them
9. **Assess impact accurately**: Help the team prioritize by being honest about severity and impact
10. **Update as you learn**: Add new information in comments as the bug is investigated

---

## Severity vs Priority Guide:

**Severity** = Impact of the bug (What breaks?)
**Priority** = Urgency of the fix (When to fix?)

**Examples:**

| Scenario | Severity | Priority | Reasoning |
|----------|----------|----------|-----------|
| Production login page down | Critical | P0 | No one can access system |
| Spelling error on dashboard | Low | P3 | Cosmetic, no functionality impact |
| Report shows wrong data | High | P1 | Data accuracy critical for decisions |
| Feature works but slow | Medium | P2 | Usable but impacts user experience |
| Beta feature broken | High | P3 | Serious bug but not yet released |

---

## Bug Triage Process:

1. **Reporter** creates bug with all required information
2. **Team Lead** reviews and assigns severity/priority (or confirms reporter's assessment)
3. **Development Team** investigates and identifies root cause
4. **Developer** implements fix and updates bug with fix summary
5. **QA/Reporter** verifies the fix in test environment
6. **Team Lead** approves deployment to production (for production bugs)
7. **Bug closed** after verification in production

---

## Common Bug Categories for Salesforce:

**Functional Bugs:**
- Feature not working as designed
- Incorrect calculations or logic
- Missing functionality

**Data Bugs:**
- Incorrect data displayed
- Data not saving properly
- Data loss or corruption

**Integration Bugs:**
- API calls failing
- External system connections broken
- Data sync issues

**UI/UX Bugs:**
- Display issues
- Responsive design problems
- Accessibility issues

**Performance Bugs:**
- Slow load times
- Timeout errors
- Governor limit exceptions

**Security Bugs:**
- Unauthorized access
- Data exposure
- Permission issues

---

## When to Create a Bug vs Reopening:

**Create a NEW bug when:**
- Different root cause than original bug
- Different symptoms or behavior
- Occurs in different component/feature

**REOPEN existing bug when:**
- Same root cause reappears
- Fix was incomplete
- Regression of the exact same issue