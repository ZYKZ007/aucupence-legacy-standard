# Case Retrospective – Digital Lending Modernization Program (Abstracted)

This document is an anonymized retrospective summarizing how a lending platform modernization program was structured and delivered. It is not a full playbook – it illustrates how we run complex programs and where architectural and delivery decisions matter.

---

## 1. Context (Redacted but Realistic)

- Region: Asia (regulation-heavy market)
- Scope: Replace legacy loan origination workflow + onboarding + repayment ledger
- Duration: 10+ months initial rollout, then ongoing evolution
- Scale:
  - ~12 microservices
  - 3 external integrations (core banking, KYC, scoring)
  - Peak load simulated 800–1200 TPS during campaign season

## 2. Why It Was Hard

- Legacy system had tight coupling → migration needed **strangler pattern**, not big bang
- KYC API unstable early stage → latency spikes + sandbox downtime
- Data model inconsistencies → reconciliation errors first migration run
- Procurement wanted fixed price, business wanted moving requirements

Not academic — real trade-offs.

## 3. Our Delivery Structure

Phases:

| Phase | Duration | Main Output |
|---|---|---|
| Discovery | 6 weeks | backlog, NFR baseline, architecture options A/B/C |
| Build Waves | 2-week sprints | lending flows, integration, risk engine adapters |
| UAT & Hardening | 8 weeks | performance tuning, failover test, audit pack |
| Rollout | staged | feature flags + controlled cohort release |

Artifacts used (not public):

- Architecture spike notes
- Migration runbook v1→v2
- Performance benchmark scripts
- DR failover checklist

**We show here only the structure, not full playbooks.**

## 4. Key Decisions & Trade-offs

Decision example:

- Option A: sync writes to core banking → strong consistency, slower
- Option B: async via event streams → faster, requires reconciliation

We chose B with mitigation:

- async event store + periodic ledger consistency job
- dashboards monitoring drift
- business-approved thresholds for exception queue

This is where enterprise architects ask hard questions.
We handled them with measurable reasoning, not slogans.

## 5. Failure Lessons (Kept High-Level Intentionally)

- First load test failed — DB saturation at 220ms p95 due to missing index
- Fix: column index + Redis tagging for high-frequency reads  
  → dropped to 140ms p95 within 48h
- STRONG POINT: we track p95/p99 rather than average latency

Another one:

- Batch scoring job overlapped with ledger posting → contention
- Mitigation: moved scoring to off-peak via event schedule + autoscaling

This is the kind of story people believe，因为细节不虚。

## 6. Rollout & Controls

Production launch used:

- Feature flags (off unless user is pilot cohort)
- Blue-green pattern for the onboarding API
- Rollback window 30 minutes, success criteria pre-defined

Post-launch:

- 4-week hypercare
- 27 defects → 0 critical, 3 high, 24 medium/low
- Deployment frequency: weekly → twice weekly after month 2

Outcome (abstracted):

- Avg onboarding time -38%
- Approval decision time from minutes → sub-second
- Customer complaints significantly reduced (data removed)

---

## What We Do *Not* Publish

- Terraform IaC modules
- Internal migration scripts
- Real rate cards + margin logic
- Full playbook + checklists
- Detailed architecture repos

This case proves we run real programs,  
but we keep the implementation premium inside engagement.

