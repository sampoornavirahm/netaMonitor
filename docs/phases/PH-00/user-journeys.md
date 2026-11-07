# NetaMonitor PH-00 — User Journeys

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-050` to `PH-00-UX-149`

> Journeys describe experience, not implementation. "Capability" names such as `ballot.eligibility` are labels for traceability only; formal contracts belong to the Development agent. All people, places and figures are synthetic. Persona IDs refer to `user-personas.md`.

## 1. Top tasks by access state

| ID | Access state | Top tasks (in priority order) |
|---|---|---|
| PH-00-UX-050 | Anonymous | Find my representative · read a promise and its evidence · understand how a status was decided · report a mistake · read methodology and funding |
| PH-00-UX-051 | Registered | Confirm contact · see what verification is needed · follow a representative or promise · submit evidence or a suggestion · manage privacy and language |
| PH-00-UX-052 | Identity verified | Finish constituency step · track verification status and expiry · appeal a decision |
| PH-00-UX-053 | Constituency verified | Evaluate a due promise in own constituency · change an evaluation · view own evaluations privately |
| PH-00-UX-054 | Profile claimant | Claim a profile · reply to a record · dispute a factual error through corrections |
| PH-00-UX-055 | Data Editor | Draft a sourced record · attach sources and attribution · submit for review |
| PH-00-UX-056 | Content Reviewer | Review a draft or correction · record an adjudication with reasons · publish or return |
| PH-00-UX-057 | Verification Officer | Review minimal evidence · decide with a reason code · request more information |
| PH-00-UX-058 | Moderator | Triage reports · apply graduated action · handle appeals |
| PH-00-UX-059 | Support Admin | Help a user with account problems · use guarded impersonation when essential |
| PH-00-UX-060 | Analytics Viewer | Read aggregate health and anomaly summaries |
| PH-00-UX-061 | SuperAdmin | Administer roles and global settings · run election-period mode · break-glass with dual control |

## 2. Journey conventions
- Notation: `[Screen]` · `(decision)` · `{system outcome}` · `✖` failure or alternative.
- Every journey step that blocks the user explains the **reason** and the **next step** (`PH-00-UX-070`).
- Every journey shows the relevant **trust cues** defined in `information-architecture.md` §5.

| ID | Cross-journey requirement |
|---|---|
| PH-00-UX-070 | A blocked or unavailable action always states why and what to do next. A disabled control with no explanation is not allowed. |
| PH-00-UX-071 | Anonymous reading never requires an account, location permission, or acceptance of non-essential tracking. |
| PH-00-UX-072 | Language can be switched in every journey without losing the user's place. |
| PH-00-UX-073 | Pending states show expected next step and a way to check status. |
| PH-00-UX-074 | Every journey defines its failure states (see per-journey notes and `low-fidelity-flows.md`). |

## 3. Public and account journeys

### J01 — Anonymous browsing and discovery (P1, P5, P6)
```
[Home] ⟶ (search or "Find my representative")
   ├─ Search ⟶ [Results grouped: People · Constituencies · Promises] ⟶ [Profile]
   └─ Location or manual pick ⟶ [Constituency selector]
        ⟶ (more than one match?) yes ⟶ [Disambiguation: office type · body · term dates · current/former]
        ⟶ [Representatives list] ⟶ [Profile] ⟶ [Promise list] ⟶ [Promise detail]
✖ no result ⟶ "Not covered yet" + suggest a record
✖ ambiguous ⟶ never auto-pick
✖ location denied ⟶ manual selector, no penalty
```

| ID | Requirement |
|---|---|
| PH-00-UX-080 | J01 completes with no account, no location permission, and no blocking cookie dialog. |
| PH-00-UX-081 | When more than one representative or office matches, all are listed with office type, body, term dates and current/former status. The system does not choose one. |
| PH-00-UX-082 | The first viewport of a promise page orders: title, original statement with source, who is responsible, then evidence status. |
| PH-00-UX-083 | Chosen constituency is labelled "selected by you" and never implies verified residence. |

### J02 — Offline public reading (P1)
```
[Previously opened public page] ⟶ (connection lost)
   ⟶ [Cached page with "As of {date and time}" and stale notice]
   ⟶ (tries sign-in, verify, evaluate, submit) ⟶ [Needs a connection — nothing is queued]
```

| ID | Requirement |
|---|---|
| PH-00-UX-085 | Offline mode shows only previously viewed public content with an "as of" label. |
| PH-00-UX-086 | Evaluation, verification, sign-in, evidence submission and all admin actions are never offered or queued offline, and never shown as "sent". |
| PH-00-UX-087 | No identity evidence, admin data or private records are shown from a cache. |

### J03 — Register and confirm contact (P2)
```
[Public page: "Sign in to do this"] ⟶ [Create account: consent summary]
   ⟶ [Confirm contact] ⟶ {Registered tier} ⟶ [What this unlocks / what is still needed]
✖ code not received ⟶ resend with neutral wording and an alternative method
✖ too many attempts ⟶ neutral wait message
```

| ID | Requirement |
|---|---|
| PH-00-UX-090 | After confirmation the screen states the account is "Registered (contact confirmed)" and that this does not prove identity or residence. |
| PH-00-UX-091 | Consent choices are specific, optional where possible, and recorded history is viewable in the account area. |
| PH-00-UX-092 | Sign-in avoids cognitive-test-only steps (accessible authentication). |

### J04 — Verification: identity then constituency (P2, P6)
```
[Account ▸ Verification status] ⟶ [Step 0: what we collect, why, who sees it, retention]
  ⟶ [Step 1: contact confirmed ✓]
  ⟶ [Step 2: choose identity route] ─ Digital route ┐
                                     └ Assisted or in-person route ┤ shown at equal weight
  ⟶ [Step 3: constituency evidence and selection]
  ⟶ [Submitted ⟶ status tracker: Received · In review · Needs info · Decided]
       ├─ Needs info ⟶ [Targeted request: which item and why]
       ├─ Approved ⟶ [Tier shown · expiry · re-verify reminder]
       └─ Declined ⟶ [Plain reason · Appeal · Resubmit]
✖ provider outage ⟶ offer assisted route
✖ upload rejected ⟶ field-level error with allowed types and size
✖ drop-off ⟶ resume later; partial uploads expire
```

| ID | Requirement |
|---|---|
| PH-00-UX-095 | Step 0 lists data collected, purpose, who can see it by role, retention and deletion. Wording needs privacy review (`PH-00-UX-Q03`). |
| PH-00-UX-096 | A non-digital route is visible before any upload starts and is presented at the same level as the digital route. |
| PH-00-UX-097 | The three tiers are always named distinctly. The word "verified" never appears without its tier. |
| PH-00-UX-098 | No identity-evidence image or number is ever shown back on public or ordinary account screens. |
| PH-00-UX-099 | Expiry and re-verification are announced ahead of time and never silently downgrade a user mid-action. |
| PH-00-UX-100 | NetaMonitor does not scrape voter rolls and does not offer biometric or Aadhaar eKYC verification. The design offers no such option. |

### J05 — Evaluate a promise (P2)
```
[Promise detail ▸ "Your evaluation" module] ⟶ {eligibility check}
   ├─ Eligible ⟶ [Choose: Fulfilled · Partially fulfilled · Not fulfilled · Unable to verify]
   │      ⟶ [Confirm: confidential · civic feedback, not an election · you can change it]
   │      ⟶ {recorded} ⟶ [Receipt: own choice only, date, Change]
   ├─ Signed out ⟶ [Sign in and verify: explainer]
   ├─ Registered only ⟶ [Start verification]
   ├─ Identity verified, no matching constituency ⟶ [Add constituency evidence]
   ├─ Promise not yet open for evaluation ⟶ [Reason: not due / review in progress]
   ├─ Impersonation or Admin context ⟶ [Disabled with reason]
   ├─ Election-period restriction ⟶ [Notice: paused, scope and dates]
   └─ Suspended account ⟶ [Status and appeal route]
[Change evaluation] ⟶ (re-confirm) ⟶ {updated and audited}
✖ network error ⟶ "Not submitted. Try again online." Never queued.
```

| ID | Requirement |
|---|---|
| PH-00-UX-105 | The evaluation module shows exactly one eligibility state at a time, each with reason and next step. |
| PH-00-UX-106 | Option labels use text plus shape or icon, never colour alone. "Unable to verify" is neutral and described as not counted in percentages. |
| PH-00-UX-107 | The confirm step states: confidential, civic feedback not an election or proof, and changeable. |
| PH-00-UX-108 | The receipt shows only the user's own choice, only in a signed-in non-cached view, with no shareable public link. |
| PH-00-UX-109 | Results show counts, percentages, window dates, cohort description, minimum-sample suppression ("Not enough responses to show") and a methodology link. No demographic cross-tabs. |
| PH-00-UX-110 | Never use "ballot", "poll result", "mandate", "official", "approval rating" or "popularity" in user-facing copy for evaluations. |
| PH-00-UX-111 | Evaluation is not available to Admin or SuperAdmin accounts or during impersonation. |

### J06 — Submit evidence, suggest a promise or comment (P3)
```
[Contribute] ⟶ (type: evidence · suggest promise · comment)
   ⟶ [Form: what · where · source link or file · optional contact] ⟶ [Receipt with reference]
   ⟶ [Status: Received · In review · Accepted · Declined with reason]
Public view while pending: "User-submitted · not yet reviewed"
✖ source missing ⟶ field-level guidance
✖ rate limit ⟶ neutral message; draft preserved
```

| ID | Requirement |
|---|---|
| PH-00-UX-115 | User-submitted material is labelled "User-submitted · not yet reviewed" and never contributes to a status until accepted. |
| PH-00-UX-116 | A source link or file is required for factual claims. |
| PH-00-UX-117 | Comments and reactions on opinions follow the moderation policy; reactions are **not** assumed in MVP (`PH-00-UX-Q02`). |

### J07 — Report a correction (P3, P1)
```
[Any fact ▸ "Report a correction"] ⟶ [Form pre-filled with record reference]
   ⟶ [Receipt: reference] ⟶ [Tracker: Received ▸ Under review ▸ Decision]
Accepted ⟶ record shows dated correction notice with prior version kept
Partly accepted ⟶ same, with what was and was not changed
Declined ⟶ reason ⟶ [Appeal] (different reviewer)
```

| ID | Requirement |
|---|---|
| PH-00-UX-120 | A correction can be started from every provenance cue in one step, with the record reference pre-filled and not editable. |
| PH-00-UX-121 | Anonymous submission is allowed with rate limiting and an abuse-prevention check; the mechanism is a Development decision. |
| PH-00-UX-122 | Outcomes appear on the public record as a dated notice that links to the prior version. There are no silent edits. |
| PH-00-UX-123 | The tracker shows reviewer role (not name), decision and reason. |

### J08 — Appeal (P2, P3)
```
[Declined verification, correction, moderation action] ⟶ [Appeal: reason and new information]
   ⟶ {assigned to a different reviewer} ⟶ [Tracker] ⟶ Decision with reason
```

| ID | Requirement |
|---|---|
| PH-00-UX-125 | Every decision type that can harm a user or submitter has an appeal route stated in the decision message. |
| PH-00-UX-126 | Appeals are routed to a different reviewer, and the screen says so. |

### J09 — Profile claim and right of reply (P4)
```
[Delegate signs in] ⟶ [Claim profile: authority evidence] ⟶ {reviewed by staff}
   ⟶ [Record list with "Respond"] ⟶ [Reply composer: text · sources · scope]
   ⟶ [Preview: exactly how it will appear] ⟶ {moderation: Pending ▸ Published or Needs edit with reason}
Public: record + dated "Response from {representative's office}" beside it
Delegate cannot: delete or hide sourced records · edit editorial assessments · vote · see voter data
```

| ID | Requirement |
|---|---|
| PH-00-UX-130 | A reply is shown beside or below the record with a distinct label, date and attribution. It never replaces or hides the original. |
| PH-00-UX-131 | The composer states moderation rules and that a reply cannot remove sourced content. "Dispute the facts" is a separate action that opens the correction journey. |
| PH-00-UX-132 | Claimed profiles show "Profile claimed by representative's office" with date. Unclaimed profiles show nothing. |
| PH-00-UX-133 | The claim method is an open owner decision (`PH-00-UX-Q10`). |

## 4. Admin and restricted journeys

### J10 — Data Editor drafts a record (A1)
```
[Admin dashboard: tasks by permission] ⟶ [Content ▸ New record or edit]
   ⟶ [Form: fact · source · issuer type · dates · attribution · status]
   ⟶ [Completeness checklist] ⟶ [Submit for review]
✖ missing source ⟶ cannot submit; field guidance
✖ edit conflict ⟶ diff and keep draft
```

### J11 — Content Reviewer reviews, adjudicates and publishes (A2)
```
[Review queue] ⟶ [Item: draft versus live diff · sources checklist · attribution]
   ├─ Sensitive record ⟶ second reviewer required
   ├─ Decision: Approve ▸ Publish · Request changes (reason) · Reject (reason code)
   └─ Adjudication form: status · reasons · confidence · sources ⟶ attributable decision
Self-authored item ⟶ approval control absent with an explanation
```

| ID | Requirement |
|---|---|
| PH-00-UX-135 | Approval controls are absent on items the viewer authored; a message explains separation of duties. Server enforcement is the real control and is the Development agent's responsibility. |
| PH-00-UX-136 | Every decision requires a reason and source references and shows a summary before submit. |
| PH-00-UX-137 | Sensitive records show a "needs second reviewer" state with progress. |

### J12 — Verification Officer decides (A3)
```
[Verification queue (separate permission)] ⟶ [Minimal evidence view · expiry · reason codes]
   ⟶ Decision: Approve tier · Need more info (specific field) · Decline (reason code)
No vote data, browsing data or unrelated profile data is shown.
Own application ⟶ not shown in own queue
```

| ID | Requirement |
|---|---|
| PH-00-UX-140 | The verification queue is a separate workspace, available only to holders of the verification permission. |
| PH-00-UX-141 | The evidence view shows the minimum needed to decide and masks anything not required. |

### J13 — Moderator triages reports (A4)
```
[Moderation queue] ⟶ [Report context · content · history] ⟶ Action: dismiss · edit request · hide pending review · sanction
   ⟶ [Notify user with reason and appeal route]
```

### J14 — Support Admin uses guarded impersonation (A5)
```
[Support tools] ⟶ [Start impersonation: reason · target · MFA] ⟶ {session with persistent banner}
   Banner: "Acting as {user} · true actor {admin} · reason · elapsed · Exit"
   Disabled while impersonating: evaluate · verification decisions · role changes
[Exit] ⟶ back to own identity, event logged
```

| ID | Requirement |
|---|---|
| PH-00-UX-145 | The banner is full width, high contrast, non-dismissible, present on every screen, and shows true actor, target, reason, elapsed time and an exit control that is first in focus order after the skip link. |
| PH-00-UX-146 | Disabled actions during impersonation say why. |

### J15 — Analytics Viewer reads aggregates (A6)
```
[Analytics] ⟶ [Aggregate tiles and trends] ⟶ [Anomaly cases (aggregate evidence only)]
Small cohorts show "Not enough data to show". No individual votes or identities.
```

### J16 — SuperAdmin restricted workspace (S1)
```
[Restricted workspace entry only for holders] ⟶ MFA ⟶ [Roles · global settings · election-period mode · break-glass]
   Each privileged action ⟶ [Confirmation: restates effect, target and that it is audited] ⟶ {logged}
Dual control for break-glass access to identity evidence.
```

| ID | Requirement |
|---|---|
| PH-00-UX-147 | The restricted workspace never appears in public or ordinary-Admin navigation. A direct visit by someone without access shows the same neutral "not available" page as a page that does not exist. |
| PH-00-UX-148 | Privileged actions use a confirmation step that restates effect, target and audit logging, with an MFA re-prompt where required. |

## 5. Assumptions
- A-04: Sensitive-record rules (second reviewer) apply at least to financial and allegation-adjacent records; the list is a policy decision.
- A-05: A moderator may temporarily hide content pending review; the policy is owned by `docs/MODERATION_POLICY.md`.

## 6. Dependencies
- `docs/VERIFICATION_POLICY.md`, `docs/RBAC_MATRIX.md`, `docs/MODERATION_POLICY.md`, `docs/ELECTION_PERIOD_POLICY.md`, `docs/SCORING_METHODOLOGY.md` (Development agent) must confirm every rule referenced here.

## 7. Open questions
`PH-00-UX-Q02`, `Q03`, `Q10` (see `ui-design-handoff.md` §6).
