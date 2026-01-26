# Work Item Effort Estimation Checklist

## How to Use This Checklist

Review each dimension below when estimating effort for a work item. Rate each dimension (e.g., Low/Medium/High or 1-5 scale) and use the combination of ratings to determine overall effort.

---

## 1. Complexity

**What this measures**: The technical difficulty of implementing the solution in Salesforce, including declarative configuration, custom code (Apex/LWC/Visualforce), integrations, and the sophistication of business logic. Higher complexity means more time spent designing, coding, and debugging the solution.

**Rating Scale**: 1 (Simple, well-understood) → 5 (Highly complex, novel challenges)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| How many systems/components are involved? | | | |
| Is the technology stack familiar to the team? | | | |
| Are there any unknown technical challenges? | | | |
| Does this require new architectural patterns? | | | |
| How complex is the business logic? | | | |
| Are there performance/scalability considerations? | | | |
| How much new code needs to be written vs. modified? | | | |
| Will this require refactoring existing code? | | | |
| Are there complex algorithms or data transformations? | | | |
| How many edge cases need to be handled? | | | |
| **TOTAL COMPLEXITY SCORE** | | **100%** | |

---

## 2. Dependencies

**What this measures**: External factors and prerequisites that must be in place before or during Salesforce development. This includes waiting on other teams, third-party apps from AppExchange, API integrations, data migrations, security reviews, and configuration dependencies. Dependencies create delays and coordination overhead.

**Rating Scale**: 1 (Self-contained) → 5 (Multiple critical dependencies)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| Does this depend on other teams' work? | | | |
| Are there third-party service integrations? | | | |
| Do we need new libraries, tools, or infrastructure? | | | |
| Are there database schema changes required? | | | |
| Does this block or unblock other work items? | | | |
| Do we need input/approval from stakeholders? | | | |
| Are there legal, compliance, or security reviews needed? | | | |
| Do we depend on external vendors or partners? | | | |
| Are there procurement or licensing requirements? | | | |
| Can work proceed in parallel or must it be sequential? | | | |
| Are dependencies already completed or still in progress? | | | |
| What's the lead time for any external dependencies? | | | |
| **TOTAL DEPENDENCIES SCORE** | | **100%** | |

---

## 3. Risk

**What this measures**: The likelihood of encountering unexpected challenges, rework, or failures during Salesforce development. This includes unclear requirements, Salesforce governor limits, data quality issues, technical unknowns, platform limitations, knowledge gaps, and potential business impact. Higher risk means more buffer time needed and greater chance of scope changes.

**Rating Scale**: 1 (Low risk, well-understood) → 5 (High risk, many unknowns)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| How well-defined are the requirements? | | | |
| Is this using proven vs. experimental technology? | | | |
| What's the likelihood of significant rework? | | | |
| Are there data migration or backward compatibility risks? | | | |
| Could this impact system stability or uptime? | | | |
| How critical is this to business objectives? | | | |
| What happens if this is delayed? | | | |
| Are resource constraints a concern? | | | |
| Is there risk of scope creep? | | | |
| Does the team have sufficient domain knowledge? | | | |
| Is there adequate documentation available? | | | |
| Are subject matter experts accessible? | | | |
| Will team members need training or ramp-up time? | | | |
| **TOTAL RISK SCORE** | | **100%** | |

---

## 4. Testing

**What this measures**: The effort required to validate the Salesforce solution works correctly across different scenarios, user profiles, and data volumes. This includes writing Apex test classes (minimum 75% code coverage), manual UAT, integration testing with external systems, performance testing against governor limits, and regression testing in sandboxes. More comprehensive testing requires more time.

**Rating Scale**: 1 (Minimal testing) → 5 (Extensive testing required)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| What level of unit test coverage is needed? | | | |
| Are integration tests required? | | | |
| Do we need end-to-end or UI tests? | | | |
| Is performance/load testing necessary? | | | |
| Are there security testing requirements? | | | |
| How difficult will it be to set up test data? | | | |
| Are test environments readily available? | | | |
| Do we need to mock external services? | | | |
| How many test scenarios/cases are needed? | | | |
| Is manual QA testing required? | | | |
| Are there accessibility requirements to verify? | | | |
| Do we need user acceptance testing (UAT)? | | | |
| What's the regression testing scope? | | | |
| **TOTAL TESTING SCORE** | | **100%** | |

---

## 5. Scope

**What this measures**: The breadth and boundaries of what needs to be built in Salesforce. This includes the number of objects, fields, flows, pages, components, automation rules, reports, and user-facing features. It also covers non-functional requirements like documentation, training materials, and deployment artifacts. Larger scope means more deliverables to create and maintain.

**Rating Scale**: 1 (Narrow, well-defined) → 5 (Broad, multi-faceted)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| How many user stories or sub-tasks are included? | | | |
| Is the scope clearly defined and bounded? | | | |
| Are there multiple user personas or use cases? | | | |
| How many screens/interfaces are affected? | | | |
| What's the minimum viable product (MVP)? | | | |
| Are there nice-to-have features we should separate? | | | |
| How much configuration or customization is needed? | | | |
| Are there reporting or analytics requirements? | | | |
| What are the documentation requirements? | | | |
| Is training material needed? | | | |
| Are there deployment or DevOps tasks? | | | |
| What monitoring or observability is required? | | | |
| **TOTAL SCOPE SCORE** | | **100%** | |

---

## 6. Collaboration

**What this measures**: The coordination effort required across team members, stakeholders, and business users during Salesforce development. This includes working with admins vs. developers, involving UX designers for Lightning pages, collaborating with business analysts for requirements, coordinating with release managers for deployments, and conducting training sessions. More collaboration means more meetings, reviews, and communication overhead.

**Rating Scale**: 1 (Individual/minimal collaboration) → 5 (Extensive cross-team coordination)

| Question | Rating (1-5) | Weight | Weighted Score |
|----------|--------------|--------|----------------|
| How many team members need to be involved? | | | |
| Will this require pairing or mob programming? | | | |
| Are specialized skills needed from specific people? | | | |
| How much knowledge sharing or handoff is required? | | | |
| Do we need design/UX involvement? | | | |
| Is product owner input required throughout? | | | |
| Do we need to coordinate with DevOps/SRE? | | | |
| Are there customer success or support considerations? | | | |
| How many meetings or sync points are anticipated? | | | |
| Are there multiple stakeholders to align? | | | |
| Will this require frequent progress updates? | | | |
| Is documentation or knowledge transfer significant? | | | |
| **TOTAL COLLABORATION SCORE** | | **100%** | |

---

## Effort Calculation Guide

### How to Use the Tables

1. **Rate each question** on a scale of 1-5 based on the rating scale provided for that dimension
2. **Assign weights** to each question within a dimension (weights should total 100% per dimension)
3. **Calculate weighted score** for each question: Rating × Weight
4. **Sum the weighted scores** to get the total score for each dimension
5. **Calculate overall effort** using the dimension scores

### Calculating Dimension Scores

For each dimension, calculate the weighted average:

**Dimension Score = Σ(Rating × Weight) where weights sum to 100%**

Example for Complexity dimension:
- Question 1: Rating 4, Weight 15% → Weighted Score = 0.60
- Question 2: Rating 2, Weight 10% → Weighted Score = 0.20
- ... (continue for all questions)
- Total Complexity Score = Sum of all weighted scores

### Simple Approach: Equal Dimension Weights

**Overall Effort = (Complexity + Dependencies + Risk + Testing + Scope + Collaboration) ÷ 6**

| Average Score | Effort Estimate |
|---------------|-----------------|
| 1.0 - 1.5 | XS (Extra Small) |
| 1.6 - 2.5 | S (Small) |
| 2.6 - 3.5 | M (Medium) |
| 3.6 - 4.5 | L (Large) |
| 4.6 - 5.0 | XL (Extra Large) |

### Weighted Approach: Custom Dimension Weights

If certain dimensions are more critical for your team, assign dimension-level weights:

**Example dimension weights:**
- Complexity: 25%
- Dependencies: 20%
- Risk: 20%
- Testing: 15%
- Scope: 15%
- Collaboration: 5%

**Overall Effort = (Complexity × 0.25) + (Dependencies × 0.20) + (Risk × 0.20) + (Testing × 0.15) + (Scope × 0.15) + (Collaboration × 0.05)**

Use the same scoring table above to convert the weighted average to an effort estimate.

---

## Red Flags 🚩

Consider breaking down the work item if:
- Any dimension scores 5/5
- Three or more dimensions score 4+/5
- Overall effort calculates to XL
- Requirements are unclear (Risk dimension high)
- Too many unknowns exist

---

## Estimation Session Tips

1. **Review together**: Go through checklist as a team
2. **Discuss disagreements**: If estimates vary widely, discuss why
3. **Identify assumptions**: Document what you're assuming to be true
4. **Plan for risks**: Note mitigation strategies for high-risk items
5. **Revisit regularly**: Update estimates as new information emerges
6. **Track actuals**: Compare estimates to actual effort for continuous improvement

---

## Document History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | [Date] | Initial checklist created |

