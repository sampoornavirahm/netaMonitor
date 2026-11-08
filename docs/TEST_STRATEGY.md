# NetaMonitor Future Test Strategy and Acceptance-Test Catalogue

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Test design only; no tests executed
**Decision owner:** Human project owner · **PH-00 QA:** specification audit only

## 1. Scope and principles

This document defines future verification, not executable tests or a commitment to a specific test runner. PH-00 has no application to run. Vitest is the proposed unit/integration runner and Playwright the proposed browser E2E runner in the existing baseline; PH-01 must confirm exact tools/commands. Use deterministic synthetic persons, offices, constituencies, elections, promises, sources, accounts and submissions only. Never use real identity documents, voter records, production data or actual politicians as test fixtures. No test may weaken a security control to pass.

Map every acceptance test to FR/NFR, UX ID, data entities, permission, threat/control and implementation phase in [the traceability matrix](./REQUIREMENTS_TRACEABILITY.md). Establish clean-clone commands and CI in PH-01. The proposed Vitest/Playwright/axe-core tools remain subject to ADR/PH-01 acceptance.

## 2. Test levels and ownership

| Level | Purpose | Examples | Owner |
|---|---|---|---|
| Unit/domain | Pure state transitions, scoring, temporal rules, input/permission policy | Due-promise eligibility, score denominator, appeal transitions | Feature developer |
| Integration | API/service, repository, transaction, authz, provider adapter contracts | Self-approval denied; import reconciliation; one active evaluation | Feature developer |
| API contract | OpenAPI/schema compatibility, runtime request/response validation, version compatibility and provider adapter behavior | Contract tests for client/server compatibility and replacement auth/object adapter | PH-01/API owners |
| Security | Abuse cases, authorization, session, uploads, rate limits, audit integrity | IDOR, privilege escalation, impersonation denials | Security reviewer |
| Privacy | Data-flow, role access, cache/log/export, aggregate linkage | No vote identity/choice join in staff/public surfaces | Privacy/security reviewer |
| Accessibility | Keyboard/screen reader, semantic structure, contrast, zoom/reflow, charts/maps | WCAG 2.2 AA target journeys | Design/QA |
| Performance/reliability | Representative low bandwidth, load, timeout, backup/restore and failure | Public browse, fail-closed evaluation, restore exercise | Operations/QA |
| Playwright E2E (proposed) | Independent role journeys against a running implementation in a controlled test environment | Anonymous browse; verify; evaluate; correction/reply; failure states | Independent QA agent |
| Manual editorial/policy | Sourcing, neutrality, legal/privacy review and decision governance | Disclosure labels, election-mode sign-off | Human owner/editor/counsel |

## 3. Synthetic fixture policy

Use clearly synthetic IDs/names and isolated test domains, e.g. `SYN-PER-001`, `SYN-CON-001`, `SYN-ACC-001`. Avoid names likely to identify real politicians or residents. Do not copy real source content unless separately approved and legally suitable; synthetic sources must be labelled. Test privacy scenarios include small cohorts and colluding roles without exposing real people.

## 4. Future acceptance-test catalogue

Each entry describes expected observable behavior. Exact harness, datasets and commands are chosen in the implementation phase. `AT-033`–`AT-038` cover shared non-functional requirements.

| ID | Scenario | Expected outcome | Trace / phase |
|---|---|---|---|
| AT-001 | Anonymous visitor searches/browses without account or location permission | Public records accessible; ambiguous match is not auto-selected | FR-001, UX-071/080; PH-17 |
| AT-002 | Person has candidacies, distinct results, terms and dated party history | Each relationship remains distinct and historical records are not overwritten | FR-002; PH-07 |
| AT-003 | Publish and later correct a sourced material fact | Provenance, reviewer, dates, correction route and prior version remain visible | FR-003/008; PH-08/10 |
| AT-004 | Promise has shared agency responsibility and incomplete evidence | Responsibility and evidence gaps are explicit; no unsupported attribution | FR-004; PH-09 |
| AT-005 | Evidence/review status changes after appeal or new source | New version and adjudication link to prior state; no silent destructive edit | FR-005; PH-10 |
| AT-006 | Author attempts to approve own submission | Server rejects; audit/decision trail records attempt as policy defines | FR-006/021, TH-03; PH-04/10 |
| AT-007 | Pending user evidence/reply is viewed publicly | Clearly marked unreviewed/pending; does not change score or adjudication | FR-007; PH-14 |
| AT-008 | Correction is declined and appealed by a different reviewer | Reason and appeal path shown; reviewer differs; prior public version retained | FR-008; PH-10 |
| AT-009 | Unverified delegate tries to claim or edit a profile | Claim awaits approved verification; cannot suppress/edit sourced facts | FR-009, Q10; PH-10 |
| AT-010 | Contact confirmed, but identity/constituency tiers incomplete | UI/API never treats OTP as identity/residence proof or permits evaluation | FR-010; PH-03/05 |
| AT-011 | Digital verification provider unavailable; assisted route used | No route receives privileged bypass; case remains trackable and appealable | FR-011; PH-05 |
| AT-012 | Signed-out, unverified, wrong-constituency, staff and suspended subjects evaluate | Each receives safe, correct explanatory state; server denies write | FR-012; PH-15 |
| AT-013 | Eligible subject retries, double-submits, and changes an evaluation | At most one active choice; explicit revision; replay is idempotent | FR-013, TH-05; PH-15 |
| AT-014 | Voter views their confirmation; another person requests shareable proof, or staff requests an individual choice | Only the authenticated voter sees a private, non-shareable/non-exportable confirmation of their own submitted choice; it cannot expose another person's vote or be verified/shared as proof; staff/public cannot retrieve individual choices | FR-014, TH-06; PH-15 |
| AT-015 | Public results/aggregates are queried at small cohort and with overlapping filters | Public results are distinct from private voter confirmations; until Q01-approved policy, no public aggregate publication; after approval, no disallowed small-cell/differencing leakage or individual linkage | FR-015; Q01; PH-15/16 |
| AT-016 | Promise statuses and citizen choices differ; evidence is incomplete | Separate output modules and measures; no composite, vote-driven editorial status or manual override | FR-016, D01/D09; PH-16 |
| AT-017 | Compare unlike offices or term windows | UI states non-comparable; no misleading common rank | FR-017; PH-17 |
| AT-018 | Financial item is self-declared; affiliation is a protest participation | Labels accurately describe source/basis/role; no net-worth or wrongdoing inference | FR-018; PH-12/13 |
| AT-019 | Import changes an effective-dated term or public project | Staging/reconciliation preserves previous version and identifies source/reviewer | FR-019/024; PH-11/22 |
| AT-020 | Moderation action targets criticism of opposing political viewpoints | Same published rule is applied; reason, appeal and reviewer are recorded | FR-020; PH-14 |
| AT-021 | Direct API call bypasses hidden admin navigation | Server denies missing scope/permission, self-approval or access to protected object | FR-021, TH-02; PH-04 |
| AT-022 | Support impersonates a user and tries evaluation, verification approval or role change | Persistent true-actor indicator; prohibited actions denied; session expires and is audited | FR-022, TH-04; PH-04 |
| AT-023 | Authorized tester alters/removes an audit record or breaks a chain | Integrity monitoring detects discrepancy; recovery limitations are documented | FR-023, TH-14; PH-04 |
| AT-024 | Import contains duplicate, poisoned, unlicensed or personal data | Quarantine/review prevents silent publication; provenance/license and reject reasons recorded | FR-024, TH-09; PH-08/22 |
| AT-025 | User requests account recovery, export or deletion | Only own authorized request processed; sensitive retention/legal exception is transparent and reviewed | FR-025, Q03; PH-03 |
| AT-026 | User switches language mid-form and reads source/translation | Input/place preserved; source language and translation attribution clear | FR-026; PH-20 |
| AT-027 | Device goes offline and reconnects during evaluation/admin action | Only stale public content appears with date; no private cache or queued/false success action | FR-027, TH-16; PH-24 |
| AT-028 | Constituency map is unavailable or historical boundary selected | Equivalent accessible list available; effective date/source clear | FR-028; PH-21 |
| AT-029 | Public API/open data request asks for sensitive fields | Allowlisted public projection excludes personal, restricted and individual evaluation data | FR-029, TH-06; PH-23 |
| AT-030 | Election mode proposed without approved jurisdiction policy | No unapproved restriction activates; proposal/audit/legal review required | FR-030, Q11, TH-17; PH-25 |
| AT-031 | Gamification/reputation changes or badge is awarded | No score, vote weight, rank or editorial status changes as a side effect | FR-031; PH-18 |
| AT-032 | Analytics query combines low-volume dimensions | Aggregation controls block or suppress disclosure; no identity/choice drill-down | FR-032, TH-06/08; PH-25 |
| AT-033 | Supported access path loses an upstream provider | Sensitive actions fail closed with no success-shaped fallback; public read degrades safely | NFR-AVA; PH-01/26 |
| AT-034 | Keyboard, screen reader, zoom, contrast, narrow viewport and chart/map alternatives | Core journeys meet approved accessibility criteria/target with no lost function | NFR-A11Y/UX; PH-02 |
| AT-035 | Representative pilot workload and low-bandwidth device | Measured performance meets owner-approved budgets; otherwise defect logged | NFR-PERF; PH-01/26 |
| AT-036 | Replace an adapter or restore database/object data | Contract/portability and restore procedure preserve records and audit lineage | NFR-PORT/DATA/AVA; PH-01/26 |
| AT-037 | Logs, analytics, cache and notifications inspected for sensitive content | No credential, identity evidence or unnecessary personal/choice data leaks | NFR-PRV/OBS; PH-01/05/15 |
| AT-038 | Clean clone runs documented quality gates | Commands and outcomes match README and CI; no hidden local dependency | NFR-MNT/TEST; PH-01 |

## 5. PH-00 specification QA (not executable E2E)

Independent QA should check: required files exist; IDs are unique/referenced; every FR/NFR has trace/test/owner; all UX IDs are either mapped or explicitly not applicable; Mermaid syntax is valid; links resolve; D01–D10 are accepted only as owner-approved; open questions remain open; eight evaluation states reconcile; no API/schema/provider/vendor/legal claim is silently accepted; data classifications and lifecycles are covered; score/privacy/election contradictions are absent; and no application code/migrations/tests were introduced. QA produces `qa-report.md`; the human owner decides acceptance.
