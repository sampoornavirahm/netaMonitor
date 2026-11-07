# NetaMonitor PH-00 — Screen and Component Inventory

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-300` to `PH-00-UX-449`

> An inventory for later design phases (PH-02 design system onward). It lists **what** must exist and **what it must communicate**. It defines no visual design, layout grid, tokens, component code or API contract. "Capability" entries are labels for traceability only. All data in examples is synthetic.

## 1. Screen inventory

Columns: **ID** · screen · access · journey/flow · capability labels · key states (L loading, E empty, V validation, P permission, X error, O offline). Offline "—" means not available offline.

### 1.1 Public screens

| ID | Screen | Access | Flow | Capability labels | L / E / V / P / X / O |
|---|---|---|---|---|---|
| PH-00-UX-300 | Home | Anonymous | J01 | `public.search`, `geo.lookup` | L skeleton · E n/a · V min length hint · P — · X retry · O cached recents |
| PH-00-UX-301 | Search results | Anonymous | J01 | `public.search` | L · E "no match, try another spelling" · V — · P — · X retry · O cached |
| PH-00-UX-302 | Constituency selector | Anonymous | J01 | `geo.lookup` | L incremental · E "not covered yet" · V level hints · P — · X list fallback · O cached hierarchy |
| PH-00-UX-303 | Disambiguation list | Anonymous | J01 | `public.profile.read` | L · E — · V — · P — · X retry · O cached |
| PH-00-UX-304 | Representative profile | Anonymous | FLOW-02 | `public.profile.read` | per-module L/E/X · O cached with stale label |
| PH-00-UX-305 | Promise list | Anonymous | FLOW-02 | `public.promise.read` | L · E "no promises recorded" · O cached |
| PH-00-UX-306 | Promise detail | Anonymous | FLOW-03 | `public.promise.read`, `scoring.explain` | per-module L/E/X · O cached; evaluation replaced by needs-connection note |
| PH-00-UX-307 | Elections and terms timeline | Anonymous | FLOW-02 | `public.profile.read` | L · E · O cached |
| PH-00-UX-308 | Schemes and projects list and detail | Anonymous | FLOW-02 | `public.project.read` | L · E · O cached |
| PH-00-UX-309 | Financial disclosures | Anonymous | FLOW-02 | `public.disclosure.read` | L · E "none published for this term" · O cached |
| PH-00-UX-310 | Affiliations and public activity | Anonymous | FLOW-02 | `public.affiliation.read` | L · E · O cached |
| PH-00-UX-311 | Compare | Anonymous | IA | `public.compare.read` | L · E "pick up to three like-for-like" · X block cross-office · O cached |
| PH-00-UX-312 | Leaderboards (separate evidence and citizen views) | Anonymous | IA | `public.leaderboard.read` | L · E "not enough data" · O cached |
| PH-00-UX-313 | Transparency centre (methodology, funding, source register, changelog, open data) | Anonymous | IA | `transparency.read` | L · E · O cached |
| PH-00-UX-314 | Correction form | Anonymous or user | J07 | `correction.create` | L progress · V required source · P rate-limit message · X draft kept · O — |
| PH-00-UX-315 | Contribute hub and forms (evidence, suggestion) | Registered (limited anonymous) | J06 | `submission.create` | L · V · P · X · O — |
| PH-00-UX-316 | Help, legal, accessibility statement | Anonymous | IA | — | O cached |
| PH-00-UX-317 | Not available (neutral denied or missing page) | Any | IA | — | all states share one neutral message |
| PH-00-UX-318 | Election-period notice (inline region, not a screen) | Any | IA | `election.mode.read` | scope and dates shown |

### 1.2 Account screens

| ID | Screen | Access | Flow | Capability labels | States |
|---|---|---|---|---|---|
| PH-00-UX-330 | Create account and consent summary | Anonymous | J03 | `auth.register`, `consent.record` | V · P throttle · X |
| PH-00-UX-331 | Confirm contact | Anonymous | J03 | `auth.confirm_contact` | V · X resend |
| PH-00-UX-332 | Sign in | Anonymous | FLOW-06 | `auth.session` | V · X neutral · O — |
| PH-00-UX-333 | Verification status | Registered | J04 | `verification.status` | tiers, expiry · P tier gating |
| PH-00-UX-334 | Verification wizard (steps 0 to 3) | Registered | FLOW-05 | `verification.apply`, `consent.record` | L upload · V per field · X outage → assisted · O — |
| PH-00-UX-335 | Verification tracker and appeal | Registered | J04, J08 | `verification.status`, `verification.appeal` | needs-info, decided |
| PH-00-UX-336 | Evaluation module (embedded in 306) | Any (eight states) | FLOW-04 | `ballot.eligibility`, `ballot.cast`, `ballot.change`, `ballot.aggregate.read` | all eight eligibility states |
| PH-00-UX-337 | My evaluations | Constituency verified | J05 | `ballot.own.read` | E · O — (private, never cached) |
| PH-00-UX-338 | My submissions and corrections | Registered | J06, J07 | `submission.track`, `correction.track` | E · X |
| PH-00-UX-339 | Following and notifications | Registered | IA | `follow.manage`, `notify.preferences` | E · V |
| PH-00-UX-340 | Privacy, consent history, data export and deletion | Registered | IA | `consent.history`, `account.export`, `account.delete` | confirmation steps |
| PH-00-UX-341 | Language and accessibility preferences | Any | IA | `i18n.locale` | — |
| PH-00-UX-342 | Delegate: claim profile | Delegate | J09 | `profile.claim` | V · pending review |
| PH-00-UX-343 | Delegate: reply composer and preview | Claimed delegate | J09 | `reply.submit`, `reply.preview` | V · moderation states |

### 1.3 Admin screens (permission-driven)

| ID | Screen | Sub-role | Flow | Capability labels | States |
|---|---|---|---|---|---|
| PH-00-UX-360 | Admin dashboard | Any Admin | FLOW-07 | `admin.tasks` | E "nothing assigned to your permissions" |
| PH-00-UX-361 | Content editor | Data Editor | J10 | `cms.draft` | V completeness · X conflict |
| PH-00-UX-362 | Review queue and item diff | Content Reviewer | J11 | `cms.review` | E · P self-authored · X conflict |
| PH-00-UX-363 | Adjudication form and evidence viewer | Content Reviewer | J11 | `adjudication.record` | V reason required |
| PH-00-UX-364 | Corrections and appeals queue | Content Reviewer | J07, J08 | `correction.decide`, `appeal.decide` | E · V |
| PH-00-UX-365 | Verification queue and minimal evidence view | Verification Officer | J12 | `verification.review` | E · P own application hidden |
| PH-00-UX-366 | Moderation queue and report context | Moderator | J13 | `moderation.decide` | E · V |
| PH-00-UX-367 | Support tools and impersonation start | Support Admin | J14 | `impersonation.start`, `impersonation.stop` | V reason and second factor |
| PH-00-UX-368 | Analytics (aggregate) and anomaly cases | Analytics Viewer | J15 | `analytics.read` | E "not enough data" |
| PH-00-UX-369 | Imports and reconciliation | Data Editor, Content Reviewer | IA | `import.review` | E · X |
| PH-00-UX-370 | Roles and permissions | Delegated role administrator, SuperAdmin | J16 | `role.manage` | confirmation step |
| PH-00-UX-371 | Audit viewer | Permitted roles | FLOW-07 | `audit.read` | chunked L · E · X chain-integrity warning |
| PH-00-UX-372 | Restricted workspace (settings, break-glass, election mode) | SuperAdmin | J16 | `settings.manage`, `election.mode.manage` | second factor · confirmation |

### 1.4 Screen requirements

| ID | Requirement |
|---|---|
| PH-00-UX-380 | A screen lists only capabilities it needs. Development must not introduce capabilities without a documented design change; gaps are raised as blockers in the handoff. |
| PH-00-UX-381 | Every screen family defines all of loading, empty, validation, permission, error and offline behaviour, even where the answer is "not applicable". |
| PH-00-UX-382 | Screens that are not available offline (336, 337, 314, 315 and all account and admin screens) show "Needs an internet connection" and never queue the action. |

## 2. Reusable component inventory

Components are described by purpose and content rules, not by appearance.

| ID | Component | Purpose and content rules |
|---|---|---|
| PH-00-UX-400 | Provenance cue | Source name, issuer type, original and retrieval dates, review status, correction link. One interaction to expand. |
| PH-00-UX-401 | Status label (evidence) | Fixed vocabulary from `PH-00-UX-183`. Text plus shape or icon. Neutral treatment except adjudicated Not fulfilled. |
| PH-00-UX-402 | Evidence assessment module (A) | Status, reasons, date, confidence, source list, methodology link. |
| PH-00-UX-403 | Citizen assessment module (B) | Distribution as a chart and table, counts, percentages, window, cohort note, suppression state, civic-feedback notice. |
| PH-00-UX-404 | Responsibility line | Primary and shared authority with the basis for attribution. |
| PH-00-UX-405 | Eligibility state panel | One of eight states: reason and next step. |
| PH-00-UX-406 | Evaluation option group | Four options, text plus shape, "Unable to verify" described as not counted. |
| PH-00-UX-407 | Confirmation summary | Three disclosures for evaluations. Variant for privileged actions restating effect, target and audit. |
| PH-00-UX-408 | Receipt | Own choice only, date, change action, shared-device notice. |
| PH-00-UX-409 | Tier badge and explainer | Names the tier exactly. Never "verified" alone. |
| PH-00-UX-410 | Verification step indicator and tracker | Steps and status. |
| PH-00-UX-411 | Disclosure block | What is collected, purpose, who sees it, retention, deletion. |
| PH-00-UX-412 | Correction notice | Dated notice with link to prior version and a what-changed view. |
| PH-00-UX-413 | Reply panel | Distinct label, date, attribution. Sits beside the record. |
| PH-00-UX-414 | User-submitted label | "User-submitted · not yet reviewed". |
| PH-00-UX-415 | Constituency selector | Hierarchical selection with non-map list alternative. |
| PH-00-UX-416 | Disambiguation card | Office, body, term dates, current/former. |
| PH-00-UX-417 | Timeline | Terms, party history, milestones with effective dates. |
| PH-00-UX-418 | Language switcher | English, Hindi, Marathi; preserves context; content-language label. |
| PH-00-UX-419 | Election-period notice region | Scope, dates, effect. |
| PH-00-UX-420 | Offline "as of" banner | Date and time, stale notice. |
| PH-00-UX-421 | Neutral denied page | Same for forbidden and missing. |
| PH-00-UX-422 | Impersonation banner | True actor, target, reason, elapsed, exit. Non-dismissible. |
| PH-00-UX-423 | Queue list and detail (master/detail) | Filters, status, ownership, drill-in on narrow screens. |
| PH-00-UX-424 | Diff viewer | Draft versus live, with source checklist. |
| PH-00-UX-425 | Decision form | Reason code, free-text reason, sources, summary before submit. |
| PH-00-UX-426 | Audit event row | Actor, action, target, time, integrity indicator. |
| PH-00-UX-427 | Error summary and field message | Accessible errors, focus moves to summary. |
| PH-00-UX-428 | Empty, loading and error blocks | Reason-bearing, never alarming for absent data. |
| PH-00-UX-429 | Comparison table and pager | Persistent row headers; stepper on narrow screens; reason when a row is not comparable. |
| PH-00-UX-430 | Rate-limit message | Neutral wait wording. |
| PH-00-UX-431 | Assisted-route card | Equal weight with the digital route card. |

## 3. Component requirements

| ID | Requirement |
|---|---|
| PH-00-UX-440 | Components 402 and 403 never share a container, chart, scale or ranking. |
| PH-00-UX-441 | Every chart component has a table alternative; every map-like component has a list alternative. |
| PH-00-UX-442 | No component uses party colours or symbols as brand or status treatment. |
| PH-00-UX-443 | Component copy follows the guardrails in `information-architecture.md` §6.1. |
| PH-00-UX-444 | Component specifications and states are fully defined in PH-02; PH-00 fixes only purpose and content rules. |

## 4. Interaction state catalogue by screen family

| Family | Loading | Empty | Validation | Permission | Error | Offline |
|---|---|---|---|---|---|---|
| Search and results | Placeholder rows, busy announced | "No match" with suggestion | Length hint | — | Retry, report | Cached recents, labelled |
| Constituency selector | Incremental | "Not covered yet" | Level hints | — | List fallback | Cached hierarchy, as-of |
| Profile | Per module | Reason-bearing | — | — | Per-module retry | Cached, stale label |
| Promise detail | Per module | "Not yet assessable" | — | — | Per-module retry | Cached; evaluation replaced by note |
| Evaluation module | Eligibility check, text shown | n/a | Option required | Eight states | Safe retry, no double submit | Needs connection |
| Verification wizard | Upload progress, cancel | Step guidance | Per field, summary | Tier gating | Outage → assisted route | Not available |
| Submission and correction | Progress | n/a | Source required, safe links | Neutral rate limit | Draft kept | Not available (`PH-00-UX-Q06`) |
| Admin queues | Placeholder rows | "Nothing assigned" | Reason required | Neutral denied | Conflict with diff | Not available |
| Audit viewer | Chunked | "No events for filter" | — | Permission | Integrity warning | Not available |
| Election-period | — | — | — | Paused notice with scope and dates | — | — |

## 5. Assumptions
- A-11: The screen list is complete for MVP scope in the handbook and will be refined as phases PH-02 to PH-25 specify detail.
- A-12: Capability labels will be renamed to the Development agent's contract terms. Design requirements stay attached to the stable `PH-00-UX` IDs.

## 6. Dependencies
- PH-02 (design system), PH-04 (RBAC), PH-05 (verification) and PH-15 (voting) will specify and refine these items.
- Development agent's `docs/API_CONTRACTS.md` must map each capability label or raise a gap.

## 7. Open questions
`PH-00-UX-Q06`, `Q08` in `ui-design-handoff.md` §6.
