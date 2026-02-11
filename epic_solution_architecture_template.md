# Epic Solution Architecture

## Purpose
This document defines the technical solution approach for an epic on an existing Salesforce org. It provides the "how" of implementation, proposes work breakdown into user stories, and estimates delivery effort to support quarterly planning.

---

## 1. Epic Overview

### 1.1 Epic Metadata
| Field | Details |
|-------|---------|
| **Epic ID** | [JIRA-XXX] |
| **Epic Name** | |
| **Document Version** | 1.0 |
| **Date** | |
| **Architect(s)** | |
| **Product Owner** | |
| **Status** | Draft / In Review / Approved |
| **Target Quarter** | QX 202X |

### 1.2 Executive Summary
*Provide a 2-3 paragraph overview answering:*
- What capability are we adding/changing?
- Why does this matter to the business?
- What's the high-level technical approach?
- What's the estimated effort and timeline?

**Business Value:**
- [Key benefit 1]
- [Key benefit 2]
- [Key benefit 3]

**Expected Outcome:**
[What will be different for users/business after this is delivered?]

---

## 2. Business Context

### 2.1 Problem Statement
*Describe the business problem or opportunity in plain language*

**Who is impacted:**
- [User group 1 and their pain point]
- [User group 2 and their pain point]

**Current Limitations:**
- [What can't users do today?]
- [What's inefficient or broken?]
- [What business impact does this have?]

### 2.2 Success Criteria
*How will we know this epic succeeded?*

| Success Metric | Current State | Target State | Measurement Method |
|----------------|---------------|--------------|-------------------|
| [KPI 1] | [baseline] | [goal] | [how measured] |
| [KPI 2] | [baseline] | [goal] | [how measured] |

### 2.3 Scope & Boundaries

**In Scope:**
- [Capability 1]
- [Capability 2]
- [User groups affected]
- [Objects/features being modified]

**Out of Scope:**
- [Explicit exclusions]
- [Deferred to future epics]
- [What we're NOT changing]

**Assumptions:**
- [Key assumption 1]
- [Key assumption 2]

---

## 3. Current State Assessment

### 3.1 Existing Org Configuration
*Describe relevant parts of the current Salesforce setup*

**Affected Objects:**
- [Standard/Custom objects involved]
- [Current field usage and data model]
- [Record volumes]

**Existing Customizations:**
- [Relevant flows, triggers, apex classes]
- [Current automation affecting this area]
- [UI customizations (pages, components)]

**Current Integrations:**
- [Systems that touch this functionality]
- [Data flows in/out]

### 3.2 Technical Debt & Constraints
*What technical challenges exist in the current state?*

**Technical Debt:**
- [Legacy code/config to work around or refactor]
- [Known issues in affected areas]

**Constraints:**
- [Org limits considerations]
- [Data volume concerns]
- [Performance considerations]
- [Governor limits]
- [License/feature limitations]

---

## 4. Proposed Solution

### 4.1 Solution Overview
*Describe WHAT we're building in business terms*

[2-3 paragraph description of the solution from a user/business perspective]

**Key Capabilities:**
1. [Capability 1 - what it enables]
2. [Capability 2 - what it enables]
3. [Capability 3 - what it enables]

### 4.2 Technical Approach (The "How")
*Describe HOW we'll implement this technically*

#### Data Model Changes
- **Objects:** [New/modified objects]
- **Fields:** [Key fields being added/modified]
- **Relationships:** [New lookups/master-details]
- **Data Migration:** [Any data transformation needed]

#### Automation & Logic
- **Flows:** [Flow automations needed]
- **Triggers/Apex:** [When and why custom code is needed]
- **Validation Rules:** [Business rules to enforce]
- **Process Automation:** [Approval processes, scheduled jobs]

#### User Interface
- **Lightning Pages:** [New/modified record/app pages]
- **Lightning Components:** [Custom LWC/Aura components]
- **App/Navigation:** [App changes, navigation updates]
- **Mobile Considerations:** [Mobile-specific requirements]

#### Integration Changes
- **Systems Affected:** [External systems involved]
- **Integration Pattern:** [API, Event-driven, Batch]
- **Data Sync:** [What data flows where, real-time vs batch]
- **Authentication:** [How systems authenticate]

#### Security & Access
- **Profiles/Permission Sets:** [Access control changes]
- **Sharing Rules:** [Record access patterns]
- **Field-Level Security:** [Sensitive data protection]
- **Data Classification:** [PII, confidential data handling]

---

## 5. Architecture Decisions

### 5.1 Key Technical Decisions
*Document major "how" decisions that shape implementation*

| Decision Point | Options Considered | Chosen Approach | Rationale | Implications |
|----------------|-------------------|-----------------|-----------|--------------|
| [e.g., Automation tool] | Flow vs Apex | Flow Builder | Maintainability, declarative-first | Requires admin training |
| [e.g., Integration] | Real-time API vs Platform Events | Platform Events | Decoupling, scalability | Eventual consistency model |
| [Add more] | | | | |

### 5.2 Design Patterns & Standards
*How will this follow org best practices?*

- **Naming Conventions:** [How will components be named?]
- **Code Standards:** [Trigger framework, bulkification, etc.]
- **Error Handling:** [How errors are logged/surfaced]
- **Testing Approach:** [Unit test coverage, test data strategy]

---

## 6. Integration & Data Strategy

### 6.1 Integration Requirements
*Only if this epic involves integration changes*

| External System | Purpose | Integration Type | Data Flow | Frequency | Owner |
|-----------------|---------|------------------|-----------|-----------|-------|
| [System 1] | [Why integrating] | REST API / Event / Batch | SF ↔ System | Real-time / Daily | [Team] |

**Integration Impact:**
- [What changes in external systems?]
- [Backward compatibility concerns?]
- [Testing approach for integrations?]

### 6.2 Data Considerations

**Data Volume:**
- [Estimated record volumes]
- [Growth projections]
- [Storage/API limit impacts]

**Data Quality:**
- [Validation requirements]
- [Cleansing needed]
- [Duplicate management]

**Data Migration:**
- [Any historical data to migrate?]
- [Data transformation rules]
- [Cutover approach]

---

## 7. Security & Compliance

### 7.1 Security Requirements
*Only if this epic has specific security implications*

**Access Control:**
- [Who should access what]
- [Permission set strategy]

**Data Privacy:**
- [PII/sensitive data involved]
- [Encryption requirements]
- [Retention/deletion policies]

**Compliance:**
- [Regulatory requirements: GDPR, HIPAA, SOX, etc.]
- [Audit trail requirements]

---

## 8. Work Breakdown & Story Themes

### 8.1 Implementation Themes
*High-level groupings of work - these become story epics or labels*

#### Theme 1: [e.g., Data Model & Configuration]
**Purpose:** [What this theme accomplishes]

**Stories in this theme:**
- Data model changes (objects, fields, relationships)
- Validation rules and picklist setup
- Page layouts and record types
- Initial test data setup

**Dependencies:** [What must be done first]

---

#### Theme 2: [e.g., Core Automation]
**Purpose:** [What this theme accomplishes]

**Stories in this theme:**
- Flow automations for [specific process]
- Apex triggers for [specific logic]
- Email alerts and notifications
- Unit tests for custom code

**Dependencies:** [What must be done first]

---

#### Theme 3: [e.g., User Interface]
**Purpose:** [What this theme accomplishes]

**Stories in this theme:**
- Lightning record pages
- Custom Lightning components
- App navigation and utility items
- Mobile optimization

**Dependencies:** [What must be done first]

---

#### Theme 4: [e.g., Integration]
**Purpose:** [What this theme accomplishes]

**Stories in this theme:**
- API endpoint development
- Integration middleware configuration
- Error handling and logging
- Integration testing

**Dependencies:** [What must be done first]

---

#### Theme 5: [e.g., Testing & Enablement]
**Purpose:** [What this theme accomplishes]

**Stories in this theme:**
- UAT test scenarios and execution
- Training materials and documentation
- User permissions and access setup
- Data migration/cleanup

**Dependencies:** [What must be done first]

---

### 8.2 Story Generation Guidance
*How developers/BAs should break themes into Jira stories*

**Story Sizing Guidelines:**
- Stories should be completable in 1-2 sprints
- Each story should be independently testable
- Stories should deliver incremental value when possible
- Keep stories aligned with one theme

**Story Template:**
```
Title: [Action] + [Component] + [Purpose]
Example: "Build Flow for Opportunity Auto-Assignment"

As a [user type]
I want [capability]
So that [business value]

Acceptance Criteria:
- [ ] [Testable criterion 1]
- [ ] [Testable criterion 2]
- [ ] [Testable criterion 3]

Technical Notes:
- [Implementation guidance]
- [Dependencies]
- [Testing requirements]
```

---

## 9. Testing Strategy

### 9.1 Testing Approach

**Unit Testing:**
- [Code coverage targets: 85%+]
- [Test data strategy]
- [Mock/stub approach for integrations]

**Integration Testing:**
- [End-to-end scenarios]
- [Systems involved]
- [Test environment requirements]

**User Acceptance Testing:**
- [Test scenarios by user role]
- [UAT environment]
- [Success criteria]

**Performance Testing:**
- [Load/volume testing if needed]
- [Performance benchmarks]

### 9.2 Test Data Requirements
- [What test data is needed]
- [How will it be created/refreshed]
- [Sandbox strategy]

---

## 10. Deployment & Release Strategy

### 10.1 Environment Strategy

**Development Path:**
```
Developer Sandbox → Integration Sandbox → UAT Sandbox → Production
```

| Environment | Purpose | Refresh Frequency | Data |
|-------------|---------|-------------------|------|
| Dev Sandbox | Individual development | Weekly | Minimal test data |
| Integration Sandbox | Integration testing | Bi-weekly | Representative data |
| UAT Sandbox | User acceptance testing | Monthly | Production-like data |
| Production | Live environment | N/A | Real data |

### 10.2 Release Approach

**Deployment Method:**
- [ ] Change Sets
- [ ] Salesforce CLI / SFDX
- [ ] Metadata API
- [ ] Managed Package
- [ ] DevOps tooling: [Specify: Copado, Gearset, AutoRABIT, etc.]

**Deployment Components:**
- [What will be deployed: Metadata types]
- [Configuration vs code]
- [Manual steps required]

**Release Sequence:**
1. **Pre-Deployment**
   - [Pre-deployment steps: backup, communication]
   - [Manual configuration needed first]

2. **Deployment**
   - [Automated deployment steps]
   - [Deployment window/timing]
   - [Rollback plan]

3. **Post-Deployment**
   - [Post-deployment verification]
   - [Data migration/cutover if needed]
   - [User enablement]
   - [Smoke testing]

**Rollback Strategy:**
- [How to rollback if deployment fails]
- [What can/cannot be rolled back]
- [Recovery time objective]

### 10.3 Go-Live Readiness Checklist

**Technical Readiness:**
- [ ] All code deployed and tested in production
- [ ] All integrations tested end-to-end
- [ ] Performance testing completed
- [ ] Security review completed
- [ ] Backup/rollback plan documented

**User Readiness:**
- [ ] Training completed
- [ ] Documentation published
- [ ] Permissions assigned
- [ ] Support team briefed

**Business Readiness:**
- [ ] UAT sign-off received
- [ ] Change management communication sent
- [ ] Business processes updated
- [ ] Success metrics baseline captured

---

## 11. Effort Estimation & Timeline

### 11.1 T-Shirt Sizing (End-to-End Delivery)

**Sizing Dimensions:**
- Development effort (coding, configuration)
- Testing effort (unit, integration, UAT)
- Deployment complexity
- Risk/uncertainty

**Overall Epic Size:** [XS / S / M / L / XL / XXL]

**Sizing Breakdown by Theme:**

| Theme | Size | Dev Effort | Testing Effort | Risk Level | Notes |
|-------|------|------------|----------------|------------|-------|
| Theme 1: [Name] | M | 2-3 sprints | 1 sprint | Low | [Key considerations] |
| Theme 2: [Name] | L | 3-4 sprints | 1-2 sprints | Medium | [Key considerations] |
| Theme 3: [Name] | S | 1 sprint | 0.5 sprint | Low | [Key considerations] |
| **TOTAL** | **L** | **6-8 sprints** | **2.5-3.5 sprints** | **Medium** | |

**T-Shirt Size Reference:**
- **XS:** 1-2 weeks (1 sprint) - Simple config change, minimal testing
- **S:** 2-4 weeks (1-2 sprints) - Single component, straightforward
- **M:** 1-2 months (2-4 sprints) - Multiple components, moderate complexity
- **L:** 2-3 months (4-6 sprints) - Cross-functional, integration involved
- **XL:** 3-4 months (6-8 sprints) - Complex, high integration, data migration
- **XXL:** 4+ months (8+ sprints) - Very complex, consider breaking into multiple epics

### 11.2 Delivery Timeline

**Target Delivery:** [QX 202X]

**High-Level Milestones:**

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| Solution Architecture Approved | [Date] | Pending |
| Theme 1 Complete | [Date] | Not Started |
| Theme 2 Complete | [Date] | Not Started |
| Integration Testing Complete | [Date] | Not Started |
| UAT Complete | [Date] | Not Started |
| Production Deployment | [Date] | Not Started |
| Hypercare Complete | [Date] | Not Started |

**Sprint Allocation:**
- Discovery & Design: [X sprints]
- Development: [X sprints]
- Testing: [X sprints]
- Deployment & Stabilization: [X sprints]
- **Total:** [X sprints] ≈ [X months]

### 11.3 Resource Requirements

| Role | Allocation | Duration | Notes |
|------|------------|----------|-------|
| Solution Architect | 25% | Full epic | Design decisions, reviews |
| Developer(s) | 100% (X people) | [X sprints] | Implementation |
| Admin/Configurator | 50% | [X sprints] | Declarative config |
| QA/Tester | 50% | [X sprints] | Testing & UAT support |
| Integration Specialist | 25% | [X sprints] | If integration work needed |
| Product Owner | 10% | Full epic | Acceptance, prioritization |

---

## 12. Risks & Dependencies

### 12.1 Risk Register

| Risk | Likelihood | Impact | Mitigation Strategy | Owner |
|------|------------|--------|---------------------|-------|
| [Risk 1] | High/Med/Low | High/Med/Low | [How we'll mitigate] | [Name] |
| Integration complexity underestimated | Medium | High | Early POC, spike stories | Tech Lead |
| Third-party system delays | Low | High | Identify early, escalation path | PM |
| [Add more] | | | | |

### 12.2 Dependencies

**Internal Dependencies:**
- [Dependency on other epics/teams]
- [Org configuration that must exist]
- [Resources that must be available]

**External Dependencies:**
- [Third-party system availability]
- [Vendor timelines]
- [External data sources]

**Blockers:**
- [Known blockers to starting]
- [Approvals required]
- [Infrastructure/licensing needed]

---

## 13. Non-Functional Requirements

### 13.1 Performance
- **Page Load:** [Target: <2 seconds]
- **API Response:** [Target: <500ms]
- **Batch Processing:** [Volume and time targets]

### 13.2 Scalability
- **User Concurrency:** [Number of concurrent users]
- **Data Volume:** [Projected growth over 2 years]
- **Governor Limits:** [Specific concerns and mitigation]

### 13.3 Availability & Support
- **Uptime Requirement:** [e.g., 99.5%]
- **Support Model:** [Who supports this post-launch]
- **Monitoring:** [What will be monitored]

---

## 14. Success Validation

### 14.1 Definition of Done (Epic Level)

**Functional Completeness:**
- [ ] All stories in all themes completed and accepted
- [ ] All acceptance criteria met
- [ ] UAT sign-off received

**Technical Quality:**
- [ ] Code coverage ≥85%
- [ ] No critical/high bugs open
- [ ] Security review passed
- [ ] Performance benchmarks met

**Deployment:**
- [ ] Successfully deployed to production
- [ ] Post-deployment verification complete
- [ ] Rollback plan tested

**Enablement:**
- [ ] Documentation complete
- [ ] Training delivered
- [ ] Support team trained

### 14.2 Success Metrics (Post-Launch)

*To be measured 30/60/90 days after launch*

| Metric | Target | Actual (30d) | Actual (60d) | Actual (90d) |
|--------|--------|--------------|--------------|--------------|
| [KPI 1] | [Target] | | | |
| [KPI 2] | [Target] | | | |
| User Adoption | [Target %] | | | |
| System Performance | [Target] | | | |

---

## 15. Approvals & Sign-Off

### 15.1 Review & Approval

| Role | Name | Approval Status | Date | Comments |
|------|------|-----------------|------|----------|
| Solution Architect | | ☐ Approved | | |
| Product Owner | | ☐ Approved | | |
| Tech Lead | | ☐ Approved | | |
| Security (if needed) | | ☐ Approved | | |
| [Other Stakeholder] | | ☐ Approved | | |

### 15.2 Open Questions
*Unresolved items that need answers before stories are created*

1. [Question 1] - **Owner:** [Name], **Due:** [Date]
2. [Question 2] - **Owner:** [Name], **Due:** [Date]

---

## 16. Appendices

### Appendix A: Glossary
| Term | Definition |
|------|------------|
| [Term 1] | [Definition] |
| [Term 2] | [Definition] |

### Appendix B: Reference Links
- Jira Epic: [Link]
- Related Epics: [Links]
- Design Mockups: [Link]
- API Documentation: [Link]
- Org Documentation: [Link]

### Appendix C: Meeting Notes
*Key decisions from solution design sessions*
- [Date]: [Summary of decisions]

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | [Date] | [Name] | Initial draft |
| 1.0 | [Date] | [Name] | Approved for story creation |
