# Technical Proposal Kit (Legacy Baseline)

This module contains reusable proposal-stage technical narratives for cloud-hosted digital platforms, with emphasis on regulatory-ready clarity and distributed delivery realities.

The intent is not to prescribe a single technology stack. The goal is to provide answerable, auditable, and defensible patterns that help vendor teams communicate architecture, NFR posture, security boundaries, and operability to demanding client stakeholders.

## How this module is used

- As a proposal-writing baseline for regulated programs (banking, lending, payments).
- As a coaching reference for PMs and tech leads preparing for presales defense.
- As a consistency anchor aligned with estimation, governance, and quality modules.

## Key assets

- 01_NFR_Response_Digital_Lending.md  
A reusable NFR response structure with performance, availability, security, auditability, and SLA/SLO framing.

- 02_Solution_Architecture_Reference.md  
A reference narrative describing logical layers, responsibility boundaries, deployment patterns, and integration assumptions.

- 02_Solution_Overview_Architecture_Notes.md  
A shorter overview format used in executive-friendly proposal sections and RFP “solution approach” summaries.

- 03_Cloud_and_DevSecOps_Baseline.md  
A practical baseline for cloud landing zone assumptions, CI/CD, security scanning, and environment segregation.

- 04_Data_and_Integration_Reference.md  
Patterns for data domains, integration modes, data residency constraints, and audit-grade observability.

## Reference diagrams

![High-level reference architecture](../diagrams/architecture-high-level.svg)

![Runtime and flow patterns](../diagrams/architecture-runtime-flows.svg)
