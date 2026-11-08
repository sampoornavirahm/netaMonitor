# PH-00 — Product Definition, Governance and Decision Baseline

**Project:** NetaMonitor  
**Status:** IN_DEVELOPMENT
**Dependencies:** None  
**Phase type:** Documentation/specification only — no production application code.

## Objective
Freeze a clear, testable product contract before software implementation: scope, personas, journeys, domain boundaries, data and source policies, voting/verification trust model, scoring definitions, privacy/security principles, governance, MVP boundaries and decision records.

## Agent sequence
1. UI Design: product experience, information architecture, personas, user journeys, service blueprint and low-fidelity flows. No polished screens or app code.
2. Development: synthesise approved product inputs into requirements, domain/data model, proposed system architecture, trust/security/privacy policies, technical contracts, ADR proposals and traceability. No application code, endpoints, migrations or runtime setup.
3. Independent QA: audit the full specification set, test internal consistency and coverage, produce requirement traceability, risk/gap findings and a future executable test catalogue. No browser E2E execution or app code.

## Required outputs
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/NON_FUNCTIONAL_REQUIREMENTS.md`
- `docs/DOMAIN_GLOSSARY.md`
- `docs/DOMAIN_MODEL.md`
- `docs/DATA_MODEL.md` and initial ERD
- `docs/SYSTEM_ARCHITECTURE.md` (proposed; decisions marked)
- `docs/RBAC_MATRIX.md`
- `docs/SCORING_METHODOLOGY.md`
- `docs/VERIFICATION_POLICY.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md` and privacy threat model
- `docs/SECURITY_MODEL.md`
- `docs/MODERATION_POLICY.md`
- `docs/ELECTION_PERIOD_POLICY.md`
- `docs/DATA_SOURCE_REGISTER.md` (template)
- `docs/REQUIREMENTS_TRACEABILITY.md`
- `docs/TEST_STRATEGY.md` and future acceptance-test catalogue
- Proposed ADRs in `docs/adr/` and product/policy decisions in `docs/decisions/`
- Eight UI Design source deliverables in `docs/phases/PH-00/`: personas, journeys, information architecture, service blueprint, low-fidelity flows, screen/component inventory, accessibility/responsive principles and UI handoff. Keep these source documents in the phase folder; root-level specifications reference them rather than duplicate them.
- `docs/phases/PH-00/ui-design-handoff.md`
- `docs/phases/PH-00/developer-handoff.md`
- `docs/phases/PH-00/qa-report.md`
- `docs/phases/PH-00/acceptance-record.md` (completed by human phase owner)

`docs/NON_FUNCTIONAL_REQUIREMENTS.md` is also required for the development specification pack.

## Acceptance gate
PH-00 can be accepted only when all required documents exist, requirements are traceable, high-risk trust/privacy/security/election issues are explicitly addressed or blocked by a documented owner decision, critical contradictions are resolved, and QA's documentation audit has no unresolved critical/high finding. Legal review items may remain open only if clearly assigned and treated as launch blockers where appropriate.

## Explicitly out of scope
No production UI implementation, React project scaffold, API implementation, database schema migrations, infrastructure provisioning, real user data, production integrations, browser E2E execution or deployment.
