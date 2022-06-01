# Pricing Scenarios – Digital Programs with Offshore / Nearshore Delivery

This document contains reference scenarios for pricing digital programs. It explains how we combine effort, rate cards and risk assumptions into concrete commercial options.

---

## 1. Baseline: Effort Model

We start from an effort model similar to 01_Estimation_Model_Digital_Project.md:

- Decomposed person-day estimates per workstream.
- Three-point estimates for high-uncertainty items.
- Separate lines for governance, environments and migration.

For illustration we use:

- Total visible effort: 900 person-days.
  - Build and test: 700
  - DevOps and environments: 100
  - Governance and PM: 100

We then apply different commercial lenses.

---

## 2. Scenario A – Pure Time & Materials

Description:

- All effort charged on a per-day basis.
- Rates per role; actual cost depends on burn pattern.

Example rate card (simplified):

| Role                 | Location   | Daily Rate (EUR) |
|:---------------------|:----------:|-----------------:|
| Engagement Director  | Onshore    | 1,400            |
| Solution Architect   | Nearshore  | 1,050            |
| Project Manager      | Nearshore  | 900              |
| Senior Engineer      | Nearshore  | 800              |
| Mid Engineer         | Offshore   | 600              |
| QA Automation        | Offshore   | 550              |

We compute an average blended rate by weighting per role and their expected allocation:

- Example blended rate: ~700–750 EUR / day.

Total price range:

- 900 person-days × 720 EUR ≈ 648,000 EUR (excluding contingency).

This model is transparent but gives the client less certainty on final cost.

---

## 3. Scenario B – Mixed Fixed-Price and T&M

Description:

- Stable scope items moved to fixed price.
- High-uncertainty items remain T&M with caps.

Example split:

- Fixed-price scope: 600 person-days (channels, core services, basic reporting).
- T&M scope: 300 person-days (data migration, 3rd-party integrations, regulatory review).

Pricing:

- Fixed price: 600 × 720 EUR × (1 + 0.12 contingency) ≈ 483,840 EUR.
- T&M capped budget: 300 × 720 EUR = 216,000 EUR.

Total envelope:

- 699,840 EUR (with flexibility to shift effort within T&M cap).

Benefits:

- Procurement gets a solid number for most of the build.
- Risk-heavy items are handled flexibly without forcing us to add a large risk premium to everything.

---

## 4. Scenario C – Capacity-Based Model

Description:

- Client contracts a stable team (for example 8–10 FTE) for a defined period.
- Throughput measured via velocity (story points per sprint) and DORA metrics (deployment frequency, change lead time, failure rate, MTTR).

Example:

- Team: 1 PM, 1 Architect (part-time), 5 Engineers, 2 QA.
- Contract: 12 months, 160 person-days per month (approx. 8 FTE).
- Monthly cost: 160 × 720 EUR = 115,200 EUR.
- Annual cost: ≈ 1.38M EUR.

This model works well when the client has a strong product organisation and expects a long roadmap, not a one-off project.

We define:

- Target velocity (for example 120–160 story points per sprint).
- Expected time-to-market for key features.
- Regular reviews where client can resize or reshuffle capacity.

---

## 5. Commercial Guardrails

Regardless of scenario, we apply guardrails:

- Clear assumptions document (for example number of environments, support hours, number of interfaces).
- Rules for change control when assumptions are broken.
- Explicit definition of what is included in “warranty / hypercare” versus paid change.

This turns pricing discussions from “your rate is too high” into “these are the levers and risks; let us choose together how to balance them”.

