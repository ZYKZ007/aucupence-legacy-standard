# Estimation Model – Digital Delivery Projects

This document describes how we estimate the effort and cost for a typical digital delivery project, especially in an offshore / nearshore setup. It connects directly to:

- RFP decomposition and compliance analysis,
- NFR and architecture decisions,
- Commercial models and rate-card structures.

---

## 1. Estimation Principles

1. Decompose first, estimate second  
   We avoid “single number” estimates on a whole project. We break work into workstreams and epics, then estimate each separately.

2. Use the right method for the right item  
   - High-uncertainty activities use three-point estimates (optimistic, most likely, pessimistic).  
   - Repetitive or well-known activities use historical velocity and throughput.

3. Separate effort types  
   We explicitly separate:
   - Build effort (implementation and testing),
   - Environments / DevOps effort,
   - Governance and coordination overhead,
   - One-off activities (data migration, cut-over, training).

4. Link to non-functional requirements  
   Performance, resilience and security requirements have cost. Higher NFR targets usually mean more design, hardware, tuning and testing.

---

## 2. Example Workstream Breakdown

| Workstream                  | Description                                          | Estimated Effort (Person-Days) |
|:--------------------------- |:-----------------------------------------------------|:--------------------------------|
| Discovery & Elaboration     | Workshops, backlog refinement, architecture baseline | 40–60                           |
| Core Services Development   | Business microservices and APIs                      | 180–240                         |
| Frontend & UX               | Web/mobile UI, design system integration             | 80–120                          |
| Test Automation             | Unit, API and E2E automation                         | 60–90                           |
| DevOps & Environments       | CI/CD pipelines, monitoring, logging, IaC            | 50–80                           |
| Data Migration              | ETL design, test loads, reconciliation               | 50–100                          |
| Cut-over & Hypercare        | Dress rehearsal, go-live, post-go-live support      | 30–50                           |

These ranges are refined once user stories, NFRs and integration details are understood.

---

## 3. Effort Drivers and RFP Link

Key drivers that increase or reduce effort include:

- Integration count and quality  
  - Number of external systems (core banking, CRM, KYC, scoring engines, payment gateways).  
  - Availability of sandboxes, documentation and test data.  
  - Stability of APIs (frequency of breaking changes).

- Non-functional constraints  
  - Performance and latency requirements (for example p95 < 300 ms vs < 800 ms).  
  - Availability targets (for example 99.5% vs 99.95% vs active-active).  
  - Regulatory constraints (audit, data residency, security reviews and approvals).

- Data complexity  
  - Volume and quality of data to be migrated.  
  - Number of data sources and reconciliation rules.  
  - Need for parallel run or dual-write periods.

- Team maturity and asset reuse  
  - Whether the team has delivered similar architectures and domains.  
  - Whether there are existing templates, libraries, playbooks and test assets to reuse.

We make these drivers explicit in the proposal so that the client understands why effort looks the way it does. They are linked back to RFP requirements and NFR statements.

---

## 4. Three-Point Estimation and Contingency

For high-uncertainty items we use three-point estimates:

E = (Optimistic + 4 × Most Likely + Pessimistic) / 6

Contingency is then applied based on:

- Technical complexity (for example +10–20%)
- Dependency risk (third-party providers, legacy systems)
- Regulatory unknowns (audits, approvals, new guidelines)

Management reserve is kept separate from visible contingency to handle strategic or aggregate risk at programme level.

---

## 5. From Effort to Team Shape

Before price, we derive the delivery footprint:

- Required number of squads or feature teams,
- Balance of onshore / nearshore / offshore,
- Senior vs mid-level vs junior roles,
- Capacity reserved for architecture, QA and governance.

Example mapping for a 9–12 month programme:

- 1 onshore solution architect (0.5–0.8 FTE),
- 1 vendor PM (1.0 FTE),
- 2 feature teams (6–8 FTE each) offshore / nearshore,
- Part-time DevOps and QA specialists shared across teams.

This mapping then feeds into the commercial model and ratecard.

---

## 6. Linking to Commercial Models

Once effort and team shape are estimated, we select an appropriate commercial pattern:

- Time & Materials  
  - Direct mapping of person-days into a blended model.  
  - Transparent for the client; suitable when scope is evolving.

- Fixed Price (with assumptions)  
  - Use T&M estimates as input, add contingency and risk premium.  
  - Assumptions and change-control rules are documented; certain workstreams (discovery, integration spikes) may remain T&M.

- Capacity-based  
  - Long-running teams with a stable or growing backlog.  
  - Commercials expressed in terms of team capacity per month.

Effort and model are always presented together with assumptions, so that changes in scope, NFRs or dependencies can be traced back to effort and price adjustments.
