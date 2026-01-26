# Ticket Type: Task

## Relation to other tickets:

- Can be a child of an Epic and can have Subtasks.
- Tasks can be standalone or grouped under an Epic for tracking purposes.
- Unlike User Stories, Tasks are not required to deliver direct user-facing value.

## Purpose:

- Tasks are general work items that don't fit the format of a User Story but still need to be tracked.
- They may not be tied directly to user-facing features (e.g., configuration work, setting up CI/CD pipelines, environment setup, technical debt).
- They might not be tied to a user-facing story but are essential for project delivery.
- Examples: Setting up sandboxes, configuring DevOps pipelines, data migration scripts, documentation, technical research.

## Roles & Accountability (RACI):

| Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-----------|----------|
| Development Team | Team Lead | Solution Architect | Project Manager<br>Product Owner<br>Business Analyst |

**Definitions:**
- **Responsible**: Executes the task and owns delivery
- **Accountable**: Ensures the task is completed and meets requirements
- **Consulted**: Provides technical guidance when needed
- **Informed**: Kept up-to-date on task progress

## Mandatory Content:

- **Descriptive title** following the format: `[Category] - [Action]`
  - Example: "CI/CD - Configure GitHub Actions for Apex Tests"
- **Summary**: What needs to be done? (Clear, concise description)
- **Acceptance Criteria**: Specific, measurable criteria defining when the task is complete
- **Validation Steps**: How will we verify the task was completed successfully?

## Optional Content:

- **Context**: Why this task needs to be done (helpful for understanding priority and urgency)
- **Technical Information**: Links to technical documentation, architectural diagrams, or implementation details
- **Additional Notes**: Any notes captured during refinement sessions or discussions

## Dismissible Content:

- Feature-specific user stories or goals that are not directly relevant to the task
- UI/UX design links (if a task involves design work, it should likely be a User Story)

## Integration to Other Tools:

- Needs a PR/Branch for code-related tasks
- Has to be mentioned in the code commit for traceability
- Is part of a release
- Should link to relevant technical documentation (Confluence, wikis, runbooks)

---

## 📋 TASK TEMPLATE (Copy this into Jira Description)

```
**Title Format:** [Category] - [Action]

---

## 📝 Summary

**What needs to be done?**
[Clear, concise description of the work to be completed]

---

## ℹ️ Context (Optional)

**Why does this need to be done?**
[Brief explanation of the purpose, business driver, or technical reason]

---

## ✅ Acceptance Criteria

This task will be considered complete once:

- [ ] [Expected result 1]
- [ ] [Expected result 2]
- [ ] [Expected result 3]

*[Add 2-5 clear, measurable completion criteria]*

---

## ✔️ Validation Steps

**How to verify this task is complete:**

1. [Verification step 1]
2. [Verification step 2]
3. [Verification step 3]

*[Provide specific steps someone can follow to confirm the work is done correctly]*

---

## 🏷️ Task Type

- [ ] Configuration/Setup
- [ ] CI/CD/DevOps
- [ ] Data Management
- [ ] Integration
- [ ] Documentation
- [ ] Environment Management
- [ ] Technical Debt
- [ ] Security/Compliance
- [ ] Other: [specify]

---

## ⚙️ Salesforce Environment

**Target Environment(s):**
- [ ] Production
- [ ] Full Sandbox
- [ ] Partial Sandbox
- [ ] Developer Sandbox
- [ ] Scratch Org
- [ ] Other: [specify]

**Needs to be replicated across environments?** [Yes/No]

**Impacted Salesforce Components:**
-
-

---

## 🔗 Dependencies

**Depends On:** [List tasks/stories that must be completed first]
-
-

**Blocks:** [List tasks/stories that are waiting on this one]
-
-

**Related Tasks:** [Link related tasks for context]
-
-

---

## 📋 Definition of Done

- [ ] Task completed as described in acceptance criteria
- [ ] Changes validated using verification steps
- [ ] Code reviewed (if applicable)
- [ ] Deployed to target environment(s)
- [ ] Documentation updated (runbooks, wikis, technical docs)
- [ ] Team Lead/Stakeholders notified of completion

---

## 🔧 Technical Information (Optional)

**Technical Documentation:**
[Link to Confluence, architectural diagrams, technical specs, or implementation details]

**Technical Approach:**
[Brief description of how this will be implemented, if relevant]

**Tools/Technologies:**
-
-

---

## 📝 Additional Notes (Optional)

**Assumptions:**
-
-

**Risks/Concerns:**
-
-

**Discussion Notes:**
[Key decisions or insights from refinement or planning discussions]

---

## 📊 Estimation (Optional)

**Story Points:** [T-shirt size: XS/S/M/L/XL or Fibonacci: 1/2/3/5/8]

**Estimated Hours:** [For capacity planning]

---

## 📎 Linked Items

- Epic: [Link to parent Epic if applicable]
- Release: [Link to Release]
- Technical Docs: [Link to Confluence/architecture docs]
- Related PR/Branch: [Link when available]
```

---

## Tips for Creating Effective Tasks:

1. **Be specific**: "Configure CI/CD" is vague; "Configure GitHub Actions to run Apex tests on every PR" is clear
2. **Keep it focused**: Tasks should be single-purpose and completable within a sprint
3. **Make it testable**: Include clear validation steps so anyone can verify completion
4. **Document the "why"**: Even if optional, context helps with prioritization
5. **Track dependencies**: Especially important for infrastructure and setup tasks
6. **Link to documentation**: Technical tasks often require reference materials
7. **Consider replication**: Many Salesforce tasks need to be done across multiple environments
8. **Communicate completion**: Keep stakeholders informed, especially for blocking tasks

---

## Common Task Categories for Salesforce Projects:

**Configuration/Setup:**
- Sandbox refresh and configuration
- User provisioning and profile setup
- Permission set assignments
- Field-level security configuration

**CI/CD/DevOps:**
- Pipeline setup and configuration
- Automated testing framework setup
- Deployment automation
- Branch strategy implementation

**Data Management:**
- Data migration scripts
- Data cleanup and deduplication
- Mass data updates
- Test data generation

**Integration:**
- API endpoint configuration
- External system connection setup
- Middleware configuration
- Authentication setup

**Environment Management:**
- Sandbox creation/refresh
- Package installation
- Metadata deployment
- Environment synchronization

**Documentation:**
- Technical documentation
- Runbook creation
- Process documentation
- Knowledge base articles

**Technical Debt:**
- Code refactoring
- Deprecated API updates
- Performance optimization
- Test coverage improvement

---

## Task vs User Story: When to Use Which?

**Use a Task when:**
- No direct user-facing value (e.g., CI/CD setup, infrastructure work)
- Technical enabler that doesn't fit the user story format
- Configuration or maintenance work
- Documentation or research activities

**Use a User Story when:**
- There's a clear user benefit
- Work delivers functionality users will interact with
- Can be described in "As a [user], I need to [action], so that [outcome]" format