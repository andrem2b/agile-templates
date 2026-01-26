# Ticket Type: User Story

## Relation to other tickets:

- Can be delivered alone or as part of an Epic. It can have Subtasks.
- **Note for Epic-linked stories**: When a User Story is part of an Epic, pay special attention to dependencies and sequencing order. Stories within the same Epic often have dependencies on each other and may need to be completed in a specific order. Always document these dependencies clearly.

## Purpose:

- Describes a feature that delivers value to the user and can be completed in a single sprint.
- Focuses on the user's perspective and the value they receive.
- Should be independently testable and deployable (when possible).

## Roles & Accountability (RACI):

| Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-----------|----------|
| Team Lead<br>Solution Architect | Product Owner<br>Business Analyst | Development Team | Project Manager |

**Definitions:**
- **Responsible**: Implements the User Story and owns technical delivery
- **Accountable**: Defines requirements and accepts the completed story
- **Consulted**: Provides input during implementation
- **Informed**: Kept up-to-date on story progress

## Mandatory Content:

- **Descriptive title** following the format: `[User Role] - [Action/Capability]`
  - Example: "Sales Rep - View Customer Purchase History"
- **User Story Statement**: In the format "As a [user], I need to [action], so that [outcome]"
- **Acceptance Criteria**: 3-7 testable criteria that clearly define what "done" means
  - Use Given-When-Then format (Gherkin syntax) for clarity
- **Testing Requirements**: Test scenarios, test data needs, and UAT owner
- **Salesforce Context**: Impacted objects, profiles, configuration vs code approach
- **Design Link**: Link to mockups, wireframes, or UI specifications (if applicable)

## Optional Content:

- Technical implementation details should be kept minimal in the User Story unless they directly impact the user experience
- Highly technical details can be captured in Subtasks or Technical Information section
- Story Points and estimated hours (if your team uses these for capacity planning)

## Integration to Other Tools:

- Requires a PR/Branch for development tracking
- Must be part of a release
- Should link to design files (Figma, Sketch, etc.)
- Should link to technical documentation or architecture diagrams (Confluence, Lucidchart, etc.)

---

## 📋 USER STORY TEMPLATE (Copy this into Jira Description)

```
**Title Format:** [User Role] - [Action/Capability]

---

## 💡 User Story

**As a** [user role]
**I need to** [perform an action]
**So that** [I can achieve this outcome/benefit]

---

## ✅ Acceptance Criteria

This story will be considered complete once:

1. **[Criterion 1]**
   - **Given** [some context or precondition]
   - **When** [some action is carried out]
   - **Then** [a particular set of observable consequences should occur]

2. **[Criterion 2]**
   - **Given** [some context or precondition]
   - **When** [some action is carried out]
   - **Then** [a particular set of observable consequences should occur]

3. **[Criterion 3]**
   - **Given** [some context or precondition]
   - **When** [some action is carried out]
   - **Then** [a particular set of observable consequences should occur]

*[Add 3-7 acceptance criteria - each should be specific, measurable, and testable]*

---

## 🧪 Testing Requirements

**Test Scenarios:**
- Scenario 1: [Description]
- Scenario 2: [Description]
- Scenario 3: [Description]

**Test Data Requirements:**
- [What test data is needed?]
- [Any specific data volumes or conditions?]

**UAT Owner:**
- [Name/Role of person responsible for user acceptance testing]

---

## 🎨 Design

**Design Link:** [Link to Figma/Sketch/Wireframes]

**Key UI/UX Notes:**
-
-

---

## ⚙️ Salesforce Context

**Impacted Salesforce Objects:**
-
-

**Impacted Users/Profiles:**
- [ ] System Administrator
- [ ] Sales User
- [ ] Service User
- [ ] Custom Profile: [specify]

**Implementation Approach:**
- [ ] Declarative (Flow, Process Builder, Validation Rules, etc.)
- [ ] Code (Apex, LWC, Aura, Visualforce)
- [ ] Hybrid (Both declarative and code)

**Configuration Changes Required:**
- [ ] Page Layouts
- [ ] Record Types
- [ ] Permissions/Profiles
- [ ] Fields (new/modified)
- [ ] Other: [specify]

**Data Considerations:**
- Data Migration Required: [Yes/No]
- Data Volume Impact: [Low/Medium/High]
- Data Cleanup Needed: [Yes/No]

---

## 🔗 Dependencies

**Depends On:** [List stories/tasks that must be completed first]
-
-

**Blocks:** [List stories/tasks that are waiting on this one]
-
-

**Related Stories:** [Link related stories for context]
-
-

---

## 📋 Definition of Done

- [ ] Code reviewed and approved
- [ ] Unit tests written (80%+ code coverage for Apex)
- [ ] Deployed to QA/UAT sandbox
- [ ] UAT completed and signed off by business
- [ ] Documentation updated (technical docs, user guides)
- [ ] No critical or high-priority bugs remaining

---

## 🔧 Technical Information / Additional Notes

**Architecture/Technical Approach:**
[Link to technical documentation, architectural diagram, or describe technical approach]

**Assumptions:**
-
-

**Outstanding Questions:**
-
-

**Discussion Notes:**
[Key decisions made during refinement sessions or discussions with the team]

---

## 📊 Estimation (Optional)

**Story Points:** [T-shirt size: XS/S/M/L/XL or Fibonacci: 1/2/3/5/8/13]

**Estimated Hours:** [Optional - for capacity planning]

---

## 📎 Linked Items

- Epic: [Link to parent Epic if applicable]
- Release: [Link to Release]
- Design: [Link to design files]
- Technical Docs: [Link to Confluence/architecture docs]
```

---

## Tips for Creating Effective User Stories:

1. **Focus on the user**: Always write from the user's perspective, not the system's
2. **Keep it small**: Stories should be completable in a single sprint (typically 1-5 days of work)
3. **Make it testable**: Every acceptance criterion should be verifiable
4. **Avoid technical jargon in the story statement**: Save technical details for the Technical Information section
5. **Collaborate early**: Refine stories with the team before sprint planning
6. **INVEST principle**: Stories should be Independent, Negotiable, Valuable, Estimable, Small, and Testable
7. **Document dependencies**: Especially important for stories within the same Epic
8. **Link to designs**: Visual context helps developers understand requirements better
9. **Be specific with Salesforce context**: Knowing which objects and profiles are impacted helps with estimation and testing

---

## Common Pitfalls to Avoid:

- **Writing technical tasks as user stories**: If there's no user benefit, it might be a Task instead
- **Too large**: If a story can't be completed in one sprint, break it down
- **Vague acceptance criteria**: "System should work correctly" is not testable
- **Missing UAT owner**: Always identify who will validate the story
- **Ignoring dependencies**: Especially critical for Epic-linked stories