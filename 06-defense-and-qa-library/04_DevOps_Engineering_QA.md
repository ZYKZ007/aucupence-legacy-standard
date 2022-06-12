# DevOps & Engineering Q&A (18)

## Q1. GitFlow vs trunk-based — what do you recommend?
We prefer trunk-based for modern multi-squad delivery. Short-lived branches reduce merge debt. GitFlow can be used for legacy release trains with strict gates.

## Q2. What CI quality gates do you enforce?
Unit coverage thresholds for critical paths. Static analysis with zero new critical issues. Dependency scanning and container image policies.

## Q3. How do you handle database changes safely?
We use expand-migrate-contract strategies. Backward compatibility is validated in CI. Destructive changes are deferred until stable adoption.

## Q4. How do you manage release strategies?
Blue/green or canary depending on risk appetite. Automated rollback ties to SLO alarms. Release notes and change records are mandatory.

## Q5. How do you ensure environment reproducibility?
IaC modules with version pinning. Immutable images and standardized pipelines. Manual server changes are prohibited.

## Q6. How do you control configuration?
Config is externalized and audited. Secrets are separated from app config. Drift detection alerts governance.

## Q7. How do you enforce DevSecOps?
Security scans run as pipeline stages, not optional checks. Threat modeling is performed for critical flows. Findings are tracked to closure.

## Q8. How do you measure delivery health?
We track DORA-style indicators and operational SLIs. Lead time and deployment frequency are balanced with reliability. Metrics inform governance decisions.

## Q9. How do you handle incident management?
Severity definitions and response targets are pre-agreed. On-call runbooks are maintained and tested. Post-incident reviews drive systemic fixes.

## Q10. How do you handle third-party library risks?
SBOM practices where feasible. Patch windows are scheduled. High-severity CVEs trigger hotfix processes.

## Q11. How do you support infrastructure testing?
We validate IaC with plan checks and policy-as-code. Staging applies mimic production patterns. DR automation is periodically exercised.

## Q12. What is your approach to observability as code?
Dashboards, alerts and SLO definitions are versioned. Changes follow PR reviews. This reduces tribal-knowledge operations.

## Q13. How do you handle multi-repo programs?
We standardize CI templates and governance policies. Shared interface contracts reduce cross-repo risk. Dependency ownership is published.

## Q14. How do you prevent “works on my machine” issues?
Containerized dev environments and pinned toolchains. Automated checks validate local parity. Repository bootstrap scripts reduce setup variance.

## Q15. How do you manage feature flags?
We use controlled rollout via environment and cohort rules. Flags have owners and expiry dates. This reduces long-lived hidden complexity.

## Q16. How do you approach performance testing in CI?
We run lightweight smoke benchmarks per build. Full load tests run per milestone. Results feed release readiness gates.

## Q17. How do you handle compliance evidence?
Pipeline logs, scan reports and change histories are archived. Evidence mapping to control requirements is maintained. This supports audit requests.

## Q18. How do you manage cost efficiency in DevOps?
Autoscaling guardrails and resource quotas. Build pipeline optimization reduces waste. FinOps dashboards support governance.
