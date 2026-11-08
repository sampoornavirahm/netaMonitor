# NetaMonitor Logical Domain Model

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review

## 1. Model principles

- Separate public civic records from account, verification, security and evaluation-identity domains.
- Separate a person from account, candidacy, election result, office and term.
- Preserve effective-time history and recorded-time history; corrections append new versions rather than overwriting evidence.
- Link every material assertion to source, attribution, review state and correction path.
- Keep evidence adjudication, citizen opinion and data coverage as different bounded contexts and measures.
- Model permissions as grants over actions/resources; verification status is not a role.

## 2. Bounded contexts

| Context | Owns | Must not own |
|---|---|---|
| Public civic record | Persons, offices, constituencies, elections, terms, parties, promises, projects, disclosures, affiliations, sources, evidence and publication versions | Account credentials, identity evidence, vote identity mapping |
| Editorial governance | Review assignments, adjudications, corrections, replies, appeals, moderation and publication decisions | Citizen vote choice or identity verification documents |
| Account and verification | Accounts, contact state, consent, recovery, verification cases/evidence, eligibility facts | Public editorial status; vote choices |
| Evaluation privacy | Eligibility references, opaque subject/token mapping, choices, revisions and disclosure-safe aggregates | Identity evidence, public user profiles or staff-visible individual choices |
| Administration and audit | Permission grants, privileged session/impersonation, audit events, election-mode configuration proposals | Unrestricted bypass of domain rules |
| Delivery/integration | Import jobs, notification requests, object metadata, provider adapters | Provider-specific business rules |

## 3. Core entities and relationships

### Public and political records

- `Person` 1—N `Candidacy`; `Person` 1—N `OfficeTerm`; `Person` 1—N `PartyMembership`.
- `OfficeType` 1—N `OfficeTerm`; `Constituency` 1—N `OfficeTerm` and `BoundaryVersion`.
- `ElectionEvent` 1—N `Candidacy` and `ElectionResult`; election result does not itself create a term without a reviewed/authoritative basis.
- `Promise` N—1 originating `Person`/`OfficeTerm` (where applicable); 1—N `Milestone`, `PromiseSource`, `Evidence`, `Adjudication`, `Correction` and `ResponsibilityLink`.
- `Evidence` N—N `Source`; each relationship carries a relevance/claim reference. `Adjudication` references the reviewed evidence and a methodology/status version.
- `PublicProject` N—N `ImplementingAgency`, `Promise` and `Source`; involvement/credit is explicit and sourced.
- `FinancialDisclosure` 1—N `DisclosureItem`, each item dated/scoped and labelled by basis. `Affiliation` links Person to Organisation/Event/SocialAccount with typed, temporal role and evidence.

### Account, restricted verification and evaluations

- `Account` 1—N `ContactMethod`, `ConsentRecord`, `VerificationCase`, `Subscription`, `Submission` and `AuditActorReference`.
- `VerificationCase` 1—N restricted `VerificationEvidence` and decisions. Review assignment and outcome identify reviewer and prevent self-approval.
- `VerifiedEligibility` binds an account subject to a constituency and validity interval; it stores only approved minimum facts, not public residence evidence.
- `EvaluationSubject` is an opaque, purpose-limited reference derived from an eligible account; the restricted mapping service prevents direct identity lookup from the choice store.
- `PromiseEvaluation` references promise, opaque subject and choice. Revision history is controlled; at most one active choice per eligible subject/promise under a proposed invariant.
- `AggregateSnapshot` references methodology/suppression policy version, cohort/window and disclosure-safe counts; it must not permit small-cell or differencing disclosure.

### Governance and history

- `SourceRegistryEntry`, `SourceSnapshot`, `ImportJob` and `ImportReview` preserve source terms, retrieval/input hash, transformations, reconciliation and reviewer outcome.
- `PublishedRecordVersion` identifies public snapshots and correction links; current publication is a pointer to a version, not destructive replacement.
- `ReviewCase`, `CorrectionRequest`, `RightOfReply`, `Appeal` and `ModerationCase` retain lifecycle, reasons, dates, access and reviewer separation.
- `AuditEvent` references actor, action, target, time, reason/correlation and integrity predecessor/checkpoint where applicable. No single-database absolute-immutability claim.

## 4. Lifecycle models

### Citizen evaluation eligibility (eight explanatory outcomes)

The UI describes exactly one primary state to the user. It is a derived authorization result, not a persisted role:

1. `SIGNED_OUT`
2. `IDENTITY_REQUIRED` (registered/contact confirmed, identity step incomplete)
3. `CONSTITUENCY_REQUIRED` (identity verified, no currently matching constituency eligibility)
4. `ELIGIBLE` (all account, constituency, promise and policy conditions pass)
5. `PROMISE_NOT_OPEN` (not due, under review, withdrawn/out-of-scope or otherwise not accepting evaluations)
6. `STAFF_CONTEXT_BLOCKED` (admin/SuperAdmin context or impersonation)
7. `POLICY_PAUSED` (applicable, owner/legal-approved election-period restriction)
8. `ACCOUNT_RESTRICTED` (suspension or relevant restriction; disclose appeal path where safe)

`ELIGIBLE` is returned only after all disqualifying conditions pass. A deterministic precedence rule prevents revealing multiple sensitive reasons: account restriction → staff/impersonation prohibition → policy pause → promise not open → sign-in → identity → constituency → eligible. Product/security review may change copy or safe precedence; it may not weaken enforcement. The eight states are explanatory UX outcomes, not eight mutually exclusive database statuses. This formalizes the seven baseline outcomes plus the separately shown election pause in the source flows.

### Other state machines

| Object | Proposed lifecycle (transitions require actor, reason, time and audit) |
|---|---|
| Account | `created → contact_pending → contact_confirmed → restricted/closed`; recovery is a separate verified process, not identity verification. |
| Verification case | `draft → submitted → in_review → needs_information ↔ in_review → approved/declined → appealed → appeal_decided → expired/revoked`; decision owner and retention are open. |
| Promise | `draft → submitted_for_review → published → under_review → adjudicated`; correction creates a new version, not an overwrite. Due/withdrawn/out-of-scope are domain conditions with reason, not deletion. |
| Evidence | `submitted → safety_triage → editorial_review → accepted/rejected/disputed/superseded`; user-submitted status is visible until reviewed. |
| Publication | `draft → review → approved → published → corrected/withdrawn`; every public transition has immutable version reference and provenance. |
| Correction / reply | `submitted → triaged → in_review → needs_information ↔ in_review → accepted/partly_accepted/declined → appealed → appeal_decided → closed`; a reply follows `draft → moderation → published/needs_edit/declined → appealed/closed` and never replaces the source record. |
| Evaluation | `eligible → active_choice → revised_choice/withdrawn` subject to policy; a failed network response is not a success. One active choice invariant is proposed, not implementation. |
| Admin action | `requested → authorized → executed/denied → audited`; sensitive actions may require dual control, re-authentication and incident review. |
| Impersonation | `requested(reason,target) → approved → active(visible, expiry) → ended/expired/revoked`; vote, verification approval and security-role changes are denied while active. |

## 5. Domain invariants

1. Never conflate person, account, candidacy, result and office term.
2. Effective start/end dates and source history are retained; overlap conflicts are surfaced for review, not silently normalized.
3. Every public claim has provenance and a revision/correction route.
4. Editorial status is not derived from citizen responses.
5. Vote choice is not joined to public person/account identity in public queries or staff tools.
6. Verification evidence is not copied into a public record or analytics event.
7. Financial disclosure label describes evidence basis and as-of date; it is not an inferred net-worth verdict.
8. Affiliation/participation is a specific relationship, not an allegation.
9. `current`/`former` is derived from effective dates and as-of time; historical truth is not overwritten.
10. Constraints that depend on unresolved policy (including vote suppression and retention) remain unapproved configuration, not hard-coded defaults.

## 6. Identifiers, cardinality and temporal conventions

Every entity receives a stable, opaque internal identifier; public-facing identifiers, where needed, must not reveal sequence-sensitive or personal information. Relationships use explicit references and documented cardinality (the ERD shows core 1:N and optional relationships; N:N associations use link entities). Do not use a person's name, phone, address or provider account ID as a primary domain identifier.

Where a relationship changes over time, store an effective interval independently of recorded/transaction time. Open-ended intervals are represented explicitly. Date-only office terms and timestamped audit events have distinct precision; timezone and calendar conventions are chosen in PH-01. Boundary versions, source snapshots, disclosures, adjudications, corrections and evaluations are versioned/referenced rather than destructively replaced.

## 7. Open modeling questions

Identity resolution/duplicate person handling, exact office taxonomy and subnational boundary authority, representative profile-claim proof, evidence confidence vocabulary, legal basis/retention, election-window behavior, public data schema and evaluation suppression require owner/legal review in their assigned phases.
