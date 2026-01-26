# Ticket Type: Spike

## Relation to other tickets:

- Spikes usually stand alone but can be linked to an Epic or User Story for context.
- Spikes often precede User Stories or Tasks - they help inform the work that will follow.
- Once a spike is complete, it typically results in the creation of one or more User Stories or Tasks based on the findings.

## Purpose:

- Represents research or investigation work needed to support future work (e.g., technical exploration, prototyping, feasibility studies).
- Reduces risk by investigating unknowns before committing to implementation.
- Provides data for accurate estimation and planning of future work.
- Explores multiple solutions before choosing the best approach.
- Time-boxed research with specific questions to answer.

## Role of the Owner:

- Business Analyst, Solution Architect, Developer
- Typically owned by technical roles who can conduct the investigation

## Roles & Accountability (RACI):

| Responsible | Accountable | Consulted | Informed |
|-------------|-------------|-----------|----------|
| Team Lead<br>Development Team | Solution Architect<br>Business Analyst | Product Owner | Project Manager |

**Definitions:**
- **Responsible**: Conducts the research and investigation
- **Accountable**: Ensures the spike answers the key questions and delivers findings
- **Consulted**: Provides input on research direction and reviews findings
- **Informed**: Kept up-to-date on spike progress and outcomes

## Mandatory Content:

- **Descriptive title** following the format: `[Investigation Type] - [What We're Exploring]`
  - Example: "Feasibility - Real-time Data Sync with External System"
  - Example: "Performance - Optimize Bulk Account Processing"
  - Example: "Architecture - Integration Pattern for Payment Gateway"
- **Key questions or areas to investigate** - Specific questions the spike must answer
- **Goals or outcomes expected from the research** - What decisions will this enable?
- **Time Box** - Maximum time allocated for the spike (typically 2-5 days)
- **Success Criteria** - What does "done" look like?
- **Expected Deliverables** - What the spike will produce (documentation, POC, recommendation)

## Optional Content:

- Proof of concept code (if needed to answer questions)
- Prototype or demo (if helpful for validation)

## Dismissible Content:

- Full technical implementation (the spike should focus on gathering information, not building features)
- Production-ready code (spikes are for exploration, not delivery)
- Detailed implementation plans (those come after the spike informs the approach)

## Integration to Other Tools:

- Usually doesn't require PR/Branch unless a prototype or proof-of-concept is created
- Can be part of a release if necessary
- Should link to technical documentation created during research
- Findings should be documented in Confluence or similar knowledge base

---

## 📋 SPIKE TEMPLATE (Copy this into Jira Description)

```
**Title Format:** [Investigation Type] - [What We're Exploring]

---

## 🔬 Spike Summary

**In order to** [achieve some goal]
**[a system or persona]**
**needs to** [some action]

---

## ❓ Questions to Answer

This spike will be considered complete once we have answered the following:

- **What is the problem that we want to solve?**
  -

- **Is it feasible?**
  -

- **How much effort does it take?**
  -

- **What are the risks/unknowns?**
  -

- **What are the technical constraints or Salesforce limits?**
  -

- **What approach/solution do we recommend?**
  -

- **What alternatives did we consider?**
  -

- **What are the next steps after this spike?**
  -

---

## 🎯 Goals & Success Criteria

**Goals/Outcomes Expected:**
[What decisions will this research enable? What do we need to know?]

**Success Criteria:**
This spike is complete when:
- [ ] All key questions are answered
- [ ] Sufficient information gathered to make an informed decision
- [ ] Recommendation documented
- [ ] Follow-up work items identified

---

## ⏱️ Time Box

**Expected Duration:** [2-5 days recommended]

**Start Date:** [Date]

**Target Completion:** [Date]

**Maximum Time Allowed:** [Do not exceed X days]

**Check-in Milestones:**
- Day 1: [Milestone]
- Day 2: [Milestone]
- Final: [Deliverables complete]

---

## 📦 Expected Deliverables

What this spike will produce:

- [ ] Technical documentation
- [ ] Proof of concept code
- [ ] Architecture diagram
- [ ] Feasibility report
- [ ] Performance analysis
- [ ] Recommendation document
- [ ] Presentation/demo
- [ ] Other: [specify]

---

## 🔍 Investigation Scope

**In Scope:**
-
-
-

**Out of Scope:**
-
-
-

---

## ⚙️ Salesforce Context

**Investigation Type:**
- [ ] Feasibility Study
- [ ] Performance Analysis
- [ ] Integration Pattern
- [ ] Architecture Decision
- [ ] Data Model Design
- [ ] Security/Compliance
- [ ] API/Governor Limits
- [ ] Tool/Technology Evaluation
- [ ] Other: [specify]

**Test Environments:**
- [ ] Developer Sandbox
- [ ] Scratch Org
- [ ] Full Sandbox
- [ ] Other: [specify]

**Salesforce Limits to Consider:**
- [ ] Governor Limits (SOQL queries, DML operations, CPU time)
- [ ] API Limits (daily API calls, concurrent requests)
- [ ] Storage Limits (data storage, file storage)
- [ ] Feature Limits (workflow rules, process builders, flows)
- [ ] Other: [specify]

**Technologies/Tools to Explore:**
- [ ] Apex
- [ ] Lightning Web Components
- [ ] Flow/Process Builder
- [ ] Platform Events
- [ ] Change Data Capture
- [ ] External Objects
- [ ] Integration Patterns (REST, SOAP, Bulk API)
- [ ] Third-party Tools/Packages
- [ ] Other: [specify]

**Salesforce Objects/Features Involved:**
-
-

---

## 🧪 Research Approach

**Method:**
[How will you conduct this investigation?]

**Steps:**
1.
2.
3.

**Resources Needed:**
- Access to: [environments, tools, documentation]
- Support from: [team members, stakeholders]

---

## 📊 Findings & Recommendations (To be filled upon completion)

**Summary of Findings:**
[High-level summary of what was learned]

**Detailed Findings:**

### What is the problem we want to solve?
[Answer]

### Is it feasible?
[Answer: Yes/No/Partially - with explanation]

### How much effort does it take?
[Estimation: Story points, days, complexity assessment]

### What are the risks/unknowns?
[List risks discovered and any remaining unknowns]

### What are the technical constraints?
[Salesforce limits, platform constraints, technical blockers]

### Recommended Approach:
[Detailed recommendation with reasoning]

### Alternatives Considered:
| Alternative | Pros | Cons | Recommendation |
|-------------|------|------|----------------|
| Option 1 | | | |
| Option 2 | | | |
| Option 3 | | | |

**Recommended Solution:** [Which option and why?]

---

## 🎬 Next Steps & Follow-up Work

**Follow-up User Stories/Tasks to Create:**
1. [Story/Task 1 based on findings]
2. [Story/Task 2 based on findings]
3. [Story/Task 3 based on findings]

**Dependencies Identified:**
-
-

**Blockers Identified:**
-
-

**Additional Research Needed:**
-
-

---

## 💡 Additional Notes

**Links to Technical Documentation:**
[Link to Confluence, architectural diagrams, POC code repository, research notes]

**Proof of Concept:**
[Link to prototype, demo, or POC code if created]

**References:**
[Salesforce documentation, articles, blog posts, videos consulted]

**Discussion Notes:**
[Key insights from conversations with team members or stakeholders]

---

## 📎 Linked Items

- Epic: [Link to parent Epic if applicable]
- User Story: [Link to related User Story for context]
- Technical Docs: [Link to Confluence/documentation]
- POC Repository: [Link to code if applicable]
```

---

## Tips for Conducting Effective Spikes:

1. **Time-box strictly**: Spikes should be short (2-5 days max). If more time is needed, break into multiple spikes.
2. **Focus on answering questions**: The goal is information gathering, not building production features.
3. **Document as you go**: Don't wait until the end to document findings - capture insights continuously.
4. **Share early and often**: Present preliminary findings to the team to validate direction.
5. **Prototype wisely**: Build just enough to answer questions - no more, no less.
6. **Consider multiple options**: Evaluate at least 2-3 alternatives before recommending one.
7. **Be data-driven**: Use metrics, performance tests, and concrete evidence to support recommendations.
8. **Think about Salesforce limits**: Always consider governor limits, API limits, and platform constraints.
9. **Plan follow-up work**: Identify the User Stories/Tasks that will result from the spike.
10. **Present findings**: Schedule a demo or presentation to share learnings with the team.

---

## Common Spike Categories for Salesforce Projects:

**Feasibility Studies:**
- Can we integrate with this external system?
- Is real-time data sync possible within governor limits?
- Can we achieve this performance requirement?

**Performance Analysis:**
- How can we optimize bulk data processing?
- What's causing slow page load times?
- Can we handle this data volume?

**Integration Patterns:**
- What's the best way to integrate with this third-party API?
- Should we use Platform Events or Custom Metadata for this use case?
- Which middleware solution is most appropriate?

**Architecture Decisions:**
- Should we use Lightning Web Components or Aura?
- What's the best data model for this requirement?
- How should we structure our org (single vs multiple)?

**Tool/Technology Evaluation:**
- Should we use a managed package or build custom?
- Which AppExchange solution best fits our needs?
- Is this third-party integration tool worth the cost?

**Security/Compliance:**
- How do we implement field-level encryption?
- What's needed for GDPR/CCPA compliance?
- How do we secure this integration?

---

## Spike vs Task: When to Use Which?

**Use a Spike when:**
- The solution or approach is unknown
- You need to investigate multiple options
- Uncertainty exists that blocks estimation or implementation
- Research is needed to inform future work
- Risk is high and needs to be reduced through investigation

**Use a Task when:**
- The work is known and defined
- No research or investigation is needed
- You're implementing a known solution
- The approach is clear and straightforward

---

## After the Spike: Next Steps

1. **Present Findings**: Share results with the team in sprint review or dedicated session
2. **Update Epic/Story**: Add findings to related Epic or User Story for context
3. **Create Follow-up Work**: Generate User Stories or Tasks based on recommendations
4. **Update Documentation**: Ensure findings are captured in Confluence or knowledge base
5. **Close the Spike**: Once findings are documented and follow-up work is created