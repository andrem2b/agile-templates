# 🧩 Solutioning Strategy Template

This template is used during pre-sprint scoping to clarify the technical direction of a user story and support accurate T-shirt sizing and story point estimation. It enables collaboration between the architect and senior developers (feature owners) and supports visibility during team planning.

| **Field** | **Guidance & Examples** |
|-----------|-------------------------|
| **Suggested T-Shirt Size** | **XS** - Config/toggle change only<br>**S** - Single component, no data model impact<br>**M** - Multiple components OR data model changes<br>**L** - Multiple components AND data model changes OR complex integration<br>**XL** - Major refactoring, multiple integrations, or architectural changes |
| **Technical Reviewer** | Senior dev responsible for review & estimation |
| **Frontend Impact** | What UI changes are needed?<br>*Examples: New LWC components, HTML updates, component reuse, style changes* |
| **Backend Impact** | What server-side changes are required?<br>*Examples: Apex classes, triggers, services, refactoring, new objects, fields, relationships, schema impacts* |
| **Integration Needs** | Any API calls, external services, platform events, etc.?<br>*Examples: REST APIs, webhooks, third-party systems, platform events* |
| **Testing Requirements** | Unit tests, LWC tests, data setup, or specific QA environments required?<br>*Examples: Jest tests, Apex test classes, integration tests, test data setup* |
| **Environments Affected** | Sandboxes, Experience Cloud, managed packages, external systems?<br>*Examples: Dev/QA/UAT sandboxes, production, Experience Cloud sites* |
| **Feature Flags / Configs** | Will this require toggles or config-driven logic?<br>*Examples: Custom settings, custom metadata, feature toggles for phased release* |
| **Dependencies** | Blocked by/influences other tickets? Any sequencing constraints?<br>*Examples: Dependent stories, team dependencies, data migration prerequisites* |
| **Security & Compliance** | Any security, privacy, or compliance concerns?<br>*Examples: PII handling, sharing rules, field-level security, audit requirements* |
| **Assumptions & Constraints** | Known trade-offs or limitations? Anything still under discovery?<br>*Examples: Performance constraints, technical debt, open questions* |
