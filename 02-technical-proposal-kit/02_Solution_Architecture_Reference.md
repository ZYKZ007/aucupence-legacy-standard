# Solution Architecture Reference – Proposal Baseline (Deep)

This document provides a reusable, multi-view structure for describing a cloud-hosted digital platform architecture in proposals without disclosing client-specific assets.

It is intended to be used together with:
- 02_Solution_Overview_Architecture_Notes.md
- 01_NFR_Response_Digital_Lending.md
- 03_Cloud_and_DevSecOps_Baseline.md
- 04_Data_and_Integration_Reference.md
- diagrams/architecture-high-level.svg
- diagrams/architecture-runtime-flows.svg

---

## 1. Architecture Objectives

- Satisfy regulated-client audit, security and operational expectations.
- Enable horizontal scaling for transaction-heavy workloads.
- Maintain modularity for phased delivery and partial-scope awards.
- Reduce delivery and integration risk through explicit assumptions and constraints.
- Avoid hard vendor lock-in by choosing standard interface patterns and IaC discipline.

---

## 2. Reference Deployment Model

- Containerized services deployed on a managed Kubernetes platform.
- Edge controls fronted by:
  - WAF,
  - API gateway,
  - identity integration,
  - rate limiting and threat rules.
- Stateful components hosted via managed services.
- Centralized observability for logs, metrics and traces.
- CI/CD pipelines with automated quality and security gates.

This model is compatible with major cloud providers; concrete services are confirmed during solution workshops.

---

## 3. Logical Component Groups

### 3.1 Edge and Access

- WAF and threat rules aligned to common abuse patterns.
- API gateway policy enforcement:
  - authentication,
  - quotas,
  - request validation,
  - schema and contract checks where required.
- Identity provider integration supporting:
  - workforce users,
  - external customer identities,
  - delegated access for partner channels.

### 3.2 Business Services

Domain-aligned capabilities typically include:

- onboarding and identity verification orchestration,
- loan origination and product configuration,
- decisioning and rules,
- pricing and limit management,
- repayment and ledger-adjacent flows,
- collections and servicing,
- customer profile and consent management.

Granularity is governed by:
- domain ownership,
- change frequency,
- regulatory boundaries,
- deployment independence needs.

### 3.3 Data and Event Services

- Transactional stores for authoritative records.
- Event and audit streams for regulator-grade traceability.
- Reporting marts designed to avoid operational-store overload.
- Data-quality monitoring for migration and reconciliation.

### 3.4 Platform Services

- caching for hot-path optimisation,
- messaging/event backbone,
- configuration and secrets management,
- feature flagging and safe rollout controls.

---

## 4. Integration Architecture

Reference integration patterns:

- Synchronous APIs for interactive customer journeys.
- Asynchronous events for:
  - audit trails,
  - notifications,
  - ledger updates,
  - non-blocking enrichment.
- Adapter layers for external dependencies with clear ownership of:
  - versioning,
  - retry semantics,
  - fallbacks.

A proposal should include an “integration readiness assumptions” list covering:
- sandbox availability,
- test data access,
- change notice periods,
- client-owned interface SLAs.

---

## 5. Scalability and Performance Strategy

- Stateless-first service design.
- Capacity envelopes derived from:
  - baseline daily volumes,
  - peak multipliers,
  - growth outlook.
- Read/write separation and caching.
- Queue-based buffering for bursty workloads.
- Controlled degradation for non-critical features.

Performance commitments remain conditional on:
- dependency SLAs,
- data volumes,
- encryption and audit overhead requirements.

---

## 6. Security-by-Design

Proposal-safe security commitments:

- Least-privilege RBAC and MFA for privileged roles.
- Segregated environments with production access under client approval.
- Secure SDLC gates integrated into build pipelines.
- Evidence-ready artifacts:
  - scan summaries,
  - remediation logs,
  - release approvals.

Where formal certifications are required, the proposal positions:
- compensating control narratives,
- certification roadmap milestones,
- scope statements aligned to delivery locations.

---

## 7. Resilience and DR

- Multi-AZ baseline for core services.
- Optional secondary-region models:
  - warm standby,
  - pilot light,
  - active-active for highest criticality.

DR detail is aligned to:
- data criticality tiers,
- regulatory retention and recovery standards,
- client enterprise DR policy.

---

## 8. Architecture Governance

- ADR-style logging for major decisions.
- Design authority cadence tied to sprint and release cycles.
- Definition of Done including:
  - security readiness,
  - test readiness,
  - observability minimums.

