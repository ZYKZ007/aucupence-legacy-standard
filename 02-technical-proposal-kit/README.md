# 02 – Technical Proposal Kit

This folder contains the technical core of the asset library. It is not marketing copy – it is the engineering baseline reused when shaping non-functional requirements (NFR), architecture options and infrastructure for regulated clients (banking, lending, payments).

The documents here are designed to answer four concrete questions:

1. Can the platform scale and stay available under real volumes?
2. Is the security, auditability and data-residency story credible for banks and regulators?
3. What does the target architecture look like in practice, not just as boxes and arrows?
4. How does this map to real cloud infrastructure (for example AWS) that can be deployed and operated?

## Files

### 1. 01_NFR_Response_Digital_Lending.md

Purpose:  
Reusable baseline for non-functional requirements when proposing a digital lending or credit-origination platform.

Focus:

- Target TPS and latency numbers and how they are achieved (EKS, HPA, Redis, RDS read-replicas).
- Availability targets and resilience patterns (multi-AZ, circuit breakers, graceful degradation).
- Security model (IAM, encryption, secure SDLC, threat modelling).
- Auditability (structured logging, admin change trails, retention).

Typical usage:

- Copy relevant sections into the “NFR Response” chapter of an RFP.
- Use as a checklist when reviewing whether a concrete solution design is complete.

### 2. 02_Solution_Architecture_Reference.md

Purpose:  
Reference architecture for transaction-heavy, API-driven systems such as lending, wallets or digital onboarding.

Focus:

- Breakdown into channels, API gateway, domain services, data stores and integration layer.
- Cross-cutting concerns: observability, security, configuration, feature toggles.
- How NFR commitments from 01_NFR_Response_Digital_Lending.md are realised in the architecture.

Typical usage:

- As the backbone for architecture sections in proposals or client workshops.
- As a starting point for tailoring to specific cloud or provider constraints.

### 3. 02_Solution_Overview_Architecture_Notes.md

Purpose:  
Higher-level narrative that can be read by non-deep-technical stakeholders (business, procurement, PMO) without losing the engineering logic.

Focus:

- Plain-language explanation of the architecture layers and main components.
- How responsibilities are split between vendor, client and third-party systems.
- Key decisions that impact cost, performance and risk.

Typical usage:

- Attach as an appendix to an RFP response.
- Use as talking points for steering-committee decks or presales sessions.

## How to Use This Kit

1. Start from 01_NFR_Response_Digital_Lending.md to understand the non-functional commitments.
2. Map those commitments into the reference architecture in 02_Solution_Architecture_Reference.md.
3. Use 02_Solution_Overview_Architecture_Notes.md to translate the same ideas into language that PMO and business stakeholders can absorb.
4. Align infrastructure and run-operations with:

   - ../infrastructure/aws/main.tf  
   - ../docs/architecture/decisions/ADR-001-high-level-architecture.md
