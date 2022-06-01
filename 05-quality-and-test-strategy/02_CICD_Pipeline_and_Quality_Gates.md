# CI/CD Pipeline and Quality Gates – Reference Blueprint

This document describes a reference CI/CD pipeline and associated quality gates. It is used to explain to clients how we enforce quality and security via automation.

---

## 1. Pipeline Stages

Typical stages for each service:

1. Checkout and build
2. Static checks (linting, SAST, dependency scanning)
3. Unit tests
4. Integration / contract tests
5. Docker image build and scan
6. Deploy to Integration and run smoke tests
7. Deploy to higher environments (System Test, UAT, Production) with approvals

Each stage has pass/fail criteria.

---

## 2. Example Quality Gates

We define objective thresholds, for example:

- Code coverage:
  - Minimum 80% line coverage on new and changed code.
- Static analysis:
  - No new critical or high-severity issues.
  - Maintainability rating A or B.
- Dependency scanning:
  - No high or critical CVEs in direct dependencies without documented exceptions.
- Container scanning:
  - Base images must come from approved list.
  - No critical vulnerabilities in final images.

If a gate fails, the pipeline stops. Exceptions require explicit approval and documented justification.

---

## 3. Example Pipeline Logic (Pseudo YAML)

This is a conceptual example; the actual syntax depends on the CI platform.

- Stage: build_and_test
  - Steps:
    - Install dependencies.
    - Run linter.
    - Run unit tests with coverage.
    - Publish coverage report.
  - Conditions:
    - Fail if coverage < 80%.

- Stage: security_scan
  - Steps:
    - Run SAST.
    - Run dependency scan.
  - Conditions:
    - Fail if any new critical or high-severity issues.

- Stage: build_image
  - Steps:
    - Build Docker image.
    - Scan image.
    - Push to registry with version tag.
  - Conditions:
    - Fail if non-approved base image or critical vulnerabilities.

- Stage: deploy_integration
  - Steps:
    - Deploy Helm chart to integration cluster.
    - Run smoke tests.
  - Conditions:
    - Rollback if smoke tests fail.

- Stage: promote_to_stg_and_prod
  - Steps:
    - Manual approval gate.
    - Deploy to System Test and later Production.
  - Conditions:
    - Require sign-off from PM and Architect for production.

This structure aligns with typical DevSecOps expectations in banking and payments.

---

## 4. Reporting and Metrics

We track and regularly report:

- Build success rate.
- Mean time to fix broken builds.
- Test coverage trends.
- Number of vulnerabilities over time.
- Deployment frequency and lead time.

These metrics are used both internally for continuous improvement and externally in steering committee packs to demonstrate control.

