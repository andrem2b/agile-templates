# Ticket Type: Subtask

## Relation to other tickets:

- Subtasks are children of User Stories or Tasks (not Epics directly).
- Subtasks break down the parent ticket into smaller, manageable pieces of work.
- All subtasks must be completed before the parent User Story or Task can be marked as done.
- Subtasks should be independently completable when possible.

## Purpose:

- Breaks down a larger User Story or Task into smaller, actionable pieces.
- Makes work more manageable and easier to track progress.
- Allows parallel work by multiple team members on different subtasks.
- Provides granular visibility into what's being worked on.
- Typical size: 0.5-1 day (2-8 hours) of work.

## Roles & Accountability (RACI):

| Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-----------|----------|
| Development Team | Team Lead | Solution Architect | Project Manager<br>Product Owner<br>Business Analyst |

**Definitions:**
- **Responsible**: Executes the subtask
- **Accountable**: Ensures the subtask is completed and meets quality standards
- **Consulted**: Provides guidance when needed
- **Informed**: Kept up-to-date through parent ticket progress

## Mandatory Content:

- **Descriptive title** following the format: `[Action] - [Component/Area]`
  - Example: "Write Unit Tests - AccountService Class"
  - Example: "Create Field - Opportunity.ExpectedCloseDate"
  - Example: "Update Permission Set - Sales User Profile"
  - Example: "Configure Flow - Opportunity Stage Update"
- **Short description of the specific task** - What needs to be done?
- **Generic acceptance criterion** - What does "done" look like for this subtask?
  - Example: "Function works as expected, has unit tests, and doesn't break automation"
  - Example: "Field created, added to page layout, and permission set updated"
  - Example: "Documentation written, reviewed, and published to Confluence"

## Optional Content:

- **Estimated Hours**: For more granular tracking than story points
- **Technical Notes**: Brief implementation details (which class, object, component)
- **Blockers**: What's preventing completion?
- **Dependencies**: Other subtasks that must be completed first

## Dismissible Content:

- Full implementation details if they are covered elsewhere (in code reviews or documentation)
- Information already captured in the parent User Story or Task
- Overly detailed technical specifications (save for code comments or technical docs)

## Integration to Other Tools:

- Needs a PR/Branch (often shares the same branch as parent ticket)
- Must be mentioned in the code commit
- Is part of a release (through parent ticket)
- Subtasks roll up to parent ticket for release tracking

---

## 📋 SUBTASK TEMPLATE (Copy this into Jira Description)

```
**Title Format:** [Action] - [Component/Area]

---

## 💡 Summary

**What needs to be done?**
[Clear, specific description of this subtask]

---

## ✅ Acceptance Criteria

This subtask will be considered complete once:
- [ ] [Expected result 1]
- [ ] [Expected result 2]

**Example acceptance criteria:**
- Function works as expected, has unit tests, and doesn't break automation
- Field created, added to page layout, and permission set updated
- Documentation written, reviewed, and published

---

## 🏷️ Subtask Type (Optional)

- [ ] Code Development
- [ ] Configuration
- [ ] Testing
- [ ] Documentation
- [ ] Code Review
- [ ] Deployment
- [ ] Bug Fix
- [ ] Other: [specify]

---

## ⚙️ Technical Context (Optional)

**Component/Area:**
[Apex Class, LWC, Flow, Validation Rule, Page Layout, etc.]

**Salesforce Object(s):**
[If applicable]

**Environment:**
- [ ] Developer Sandbox
- [ ] Scratch Org
- [ ] Shared Dev Environment
- [ ] Other: [specify]

**Implementation Notes:**
[Brief technical details - where in the code, which object, specific requirements]

---

## 🔗 Dependencies (Optional)

**Depends On (Subtasks):**
[List other subtasks that must be completed first]
-
-

**Blocks (Subtasks):**
[List subtasks that are waiting on this one]
-
-

---

## 🚧 Blockers (Optional)

**Current Blockers:**
[What's preventing work on this subtask?]
-
-

---

## 📋 Definition of Done

- [ ] Work completed as described in summary
- [ ] Code written (if applicable)
- [ ] Unit tests written and passing (if code)
- [ ] Code reviewed and approved (if code)
- [ ] Configuration validated (if config work)
- [ ] Changes committed to branch
- [ ] Subtask tested independently

---

## 📊 Estimation (Optional)

**Estimated Hours:** [0.5 - 8 hours recommended]

**Actual Hours:** [To be filled upon completion]

---

## 📝 Notes (Optional)

[Any additional context, decisions made, or issues encountered during implementation]

---

## 📎 Linked Items

- Parent: [Link to parent User Story or Task]
- PR/Branch: [Link when available]
```

---

## Tips for Creating Effective Subtasks:

1. **Keep them small**: Subtasks should be completable in 0.5-1 day (2-8 hours max)
2. **Make them specific**: "Update code" is vague; "Add validation to AccountService.updateAccount() method" is specific
3. **Make them testable**: Each subtask should have clear acceptance criteria
4. **Consider dependencies**: Order subtasks logically based on dependencies
5. **Balance granularity**: Too many tiny subtasks create overhead; too few large subtasks reduce visibility
6. **Use clear action verbs**: Create, Update, Write, Configure, Test, Deploy, Review, Document
7. **Keep them independent when possible**: Allows parallel work by multiple developers
8. **Don't duplicate parent details**: Reference the parent ticket for context
9. **Update parent as you go**: Close subtasks as completed to show progress on parent ticket

---

## Common Subtask Patterns for Salesforce Development:

### **User Story Breakdown Example:**

**Parent User Story:** "Sales Rep - View Customer Purchase History"

**Subtasks:**
1. Create Custom Object - PurchaseHistory__c
2. Create Fields - Customer__c, Amount__c, PurchaseDate__c
3. Write Apex Class - PurchaseHistoryService
4. Write Unit Tests - PurchaseHistoryService Tests
5. Create LWC Component - purchaseHistoryList
6. Write Jest Tests - purchaseHistoryList Tests
7. Update Page Layout - Account Record Page
8. Configure Permission Set - Sales User Permissions
9. Write Technical Documentation - Purchase History Feature
10. Code Review - Complete Review and Address Feedback

### **Task Breakdown Example:**

**Parent Task:** "CI/CD - Configure GitHub Actions for Apex Tests"

**Subtasks:**
1. Create GitHub Workflow File - .github/workflows/apex-tests.yml
2. Configure SFDX Authentication - Set up JWT Auth
3. Set Up GitHub Secrets - Add Certificate and Consumer Key
4. Write Test Execution Script - Run Apex Tests and Report Results
5. Configure Code Coverage Check - Enforce 80% Coverage
6. Test Workflow - Validate on Feature Branch
7. Document Workflow - Add README for Team

---

## Subtask Categories by Type:

### **Development Subtasks:**
- Write Apex Class
- Create Lightning Web Component
- Develop Aura Component
- Write Visualforce Page
- Create Trigger
- Implement API Integration

### **Configuration Subtasks:**
- Create Custom Object
- Create Custom Fields
- Configure Page Layout
- Create Record Types
- Set Up Validation Rules
- Configure Workflow/Process Builder
- Build Flow

### **Testing Subtasks:**
- Write Apex Unit Tests
- Write Jest Tests (LWC)
- Create Test Data
- Perform Manual Testing
- Execute UAT Scenarios
- Regression Testing

### **Documentation Subtasks:**
- Write Technical Documentation
- Create User Guide
- Update Process Documentation
- Document API Endpoints
- Create Training Materials

### **Deployment Subtasks:**
- Deploy to QA Sandbox
- Deploy to UAT Sandbox
- Deploy to Production
- Create Change Set
- Prepare Deployment Package

### **Code Review Subtasks:**
- Submit Pull Request
- Address Review Feedback
- Update Based on Comments
- Final Review and Approval

---

## When to Create Subtasks:

**Create subtasks when:**
- User Story or Task is estimated at more than 3-5 story points
- Work involves multiple distinct activities (development, testing, documentation)
- Multiple team members need to work on different parts
- You want to track progress more granularly
- Work has clear sequential or parallel steps

**Don't create subtasks when:**
- User Story or Task is already small (1-2 story points)
- Work is simple and straightforward
- Creating subtasks adds unnecessary overhead
- The work is better tracked as separate User Stories

---

## Subtask Sizing Guidelines:

**Good Subtask Size:**
- Completable in 2-8 hours (0.25 to 1 day)
- Independently testable
- Has clear acceptance criteria
- Adds measurable progress to parent

**Too Small:**
- Less than 1 hour of work
- Creates excessive tracking overhead
- Example: "Add one field" (unless complex)

**Too Large:**
- More than 1 day (8 hours) of work
- Should be broken down further
- Example: "Build entire Lightning component with all functionality"

---

## Subtask Workflow:

1. **Parent ticket moves to In Progress**: Create subtasks
2. **Team member picks subtask**: Moves it to In Progress
3. **Work completed**: Move subtask to Done
4. **All subtasks Done**: Parent ticket can move to Done/Review

**Best Practice**: Don't close the parent until ALL subtasks are completed and verified.

---

## Common Mistakes to Avoid:

1. **Too many subtasks**: 15+ subtasks indicates the parent might need to be split
2. **Subtasks that are actually separate stories**: If a subtask could stand alone, make it a story
3. **No acceptance criteria**: Every subtask needs clear "done" criteria
4. **Duplicate information**: Don't repeat parent ticket details
5. **Generic titles**: "Work on feature" tells you nothing
6. **Waterfall approach**: Don't create all subtasks upfront if requirements might change
7. **Forgetting dependencies**: Document which subtasks block others

---

## Relationship to Parent Tickets:

**Parent User Story:**
- Defines WHAT we're building and WHY
- Contains business context and user value
- Has overall acceptance criteria

**Subtasks:**
- Define HOW we're building it
- Break down the implementation into steps
- Each subtask is a specific piece of work

**Example:**
- Parent: "Sales Rep - View Customer Purchase History" (WHAT & WHY)
- Subtask: "Create LWC Component - purchaseHistoryList" (HOW - specific implementation step)