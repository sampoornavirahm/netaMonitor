# PH-00 — Phase workspace

This folder holds the phase brief, approved UI/product deliverables, development handoff, QA report, defect register and human acceptance record. See `phase-register.csv` and `prompts/PH-00/`.

## UI Design deliverables (Agent 1, branch `ph00/ui-design`)
| File | Purpose |
|---|---|
| `user-personas.md` | Synthetic personas, access states, accessibility and literacy needs |
| `user-journeys.md` | Top tasks and journeys J01–J16 for every access state and Admin sub-role |
| `information-architecture.md` | Site maps, navigation model, content hierarchy, trust cues |
| `service-blueprint.md` | Frontstage and backstage blueprint, separation-of-duties checkpoints |
| `low-fidelity-flows.md` | Text flow diagrams FLOW-01 to FLOW-10 |
| `screen-and-component-inventory.md` | Screens, reusable components, interaction states |
| `accessibility-and-responsive-principles.md` | WCAG 2.2 AA, responsive, multilingual, offline principles |
| `ui-design-handoff.md` | Handoff, decisions, open questions, self-review |

Other files in this folder (`PHASE_BRIEF.md`, `acceptance-record.md`) are owned by the brief and the human phase owner.

## Development specification (Agent 2)

The canonical technical/product specifications are maintained in `docs/`, not duplicated here:

- Product, non-functional, domain glossary/model and logical data model: `docs/PRODUCT_REQUIREMENTS.md`, `docs/NON_FUNCTIONAL_REQUIREMENTS.md`, `docs/DOMAIN_GLOSSARY.md`, `docs/DOMAIN_MODEL.md`, `docs/DATA_MODEL.md`.
- Architecture and controls: `docs/SYSTEM_ARCHITECTURE.md`, `docs/RBAC_MATRIX.md`, `docs/SCORING_METHODOLOGY.md`, `docs/VERIFICATION_POLICY.md`, `docs/PRIVACY_POLICY_REQUIREMENTS.md`, `docs/SECURITY_MODEL.md`, `docs/MODERATION_POLICY.md`, `docs/ELECTION_PERIOD_POLICY.md`.
- Assurance/source governance: `docs/DATA_SOURCE_REGISTER.md`, `docs/REQUIREMENTS_TRACEABILITY.md`, `docs/TEST_STRATEGY.md`.
- Canonical decisions: `docs/adr/` and `docs/decisions/`.
- Agent 2 report: `developer-handoff.md`.

The existing UI documents remain the source artifacts and are linked from the root specifications/traceability. Do not copy them to root-level duplicates. `qa-report.md` belongs to independent QA; `acceptance-record.md` remains human-owned.
