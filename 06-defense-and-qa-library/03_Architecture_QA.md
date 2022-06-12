# Architecture Q&A (20)

## Q1. Monolith vs microservices — how do you decide?
We evaluate domain complexity, change rate and team topology. If boundaries are unclear, we start with a modular monolith. We evolve to services when scaling and release independence justify it.

## Q2. How do you define service boundaries?
We use domain-driven principles and business capability mapping. Shared data ownership is avoided. Contracts are explicit and versionable.

## Q3. When do you use event-driven patterns?
For high-volume, loosely coupled workflows and resilience under spikes. Events reduce synchronous dependency chains. We accept eventual consistency where the domain allows it.

## Q4. How do you prevent dual-write issues?
We apply outbox patterns and single-source-of-truth rules. Transactional boundaries are respected. Reconciliation jobs and idempotency policies are built in.

## Q5. How do you handle distributed transactions?
We use sagas with compensating actions. The business defines acceptable rollback semantics. We avoid global locks across services.

## Q6. How do you approach caching?
We identify hot reads and define clear invalidation rules. We prefer cache-aside with TTL plus explicit evictions for critical data. Cache consistency requirements are documented.

## Q7. Database selection principles?
We align choices with access patterns and consistency needs. OLTP remains relational by default. NoSQL is used when throughput and schema flexibility outweigh relational constraints.

## Q8. How do you scale read-heavy systems?
Read replicas, CDN where appropriate and multi-level caching. Query optimization is continuous. We separate operational reads from analytics where possible.

## Q9. How do you scale write-heavy systems?
We segment workloads, adopt async ingestion and consider sharding. Append-only logs simplify auditability. CQRS is introduced for extreme divergence.

## Q10. REST vs gRPC vs GraphQL?
REST for public APIs and broad tooling support. gRPC for low-latency internal services. GraphQL for complex client aggregation when governance is mature.

## Q11. How do you manage API versioning?
We enforce backward compatibility policies and deprecation windows. Contract tests validate changes. Breaking changes require new versions.

## Q12. How do you structure observability in architecture?
Correlation IDs propagate across all layers. Tracing is mandatory for critical journeys. Logs and metrics are aligned to SLIs.

## Q13. How do you address multi-tenancy?
We select isolation level based on regulatory risk. Options include database-per-tenant or schema isolation. Shared tenancy requires strong access control and encryption boundaries.

## Q14. How do you design for audit trails?
We treat audit as a domain feature. Critical actions are immutable and time-stamped. Roles and justifications are captured where required.

## Q15. How do you handle batch and real-time coexistence?
We define clear data ownership and latency tiers. Streaming handles near-real-time needs. Batch supports reconciliation and historical reporting.

## Q16. How do you approach data migration?
We perform early profiling and define reconciliation logic. Migration is staged with parallel-run where risk is high. Cutover checklists are documented.

## Q17. How do you ensure architecture governance?
Key decisions are recorded in ADRs. Architecture reviews are scheduled on cadence. Non-compliant changes are escalated.

## Q18. How do you treat NFRs within architecture?
NFRs are part of design authority, not an appendix. Availability, security and latency influence component selection. We maintain traceability to RFP constraints.

## Q19. How do you design for resilience?
We implement timeouts, retries and circuit breakers. Dependency SLAs inform fallback strategies. Chaos or fault-injection tests are considered for critical systems.

## Q20. How do you avoid over-engineering?
We align architecture to business value and maturity. We build for the next scaling milestone, not the distant future. Complexity must be justified.
