# Environment and Release Strategy – Reference Model

This document describes how we structure environments, promotion flows and release strategy for a regulated client.

---

## 1. Environment Stack

Typical environment stack:

1. Local dev
2. Integration (shared)
3. System test (ST)
4. UAT / Pre-production
5. Production

Key rules:

- Configuration is stored as code; environment differences are handled via configuration, not manual tweaks.
- Access rights become progressively stricter towards production.
- Data usage is controlled; only anonymised or synthetic data in non-production.

---

## 2. Promotion Flow

We define a strict promotion flow:

- Feature branches → Pull Request → Merge into `develop` or `main`.
- Automated pipeline runs:
  - Static analysis
  - Unit tests
  - Integration tests (where feasible)
- Artifacts (Docker images, Helm charts) are versioned and pushed to a registry.

Promotion sequence:

1. Deploy to Integration:
   - Verify that services work end-to-end with other systems.
   - Run regression pack.

2. Deploy to System Test:
   - Run full regression, performance and security scans.
   - Only tagged builds that passed Integration are allowed.

3. Deploy to UAT:
   - Triggered only after sign-off in System Test.
   - Used by business users and client testers.

4. Deploy to Production:
   - Manual approval by Change Advisory Board (CAB) or equivalent.
   - Rollback plan documented.

Each environment has its own pipeline stage with clear inputs and outputs.

---

## 3. Release Cadence

We propose the release cadence based on business and risk appetite:

- Standard: 2-week sprints, production release every 4 weeks.
- Alternative: more frequent releases (for example every 2 weeks) once platform stabilises and automated tests are mature.

For each cadence we define:

- Cut-off dates for scope inclusion.
- Freeze periods before critical dates (for example year-end, regulatory milestones).
- Rules for hotfixes.

Example:

- Sprint 1–2: build and stabilise features in lower environments.
- End of Sprint 2: release candidate prepared for UAT.
- Start of Sprint 3: production deployment if UAT sign-off is obtained.

---

## 4. Change Types

We distinguish change types:

- Standard changes:
  - Pre-approved patterns (for example routine patch, small config change).
  - Short lead time; can be executed within agreed windows.

- Normal changes:
  - Go through CAB review.
  - Require risk assessment and rollback plan.

- Emergency changes:
  - Used for Sev-1 incidents.
  - Post-implementation review mandatory.

These categories are reflected in both technical pipelines and governance documents.

