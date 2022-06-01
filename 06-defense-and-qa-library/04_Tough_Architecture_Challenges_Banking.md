# Tough Architecture Challenges – Banking Stakeholders Q&A

This library contains questions that typically come from senior architects, risk and security teams at banks. The answers are structured for presales and design-review sessions.

---

## 1. Resilience and Failure Modes

Question: What happens if your primary region goes down? How do you avoid partial failures that break customer journeys?

Answer:  
We design for failure by default. The platform uses:

- Multi-AZ deployment in the primary region; loss of a single AZ should not impact availability.
- Clear separation of critical and non-critical services:
  - Critical: onboarding, authentication, transaction posting.
  - Non-critical: campaign services, recommendation engines.

For full region failure scenarios:

- We can support a second region in “pilot-light” mode:
  - Core data replicated asynchronously with clear RPO (for example 15 minutes).
  - Minimal services pre-provisioned, others deployable via infrastructure-as-code within hours.

We also:

- Document explicit failure modes (for example upstream core banking outage).
- Implement graceful degradation (for example read-only mode, limited features) rather than binary “up or down” behaviour.

---

## 2. Regulatory Isolation and Multi-Tenant Design

Question: Can you host multiple banks on the same platform without violating regulatory isolation requirements?

Answer:  
Yes, with a combination of:

- Logical isolation:
  - Each bank has its own tenant identifier and data schema separation.
  - Access control enforced per tenant at the application and database level.

- Technical isolation options:
  - Dedicated VPC, Kubernetes namespace and database instance per tenant for higher sensitivity.
  - Shared infrastructure only for non-PII components (for example logging, metrics, CI/CD).

We discuss with each client where on the isolation spectrum they feel comfortable:

- Shared-everything except data.
- Shared platform services with dedicated data plane.
- Fully dedicated stack with only shared tooling.

The choice drives cost, but the architecture supports all three patterns.

---

## 3. Vendor Lock-In and Portability

Question: How hard is it to move away from your solution in five years?

Answer:  
We deliberately avoid proprietary lock-in where possible:

- Use open protocols and formats:
  - REST / gRPC APIs.
  - Standard data formats (JSON, CSV, Parquet where relevant).

- Infrastructure-as-code:
  - All infrastructure defined through Terraform or equivalent.
  - Deployment scripts can be adapted to another cloud or on-prem platform.

- Documentation:
  - Architecture decision records.
  - API catalogue.
  - Data model documentation.

In exit scenarios we can:

- Provide full data exports in agreed formats.
- Hand over IaC and deployment scripts.
- Support knowledge transfer to the incoming team under a separate agreement.

