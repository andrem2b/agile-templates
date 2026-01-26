# Jira Ticket Types - Quick Reference Guide
## Salesforce Development Project

---

## 📊 Ticket Type Decision Tree

```
START: What kind of work do I need to track?

├─ Is this a LARGE initiative spanning multiple sprints?
│  └─ YES → Use EPIC
│
├─ Is this RESEARCH or INVESTIGATION work?
│  └─ YES → Use SPIKE
│
├─ Is this a PROBLEM or DEFECT in existing functionality?
│  └─ YES → Use BUG
│
├─ Does this deliver direct USER VALUE?
│  ├─ YES → Use USER STORY
│  └─ NO → Continue...
│
├─ Is this TECHNICAL work with no direct user-facing value?
│  └─ YES → Use TASK
│
└─ Is this breaking down a User Story or Task into smaller pieces?
   └─ YES → Use SUBTASK
```

---

## 📋 Ticket Types at a Glance

| Ticket Type | Purpose | Duration | Parent | Can Have Children | Key Question |
|-------------|---------|----------|--------|-------------------|--------------|
| **Epic** | Large feature/initiative | Multiple sprints | None | User Stories, Tasks | "What's the big goal?" |
| **User Story** | User-facing feature | 1 sprint | Epic (optional) | Subtasks | "What value does the user get?" |
| **Task** | Technical/non-user work | 1 sprint | Epic (optional) | Subtasks | "What technical work needs doing?" |
| **Bug** | Issue/defect | Varies | Any ticket | None | "What's broken?" |
| **Spike** | Research/investigation | 2-5 days | Epic/Story (optional) | None | "What do we need to learn?" |
| **Subtask** | Breakdown of work | 0.5-1 day | User Story or Task | None | "What's the specific action?" |

---

## 🎯 When to Use Each Ticket Type

### Epic 🎯
**Use when:**
- Initiative spans multiple sprints (months)
- Requires multiple User Stories to deliver
- High-level business goal or capability
- Needs executive visibility

**Examples:**
- "Customer Portal - Self-Service Capabilities"
- "Sales Process Automation - Lead to Opportunity"
- "Data Migration - Legacy System to Salesforce"

**Don't use when:**
- Work can be completed in 1-2 sprints → Use User Story
- No clear business initiative → Use Task

---

### User Story 📖
**Use when:**
- Delivers value directly to users
- Can be completed in one sprint
- Fits "As a [user], I need to [action], so that [outcome]" format
- Has UI/UX components

**Examples:**
- "Sales Rep - View Customer Purchase History"
- "Manager - Approve Discount Requests"
- "Customer - Submit Support Cases via Portal"

**Don't use when:**
- No direct user value → Use Task
- Too large for one sprint → Break into multiple stories or create Epic
- Fixing something broken → Use Bug

---

### Task 🔧
**Use when:**
- Technical/infrastructure work
- No direct user-facing value
- Configuration, setup, or maintenance
- Documentation or process work

**Examples:**
- "CI/CD - Configure GitHub Actions for Apex Tests"
- "Environment - Refresh Full Sandbox"
- "Documentation - Update API Integration Guide"
- "Security - Configure SSO with Okta"

**Don't use when:**
- Delivers user value → Use User Story
- Fixing a defect → Use Bug
- Research needed → Use Spike

---

### Bug 🐛
**Use when:**
- Something is broken or not working as expected
- Existing functionality has issues
- Unexpected behavior occurs
- Data is incorrect

**Examples:**
- "Contact Record - Validation Rule Blocking Valid Data"
- "Opportunity Page - Save Button Not Working on Mobile"
- "Report - Showing Incorrect Revenue Totals"

**Don't use when:**
- It's a new feature request → Use User Story
- It's expected behavior you want to change → Use User Story
- No clear reproduction steps yet → Investigate first

---

### Spike 🔬
**Use when:**
- Solution approach is unknown
- Need to investigate multiple options
- High uncertainty blocks estimation
- Technical feasibility unknown
- Risk reduction needed

**Examples:**
- "Feasibility - Real-time Data Sync with External System"
- "Performance - Optimize Bulk Account Processing"
- "Architecture - Integration Pattern for Payment Gateway"

**Don't use when:**
- Work is well-defined → Use Task or User Story
- Just need to build something → Use Task/User Story
- It's a straightforward question → Research during refinement

---

### Subtask ✔️
**Use when:**
- Breaking down User Story or Task
- Multiple distinct activities needed
- Want granular progress tracking
- Parallel work by multiple people

**Examples:**
- "Create Custom Object - PurchaseHistory__c"
- "Write Unit Tests - AccountService Tests"
- "Configure Permission Set - Sales User Permissions"

**Don't use when:**
- Work is already small (1-2 hours) → Keep in parent
- It could stand alone as separate story → Make it a User Story
- Creating excessive overhead → Consolidate

---

## 📝 Title Formats Quick Reference

| Ticket Type | Format | Example |
|-------------|--------|---------|
| **Epic** | [Business Goal] - [High-level Capability] | Customer Portal - Self-Service Capabilities |
| **User Story** | [User Role] - [Action/Capability] | Sales Rep - View Customer Purchase History |
| **Task** | [Category] - [Action] | CI/CD - Configure GitHub Actions |
| **Bug** | [Component/Feature] - [Brief Description] | Opportunity Page - Save Button Not Working |
| **Spike** | [Investigation Type] - [What We're Exploring] | Feasibility - Real-time Data Sync |
| **Subtask** | [Action] - [Component/Area] | Write Unit Tests - AccountService Class |

---

## 👥 RACI Quick Reference

| Ticket Type | Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-------------|-----------|----------|
| **Epic** | Business Analyst | Product Owner | Team Lead<br>Solution Architect | Project Manager<br>Dev Team |
| **User Story** | Team Lead<br>Solution Architect | Product Owner<br>Business Analyst | Dev Team | Project Manager |
| **Task** | Dev Team | Team Lead | Solution Architect | PM, PO, BA |
| **Bug** | Dev Team | Team Lead | Solution Architect | PM, PO, BA |
| **Spike** | Team Lead<br>Dev Team | Solution Architect<br>Business Analyst | Product Owner | Project Manager |
| **Subtask** | Dev Team | Team Lead | Solution Architect | PM, PO, BA |

---

## ✅ Mandatory Fields Quick Check

| Field | Epic | User Story | Task | Bug | Spike | Subtask |
|-------|------|------------|------|-----|-------|---------|
| Descriptive Title | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Summary/Description | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Business Value | ✓ | - | - | - | - | - |
| User Story Statement | - | ✓ | - | - | - | - |
| Acceptance Criteria | ✓ | ✓ | ✓ | - | - | ✓ |
| Steps to Reproduce | - | - | - | ✓ | - | - |
| Expected vs Actual | - | - | - | ✓ | - | - |
| Environment | - | - | - | ✓ | - | - |
| Visual Proof | - | - | - | ✓ | - | - |
| Severity/Priority | - | - | - | ✓ | - | - |
| Questions to Answer | - | - | - | - | ✓ | - |
| Time Box | - | - | - | - | ✓ | - |
| Testing Requirements | ✓ | ✓ | ✓ | - | - | - |
| Technical Approach | ✓ | - | - | - | - | - |
| Salesforce Context | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

---

## ⏱️ Typical Duration Guide

| Ticket Type | Typical Duration | Story Points |
|-------------|------------------|--------------|
| **Epic** | 1-6 months, multiple sprints | 20-100+ |
| **User Story** | 1-10 days (completable in 1 sprint) | 1-8 |
| **Task** | 1-10 days (completable in 1 sprint) | 1-8 |
| **Bug** | Varies (P0: hours, P3: days) | 1-5 |
| **Spike** | 2-5 days (strictly time-boxed) | 2-5 |
| **Subtask** | 2-8 hours (0.5-1 day) | Hours |

---

## 🔗 Hierarchy & Relationships

```
Epic
├── User Story
│   ├── Subtask
│   ├── Subtask
│   └── Subtask
├── User Story
│   └── Subtask
├── Task
│   ├── Subtask
│   └── Subtask
└── Task

Bug (can link to Epic, User Story, or Task)

Spike (usually standalone, can link to Epic or User Story)
```

**Key Rules:**
- Epics contain User Stories and Tasks (NOT Subtasks directly)
- User Stories and Tasks contain Subtasks
- Bugs can link to any ticket type
- Spikes usually standalone but can link for context
- Subtasks ONLY belong to User Stories or Tasks

---

## 🎨 Salesforce-Specific Considerations

### For ALL Ticket Types:
- **Environment/Org**: Which Salesforce environment?
- **Objects Impacted**: Which Salesforce objects affected?
- **Users/Profiles**: Which users are impacted?
- **Governor Limits**: Any limit considerations?

### Configuration vs Code:
| Work Type | Ticket Type | Example |
|-----------|-------------|---------|
| Declarative (Clicks) | Task or User Story | Create Flow, Validation Rule, Page Layout |
| Code (Apex, LWC) | User Story or Task | Write Apex Class, Build LWC |
| Configuration Setup | Task | Sandbox Refresh, SSO Setup |
| Bug in Config | Bug | Validation Rule Blocking Valid Data |
| Bug in Code | Bug | Apex Trigger Error |

---

## 🚨 Bug Severity & Priority Quick Guide

### Severity (What breaks?)
- **Critical**: System down, data loss, security breach
- **High**: Major functionality broken, many users affected
- **Medium**: Feature partially broken, workaround exists
- **Low**: Cosmetic, minimal impact

### Priority (When to fix?)
- **P0 (Blocker)**: Fix immediately (production down)
- **P1 (High)**: Fix in current sprint
- **P2 (Medium)**: Fix in next sprint
- **P3 (Low)**: Fix when time permits

### Quick Decision Matrix:
| Severity | User Impact | Priority | Action |
|----------|-------------|----------|--------|
| Critical | All users | P0 | Drop everything |
| Critical | Small group | P1 | Current sprint |
| High | Many users | P1 | Current sprint |
| High | Few users | P2 | Next sprint |
| Medium | Any | P2-P3 | Schedule normally |
| Low | Any | P3 | Backlog |

---

## 📊 Estimation Guidelines

### Story Points Scale (Fibonacci):
- **1**: Trivial change, < 2 hours
- **2**: Simple change, 2-4 hours
- **3**: Moderate work, 1 day
- **5**: Substantial work, 2-3 days
- **8**: Complex work, 3-5 days
- **13**: Very complex, 5+ days (consider breaking down)

### When Story Points Exceed 8:
→ Break down into multiple User Stories or Tasks
→ Or consider if it should be an Epic

### For Subtasks:
→ Use hours instead of story points
→ Keep under 8 hours (1 day)

---

## 🔄 Common Workflow Patterns

### User Story Flow:
1. **Backlog** → Requirements defined
2. **Ready for Dev** → Acceptance criteria clear
3. **In Progress** → Development underway
4. **Code Review** → PR submitted
5. **QA/Testing** → Being tested
6. **UAT** → Business validation
7. **Done** → Deployed & verified

### Bug Flow:
1. **New** → Just reported
2. **Triage** → Team Lead assessing severity/priority
3. **Approved** → Confirmed as valid bug
4. **In Progress** → Being fixed
5. **Fix Ready** → PR submitted
6. **Testing** → Verifying fix
7. **Verified** → Fix confirmed
8. **Closed** → Deployed to production

### Spike Flow:
1. **To Do** → Queued for research
2. **In Progress** → Investigation underway
3. **Done** → Findings documented, follow-up work identified

---

## 💡 Quick Tips

### DO:
✅ Use descriptive titles with consistent formats
✅ Fill in all mandatory fields
✅ Link related tickets
✅ Update tickets as work progresses
✅ Add comments for important decisions
✅ Close tickets when truly complete

### DON'T:
❌ Create Epics for work completable in 1-2 sprints
❌ Use User Stories for non-user-facing work
❌ Skip acceptance criteria
❌ Leave tickets in "In Progress" indefinitely
❌ Create subtasks for work under 2 hours
❌ Forget to link bugs to related User Stories

---

## 🤔 Common Questions

### Q: User Story or Task?
**A:** Ask: "Does this deliver direct value to a user?"
- YES → User Story
- NO → Task

### Q: When should I create an Epic?
**A:** When work:
- Spans multiple sprints (months)
- Requires 5+ User Stories
- Represents a major business initiative

### Q: How many Subtasks should I create?
**A:** As many as needed for visibility, but typically:
- 3-10 subtasks per User Story/Task
- If more than 15, consider if parent should be split

### Q: Should I create a Spike or just research during refinement?
**A:** Create a Spike when:
- Investigation takes 2+ days
- Multiple options need evaluation
- High technical uncertainty
- Outcome affects architecture

### Q: Bug vs New User Story?
**A:** 
- **Bug**: Existing functionality broken or not working as designed
- **User Story**: New functionality or enhancement

### Q: Can Bugs have Subtasks?
**A:** Generally no. If a bug fix is complex enough to need subtasks, consider if it's actually a larger piece of technical work (Task) rather than a simple bug fix.

---

## 📞 Need Help?

**Still not sure which ticket type to use?**
1. Review the Decision Tree at the top
2. Check the "When to Use" section for each type
3. Ask your Team Lead or Scrum Master
4. When in doubt, start with User Story or Task - you can always convert later

**Remember:** The goal is clarity and tracking, not perfect categorization. Choose the type that best communicates the work to your team.

---

## 🔗 Full Template Links

For complete templates with all fields and guidance:
- See: `epic_template.md`
- See: `user_story_template.md`
- See: `task_template.md`
- See: `bug_template.md`
- See: `spike_template.md`
- See: `subtask_template.md`
