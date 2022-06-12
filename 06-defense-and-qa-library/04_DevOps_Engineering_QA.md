# DevOps & Engineering Q&A – Standard Library

---

**Q1. What does your CI/CD baseline include?**  
A1. Automated build, test and security gates, plus controlled promotion across environments.

**Q2. What quality gates do you typically enforce?**  
A2. Code coverage thresholds, static analysis quality gates and high-severity vulnerability blocking.

**Q3. How do you handle secrets?**  
A3. Central secrets management with rotation policies and zero hard-coded credentials.

**Q4. How do you prevent unstable releases?**  
A4. Progressive delivery, feature flags and automated rollback criteria.

**Q5. How do you manage environment drift?**  
A5. Infrastructure as code with version-controlled modules and approval workflow.

**Q6. How do you ensure reproducible builds?**  
A6. Containerized build environments and pinned dependency versions.

**Q7. What is your approach to incident response?**  
A7. Severity model, on-call rota, runbooks and post-incident reviews tied to process improvements.

**Q8. How do you measure DevOps maturity?**  
A8. Lead time, deployment frequency, MTTR and change failure rate, contextualized to risk posture.

**Q9. How do you support regulated change approval?**  
A9. Evidence packs generated from pipeline logs, test results and security scans.

**Q10. What is your stance on Git workflow?**  
A10. Trunk-based with short-lived branches for high-velocity teams; GitFlow-like gating where audit requirements are stricter.

