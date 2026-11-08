# NetaMonitor Product Requirements

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review
**Decision owner:** Human project owner
**Scope:** Product contract and phased delivery; not implementation approval

## 1. Product purpose and boundaries

NetaMonitor is an India-first, non-partisan, evidence-led civic accountability platform. It makes dated, sourced public records about elected representatives and public commitments easier to inspect. It is not an official election system, a campaign tool, a measure of a person's worth, or a substitute for government or electoral processes.

The public experience must keep three concepts distinct:

1. **Evidence assessment:** editorially reviewed, source-backed assessment of eligible public commitments.
2. **Citizen assessment:** confidential, eligible citizens' opinions, shown only as approved aggregates.
3. **Evidence/data coverage:** what is and is not documented; incompleteness is not failure.

PH-00 defines requirements and proposals only. Feature ownership and implementation sequencing follow `phase-register.csv`; inclusion here does not authorize implementation before that phase's dependencies are accepted.

## 2. Actors and common rules

Actors: anonymous visitor; registered/contact-confirmed user; identity-verified user; constituency-verified user; contributor; profile claimant; scoped staff permissions (Data Editor, Content Reviewer, Verification Officer, Moderator, Support Admin, Analytics Viewer); SuperAdmin; and external source/provider.

Identity and verification states are attributes, not mutually exclusive job roles. Authorization is enforced server-side. All flows must preserve provenance, effective dates, language, accessible error handling and an appeal/correction route where a decision materially affects a person. See [the approved UX journeys](./phases/PH-00/user-journeys.md) and [traceability matrix](./REQUIREMENTS_TRACEABILITY.md).

## 3. Functional requirements

Requirements are stable PH-00 IDs. Acceptance statements are specification-level outcomes for future tests.

| ID | Requirement and acceptance criteria | Primary actor | Phase |
|---|---|---|---|
| FR-001 | Public records are readable without account creation or location permission. Search and manual constituency selection must work without choosing a location. | Anonymous visitor | PH-06, PH-07, PH-17 |
| FR-002 | A public profile distinguishes a person, candidacy, election result, office and dated term; historical terms and party memberships remain inspectable. | Visitor, editor | PH-06, PH-07 |
| FR-003 | Every material public assertion carries provenance: source/issuer, source date, retrieval or record date as relevant, attribution, review status and a correction route. | Visitor, editor | PH-08, PH-10 |
| FR-004 | Promise records preserve original wording/context, source, measurable criteria, due date, responsible authority and any shared attribution. Acceptance must not imply responsibility unsupported by evidence. | Visitor, editor | PH-08, PH-09 |
| FR-005 | Milestones, evidence, editorial adjudications and revisions are separately identifiable and historically retained; a revision never silently erases a prior public decision. | Reviewer | PH-09, PH-10 |
| FR-006 | Editorial promise status is assigned through a documented review process with evidence, reasons, reviewer separation and version history. Citizen votes never determine this status. | Content Reviewer | PH-08, PH-10 |
| FR-007 | The public can submit corrections, source-backed material and a right of reply through distinct workflows; pending submissions are labelled unreviewed and cannot change an adjudication. | Visitor, contributor, claimant | PH-10, PH-14 |
| FR-008 | A correction outcome is reasoned, dated and appealable where applicable; published corrections link to the prior version. Appeals are decided by a different reviewer. | Submitter, reviewer | PH-10, PH-14 |
| FR-009 | Profile claims require an owner-approved proof/authority process; a claimant may reply but may not remove sourced facts or edit editorial assessments. | Profile claimant | PH-10 |
| FR-010 | Account contact confirmation, identity verification and constituency verification are distinct states. OTP/contact confirmation is never represented as identity or residence proof. | User, Verification Officer | PH-03, PH-05 |
| FR-011 | Verification offers an assisted/non-digital route with equal standing to supported digital routes, minimal evidence collection, status tracking, expiry/re-verification and appeal. Method/vendor and retention remain gated. | User, Verification Officer | PH-05 |
| FR-012 | Citizen evaluation is available only to an eligible constituency-verified person, for an open/assessable promise, outside prohibited staff/impersonation and any owner/legal-approved pause. Server-side checks are authoritative. | Eligible citizen | PH-15 |
| FR-013 | An eligible person has at most one active evaluation per promise; any permitted change is explicit, confirmed and audited. No offline submission or retry may create a second active evaluation. | Eligible citizen | PH-15 |
| FR-014 | Individual vote choices and identity-to-choice mappings are never public; staff tools expose neither individual choices nor per-user vote history. A receipt is private, non-shareable, and must not function as coercive proof. | Citizen, staff | PH-15 |
| FR-015 | Public citizen reporting is aggregate-only. Publication, cohort and suppression rules remain blocked on Q01; no threshold is approved by this specification. | Visitor, analytics staff | PH-15, PH-16 |
| FR-016 | Evidence performance, citizen assessment and evidence/data coverage are calculated and presented separately with definitions, denominators, dates, exclusions, methodology version and limitations. No admin override or paid weighting. | Visitor, editor | PH-16, PH-17 |
| FR-017 | Comparisons and leaderboards use documented like-for-like cohorts and show insufficient-data and non-comparability states rather than implying equivalence. Cohort/ranking policy remains reviewable. | Visitor | PH-16, PH-17 |
| FR-018 | Public disclosures and financial/business facts are dated, sourced and labelled by evidentiary basis (self-declared, official record, independently corroborated); association is not evidence of wrongdoing. | Visitor, editor | PH-08, PH-12, PH-13 |
| FR-019 | Schemes, projects, agencies, affiliations, movements, protests and public accounts are represented with precise, dated relationships and source attribution. | Visitor, editor | PH-11, PH-13 |
| FR-020 | Moderation distinguishes reported, unreviewed, disputed and adjudicated material; applies documented, viewpoint-neutral rules, graduated actions, reasons, conflict review and appeal. | Contributor, Moderator | PH-14 |
| FR-021 | Role permissions follow least privilege and separation of duties. Admins cannot approve their own verification/content submissions; SuperAdmin powers are explicit, restricted, MFA-protected where approved, and audited. | Staff | PH-04 |
| FR-022 | Support impersonation is explicit, justified, time-bounded, visible to the operator and audited; it cannot vote, approve verification, or mutate security roles. | Support Admin | PH-04 |
| FR-023 | Audit records are append-only by application policy and tamper-evident with documented detection/recovery limits; privileged access is monitored. | Auditor, SuperAdmin | PH-04 |
| FR-024 | Source records capture owner, jurisdiction, licence/terms, provenance, update cadence, method, confidence/review and permitted use. Imports are reviewable and never silently overwrite authoritative history. | Editor, reviewer | PH-08, PH-22 |
| FR-025 | Users can manage account recovery, preferences, consent history, subscriptions, notifications and eligible data-access/deletion requests subject to documented retention and legal review. | Registered user | PH-03, PH-19 |
| FR-026 | Interface/content supports English, Hindi and Marathi without replacing source text with translation; translation language and source remain clear. | All | PH-02, PH-20 |
| FR-027 | Offline access is public, read-only and freshness-labelled; it never exposes identity evidence, private/account/admin data or an individual's evaluations, and never queues sensitive actions. | Visitor | PH-02, PH-24 |
| FR-028 | Public maps/geographic views have an accessible non-map alternative and use effective-dated boundaries. | Visitor | PH-06, PH-21 |
| FR-029 | Public methodology, funding, source practices, platform limitations, correction routes and approved open-data/API terms are inspectable. Public data must exclude restricted/personal information. | Visitor | PH-23 |
| FR-030 | Election-related restrictions are configurable only after jurisdiction-specific owner and legal review; no universal legal safe harbour or policy is asserted. | Staff, visitor | PH-25 |
| FR-031 | Gamification/reputation, if approved in its phase, rewards constructive contributions only and cannot affect votes, evidence status, ranking weights or editorial decisions. | Contributor | PH-18 |
| FR-032 | Analytics and anti-manipulation workflows use minimum necessary data, restrict individual-level access, suppress small groups under approved rules, and support accountable review/appeal. | Analytics Viewer | PH-25 |

## 4. Lifecycle and interaction states

The detailed state models are in [the domain model](./DOMAIN_MODEL.md), [verification policy](./VERIFICATION_POLICY.md), [moderation policy](./MODERATION_POLICY.md) and [security model](./SECURITY_MODEL.md). User-facing evaluation eligibility has eight mutually exclusive explanatory states, not eight identity states:

1. Signed out.
2. Account registered/contact-confirmed but identity verification incomplete.
3. Identity verified but no matching verified constituency.
4. Eligible, promise open and evaluation permitted.
5. Promise not open/not assessable.
6. Admin/SuperAdmin context or active impersonation (evaluation prohibited).
7. Applicable election-period restriction (only after approval).
8. Account suspended/restricted, with available appeal information.

The evaluation decision service evaluates disqualifiers server-side in a documented precedence order and returns only the minimum safe explanation. After sign-in or a changed status, eligibility is re-evaluated. A policy decision may add a new public state; it must not be hidden inside a generic success/failure response.

## 5. Product scope and phase allocation

All roadmap capabilities in `phase-register.csv` are in the product vision, but PH-00 commits only their requirements. User accounts/authentication (PH-03); authorization/audit (PH-04); verification (PH-05); geography/elections (PH-06); people/terms (PH-07); CMS/provenance (PH-08); promises (PH-09); evidence/corrections (PH-10); projects (PH-11); financial disclosures (PH-12); affiliations (PH-13); submissions/moderation (PH-14); evaluation privacy (PH-15); scoring (PH-16); discovery (PH-17); reputation (PH-18); notifications (PH-19); localization (PH-20); maps (PH-21); imports (PH-22); transparency/API (PH-23); offline (PH-24); analytics/election safeguards (PH-25); hardening/launch (PH-26).

Local persona assumptions, pilot geography, sources, service levels, thresholds, identity routes and legal interpretations are not validated product facts. They remain open until the named owner/reviewer records a decision.

## 6. Approved decisions and open questions

Owner-approved UI decisions D01–D10 are recorded in [DEC-001](./decisions/DEC-001-ui-experience-baseline.md); approval does not resolve separate legal, privacy or operational questions. Remaining questions are tracked in [DEC-002](./decisions/DEC-002-open-product-and-policy-questions.md). Proposal statuses and ADRs are indexed separately.

## 7. Acceptance criteria for PH-00 specification

- Every FR has an implementation phase and a future acceptance criterion.
- All eight UI deliverables and their `PH-00-UX-*` IDs map into traceability; no duplicate copies are introduced.
- The three assessment concepts remain separate throughout requirements, domain, data, scoring and UX.
- Sensitive data classes, controllers/access, lifecycle and unresolved retention decisions are explicit.
- Proposed technical choices remain proposed; only owner-approved D01–D10 may be accepted in the PH-00 records.
- No unresolved critical/high contradiction is hidden; policy/legal gates identify owners and gating phases.
- PH-00 remains documentation-only; human QA and acceptance remain outstanding.
