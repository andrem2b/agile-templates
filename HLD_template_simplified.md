# High-Level Design (HLD) — Salesforce [Epic / Feature Name]

**Purpose:** High-level technical picture so the dev team can implement consistently. Describes components, data, integration, automation, and security. No class names or field lists — those go in LLD.

**Short-term value:** Dev and technical client see “how it fits together” in one place; fewer surprises and rework. Use only when the epic spans multiple stories or touches integration/security.

**Parent:** Solution Brief / Epic [link]

---

## 1. Metadata [Optional]

**What to put here:** Doc identity and links for traceability.

**Triggering questions:** Which Epic/feature is this? Where is the Solution Brief? Which LLDs will implement this?

| Field | Value |
|-------|--------|
| Epic / Feature | [Jira link] |
| Version | 1.0 |
| Date | |
| Author | |
| Status | Draft / In Review / Approved |
| Related | Solution Brief: [link] · LLDs: [links] · ADRs: [links] |

---

## 2. Scope of This HLD

**What to put here:** What this HLD describes (epic or feature area). Clarifies that code details belong in LLD and business case in Solution Brief.

**Triggering questions:** What’s the boundary of this design? What are we explicitly not detailing here?

**In scope:** [Epic name or feature area.]  
**Out of scope:** Detailed code (→ LLD), business case (→ Solution Brief).

---

## 3. Architecture Summary

**What to put here:** Main building blocks, Salesforce’s role vs other systems, and the most important technical decisions. Enough for a dev to understand “where things live.”

**Triggering questions:** What are the main technical pieces? Is Salesforce the source of truth for this data or just a consumer? What were the 2–3 biggest technical choices?

### 3.1 What We’re Building (Technical View)

1–2 short paragraphs. Optional: simple diagram (boxes and arrows for systems and main flows).

### 3.2 Key Architectural Decisions

**What to put here:** Decisions that affect how we build (e.g. Flow vs Apex, integration pattern). Each should have an ADR if it’s significant.

| Decision | Summary | ADR |
|----------|---------|-----|
| [e.g. Flow vs Apex for X] | [One line] | [Link] |
| [e.g. Integration pattern for Y] | [One line] | [Link] |

---

## 4. Data (High Level)

**What to put here:** Which objects are involved, who owns the data, and main data flows. No full field lists — those go in LLD.

**Triggering questions:** Which standard/custom objects? Where is data mastered (Salesforce vs external)? Any high volume or batch/async implications?

### 4.1 Objects Involved

- **Standard:** How they’re used (e.g. “Account is parent for CustomObject__c”).
- **Custom:** Name, purpose, key relationships (master-detail/lookup). No field list.

### 4.2 Data Ownership & Flows

- Where data is mastered.
- Main flows (e.g. “Account/Contact from ERP nightly; Orders from Salesforce to ERP”).

### 4.3 Volumes & Limits (If Relevant) [Optional]

- High-volume objects; batch/async implications.

---

## 5. Integration (High Level)

**What to put here:** Systems we integrate with, using **Salesforce pattern names**: Request-Reply, Fire-and-Forget, Event-Driven, Batch Data Synchronization. Direction, frequency, and where errors are handled.

**Triggering questions:** Which systems? What data in which direction? Real-time or batch? Who retries on failure?

| System | Purpose | Pattern | Direction | Notes |
|--------|---------|---------|-----------|-------|
| [Name] | [What data / why] | [Pattern] | In/Out/Both | [Frequency, auth] |

- Error handling and retries: where they happen (Salesforce vs middleware).

---

## 6. Automation Strategy

**What to put here:** When we use Flow vs Apex (trigger, batch, queueable, platform events), and the trigger approach (one per object, logic in handler). Enough for dev to choose the right tool.

**Triggering questions:** Which processes are record-triggered? Which need bulk or reuse (→ Apex)? Which are async (batch, queueable, events)?

### 6.1 When to Use What

| Tool | Use for |
|------|---------|
| Validation Rules | Field validation, required fields |
| Flow | Record-triggered, screen flows, simple logic |
| Apex Trigger | Complex logic, bulk, reuse from multiple entry points |
| Batch / Queueable | Large volume, async, callouts |
| Platform Events | Decoupled, async, cross-object |

### 6.2 Trigger Approach

- One trigger per object; logic in handler/service (details in LLD).
- Bulkification and order of execution: state as principles.

### 6.3 Key Processes (Summary)

| Process | Trigger | Tool | Brief description |
|---------|---------|------|-------------------|
| [Name] | [What starts it] | Flow / Trigger / Batch | [What it does] |

---

## 7. Security (High Level)

**What to put here:** Org/session (SSO, MFA if relevant), data access (OWD, roles, permission sets), and any sensitive data (encryption, compliance). Details stay in LLD where needed.

**Triggering questions:** How do users log in? How is record/field access controlled? Any encryption or compliance requirements?

### 7.1 Org & Session [Optional]

- SSO/MFA; session policies (if any).

### 7.2 Data Access

- Sharing (OWD) for key objects; roles, permission sets, sharing rules (summary).
- FLS/CRUD: “Enforced in code and via profiles/permission sets” (details in LLD).

### 7.3 Sensitive Data [Optional]

- Encryption, compliance (Platform Encryption, TLS, etc.), if applicable.

---

## 8. UI / Experience (Summary) [Optional]

**What to put here:** Lightning vs Classic, main record pages, custom LWC (name and purpose only). Mobile/Experience Cloud if relevant.

**Triggering questions:** Where will users see this? Any custom components or pages?

- Lightning vs Classic; key pages; custom LWC (names and purpose).
- Mobile / Experience Cloud if relevant.

---

## 9. Non-Functional (Summary) [Optional]

**What to put here:** Performance (governor limits, bulk, async), and what we monitor or log. Deep detail in LLD.

**Triggering questions:** Any governor limit risks? How do we know if something breaks?

- Performance: bulk, async, no SOQL in loops (“see LLD”).
- Monitoring / logging: e.g. debug logs, integration logs, custom log object.

---

## 10. ADR Index [Optional]

**What to put here:** Links to ADRs that document decisions referenced in this HLD.

| ADR | Decision | Link |
|-----|----------|------|
| | | |

---

## 11. Risks & Assumptions [Optional]

**What to put here:** Technical risks and mitigations; assumptions the design relies on.

**Triggering questions:** What could go wrong (limits, integration, data)? What are we assuming (external systems, team skills, timeline)?

| Risk | Mitigation |
|------|------------|
| [e.g. Governor limits] | [e.g. Batch, bulkification] |

**Assumptions:** [3–5 bullets.]

---

## HLD Definition of Done

- [ ] Sections 3–9 filled with enough guidance for dev to implement.
- [ ] Integration patterns use Salesforce taxonomy.
- [ ] Security covers org/session/data at high level.
- [ ] Major decisions linked to ADRs.

**HLD does not include:** Class diagrams, method signatures, full field lists (→ LLD).

---

## Document History [Optional]

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | | | Initial |
