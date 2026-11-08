# PH-00 — Development Specification Handoff

**Agent:** Agent 2 — Development + Unit Testing Specification
**Branch:** `ph00/development`
**Base:** `79478ea` (merge of UI Design PR #1 into `main`)
**Status:** Specification pack drafted; awaiting independent QA and human review. PH-00 is **not accepted**.

## 1. Summary

Created the PH-00 documentation-only product and engineering specification pack from the repository and the eight merged UI Design source documents. Formalized the owner's approved UI decisions D01–D10, preserved unresolved questions and proposed (not accepted) technical ADRs. Reconciled the evaluation UX into eight explanatory outcomes including election-period restriction. The UI Design sources remain in `docs/phases/PH-00/`; root specifications reference them rather than creating duplicate copies.

The pack intentionally leaves unresolved legal, privacy, operational, provider and numerical policies as gates. It does not choose an identity vendor, claim legal compliance, set the citizen-result threshold, define SQL/API implementation or create runtime/test code.

## 2. Changed files

### New root product/specification documents

- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/NON_FUNCTIONAL_REQUIREMENTS.md`
- `docs/DOMAIN_GLOSSARY.md`
- `docs/DOMAIN_MODEL.md`
- `docs/DATA_MODEL.md` (logical entity dictionary and Mermaid ERD; not executable schema)
- `docs/SYSTEM_ARCHITECTURE.md`
- `docs/RBAC_MATRIX.md`
- `docs/SCORING_METHODOLOGY.md`
- `docs/VERIFICATION_POLICY.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md`
- `docs/SECURITY_MODEL.md`
- `docs/MODERATION_POLICY.md`
- `docs/ELECTION_PERIOD_POLICY.md`
- `docs/DATA_SOURCE_REGISTER.md` (empty template)
- `docs/REQUIREMENTS_TRACEABILITY.md`
- `docs/TEST_STRATEGY.md` (future test catalogue; not executable tests)

### Decision records

- `docs/decisions/DEC-001-ui-experience-baseline.md` — owner-approved D01–D10.
- `docs/decisions/DEC-002-open-product-and-policy-questions.md` — Q01–Q13 and further unresolved gates.
- `docs/adr/ADR-001-provider-neutral-modular-architecture.md` — PROPOSED.
- `docs/adr/ADR-002-sensitive-data-boundaries.md` — PROPOSED.
- `docs/adr/ADR-003-versioned-provenance-and-audit.md` — PROPOSED.
- `docs/adr/ADR-004-contract-first-api.md` — PROPOSED.

### Updated project/phase navigation and handoff

- `AGENTS.md`, `README.md`, `CHANGELOG.md`, `docs/README.md`
- `docs/adr/README.md`, `docs/decisions/README.md`
- `docs/phases/PH-00/README.md`, `docs/phases/PH-00/PHASE_BRIEF.md`
- `docs/phases/PH-00/developer-handoff.md` (this file)

No UI source deliverable, `qa-report.md` or human-owned `acceptance-record.md` was edited.

## 3. Decision status

### Accepted by the human owner

D01–D10 in DEC-001 only. Q13 (product name NetaMonitor) is resolved as stated in the owner instruction. Existing product/security non-negotiables are preserved.

### Proposed, not accepted

All four ADRs (provider-neutral modular architecture; restricted verification/evaluation data boundaries; versioned provenance/audit; contract-first API). The stack/provider baseline remains a proposal.

### Open / blocked

- **Q01 — BLOCKED:** public citizen-result suppression/aggregation policy; no threshold selected. Handbook's planning value 20 is not adopted.
- **Q03 — BLOCKED:** privacy/legal review, identity route, retention/deletion and notice.
- **Q10 — BLOCKED:** representative/profile-claim authority evidence and review.
- **Q11 — BLOCKED:** jurisdiction-specific election wording/restrictions and legal review.
- **OPEN:** Q02, Q04–Q09, Q12, plus score policy, source/licensing, operational targets and provider decisions. Full register is in DEC-002.

## 4. Reconciliations and open defects

- The service blueprint's “seven eligibility states” and the low-fidelity flow's separate election-pause state are reconciled in the domain model as eight mutually exclusive explanatory outcomes. They are derived authorization explanations, not eight identity statuses. Enforcement remains server-side.
- The UI Design handoff's “not approved/not merged” line is recorded as a point-in-time statement. Git shows the eight deliverables were merged into `main` by PR #1; owner instructions now explicitly approve D01–D10. The historical handoff itself was not edited.
- The brief previously named root-level copies of personas, journeys and information architecture. It now points to the existing phase-folder sources to avoid duplication.
- No other critical contradiction has been declared resolved by inference. Remaining policy questions are recorded in DEC-002.

## 5. Traceability and risks

The initial traceability matrix maps FR-001–FR-032 to UX references, domain/data concepts, permission or threat controls, future acceptance IDs AT-001–AT-032 and owning phases. NFR families map to controls and future test IDs AT-033–AT-038.

Key risks: public aggregate inference/coercion; collection of identity evidence before legal/retention approval; misattribution of shared-government outcomes; source licensing and data quality; politically sensitive claims; staff conflict/insider access; election-period ambiguity; limited pilot staffing; and reliance on changing provider free tiers. The specifications identify controls and residual risks but do not claim they are implemented or fully mitigated.

## 6. Checks and exact outcomes

### Repository/state checks

- Branch check before changes: `ph00/development`.
- Starting worktree/index: clean.
- Base: HEAD `79478ea`, equal to local `main` and `origin/main`, and includes UI Design merge PR #1.
- PH-00 acceptance record was left untouched.

### Documentation checks
- Required Agent 2 deliverables: **17/17 present**.
- Markdown relative links and fenced code blocks: **PASS, 0 findings**.
- Functional requirement definitions: **32 unique IDs (`FR-001`–`FR-032`), no duplicate definitions**.
- Acceptance catalogue: **38 unique IDs (`AT-001`–`AT-038`), no duplicate rows**.
- Traceability lookup: **no missing FR or AT IDs**.
- Changed paths: **Markdown documentation only**; no non-Markdown files.
- Human-owned `acceptance-record.md` and the UI source deliverables: **unchanged**.
- `git diff --check`: **PASS after removal of one trailing-space issue in the phase brief**.
- Mermaid ERD: structure reviewed in the document; no Mermaid parser/tool was installed or run.

No unit, integration or browser E2E tests are applicable or permitted in PH-00. No application exists.

## 7. Defects, blockers and next steps

No code defects apply. The unresolved decisions above are specification blockers for the affected later phases, not reasons to invent policy in PH-00.

Next:

1. Complete static documentation/link/ID/decision-status review and inspect the full Git diff.
2. Human reviews the specification and proposed ADRs/DEC-002 entries; only the human may approve/supersede decisions.
3. Commit and push this work on `ph00/development`; open a PR to `main` for human review, without merging.
4. Independent QA works from the updated accepted base and produces `qa-report.md`.
5. Human phase owner reviews QA and records phase acceptance. Do not start dependent phases before acceptance.

## 8. Phase readiness

**Development specification:** ready for independent documentation QA after static checks are recorded.
**PH-00 gate:** not ready for acceptance. QA, human review and specified open decisions remain outstanding.
**Implementation readiness:** PH-00 does not authorize implementation; follow phase gates and decision owners.
