# Salesforce Estimation — Categories & Trigger Questions

A quick-reference card for sprint refinement. Use these to surface hidden complexity before committing to an estimate.

---

## 🔧 Complexity

- **Architecture**
  - New architectural patterns needed (async, platform events, streaming API)?
  - How many objects, components, or external systems are touched?
  - Governor limit exposure — SOQL, DML, CPU, heap?
- **Code**
  - How branchy or rule-heavy is the business logic?
  - Mostly net-new code, or modifying existing Apex / Flow / LWC?
  - Risk of regressions in existing automations?
- **Data**
  - Complex data transformations or field mappings?
  - Edge cases to handle (nulls, bulk ops, mixed DML)?
- **Unknowns**
  - Any unknown platform behaviours or undocumented Salesforce limits?

---

## 🔗 Dependencies

- **Team**
  - Waiting on another team before dev can start?
  - Are the dependencies already done, or still in flight?
- **Stakeholders**
  - Stakeholder sign-off required before development begins?
  - Security, compliance, or Salesforce security review in scope?
- **Technical**
  - Schema changes needed (new objects, fields, relationships)?
  - Third-party integrations or AppExchange packages involved?
- **Sequencing**
  - Does this block — or get blocked by — another story in the sprint?
  - Sequential steps, or can work run in parallel?

---

## ⚠️ Risk

- **Requirements**
  - Are the requirements fully defined (AC, mockups, data model)?
  - Sufficient documentation and accessible SMEs?
  - Scope creep likely during the sprint?
- **Technical**
  - Realistic chance of significant rework once dev starts?
  - Data migration, CPQ config, or backward-compatibility concerns?
  - Does the team have the right Salesforce domain knowledge?
- **Business**
  - How business-critical is this (revenue, compliance, user-facing)?
  - Impact if this slips a release?

---

## 🧪 Testing

- **Automated**
  - Apex test coverage target — and how hard to reach it?
  - Integration tests needed (callouts, platform events, external systems)?
  - End-to-end or UI testing required (Jest, manual flows)?
  - Callout mocking needed?
- **Non-Functional**
  - Bulk or performance testing needed?
  - Security model validation (FLS, CRUD, sharing rules)?
- **Manual**
  - Complex test data setup (record hierarchy, CPQ quotes)?
  - How many scenarios across profiles, record types, or orgs?
  - Sandbox regression required before deploying?

---

## 📐 Scope

- **Stories**
  - How many stories or sub-tasks are bundled in?
  - Multiple personas, profiles, or record types to support?
  - Anything that could be deferred to a follow-up story?
- **Config**
  - Declarative config volume (flows, validation rules, assignment rules)?
  - How many Lightning pages or components are affected?
  - Reports, dashboards, or list views required?
  - Permission set updates or package version changes?
- **Delivery**
  - Deployment runbook or technical docs needed?

---

## 🤝 Collaboration

- **Team**
  - How many people need to contribute (admin, dev, BA, architect)?
  - Specialist skills needed (CPQ, Experience Cloud, Marketing Cloud)?
  - UX / design involvement for Lightning pages or components?
- **Stakeholders**
  - Product Owner needed throughout, or just at review?
  - Release manager coordination for deployments?
- **Communication**
  - How many syncs, demos, or reviews are expected?
  - Heavy async communication anticipated (Slack, status updates)?
