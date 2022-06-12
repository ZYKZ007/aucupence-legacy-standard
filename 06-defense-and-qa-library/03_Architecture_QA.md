# Architecture Q&A – Standard Topics

---

**Q1. Why microservices instead of a modular monolith?**  
A1. We decide based on domain volatility, team topology and integration complexity. A modular monolith can be a valid phase-1 pattern with clear boundaries and a migration path.

**Q2. How do you enforce domain boundaries?**  
A2. Through API contracts, ownership rules, data access constraints and architecture governance with ADR records.

**Q3. How do you avoid over-engineering early?**  
A3. We tie architecture decisions to explicit NFR tiers and phased scope awards.

**Q4. How do you reduce vendor lock-in?**  
A4. Containers, standard data interfaces and IaC patterns enable portability. We also provide an exit narrative and handover artefacts.

**Q5. How do you manage multi-team dependencies?**  
A5. With a clear integration roadmap, contract testing and a shared event/API catalogue.

**Q6. What is your approach to API versioning?**  
A6. We define deprecation windows, backward-compatibility rules and publish a version policy as part of the integration appendix.

**Q7. How do you handle data model evolution?**  
A7. We maintain schema governance, backward-compatible changes and migration plans tied to release cadence.

**Q8. What makes an architecture “audit-friendly”?**  
A8. Traceable changes, immutable audit events, environment controls and enforced access logging.

**Q9. How do you validate architecture assumptions?**  
A9. Early spikes, performance baselines and integration proof-of-concepts during Discovery.

**Q10. What is your stance on multi-region active-active?**  
A10. We treat it as a premium resilience tier justified by business criticality and cost tolerance.

