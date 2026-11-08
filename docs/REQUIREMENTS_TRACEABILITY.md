# PH-00 Requirements Traceability

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for QA audit
**Trace:** product requirements → approved UX → logical domain/data → permission/risk control → future acceptance test → implementation phase

## 1. ID conventions

- Product requirements: `FR-###`; non-functional: `NFR-*`.
- UI experience requirements retain their source IDs `PH-00-UX-*` in [the eight UI source documents](./phases/PH-00/README.md); this file references ranges and selected anchors without duplicating them.
- Future acceptance tests use `AT-###` in [TEST_STRATEGY.md](./TEST_STRATEGY.md).
- Threats use `TH-##` in [SECURITY_MODEL.md](./SECURITY_MODEL.md).
- Decisions and open questions are in `docs/decisions/`.

## 2. Functional traceability matrix

| Product requirement | UX trace | Domain/data | Permission / risk | Future test | Owning phase |
|---|---|---|---|---|---|
| FR-001 Public read without login | UX-071, 080, 150–161; J01 | Person, constituency, public projection | Anonymous read only; data minimization | AT-001 | PH-06/07/17 |
| FR-002 Person/term/history separation | UX-081, 181; persona P1 | Person, candidacy, result, OfficeTerm, PartyMembership | TH-11 provenance | AT-002 | PH-06/07 |
| FR-003 Provenance/correction path | UX-180–186, 120–123 | Source, SourceSnapshot, RecordVersion | Editor/reviewer separation; TH-09/11 | AT-003 | PH-08/10 |
| FR-004 Promise/responsibility | UX-082, 167, 182; FLOW-03 | Promise, ResponsibilityLink, Source | Attribution review; TH-11 | AT-004 | PH-08/09 |
| FR-005 Evidence/review/versioning | UX-183, 185–186; J11 | Evidence, Adjudication, RecordVersion | No silent overwrite; TH-14 | AT-005 | PH-09/10 |
| FR-006 Editorial adjudication | UX-135–137; J11 | ReviewCase, Adjudication | No self-approval; TH-03/11 | AT-006 | PH-08/10 |
| FR-007 Submissions/reply | UX-115–117, 130–133; J06/J09 | Submission, RightOfReply, Evidence | Pending label, scoped moderation; TH-12 | AT-007 | PH-10/14 |
| FR-008 Correction/appeal | UX-120–126; FLOW-08 | CorrectionRequest, Appeal, RecordVersion | Independent reviewer; TH-11 | AT-008 | PH-10/14 |
| FR-009 Profile claim | UX-130–133; J09 | ProfileClaim, RightOfReply | Q10 unresolved; claimant cannot suppress | AT-009 | PH-10 |
| FR-010 Verification tier separation | UX-090, 095–100; J03/J04 | Account, ContactMethod, VerificationCase | TH-07; OTP not proof | AT-010 | PH-03/05 |
| FR-011 Accessible verification and appeals | UX-095–100, 520–522 | VerificationCase/Evidence | Least privilege, reviewer separation; TH-07 | AT-011 | PH-05 |
| FR-012 Eligibility enforcement | UX-105, 111, 265–266 | EligibilityRecord, Promise | Server-only; no staff vote; TH-02/05 | AT-012 | PH-05/15 |
| FR-013 One active evaluation/revision | UX-107, 108; FLOW-04 | Evaluation, Revision, opaque subject | Idempotency; TH-05 | AT-013 | PH-15 |
| FR-014 Confidential non-coercive receipt | UX-098, 108, 203, 267 | EvaluationSubject, Evaluation, private voter confirmation | Only authenticated voter sees own choice; non-shareable/non-exportable; TH-06 | AT-014 | PH-15 |
| FR-015 Public aggregate suppression | UX-109, 184, 403 | AggregateSnapshot | Distinct from private confirmation; Q01 open; TH-06 | AT-015 | PH-15/16 |
| FR-016 Separate measures | UX-165, 189, 440; FLOW-03 | Adjudication, Evaluation, Coverage, ScoreSnapshot | No admin override; TH-11 | AT-016 | PH-16/17 |
| FR-017 Like-for-like comparisons | UX-159–160, 535 | ScoreSnapshot/cohort | Explain non-comparability | AT-017 | PH-16/17 |
| FR-018 Financial/affiliation labels | UX-187–188 | Disclosure, DisclosureItem, Affiliation | Sensitive editorial review; TH-11 | AT-018 | PH-12/13 |
| FR-019 Projects/activity history | UX-181, 188 | Project, Agency, Affiliation, PublicActivity | Temporal provenance; TH-09/11 | AT-019 | PH-11/13 |
| FR-020 Moderation and appeal | UX-115–117, 125–126; J13 | ModerationCase, Appeal | Neutral rules; TH-12 | AT-020 | PH-14 |
| FR-021 RBAC/separation | UX-135–137, IA-153–154 | PermissionGrant, ReviewCase | TH-02/03 | AT-021 | PH-04 |
| FR-022 Impersonation | UX-154, 539; J14 | ImpersonationSession, AuditEvent | No vote/verify/role mutation; TH-04 | AT-022 | PH-04 |
| FR-023 Tamper-evident audit | UX-200–205, 426 | AuditEvent, IntegrityCheckpoint | TH-14; no absolute immutability claim | AT-023 | PH-04 |
| FR-024 Source/import governance | UX-180, inventory 369 | Source, ImportJob, ImportReview | TH-09/15; no silent overwrite | AT-024 | PH-08/22 |
| FR-025 Account preferences/data request | UX account IA; inventory 338–341 | Account, ConsentRecord, Subscription | Q03/legal; TH-01 | AT-025 | PH-03/19 |
| FR-026 Localization | UX-072, 550–557 | Localized content/original source | Preserve source text | AT-026 | PH-02/20 |
| FR-027 Safe offline | UX-085–087, 560–565 | Public cache projection | TH-16; no sensitive queue/cache | AT-027 | PH-02/24 |
| FR-028 Accessible maps/boundaries | UX-251–252, 508 | Constituency, BoundaryVersion | Source/license review | AT-028 | PH-06/21 |
| FR-029 Transparency/API | UX-156–160, IA transparency | Methodology, Source, approved projection | Privacy/linkage review; TH-06/10 | AT-029 | PH-23 |
| FR-030 Election safeguards | UX-110, 190, 539; Q11 | ElectionConfigProposal, AuditEvent | Q11/legal gate; TH-17 | AT-030 | PH-25 |
| FR-031 Non-distorting reputation | UX-192, 268 | Reputation/Contribution (later design) | No score/vote influence | AT-031 | PH-18 |
| FR-032 Privacy-safe analytics | UX-203, 368 | AggregateSnapshot, restricted signals | Q01, least privilege; TH-06/08/12 | AT-032 | PH-25 |

## 3. Non-functional traceability summary

| NFR area | Specification/control | Future tests | Phase |
|---|---|---|---|
| Authorization/secrets/security | NFR-SEC-001–004; `SECURITY_MODEL.md`; `RBAC_MATRIX.md` | AT-021–023 and security suite | PH-01/04 |
| Privacy/data lifecycle | NFR-PRV-001–004; `PRIVACY_POLICY_REQUIREMENTS.md`; `DATA_MODEL.md` | AT-010–015, privacy review | PH-03/05/15 |
| Availability/recovery/performance | NFR-AVA-001–003, NFR-PERF-001–002 | AT-033–035 | PH-01/26 |
| Accessibility/responsive/localization/offline | NFR-A11Y*, NFR-UX*, NFR-I18N* | AT-026–028, accessibility audit | PH-02/20/24 |
| Portability/data integrity | NFR-PORT*, NFR-DATA*; ADRs 001/003 | AT-024, AT-036 | PH-01/08/22 |
| Observability/maintainability/testing/cost | NFR-OBS*, NFR-MNT*, NFR-TEST*, NFR-COST* | AT-035, AT-037, AT-038 | PH-01/26 |
| Performance and reliability | NFR-AVA*, NFR-PERF* | AT-033–035 | PH-01/26 |
| Neutrality | NFR-NEUT-001; decisions D01/D07/D09 | AT-016–020, AT-030/031 | PH-08–25 |

## 4. UI source coverage

The eight source files and their complete ID ranges are retained under `docs/phases/PH-00/` and indexed in its README. This range map prevents source IDs from being silently dropped; the detailed product rows above point to representative anchors, and each individual source requirement remains authoritative in its source file.

| UI source / ID range | Requirements represented | Product/NFR and test mapping |
|---|---|---|
| `user-personas.md`, UX-001–049 | User/access-state needs, synthetic personas, staff and abuse perspectives, digital literacy/accessibility | FR-001–032 as applicable; NFR-A11Y/UX/I18N/PRV; AT-001–038 |
| `user-journeys.md`, UX-050–149 | Anonymous/account/verification/evaluation/contribution/correction/appeal/claimant/admin journeys and journey requirements | FR-001–032 as applicable; NFR-*; AT-001–032 |
| `information-architecture.md`, UX-150–199 | Navigation, site maps, trust cues, fact/status hierarchy, neutrality and discovery | FR-001–029; NFR-NEUT/A11Y/UX; AT-001–009, AT-014–019, AT-026/029 |
| `service-blueprint.md`, UX-200–249 | Frontstage/backstage work, verification/voting/review/correction/reply and separation-of-duty checkpoints | FR-003–015, FR-020–023; NFR-SEC/PRV; AT-003–015, AT-020–023 |
| `low-fidelity-flows.md`, UX-250–299 | Search, profile, promise, evaluation, verification, admin, correction and reply paths/failures | FR-001–015, FR-020–023; AT-001–015, AT-020–023 |
| `screen-and-component-inventory.md`, UX-300–449 | Public/account/admin screens, permissions, states, components and interaction inventory | FR-001–032; NFR-*; AT-001–038 |
| `accessibility-and-responsive-principles.md`, UX-500–599 | WCAG target, responsive, language, offline/shared-device, loading/error/permission states | FR-026–028; NFR-A11Y/UX/I18N/PRV; AT-026–028, AT-034/037 |
| `ui-design-handoff.md` (D01–D10, Q01–Q13) | Approved product decisions, open questions, dependencies and design self-review | DEC-001, DEC-002; FR-001–032; AT-001–038 |

## 5. Coverage status and limitations

All FR-001–FR-032 map to at least one source UX anchor, a domain/data concept, a control or risk, a future acceptance test ID and an owning phase. The range map identifies complete UX source coverage; the independent PH-00 QA agent should verify individual ID integrity against source documents, rather than treating this range-level summary as a replacement for them. Tests are catalogue entries only; detailed test fixtures, environments and executable steps belong to the owning phase. PH-00 QA must independently verify IDs, decision status, links, policy consistency and acceptance criteria. No requirement is marked implementation-verified.
