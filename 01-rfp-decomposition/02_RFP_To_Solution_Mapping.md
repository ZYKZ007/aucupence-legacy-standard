# RFP to Solution Mapping – Banking / Payments

This document shows how we translate a typical banking RFP into concrete solution, delivery and commercial elements. It is used in presales to avoid “copy-paste answers” and instead give a traceable mapping from requirement to design.

---

## 1. From RFP Sections to Workstreams

A typical retail / SME banking RFP is structured into the following sections:

- Business and functional requirements
- Non-functional requirements (NFRs)
- Regulatory and compliance
- Delivery and governance
- Commercial and contractual

We map them into internal workstreams:

| RFP Section                       | Internal Workstream                          | Primary Owner         | Key Artefacts                                       |
|:----------------------------------|:---------------------------------------------|:----------------------|:----------------------------------------------------|
| Business & Functional             | Product / Functional Design                  | Product Lead          | Domain model, use-case catalogue, user journeys     |
| Non-functional Requirements       | Architecture & NFR                           | Solution Architect    | NFR response, reference architecture, capacity plan |
| Regulatory & Compliance           | Risk & Compliance                            | Compliance SME        | Compliance matrix, control mapping                  |
| Delivery & Governance             | Delivery Governance                          | Program Manager       | Governance model, RACI, RAID log                    |
| Commercial & Contractual          | Commercial & Legal                           | Engagement Director   | Estimation model, rate card, assumptions register   |

This mapping drives who writes which sections and where decisions need to be escalated.

---

## 2. Requirement Traceability Model

We maintain a simple traceability chain:

RFP Requirement → Internal Requirement → Design Decision → Artefact / Test

Example:

- RFP: “System must support 24/7 availability with no more than 15 minutes of unplanned downtime per quarter.”
- Internal Requirement: “Target availability SLO: 99.95% for core APIs.”
- Design Decision: “Multi-AZ deployment, stateless services, active-active DB replicas.”
- Artefacts:
  - NFR Response: explicit 99.95% target and design justification.
  - Architecture Diagram: AZ layout, failover flows.
  - Test Plan: chaos tests and failover tests defined.

We use this chain to demonstrate to risk/compliance teams that each critical requirement is backed by a concrete design and test.

---

## 3. Example Mapping Table (Excerpt)

| RFP Ref | Text (Simplified)                                           | Internal Requirement ID | Design Response (Short)                                                                                 | Artefacts                                            |
|:--------|:------------------------------------------------------------|:------------------------|:--------------------------------------------------------------------------------------------------------|:-----------------------------------------------------|
| NFR-07  | 95% of core APIs < 300 ms, 99% < 800 ms                     | NFR-PERF-01             | Horizontal scaling via EKS, Redis cache, read replicas. Rate limiting and graceful degradation in place.| 01_NFR_Response_Digital_Lending.md §1; arch diagrams |
| SEC-03  | All data encrypted at rest and in transit                   | NFR-SEC-02              | KMS-managed keys on all storage; TLS 1.2+ for all connections; mTLS for sensitive internal services.    | NFR sec section; infra Terraform KMS definitions     |
| REG-10  | Ability to provide full audit trail for admin configuration | NFR-AUDIT-04            | Central audit log with admin actions, correlation IDs and retention ≥ 7 years.                         | Audit section; log schema; runbook for audit export  |
| DEL-02  | Clear escalation and issue resolution procedures            | GOV-ESC-01              | 3-layer governance model with escalation paths and SLA-based incident management.                       | Governance model; incident handbook                  |
| COM-05  | Transparent breakdown of fees and basis for estimation      | COM-EST-01              | Decomposed estimation, role mix, risk contingency and change budget described.                          | Estimation model; commercial Q&A library             |

The goal is to show that we are not answering the RFP in isolation; we plug each requirement into our existing delivery and architecture playbooks.

---

## 4. Control Mapping for Regulators

For regulated clients, we often need to map our controls to external frameworks (for example EBA, MAS, local central bank guidelines).

We maintain:

- A list of external control IDs (for example EBA-ICT-01, MAS-OB-03).
- A mapping to our internal control library (for example “AC-01: IAM”, “BC-02: DR tests”).
- A short narrative on how we implement each control in the specific engagement.

Typical structure:

- Control: “Critical systems must have tested disaster recovery plans and meet agreed RTO / RPO.”
- Implementation:
  - Multi-region DR with asynchronous replication.
  - Documented DR plan with named roles.
  - Annual DR test with documented results and remediation actions.

This mapping can be attached as an annex in proposals or shared later during due diligence.

