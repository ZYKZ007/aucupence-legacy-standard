# Data and Integration Reference – Proposal Baseline

This document provides a reusable data and integration narrative suitable for digital banking and lending tenders.

---

## 1. Data Domains

Typical domain groups:

- Customer and consent
- Product and pricing
- Application and decisioning
- Repayment and servicing
- Collections and recovery
- Audit and policy events

---

## 2. Data Quality and Reconciliation

Reference practices:

- Early profiling during discovery.
- Source-to-target mapping for migration scope.
- Sample-based reconciliation and exception reporting.

---

## 3. Audit Event Model

Proposal-ready commitments:

- Domain events for critical actions.
- Immutable storage option for regulator-grade trails.
- Controlled access with traceable reads.

---

## 4. Integration Assumptions Register

A proposal should include:

- External system ownership and SLA boundaries.
- Sandbox readiness and change notice periods.
- Test data availability commitments.
- Clear rules for handling upstream instability.

---

## 5. Reporting and Analytics

- Operational reporting separated from OLTP to protect performance.
- Tiered reporting latency options:
  - near real-time where required,
  - batch for lower priority domains.

