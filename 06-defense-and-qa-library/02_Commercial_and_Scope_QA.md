# Presales Commercial & Scope Q&A – Standard Library

This library is used when commercial or procurement stakeholders challenge the pricing model, scope handling and risk posture. The goal is to give concrete, defensible answers – not marketing slogans.

## 1. Scope and Change Control

Question: Why do you insist on a formal change-control process?

Answer:  
Complex digital projects never stay exactly as initially described. New requirements appear, regulations change, and integration constraints surface. Without a clear change mechanism, there are only two realistic outcomes:

1. The vendor silently absorbs the extra work and compensates by lowering engineering quality or cutting corners.
2. The client is surprised by late delays or hidden cost and trust collapses.

Our approach:

- We freeze a scope baseline at the end of discovery (typically after 4–6 weeks).
- Any change that affects effort, risk or external dependencies is logged as a Change Request (CR).
- For each CR we provide:

  - Effort impact (plus or minus person-days),
  - Timeline impact (for example one additional sprint),
  - Risk impact (for example new integration, new compliance check),
  - Commercial impact (time-and-materials or fixed-fee uplift).

This protects both sides: the client keeps transparency on why cost and dates move; we avoid silently lowering the engineering standard to “fit the number”.

## 2. Fixed Price versus Time and Materials

Question: Can you deliver this entire scope on a fixed price?

Answer:  
Yes, but only once the uncertainty is low enough that a fixed price is rational for both sides.

We typically use a two-step approach:

1. Discovery on time and materials (T&M)  
   - Duration: 4–8 weeks, depending on complexity.  
   - Outputs: refined backlog, agreed NFRs, integration catalogue, risk register.  
   - At the end we have a realistic estimate based on decomposition and three-point estimation.

2. Selective fixed price  
   - Stable work packages (for example channels, well-understood services) are moved to fixed price.  
   - High-uncertainty areas (for example data migration, third-party integrations, regulatory reviews) stay on T&M or have explicit risk buffers.

Example:

- Baseline estimate for build: 900 person-days.  
- We fix 600 person-days as a fixed-price scope (with 10–15% contingency included).  
- Remaining 300 person-days (data, legacy integration, change requests) are left on T&M with a capped budget or stage gates.

This way procurement gets budget certainty on the stable part, while we avoid pricing in a large risk premium for the unknowns.

## 3. Blended Rate and Nearshore/Offshore Model

Question: Why is your daily rate higher than some pure offshore vendors?

Answer:  
We use a blended delivery model rather than a pure low-cost offshore model. A typical setup:

- Engagement Director and Solution Architect: onshore or nearshore.  
- Project Manager, Tech Lead, most developers and QA: nearshore or offshore.

The blended rate reflects:

1. Higher seniority on key roles – we put genuine decision-makers in front of the client.  
2. Lower coordination waste – clearer architecture and governance reduce re-work.  
3. Expected productivity – we plan around velocity (story points per sprint), not only headcount.

In practice, when we compare effective cost per delivered feature against low-rate, low-governance teams, the total cost is often similar or lower because there is less re-work and fewer failed releases.

If requested, we can provide a scenario comparison: same scope with

- low blended rate and low governance, versus
- higher blended rate and strong governance,

and show the impact on total cost of ownership (TCO).

## 4. Risk Buffers and Contingency

Question: Your estimate includes a contingency line. Are you over-padding the numbers?

Answer:  
We separate visible effort from explicit contingency on purpose.

- Visible effort is the sum of estimates for known tasks, based on decomposition and three-point estimates.  
- Contingency is a percentage applied only where uncertainty is real (for example undocumented APIs, unclear data quality, regulatory approvals).

Typical ranges:

- 10–15% for technical uncertainty (for example third-party APIs without stable sandboxes).  
- 5–10% for governance overhead (for example additional reviews, committees).  
- 0–5% for migration risks if data has already been profiled.

We do not apply contingency everywhere. We are prepared to walk through the estimate line by line so the client can see where risk is and where it is not. If the client prefers, we can move some contingency into:

- Management reserve held on the client side, or  
- A change budget earmarked for CRs, rather than embedding everything into the base price.

## 5. Discounts and Long-Term Engagements

Question: Can you give us a better price if we commit to a longer contract?

Answer:  
Yes, but we link discounts to predictability and volume, not to vague “multi-year” statements.

Typical levers:

1. Volume commitment  
   - If the client commits to a minimum annual volume (for example 1,200 person-days per year), we can reduce the blended rate because we can plan capacity.

2. Longer team stability  
   - If we can keep a core team together for 12 months or more, ramp-up cost per phase drops and we can reflect this in the rate.

3. Simplified commercial model  
   - Fewer rate categories and simpler invoicing (for example one blended rate for all developers) reduces overhead and allows a modest discount.

What we avoid is an arbitrary headline discount that later forces us to staff the project with inexperienced people just to make the numbers work. The goal is to keep team quality and delivery standard fixed and adjust price through genuine efficiency, not through cutting corners.

## 6. Handling Scope Creep Without Constant Renegotiation

Question: Are you going to raise a change request for every small requirement tweak?

Answer:  
No. We distinguish between:

- Noise-level changes: small clarifications, copy tweaks, minor UI changes that we absorb within the sprint.  
- Material changes: new user journeys, new integrations, new regulatory requirements, or anything that displaces already agreed scope.

Only the material changes become CRs. To avoid friction:

- We agree a tolerance band up front (for example up to 5–10% of effort can move within the baseline scope without a CR).  
- We use the backlog and release plan as the single source of truth – if something pushes other items out of scope or out of the release window, it should be treated as a change and discussed.

This keeps governance practical: the client is not bombarded with paperwork for every pixel change, but there is a clear mechanism for changes that truly affect time, cost or risk.
