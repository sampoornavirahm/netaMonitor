# NetaMonitor PH-00 — UI Design Handoff (Agent 1)

**Phase:** PH-00 · **Role:** Agent 1, Product Experience and UI Design Specialist
**Branch:** `ph00/ui-design` · **Base:** `main` at commit `8113630` ("new project")
**Status:** Submitted for human review. Not approved. Not merged. PH-00 is **not** accepted.

## 1. Summary
This branch adds the eight PH-00 UI Design deliverables required by `prompts/PH-00/01-ui-design.md`. They define the NetaMonitor product experience contract: personas, journeys for every access state and Admin sub-role, information architecture, service blueprint, low-fidelity flows, a screen and component inventory, and accessibility, responsive, multilingual and offline principles.

This is a documentation-only change. It contains no application code, no React components, no CSS, no tokens, no API or schema design, and no polished screens. It makes no technical architecture decisions. All people, places and figures are synthetic and labelled as such. No real politicians, parties, sources or data are used.

## 2. Changed files

| File | Status |
|---|---|
| `docs/phases/PH-00/user-personas.md` | Added |
| `docs/phases/PH-00/user-journeys.md` | Added |
| `docs/phases/PH-00/information-architecture.md` | Added |
| `docs/phases/PH-00/service-blueprint.md` | Added |
| `docs/phases/PH-00/low-fidelity-flows.md` | Added |
| `docs/phases/PH-00/screen-and-component-inventory.md` | Added |
| `docs/phases/PH-00/accessibility-and-responsive-principles.md` | Added |
| `docs/phases/PH-00/ui-design-handoff.md` | Added (this file) |
| `docs/phases/PH-00/README.md` | Updated to index the deliverables |
| `CHANGELOG.md` | Updated with an Unreleased entry |

Not changed on purpose: `AGENTS.md` (it holds no per-phase state and needs no edit from this role), `PHASE_BRIEF.md` (status is the owner's to set), `docs/phases/PH-00/acceptance-record.md` (human-owned; left untouched), `IMPLEMENTATION_HANDBOOK.md`, `phase-register.csv`, and all other phases.

## 3. Requirement ID map

| File | ID range | Defined IDs |
|---|---|---|
| user-personas.md | `PH-00-UX-001`–`049` | personas, access states, cross-persona needs |
| user-journeys.md | `PH-00-UX-050`–`149` | top tasks, journeys J01–J16 |
| information-architecture.md | `PH-00-UX-150`–`199` | navigation, content hierarchy, trust cues |
| service-blueprint.md | `PH-00-UX-200`–`249` | line of visibility, separation-of-duties checkpoints |
| low-fidelity-flows.md | `PH-00-UX-250`–`299` | FLOW-01 to FLOW-10, state coverage |
| screen-and-component-inventory.md | `PH-00-UX-300`–`449` | screens, components, state catalogue |
| accessibility-and-responsive-principles.md | `PH-00-UX-500`–`599` | accessibility, responsive, language, offline |

Decision IDs: `PH-00-UX-D01`–`D10` (§5). Open question IDs: `PH-00-UX-Q01`–`Q13` (§6). Assumptions are `A-01`–`A-14`, listed in each file.

## 4. Coverage against the PH-00 prompt

| Prompt requirement | Where covered |
|---|---|
| Personas, accessibility and digital-literacy considerations | user-personas §3, §6; accessibility §1.1 |
| Top tasks and journeys: anonymous, registered, identity verified, constituency verified, Admin sub-roles, SuperAdmin, profile claimant | user-journeys §1 (top tasks), §3, §4 |
| Information architecture and navigation across desktop, tablet, mobile | information-architecture §2–§4; accessibility §2 |
| Service blueprint: verification, voting, evidence submission, editorial review, corrections, reply, appeals, profile ownership | service-blueprint §2, §3.1–§3.6 |
| Low-fidelity flows: search/discovery, profile, promise detail, vote, admin review, correction | low-fidelity-flows FLOW-01 to FLOW-04, FLOW-07, FLOW-08 (plus verification, sign-in, reply, appeals) |
| Responsive principles, offline/read-only, loading/empty/error/permission states | accessibility §2, §4, §5; inventory §4 |
| Multilingual and WCAG 2.2 AA | accessibility §1, §3 |
| Trust cues: provenance, dates, attribution, evidence status, sample sizes, uncertainty, corrections | information-architecture §6 (`PH-00-UX-180`–`193`) |
| Screen and reusable component inventory | screen-and-component-inventory §1–§3 |
| Assumptions, dependencies, open questions, decisions needing approval | each file, plus §5–§7 below |

Principles from the prompt are honoured as follows: reduce steps without hiding consent (J05 confirm step); evidence, sentiment and completeness distinct (`PH-00-UX-165`, `189`); no private identity or individual vote history shown (`PH-00-UX-098`, `203`); explain eligibility without revealing sensitive data (`PH-00-UX-266`); no dark patterns, partisan cues or manipulative gamification (`PH-00-UX-191`, `192`, `268`); browsing without login (`PH-00-UX-071`, `080`); offline is public read-only (`PH-00-UX-560`–`562`); SuperAdmin absent from ordinary navigation without relying on obscurity (`PH-00-UX-154`).

## 5. Product decisions needing owner approval
These are proposals. None is approved until the human owner accepts them.

| ID | Proposed decision | Why |
|---|---|---|
| PH-00-UX-D01 | Evidence assessment (Module A) and citizen assessment (Module B) are always separate regions, A before B. | Prevents sentiment from overriding evidence; handbook non-negotiable. |
| PH-00-UX-D02 | Location is optional; a selected constituency is labelled differently from a verified one. | Inclusive browsing; avoids false eligibility. |
| PH-00-UX-D03 | No login required for any read journey. | Lowers barriers; serves low-engagement users. |
| PH-00-UX-D04 | Explain "why unavailable" instead of showing silent disabled controls. | Accessibility and trust. |
| PH-00-UX-D05 | The evaluation receipt shows only the user's own choice, only in a signed-in view, with no shareable link. | Protects ballot privacy and reduces coercion risk. |
| PH-00-UX-D06 | The assisted or in-person verification route is shown at equal weight with the digital route. | Avoids digital-only exclusion. |
| PH-00-UX-D07 | A reply never replaces a record; factual disputes use the correction route. | Right of reply without suppression. |
| PH-00-UX-D08 | Absence of an Admin menu item is the UI control; a forbidden area shows the same neutral page as a missing one. Server-side enforcement remains the real control. | No discoverability leak; no security by secrecy. |
| PH-00-UX-D09 | Negative styling is reserved for an adjudicated "Not fulfilled" status; absent data and "not yet due" are neutral. | Avoids punitive framing of missing data. |
| PH-00-UX-D10 | Offline mode is public read-only with "as of" labels; no action is queued. | Handbook and AGENTS.md rule. |

## 6. Unresolved questions

| ID | Question | Suggested owner | Blocks |
|---|---|---|---|
| PH-00-UX-Q01 | Minimum cohort size for showing citizen results (planning default in handbook is 20) and minimum eligible promises before any representative-level figure | Privacy and product | PH-15, PH-16 copy |
| PH-00-UX-Q02 | Are reactions on comments in MVP at all? Design assumes **no** | Product and moderation | PH-14 |
| PH-00-UX-Q03 | Approved privacy notice wording, retention periods and the identity route (if any), subject to legal review | Counsel | PH-03, PH-05 |
| PH-00-UX-Q04 | How the assisted or in-person route operates in the pilot (staffing, location, evidence handling) | Phase owner | PH-05 |
| PH-00-UX-Q05 | Validate personas with pilot-area research; confirm Hindi and Marathi translators | Phase owner | PH-02, PH-20 |
| PH-00-UX-Q06 | Offline stale-data threshold, and whether non-sensitive drafts may be stored offline | Product and security | PH-24 |
| PH-00-UX-Q07 | Is audio or other assisted-literacy support in scope? | Product | PH-02, PH-20 |
| PH-00-UX-Q08 | Final wording of evidence status labels in English, Hindi and Marathi | Editorial | PH-02, PH-10 |
| PH-00-UX-Q09 | Public reviewer bylines or role-only attribution | Editorial | PH-08, PH-10 |
| PH-00-UX-Q10 | How a representative's authority to claim a profile is verified | Moderation and legal | PH-10 |
| PH-00-UX-Q11 | Default election-period wording per jurisdiction | Counsel | PH-25 |
| PH-00-UX-Q12 | Pilot geography and first office cohort (needed for any real content and for the persona context) | Phase owner | PH-06, PH-07 |
| PH-00-UX-Q13 | Final product name and brand identity (visual identity is deferred to PH-02) | Phase owner | PH-02 |

None of these is a critical architecture decision. Q01, Q03, Q10 and Q11 are policy or legal gates that must be closed before their dependent phases.

## 7. Dependencies
- **Development agent (next):** must confirm or contest every rule here in `docs/PRODUCT_REQUIREMENTS.md`, `docs/RBAC_MATRIX.md`, `docs/VERIFICATION_POLICY.md`, `docs/MODERATION_POLICY.md`, `docs/ELECTION_PERIOD_POLICY.md`, `docs/SCORING_METHODOLOGY.md`, `docs/PRIVACY_POLICY_REQUIREMENTS.md` and `docs/API_CONTRACTS.md`. Capability labels in these documents are placeholders to be mapped or replaced. Gaps must be raised as blockers, not invented.
- **QA agent:** can derive the requirement-to-test catalogue from the `PH-00-UX` IDs.
- **Later phases:** PH-02 (design system), PH-04, PH-05, PH-15, PH-20, PH-24.

## 8. Conflicts with existing approved records
None found. The repository has no accepted ADRs or decisions yet (`docs/adr/` and `docs/decisions/` contain only README files). The designs follow `AGENTS.md` §4 and handbook §5. Points the Development agent may need to reconcile:
- Capability labels use the word "ballot" internally (for example `ballot.cast`). This is a traceability label only; user-facing copy must not use it (`PH-00-UX-110`). The Development agent may rename these labels.
- The "eight eligibility states" in the evaluation flow are a design proposal. Verification, election-period and suspension policies could add or merge states.

## 9. Self-review and checks
Everything below was run on this branch. No application checks exist because there is no code.

| Check | Result |
|---|---|
| Correct base: branch created from `origin/main` at `8113630` | Confirmed |
| All eight required deliverables exist at the specified paths | Confirmed |
| Requirement IDs unique across the eight files | Confirmed by script: no duplicates |
| Each file's IDs fall inside its stated range | Confirmed by script |
| No code, CSS, tokens, schemas, endpoints or polished screens | Confirmed by review; flows are text diagrams only |
| No real politicians, parties, sources or data | Confirmed by review; all names are labelled synthetic |
| Question and decision IDs referenced in other files exist in §5–§6 | Reviewed manually |
| Links to other repo documents | Documents the Development agent will create are referenced by path and are expected to be missing until that phase |
| Automated tests, lint, build | Not applicable; none exist |

**Known limitations of this review:** it is a self-review by the authoring agent. It has not been checked against the full handbook text beyond sections 1, 5 and the PH-00/PH-04 prompts; the Development and QA agents and the human owner should treat it as unreviewed. Copy examples were not tested with Hindi or Marathi speakers.

## 10. Risks
- Persona assumptions are unvalidated (`Q05`).
- Policy gates (`Q01`, `Q03`, `Q10`, `Q11`) could change eligibility states and verification flows.
- Assisted verification (`Q04`) is essential for inclusion but has staffing and privacy implications not solved here.
- Eight evaluation states and ten flows may be heavy for a small pilot team; the owner may choose to defer low-value states.

## 11. Out-of-scope material left outside this PR
Earlier in this working session, a different, single-file specification and a set of **clickable HTML/JS/CSS prototypes** were produced under a different ID scheme (`PH-00-UI-`) and pushed to a separate remote branch named `ph-00-design`. Those do not meet the PH-00 prohibitions (no application code, no CSS, no polished screens) and **are not part of this PR**. They have not been merged to `main`. The owner should decide whether to delete that branch or keep it only as reference for PH-02. This PR does not depend on it.

## 12. Next steps
1. Human owner reviews this PR, records approval or change requests, and merges.
2. Owner assigns owners and due phases to the open questions.
3. The Development agent branches `ph00/development` from the updated `main`.
4. QA branches `ph00/qa` after the Development PR merges.

## 13. Phase readiness
UI Design deliverables: **complete and ready for human review.** PH-00 overall: **not accepted** and cannot be until the Development and QA outputs exist and the owner records the gate in `acceptance-record.md`. PH-01 must not start.
