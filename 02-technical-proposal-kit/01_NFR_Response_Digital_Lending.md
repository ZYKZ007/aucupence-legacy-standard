# Standard NFR Response – Digital Lending Platform (Reference)

This document provides a reusable NFR response structure for a cloud-hosted digital lending or credit-origination platform.

The intent is to present measurable, negotiable and defensible statements suitable for regulated procurement.

---

## 1. Performance & Scalability

Typical baseline targets used for early-stage proposals:

| Metric Area | Reference Target | Notes |
|:--|:--|:--|
| Core API latency | p95 < 300 ms, p99 < 800 ms | Measured at gateway excluding client network. |
| Peak throughput | 3–5x growth over 3 years, 8–10x seasonal peaks | Confirm via volume workshop. |
| Batch windows | Nightly jobs complete within agreed windows | Split by domain and data criticality. |

Reference design responses:

- Stateless business services deployed on a managed container platform.
- Horizontal autoscaling based on:
  - CPU/memory,
  - request rate per endpoint,
  - queue depth for asynchronous flows.
- Read/write separation where relational stores are used.
- Multi-level caching for hot paths:
  - session and token caches,
  - product/rules catalogs,
  - reference data.

Back-pressure patterns:

- Rate limiting and quotas at the gateway.
- Circuit breakers for unstable external dependencies.
- Graceful degradation for non-critical features to protect:
  - application submission,
  - decisioning,
  - repayment and ledger updates.

---

## 2. Availability & Resilience

Proposed tiered availability framing:

| Service Tier | Examples | Reference Availability |
|:--|:--|:--|
| Tier 0 | Decisioning, repayment, core onboarding | 99.95% monthly |
| Tier 1 | Loan servicing, customer profile | 99.9% monthly |
| Tier 2 | Reporting portals, non-critical exports | 99.5% monthly |

Reference practices:

- Multi-AZ deployment for all stateful components.
- Rolling updates with automated rollback conditions.
- Health-check standards for edge, service and data layers.
- Dependency resilience:
  - timeouts,
  - retries with jitter,
  - bulkheads for shared components.

---

## 3. Disaster Recovery

Proposal-level DR position:

- Primary region: multi-AZ high availability by default.
- Secondary region: optional based on criticality tier and budget.

Reference RTO/RPO bands:

| Data Criticality | RPO | RTO |
|:--|:--|:--|
| Regulatory-critical records | 5–15 minutes | 1–4 hours |
| Standard operational data | 15–60 minutes | 4–8 hours |
| Non-critical analytics | 24 hours | 24–48 hours |

RTO/RPO are confirmed during discovery based on:
- ledger and reconciliation requirements,
- regulator expectations,
- client’s enterprise DR standards.

---

## 4. Security & Compliance

Reference “proposal-safe” control statements:

- Central enterprise identity integration (OIDC/SAML).
- Least-privilege RBAC at:
  - application layer,
  - gateway,
  - data-access layer.
- Segregation of duties for:
  - production changes,
  - privileged access approvals.
- Encryption:
  - at rest using cloud-native key management,
  - in transit using modern TLS standards.
- Secure SDLC:
  - SAST for critical codebases,
  - dependency and container scanning,
  - DAST for high-risk journeys before major releases.

---

## 5. Auditability & Logging

Banks and regulators typically require:

- Traceable end-to-end request reconstruction.
- Immutable audit events for:
  - pricing and limit changes,
  - approval decisions,
  - repayment and write-off actions.
- Config and admin operation logs capturing:
  - who,
  - what,
  - when,
  - associated approval references.

Retention is aligned to local policy and client standards with:
- role-based access,
- reporting on privileged log reads,
- tamper-evident storage for critical audit streams.

---

## 6. Operability & Day-2 Readiness

Reference operational commitments:

- Service dashboards for:
  - technical SLOs,
  - business KPIs (approval rate, time-to-yes, delinquency signals).
- Runbooks for:
  - dependency outages,
  - throttling events,
  - data reconciliation exceptions.
- On-call and incident management aligned to severity definition tables.
- Release readiness checks that include:
  - performance smoke baselines,
  - security scan summaries,
  - rollback rehearsal outcomes where applicable.

