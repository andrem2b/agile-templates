# Low-Level Design (LLD) — [User Story / Feature Name]

**Purpose:** Per-feature design for the implementer. Defines layers (Controller → Service → Data Access), components, and clean-code rules. Use for stories that involve Apex/LWC or non-trivial configuration.

**Short-term value:** Developer knows exactly what to build and where; reviewer can check against the same spec. Reduces “where does this logic go?” debates.

**Parent:** User Story / Task [Jira link] · HLD [link if exists]

---

## 1. Metadata [Optional]

**What to put here:** Story/task link and related docs for traceability.

| Field | Value |
|-------|--------|
| User Story / Task | [Jira link] |
| Version | 1.0 |
| Date | |
| Author | |
| Status | Draft / In Review / Approved |
| Related | HLD: [link] · ADR: [link if applicable] |

---

## 2. Requirement Snapshot

**What to put here:** One-sentence goal and acceptance criteria from the User Story. So the LLD stays aligned with “done.”

**Triggering questions:** What’s the user story or task in one sentence? What are the 3–5 acceptance criteria?

### 2.1 User Story / Goal (One Sentence)

[As a … I need … so that …] or equivalent.

### 2.2 Acceptance Criteria (Bullets)

- Criterion 1
- Criterion 2
- Criterion 3

---

## 3. Layered Design (Enforced)

**What to put here:** Which layer each component belongs to and what each layer must / must not do. Keeps logic out of triggers and LWC controllers.

**Rule:** UI/Trigger → **Controller** → **Service** → **Data Access**. No business logic in triggers or LWC controllers beyond delegation.

### 3.1 Layer Responsibilities

| Layer | Responsibility | Do not put here |
|-------|----------------|-----------------|
| **Trigger** | Delegate to handler; no logic. | Business rules, SOQL, DML |
| **Controller (Apex)** | Parse request, validate input, call Service, return response. | Business logic, SOQL (except simple lookups if team agrees) |
| **LWC JS** | Call Apex, handle UI state, client-side validation. | Business logic, direct DML/SOQL |
| **Service** | Orchestrate business logic, call Data Access, enforce rules. | SOQL/DML (delegate to Data Access) |
| **Data Access** | SOQL, DML, shared query logic. Single place per object/aggregate. | Business rules |

### 3.2 Component Map

**What to put here:** Every class, trigger, and LWC for this feature; type, layer, and one-line purpose. Triggering questions: What’s the trigger? Handler? Service? Repository? LWC and its Apex controller?

| Component | Type | Layer | Purpose |
|-----------|------|--------|---------|
| [e.g. AccountTrigger] | Trigger | Entry | Delegate to AccountTriggerHandler |
| [e.g. AccountTriggerHandler] | Apex | Controller (trigger side) | Route by event, call Service |
| [e.g. AccountService] | Apex | Service | Create/update account logic, validations |
| [e.g. AccountRepository] | Apex | Data Access | getById, listByX, save(Account) |
| [e.g. MyComponentController] | Apex | Controller (LWC) | Entry for LWC, call Service |
| [e.g. myComponent] | LWC | UI | Wire to controller, display, events |

---

## 4. Class / Component Specifications

**What to put here:** For each Apex class (and LWC controller if non-trivial): purpose, main methods (name, in/out, responsibility), dependencies, and governor/bulk context. No full code — just enough to implement and test.

**Triggering questions:** What does each class do? What are the main entry points? Does it run in trigger context (bulk) or from LWC (single record)? What does it call?

### 4.1 [ClassName] — [Layer]

**Purpose:** [One sentence.]

**Key methods:**

| Method | Input | Output | Responsibility |
|--------|--------|--------|----------------|
| [methodName] | [params] | [return] | [What it does] |

**Dependencies:** [Other services/repos it calls.]  
**Governor limits / bulk:** [e.g. “Runs in trigger context; must handle 200 records.”]

### 4.2 [Next Class]

[Same structure.]

---

## 5. Data Access (Repository Pattern)

**What to put here:** Which objects are read/written, by which operations (e.g. getById, save), and rules: no SOQL/DML in loops; one repository per object; FLS/CRUD approach.

**Triggering questions:** Where do we query each object? Where do we insert/update/delete? Are we bulk-safe? Do we enforce FLS?

### 5.1 Objects & Queries

| Object | Operations | Notes (indexes, bulk) |
|--------|------------|------------------------|
| Account | getById, listByX, save | Use selective filters |
| [Custom__c] | getByAccountId, save | Avoid in loop; pass list to Service |

### 5.2 SOQL / DML Rules

- No SOQL/DML inside loops.
- One repository (or clear ownership) per object/aggregate.
- FLS/CRUD: use `Security.stripInaccessible` or enforce via sharing; document where FLS is bypassed and why.

---

## 6. Error Handling & Validation [Optional]

**What to put here:** Where validations run (Service layer), how errors reach the user (return DTO vs exception, LWC message), and how we log (debug, custom object, etc.).

**Triggering questions:** Where do we validate? How does the UI show errors? Do we log for support?

- Validations: Service layer (reusable).
- Errors: return DTO with success/errors or throw; LWC shows user-friendly message.
- Logging: [e.g. custom log object, debug log.]

---

## 7. Testing Strategy [Optional]

**What to put here:** What we unit test (Service, Data Access), trigger test approach (handler, bulk), and LWC tests (Jest, Apex controller if needed). Target 80%+ for Apex.

**Triggering questions:** Which classes need unit tests? Do we test trigger with 200 records? Any LWC Jest tests?

- Unit tests: Service and Data Access; target 80%+ Apex coverage.
- Trigger tests: Via handler; test bulk (e.g. 200 records).
- LWC: Jest for JS; Apex test for controller if logic is non-trivial.

---

## 8. Clean Code Checklist

**What to put here:** Quick checklist for implementer and reviewer. All items should be satisfied before “done.”

**Triggering questions:** Are names clear? Is logic in the right layer? Bulk-safe? FLS considered? Any hard-coded IDs?

- [ ] Meaningful names (classes, methods, variables).
- [ ] Single responsibility per class/method.
- [ ] No business logic in trigger or LWC controller.
- [ ] Bulk-safe (no SOQL/DML in loops).
- [ ] FLS/CRUD considered; sharing respected.
- [ ] No hard-coded IDs; use Custom Metadata / Custom Settings / Named Credentials where needed.

---

## 9. Dependencies & Order of Implementation [Optional]

**What to put here:** Build order (Data Access → Service → Controller/Trigger/LWC) and any external dependency (e.g. HLD for callouts).

**Triggering questions:** What must be built first? Any integration details in HLD?

- Implement in order: Data Access → Service → Controller/Trigger/LWC.
- External: [e.g. HLD section 5 for callout details.]

---

## Document History [Optional]

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | | | Initial |
