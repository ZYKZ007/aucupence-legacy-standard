# Presales Technical Q&A – Standard Library

These Q&A items are used when technical stakeholders challenge the proposed architecture or delivery model. The goal is to answer in a way that is concrete, testable and consistent with the reference architectures in this repository.

---

## 1. Scalability and Peak Load

Question: How will the system behave if our volumes double or we have a peak like Black Friday?

Answer:  
We design for horizontal scalability by default. Stateless services are containerised and deployed on an orchestrated platform. We scale out based on live metrics such as requests per second, queue depth and CPU/memory utilisation.

For predictable seasonal peaks we agree capacity plans in advance. For unexpected peaks, rate limiting and graceful degradation ensure that critical journeys (for example application submission, payment execution) remain available, while non-critical features can be temporarily slowed down or disabled.

---

## 2. Data Residency and Offshore Access

Question: How do you ensure that offshore teams cannot access our production data?

Answer:  
Production environments are strictly segregated and accessible only to a small, approved group under client governance. Offshore developers work on lower environments with anonymised or synthetic data.

We combine:

- Network segmentation and firewall rules,
- Identity and access management with least-privilege roles and MFA,
- Virtual desktop infrastructure with copy/paste and file-transfer restrictions.

These are technical controls, not just process rules, and we are able to demonstrate them during due diligence.

---

## 3. Vendor Lock-in and Exit Strategy

Question: How difficult would it be to move away from your team in the future?

Answer:  
We design for portability. Infrastructure is defined as code, and the application follows standard technologies (containers, mainstream databases, open API standards). We maintain:

- Up-to-date documentation and architecture decision records,
- A structured knowledge base for operations and support,
- Clear separation of configuration and environment-specific details.

During contract negotiations we can include an exit plan with handover activities, data and documentation exports and optional shadowing for incoming teams.

---

## 4. Observability and Incident Response

Question: How will you detect and diagnose issues quickly in production?

Answer:  
We implement an observability baseline that includes:

- Structured logging with correlation IDs across services,
- Metrics for both technical and business indicators,
- Traces for critical flows where required.

We define alert rules for key SLIs (latency, error rates, saturation) and connect them to agreed escalation paths and response SLAs. Runbooks describe standard diagnostic steps per incident type, so response does not depend solely on individual heroics.

---

## 5. Managing Technical Debt

Question: How do you prevent technical debt from accumulating over time?

Answer:  
We treat technical debt as a first-class topic in governance:

- We make architectural trade-offs explicit and record them in ADRs,
- We track debt items in the backlog with an owner and impact description,
- We reserve capacity for refactoring and maintenance in each release train or quarter.

Our aim is not to avoid all debt, but to ensure that it is conscious, documented and actively managed.

---

## 6. Security Testing and Hardening

Question: What do you do beyond basic vulnerability scans?

Answer:  
In addition to standard SAST, DAST and dependency scanning in the CI/CD pipeline, we:

- Include security requirements in user stories where appropriate,
- Run targeted security tests on critical flows (authentication, authorisation, payments, data export),
- Support independent penetration tests commissioned by the client.

Findings are prioritised based on risk, and remediation is tracked as part of the normal backlog with clear acceptance criteria.

---

## 7. Cloud Provider Dependency

Question: What happens if we want to change cloud provider in the future?

Answer:  
We avoid unnecessary provider-specific lock-in by:

- Using container platforms and standard orchestration patterns,
- Separating application code from infrastructure provisioning logic,
- Isolating provider-specific features behind clear interfaces.

A full re-platform is never free, but by keeping clear boundaries and using infrastructure as code, we can estimate and plan such migrations more reliably if the business case arises.
