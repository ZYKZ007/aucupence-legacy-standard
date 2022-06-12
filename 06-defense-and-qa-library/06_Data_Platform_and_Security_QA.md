# Data Platform & Security Q&A – Standard Library

---

**Q1. How do you keep PII boundaries clear?**  
A1. Separate PII stores, enforce masking rules and restrict access by role and environment.

**Q2. What is your approach to audit event integrity?**  
A2. Immutable event streams with controlled write access and retention rules.

**Q3. How do you handle data retention expectations?**  
A3. Align to local policy and define tiered retention for operational logs, audit logs and analytics data.

**Q4. How do you make offshore development safe for regulated data?**  
A4. Synthetic data, environment segregation and optional VDI constraints.

**Q5. What is your stance on encryption key ownership?**  
A5. Client-controlled keys where required, with documented rotation and access policies.

**Q6. How do you support regulator-friendly evidence?**  
A6. Provide logging design, access logs, security scan outputs and change histories.

**Q7. How do you handle data migration risk?**  
A7. Early profiling, reconciliation scripts, cutover rehearsal and rollback logic.

**Q8. How do you prevent analytics from violating residency rules?**  
A8. Aggregate/anonymize before cross-region movement; keep raw PII in-region.

**Q9. What are typical data-platform NFR signals?**  
A9. Lineage documentation, quality checks, incident runbooks and clearly defined ownership.

**Q10. How do you address third-party data processors?**  
A10. Vendor risk assessment, DPAs, and scoped access with monitoring.

