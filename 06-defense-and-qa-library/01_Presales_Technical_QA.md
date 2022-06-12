# Presales Technical Q&A – Standard Library

A concise but enterprise-aligned Q&A set used in presales workshops and technical evaluations for digital banking, lending and payments programs.

---

## 1. Scalability & Performance

**Q1. How will the platform handle sudden peak volumes?**  
A1. We design for horizontal scale with stateless services, autoscaling guardrails and capacity baselines agreed in advance. Non-critical features can degrade gracefully to protect core journeys.

**Q2. What latency targets do you propose for core APIs?**  
A2. We typically frame p95/p99 targets by service tier and validate assumptions against integration topology and client network constraints during discovery.

**Q3. How do you prevent database bottlenecks?**  
A3. We use read/write separation, connection pooling, caching for hot paths and event-driven offloading for high-volume non-blocking flows.

---

## 2. Integration

**Q4. How do you deal with unstable third-party APIs?**  
A4. We isolate external dependencies through adapters, apply circuit breakers and define contract-test and versioning expectations early.

**Q5. How do you integrate with core banking without slowing delivery?**  
A5. We separate integration discovery from feature build, establish sandboxes and agree mock/stub strategies to protect sprint predictability.

---

## 3. Security & Access

**Q6. How do you control privileged access to production?**  
A6. Production access is restricted to a small, named group under least privilege, with MFA, session logging and time-bound approvals.

**Q7. How do offshore teams work without touching sensitive data?**  
A7. Offshore work is limited to lower environments with anonymized data. For stricter clients, VDI and copy/paste/file-transfer restrictions are used.

---

## 4. Availability & DR

**Q8. What HA pattern do you recommend as a default?**  
A8. Multi-AZ for primary region core services. Cross-region DR is positioned as a negotiable resilience tier tied to business criticality.

**Q9. How do you validate RTO/RPO claims?**  
A9. We propose joint DR drills with evidence packs and a test calendar included in governance cadence.

---

## 5. Operability

**Q10. What signals prove Day-2 readiness?**  
A10. Runbooks, on-call model, automated rollback, clear SLOs and dashboards for both technical and business KPIs.

**Q11. How do you prevent “hero-driven operations”?**  
A11. We enforce documentation-driven delivery and require operational artefacts as part of Definition of Done for key releases.

