# Presales Technical Q&A (20)

## Q1. How do you ensure scalability under unpredictable traffic?
We design stateless services with horizontal scaling on Kubernetes. Autoscaling policies are driven by CPU, memory and service-level RPS. Caching and async queues protect databases from burst writes.

## Q2. What is your baseline availability design?
We default to multi-AZ for all stateful workloads. Critical services adopt active-passive with automated failover. SLIs and error budgets control release velocity.

## Q3. Can you support multi-region architectures?
Yes, with a primary write region and async replication to secondary regions. We use region-specific feature flags and rehearsed failover runbooks. Active-active is considered only when business requires it and data conflict resolution is agreed.

## Q4. How do you defend your performance claims?
We provide test plans, load models and baseline scripts. We measure p95/p99 latency at the API gateway and publish tuning assumptions. Performance targets are validated before UAT exit.

## Q5. How do you handle high-volume integration workloads?
We use bulkheads, rate limiting and back-pressure at the edge. Async processing queues decouple spikes from core services. Retry policies are bounded to avoid storm amplification.

## Q6. What is your API security approach?
Zero-trust posture with strong identity, least privilege and short-lived tokens. WAF rules and threat detection are enabled for internet-facing endpoints. Sensitive operations require step-up authentication where applicable.

## Q7. How do you manage secrets and keys?
Secrets are stored in managed vaults and rotated by policy. Keys are protected by cloud KMS with customer-managed options. No secrets are stored in code, images or CI variables.

## Q8. What encryption standards do you support?
Encryption at rest using AES-256 with managed keys. Encryption in transit using modern TLS configurations. Field-level protection is applied for high-risk PII in regulated flows.

## Q9. How do you address data residency requirements?
We lock PII storage and processing to the required region. Offshore access is restricted to masked or synthetic datasets. Logging and analytics exclude raw PII unless explicitly permitted.

## Q10. How do you handle auditability?
We implement structured logs with correlation IDs. Admin actions and configuration changes are captured with who/what/when. Retention and access control align to the client’s policy.

## Q11. How do you ensure environment parity?
Infrastructure is defined as code and versioned. Staging resembles production in topology and security posture. Configuration is externalized and validated as part of the pipeline.

## Q12. What is your approach to disaster recovery?
We define RPO/RTO targets per system tier. DR architecture options include pilot-light or warm-standby depending on criticality. DR tests are scheduled and evidenced.

## Q13. Do you support SRE-style reliability governance?
Yes. We define SLOs for critical paths and track error budgets. Release gates react to SLO burn rate. Reliability improvements are planned as first-class backlog items.

## Q14. How do you handle legacy system constraints?
We build adapter layers and normalize contracts. Integration spikes are scheduled early to derisk unknowns. We document dependency SLAs and escalation paths.

## Q15. How do you handle file/document workflows?
We use pre-signed uploads, async scanning and metadata indexing pipelines. Large files are chunked and resumed safely. Access is governed by policy and audit trails.

## Q16. What observability stack do you recommend?
Metrics, logs and traces aligned to OpenTelemetry-compatible patterns. Dashboards cover technical and business KPIs. Alerting uses severity definitions tied to response SLAs.

## Q17. How do you prevent vendor lock-in?
We prefer container platforms, standard databases and open API standards. Infrastructure code is modular and portable. Knowledge transfer and ADRs support long-term maintainability.

## Q18. How do you manage technical debt?
Debt is tracked with impact and ownership. A fixed capacity allocation is reserved for refactoring. Decisions are documented to avoid hidden architectural drift.

## Q19. How do you control privileged access?
Privileged roles are tightly scoped, time-bound and logged. Access reviews are performed on cadence. Emergency access follows a break-glass procedure.

## Q20. What is your approach to cost-aware architecture?
We align scaling policies with workload patterns. Storage lifecycle and tiering are planned early. FinOps reporting supports governance and forecasting.
