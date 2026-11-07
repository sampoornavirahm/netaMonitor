# NetaMonitor PH-00 — Service Blueprint

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-200` to `PH-00-UX-249`

> A service blueprint links what the person sees with the human and system work behind it. "System capability" entries are **labels** for traceability. They are not endpoints, services or architecture decisions; those belong to the Development agent. All actors are synthetic.

## 1. Legend
- **FS** frontstage: what the person sees and does.
- **BS** backstage: human work by staff or delegates the person does not see.
- **SYS** system capability label.
- **Evidence out** the trust signal the person receives.
- **Line of visibility** separates FS from BS.

## 2. End-to-end overview

| Stage | Person's actions | FS surface | BS human work | SYS capability label | Evidence out |
|---|---|---|---|---|---|
| Discover | Search, browse, pick a constituency | Home, search, selector | Data Editors keep records current | `public.search`, `geo.lookup` | Records with provenance cues |
| Understand | Read profile, promise, evidence, disclosures | Profile, promise detail, methodology | Content Reviewers adjudicate | `public.profile.read`, `public.promise.read`, `scoring.explain` | Status, reasons, sample sizes |
| Register | Create account, confirm contact | Auth screens | none | `auth.register`, `auth.confirm_contact`, `consent.record` | Registered tier only |
| Verify | Submit minimal evidence or use assisted route | Verification wizard | Verification Officer reviews | `verification.apply`, `verification.review`, `verification.appeal` | Identity and constituency tiers with expiry |
| Evaluate | Evaluate a due promise in own constituency | Evaluation module | none (aggregate only) | `ballot.eligibility`, `ballot.cast`, `ballot.change`, `ballot.aggregate.read` | Confidential choice; public aggregate |
| Contribute | Submit evidence, suggestion or comment | Contribute forms, threads | Moderator and Content Reviewer | `submission.create`, `moderation.report`, `moderation.decide` | "User-submitted, not yet reviewed" label |
| Correct | Report an error and track it | Correction form, tracker | Reviewer decides, version kept | `correction.create`, `correction.decide`, `correction.appeal` | Dated correction notice |
| Reply | Delegate responds to a record | Reply panel | Moderator reviews, never suppresses sourced facts | `reply.submit`, `reply.moderate` | "Response from representative" |
| Profile ownership | Delegate claims a profile | Claim flow | Staff verify authority | `profile.claim`, `profile.claim.review` | "Profile claimed" label |
| Appeal | Contest a decision | Appeal form, tracker | Different reviewer decides | `appeal.create`, `appeal.decide` | Decision with reason |
| Admin review | Review, adjudicate, publish | Admin workspace | Two-person review for sensitive items | `cms.review`, `adjudication.record`, `audit.read` | Attributed decision, audit trail |

## 3. Blueprints by service

### 3.1 Identity and constituency verification
| Layer | Step 1 Apply | Step 2 Evidence | Step 3 Review | Step 4 Outcome |
|---|---|---|---|---|
| Person | Opens verification | Chooses digital or assisted route, supplies minimal evidence | Waits, may be asked for one item | Sees tier, expiry or reason |
| FS | Step 0 disclosure and consent | Route choice and upload or appointment | Status tracker | Result screen with appeal |
| BS | none | Evidence held under role-limited access | Verification Officer reviews, not for own application | Decision recorded with reason code |
| SYS | `verification.apply`, `consent.record` | `verification.evidence.store` (retention applies) | `verification.review` | `verification.decide`, `verification.expire` |
| Failure points | Provider outage → assisted route · upload rejected · drop-off | Wrong evidence type · unreadable file | Backlog · needs info | Declined → appeal · expiry → reminder |

### 3.2 Voting (citizen evaluation)
| Layer | Check | Choose | Confirm | Record |
|---|---|---|---|---|
| Person | Opens promise | Picks an option | Reads three disclosures | Sees own receipt |
| FS | Eligibility state with reason | Four labelled options | Confirmation step | Receipt, change link |
| BS | none | none | none | none (no staff sees individual choices) |
| SYS | `ballot.eligibility` | n/a | `ballot.cast` (safe to retry once) | `ballot.aggregate.read` for public view |
| Failure points | Seven eligibility states · election pause · network error | Required option | Double-submit prevented | Small-cohort suppression |

### 3.3 Evidence submission
| Layer | Submit | Triage | Review | Outcome |
|---|---|---|---|---|
| Person | Provides claim and source | Waits | May be asked for more | Sees result |
| FS | Form and receipt | Tracker "Received" | Tracker "In review" | Accepted, declined with reason |
| BS | none | Moderator checks safety | Content Reviewer assesses source | Decision logged |
| SYS | `submission.create` | `moderation.triage` | `cms.review` | `submission.decide` |
| Failure points | Invalid source · rate limit | Unsafe content | Insufficient sourcing | Decline → appeal |

### 3.4 Editorial review and adjudication
| Layer | Draft | Review | Adjudicate | Publish |
|---|---|---|---|---|
| Person (staff) | Data Editor drafts | Content Reviewer reviews diff | Records status with reasons | Publishes or returns |
| FS | Admin content form | Review queue and diff | Assessment form | Public record updated |
| BS | Sources gathered | Second reviewer for sensitive records | Confidence and sources recorded | Change notice prepared |
| SYS | `cms.draft` | `cms.review` | `adjudication.record` | `cms.publish`, `audit.append` |
| Failure points | Missing source | Self-approval blocked | Disagreement between reviewers | Edit conflict |

### 3.5 Corrections, right of reply and appeals
| Layer | Correction | Reply | Appeal |
|---|---|---|---|
| Person | Reports an error | Delegate responds | Contests a decision |
| FS | Pre-filled form, tracker | Composer, preview | Appeal form, tracker |
| BS | Reviewer decides; prior version kept | Moderator reviews text; sourced facts untouched | Different reviewer decides |
| SYS | `correction.create`, `correction.decide` | `reply.submit`, `reply.moderate` | `appeal.create`, `appeal.decide` |
| Failure points | Invalid source · decline | Needs edit · unauthorised delegate | Late or repeat appeal |

### 3.6 Profile ownership
| Layer | Claim | Review | Active |
|---|---|---|---|
| Person | Delegate submits authority evidence | Waits | Can reply; cannot edit records |
| FS | Claim flow | Status | "Profile claimed" label |
| BS | none | Staff verify authority (method is an owner decision) | Re-check on role change |
| SYS | `profile.claim` | `profile.claim.review` | `profile.claim.revoke` |

## 4. Line-of-visibility requirements

| ID | Requirement |
|---|---|
| PH-00-UX-200 | Citizens see reviewer **role** and decision date, never reviewer identity, unless a byline is public by editorial policy (`PH-00-UX-Q09`). |
| PH-00-UX-201 | Every backstage state that affects a citizen has a defined frontstage label (for example under review, disputed, evidence expired). There are no silent state changes. |
| PH-00-UX-202 | Every frontstage pending state shows the expected next step and a way to check status. |
| PH-00-UX-203 | No staff screen shows an individual's evaluation choice. Staff see aggregates only. |
| PH-00-UX-204 | Verification evidence is visible only to the Verification Officer permission, never to editors, moderators or analytics. |
| PH-00-UX-205 | Failure points per stage are designed as states: provider outage, ineligible user, expired evidence, declined submission, rate limit, election-period pause, offline. See `low-fidelity-flows.md`. |

## 5. Separation-of-duties checkpoints (experience view)

| ID | Checkpoint | Experience rule |
|---|---|---|
| PH-00-UX-210 | Content publishing | The author does not see an approve control. A message explains separation of duties. |
| PH-00-UX-211 | Verification decisions | An officer never sees their own application in their queue. |
| PH-00-UX-212 | Appeals | The screen states that a different reviewer decides. |
| PH-00-UX-213 | Impersonation | Evaluation, verification decisions and role changes are disabled with a stated reason. |
| PH-00-UX-214 | Sensitive records | A second reviewer is required and progress is visible. |

Server-side enforcement of each rule is a Development responsibility; the experience never relies on a hidden control as the safeguard.

## 6. Assumptions
- A-08: A help-desk or assisted route exists in the pilot. Its staffing and location are not decided here.
- A-09: Profile claims are rare and manual in the MVP.

## 7. Dependencies
- Accepted verification, moderation, RBAC and election-period policies from the Development agent.

## 8. Open questions
`PH-00-UX-Q03`, `Q04`, `Q09`, `Q10` in `ui-design-handoff.md` §6.
