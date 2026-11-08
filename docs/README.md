# Documentation guide

Most living specifications (requirements, security, domain, data, API, scoring, verification, moderation and testing) live directly in `docs/`. The three subfolders below have distinct responsibilities.

- `phases/` — what is being built, phase deliverables, handoffs, defects, QA reports and acceptance records.
- `adr/` — Architecture Decision Records: why technical/architectural options were chosen.
- `decisions/` — product, governance and policy decisions: why NetaMonitor behaves in a particular way.

Do not duplicate the full text of an ADR or decision in phase reports; link to the canonical record. Phase reports should capture what changed and what remains open.

## PH-00 specification set

- [Product requirements](./PRODUCT_REQUIREMENTS.md) and [non-functional requirements](./NON_FUNCTIONAL_REQUIREMENTS.md)
- [Domain glossary](./DOMAIN_GLOSSARY.md), [domain model](./DOMAIN_MODEL.md), and [logical data model / ERD](./DATA_MODEL.md)
- [Proposed system architecture](./SYSTEM_ARCHITECTURE.md) and [RBAC matrix](./RBAC_MATRIX.md)
- [Scoring methodology](./SCORING_METHODOLOGY.md), [verification policy](./VERIFICATION_POLICY.md), [privacy requirements/threat model](./PRIVACY_POLICY_REQUIREMENTS.md), [security model](./SECURITY_MODEL.md), [moderation policy](./MODERATION_POLICY.md), and [election-period safeguards](./ELECTION_PERIOD_POLICY.md)
- [Data source register template](./DATA_SOURCE_REGISTER.md), [requirements traceability](./REQUIREMENTS_TRACEABILITY.md), and [future test strategy/catalogue](./TEST_STRATEGY.md)
- Decision status is canonical in [ADRs](./adr/README.md) and [product/policy decisions](./decisions/README.md); phase-specific UI source documents remain in [the PH-00 folder](./phases/PH-00/README.md).
