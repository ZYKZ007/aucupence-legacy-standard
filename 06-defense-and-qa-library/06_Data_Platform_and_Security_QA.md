# Data Platform & Security Q&A (12)

## Q1. How do you handle PII across environments?
We enforce masking and tokenization in non-prod. Access is role-based and audited. Synthetic datasets are preferred for offshore teams.

## Q2. How do you ensure GDPR-aligned data handling?
We map lawful basis, retention and data-subject rights to operational processes. Data minimization is enforced in design reviews. Logs avoid unnecessary PII.

## Q3. What is your data governance baseline?
We define ownership, lineage and quality rules. Critical datasets have validation checks and reconciliation routines. Governance cadence aligns with delivery forums.

## Q4. How do you choose between warehouse and lakehouse?
We evaluate query patterns, cost profile and latency needs. Warehouse suits structured reporting with strong governance. Lakehouse supports mixed workloads when maturity exists.

## Q5. How do you manage schema evolution?
Backward-compatible changes by default. Breaking changes require versioned contracts. A registry or governance gate enforces compatibility rules.

## Q6. How do you support CDC patterns?
We use CDC for low-latency replication where justified. Idempotent processing and checkpointing are mandatory. Reconciliation validates integrity.

## Q7. How do you secure data pipelines?
IAM least privilege, network segmentation and encrypted storage. Secrets are centrally managed and rotated. Access logs are retained per policy.

## Q8. How do you handle long retention requirements?
We separate hot vs cold storage tiers. Immutable storage is used for audit-grade logs. Retrieval processes are documented and tested.

## Q9. How do you approach analytics vs OLTP separation?
Operational systems remain optimized for transactions. Analytics uses replicated or curated datasets. This reduces performance contention.

## Q10. How do you address model risk if AI is used?
We require explainability expectations and monitoring thresholds. Data drift and bias checks are defined where applicable. Human override processes are documented.

## Q11. How do you handle cross-border data constraints?
We localize PII and restrict access by region. Processing roles are segmented by policy. Transfers require explicit contractual and technical controls.

## Q12. What evidence do you provide for security due diligence?
Policy summaries, scan reports and pipeline controls mappings. Access review records and incident procedures. A concise control-to-evidence matrix for auditors.
