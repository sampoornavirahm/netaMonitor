# NetaMonitor PH-00 — Low-Fidelity Flows

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-250` to `PH-00-UX-299`

> Text diagrams of structure and decisions. They are not screens and imply no visual styling, layout grid, colour or component design. All names and data are synthetic.

Notation: `[Screen]` · `(decision)` · `{system outcome}` · `⟶` flow · `✖` failure or alternative.

## 1. Search and discovery (FLOW-01)
```
[Home]
  ⟶ (search or "Find my representative")
     ├─ Search ⟶ [Results: People · Constituencies · Promises · Schemes] ⟶ [Profile]
     └─ Place ⟶ [Constituency selector: state › district › body › ward]
           ⟶ (several offices cover this place?)
                yes ⟶ [Disambiguation list] ⟶ [Profile]
                no  ⟶ [Representative] ⟶ [Profile]
✖ no result ⟶ [Not covered yet] ⟶ suggest a record / coverage request
✖ location denied ⟶ manual selector, no penalty
✖ offline ⟶ cached recents, labelled "As of"
```

| ID | Requirement |
|---|---|
| PH-00-UX-250 | Min-length hints appear as guidance, not errors. Empty result offers another spelling or script and a suggestion route. |
| PH-00-UX-251 | The selector always has a non-map list route. |
| PH-00-UX-252 | Historical constituency choices show effective dates. |

## 2. Politician profile (FLOW-02)
```
[Profile]
  ├─ Header: name · current office and body · current/former computed from dates
  ├─ Party history snapshot (dated)
  ├─ Promise summary by status (not yet due shown separately)
  ├─ Tabs or sections: Promises · Terms · Schemes and projects · Disclosures · Affiliations · Corrections and replies
  └─ Global: Report a correction · Methodology · language
✖ a module fails ⟶ that module shows a retry; the rest stays usable
✖ no data in a module ⟶ states why ("No disclosures published for this term")
```

| ID | Requirement |
|---|---|
| PH-00-UX-255 | Each profile module loads, fails and empties independently. |
| PH-00-UX-256 | Empty states describe the reason (not collected, not due, not published) and never use warning treatment. |

## 3. Promise detail (FLOW-03)
```
[Promise detail]
  1 Title
  2 Original statement ▸ source cue
  3 Who is responsible (primary · shared)
  4 [Module A: Evidence assessment]  status · reasons · date · sources · methodology
  5 [Module B: Citizen assessment]   distribution · sample size · window · notice
        └─ [Your evaluation] ⟶ see FLOW-04
  6 Milestones ▾  Corrections ▾  Replies ▾  History ▾
  7 Report a correction
✖ not yet assessable ⟶ "No evidence published yet" in Module A, with date due
```

| ID | Requirement |
|---|---|
| PH-00-UX-260 | The order above is fixed. Module A always precedes Module B. |
| PH-00-UX-261 | Each module has its own error state. A failure in B never hides A. |

## 4. Evaluation (vote) flow (FLOW-04)
```
[Your evaluation] ⟶ {check eligibility}
  ├─ Eligible
  │    ⟶ [Choose option] ⟶ [Confirm: confidential · not an election · changeable]
  │    ⟶ {recorded} ⟶ [Receipt: own choice only] ⟶ aggregate refreshes or "Not enough responses"
  ├─ Signed out ⟶ [Explainer + Sign in] ⟶ FLOW-06
  ├─ Registered only ⟶ [Why not yet] ⟶ [Start verification]
  ├─ Identity verified, no matching constituency ⟶ [Constituency step]
  ├─ Promise not open ⟶ [Reason: not due / review in progress]
  ├─ Impersonation or Admin ⟶ [Disabled with reason]
  ├─ Election-period restriction ⟶ [Paused notice with scope and dates]
  └─ Suspended ⟶ [Status + appeal]
[Receipt ▸ Change] ⟶ [Re-confirm] ⟶ {updated, audited}
✖ network error ⟶ "Not submitted. Try again online." Never queued.
✖ double tap ⟶ one submission only
```

| ID | Requirement |
|---|---|
| PH-00-UX-265 | Each of the eight states above has defined copy intent, reason and next step. |
| PH-00-UX-266 | Eligibility explanations never reveal verification data or the reason a verification decision was made beyond the user's own status. |
| PH-00-UX-267 | The receipt appears only in the signed-in session and shows a shared-device notice. |
| PH-00-UX-268 | Nothing in this flow celebrates, rewards or gamifies the act of evaluating. |

## 5. Verification wizard (FLOW-05)
```
[Step 0: collected data · purpose · who sees it · retention] ⟶ consent
[Step 1: contact confirmed]
[Step 2: identity route: Digital | Assisted/in person (equal weight)]
[Step 3: constituency evidence and selection]
[Submitted ⟶ tracker: Received · In review · Needs info · Decided]
✖ outage ⟶ assisted route offered · ✖ rejected upload ⟶ field-level message
✖ drop-off ⟶ resume; partial uploads expire · ✖ declined ⟶ reason · appeal · resubmit
```

## 6. Registration and sign-in (FLOW-06)
```
[Action needs account] ⟶ [Create account + consent summary] ⟶ [Confirm contact] ⟶ [Registered]
[Return] ⟶ [Sign in] ⟶ (optional second factor for staff)
✖ code not received ⟶ resend, alternative method · ✖ throttled ⟶ neutral wait message
```

## 7. Admin review (FLOW-07)
```
[Dashboard: tasks by permission]
  ├─ [Review queue] ⟶ [Item: diff · sources checklist · attribution]
  │      ⟶ (sensitive?) yes ⟶ second reviewer required
  │      ⟶ Decision: Approve ▸ Publish | Request changes | Reject (reason required)
  ├─ [Adjudication] ⟶ [Evidence viewer · assessment form] ⟶ attributable decision
  ├─ [Verification queue (separate permission)] ⟶ [Minimal evidence view] ⟶ decision + reason code
  ├─ [Moderation] ⟶ [Report context] ⟶ graduated action + appeal route
  └─ [Audit viewer] ⟶ filter by actor, action, target · chain-integrity status
✖ no permission ⟶ neutral "not available" (same as a missing page)
✖ session expired ⟶ re-authenticate, draft preserved
✖ edit conflict ⟶ show diff, keep draft, no silent overwrite
Impersonation: [Reason · target · second factor] ⟶ persistent banner · disabled actions explained
```

| ID | Requirement |
|---|---|
| PH-00-UX-270 | Every decision form requires a reason and source references and shows a summary before submit. |
| PH-00-UX-271 | The author of an item does not see an approve control on it. |
| PH-00-UX-272 | The queue and detail work as master/detail on wide screens and as drill-in on narrow ones. |

## 8. Correction workflow (FLOW-08)
```
[Fact ▸ Report a correction] ⟶ [Form: what is wrong · where (pre-filled) · proposed change · source]
  ⟶ [Receipt: reference] ⟶ [Tracker]
        ├─ Accepted ⟶ [Record updated + dated correction notice + prior version link]
        ├─ Partly accepted ⟶ [Notice explains what changed and what did not]
        └─ Declined ⟶ [Reason] ⟶ [Appeal ⟶ different reviewer]
✖ source missing ⟶ field guidance · ✖ upload rejected ⟶ allowed types and size · ✖ throttled ⟶ neutral message, draft kept
```

## 9. Right of reply and profile claim (FLOW-09)
```
[Delegate] ⟶ [Claim profile: authority evidence] ⟶ {staff review}
   ⟶ [Record list ▸ Respond] ⟶ [Composer] ⟶ [Preview] ⟶ {moderation: Pending ▸ Published | Needs edit}
Public: record + "Response from {office}" beside it
Dispute facts ⟶ FLOW-08 (separate action)
```

## 10. Appeals (FLOW-10)
```
[Decision message with appeal link] ⟶ [Appeal form] ⟶ {different reviewer} ⟶ [Tracker] ⟶ [Decision + reason]
```

## 11. State coverage

| ID | Requirement |
|---|---|
| PH-00-UX-280 | Every flow above has defined loading, empty, validation, permission, error and offline states, listed per family in `screen-and-component-inventory.md` §4. |
| PH-00-UX-281 | Error copy never exposes technical detail, hidden admin areas or another person's data. |
| PH-00-UX-282 | Rate-limit messages are neutral ("Too many attempts. Try again in N minutes"). |
| PH-00-UX-283 | Edit conflicts show a difference view and preserve the draft. |

## 12. Assumptions and dependencies
- A-10: Flow labels `FLOW-NN` are for cross-reference in this phase only.
- Dependencies: `docs/VERIFICATION_POLICY.md`, `docs/MODERATION_POLICY.md`, `docs/ELECTION_PERIOD_POLICY.md`.

## 13. Open questions
`PH-00-UX-Q03`, `Q11` (election-period wording), `Q10` in `ui-design-handoff.md` §6.
