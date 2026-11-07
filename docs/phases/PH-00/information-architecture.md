# NetaMonitor PH-00 — Information Architecture

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-150` to `PH-00-UX-199`

> Structure and navigation only. URL formats, routing and API design belong to the Development agent. All names and data are synthetic.

## 1. Content model at the experience level
Terms used consistently across all deliverables. Formal definitions belong in `docs/DOMAIN_GLOSSARY.md` (Development agent).

| Term | Experience meaning |
|---|---|
| Person | An individual. Distinct from any office they hold. |
| Office and term | A position held over dated periods. Past terms are kept. |
| Candidacy | Standing in an election. Not the same as being elected. |
| Party membership | A dated relationship. Past memberships are kept. |
| Promise | An exact public commitment with original wording, source, deadline and responsible authority. |
| Evidence | A sourced item bearing on a promise or record. Labelled by issuer type and review status. |
| Evidence assessment | The editorial status decision, with reasons. |
| Citizen assessment | Aggregated evaluations from constituency-verified residents. Civic feedback only. |
| Provenance cue | The visible source, date and status label on a fact. |

## 2. Public site map

```
Home
├─ Search (people · constituencies · promises · schemes)
├─ Find my representative (location optional)
│   └─ Constituency selector (state › district › body › ward / constituency)
├─ Representatives
│   └─ Profile
│       ├─ Overview (current and former terms, party history snapshot)
│       ├─ Promises ▸ Promise detail
│       │     ├─ Original statement and source
│       │     ├─ Who is responsible
│       │     ├─ Milestones and timeline
│       │     ├─ Module A: Evidence assessment
│       │     ├─ Module B: Citizen assessment (separate)
│       │     └─ Corrections · Replies · History
│       ├─ Elections and terms
│       ├─ Schemes and projects
│       ├─ Financial disclosures
│       ├─ Affiliations and public activity
│       └─ Corrections and replies
├─ Compare (like-for-like only)
├─ Leaderboards (evidence and citizen shown separately; cohort filters)
├─ Schemes and projects
├─ Transparency centre (methodology · funding · source register · changelog · open data)
├─ Contribute (submit evidence · suggest a promise · report a correction)
└─ Help and legal (civic-feedback notice · privacy · terms · accessibility)
```

## 3. Account and Admin site maps

### 3.1 Account area
```
My account
├─ Verification status (three tiers, expiry, appeal)
├─ My evaluations (private; change)
├─ My submissions and corrections (trackers)
├─ Following and notifications (channels, quiet hours)
├─ Privacy and consent history · data export and deletion
└─ Language and accessibility preferences
```

### 3.2 Admin workspace (permission-driven)
```
Admin
├─ Dashboard (tasks by permission)
├─ Content (records · sources · media · versions · publishing)       Data Editor
├─ Review queues (drafts · corrections · adjudication · replies)      Content Reviewer
├─ Verification queue                                                 Verification Officer
├─ Moderation (reports · sanctions · appeals)                         Moderator
├─ Support tools (account help · guarded impersonation)               Support Admin
├─ Analytics (aggregate only) · Anomaly cases                         Analytics Viewer
├─ Imports and reconciliation
├─ Roles and permissions · Audit viewer
└─ Restricted workspace (settings · break-glass · election mode)      SuperAdmin only
```
The sub-role labels on the right are the experience mapping of handbook §5. Which permission unlocks which item is defined in `docs/RBAC_MATRIX.md`.

## 4. Navigation model

| ID | Requirement |
|---|---|
| PH-00-UX-150 | Public information architecture is at most three levels deep. Any representative is reachable from Home in at most three interactions. |
| PH-00-UX-151 | Primary public navigation has at most five items: Find my representative, Promises, Compare, Transparency, Contribute. Search is a persistent entry at every breakpoint. |
| PH-00-UX-152 | Mobile (narrow): compact bottom or top navigation. Tablet: top bar with search. Desktop: top bar, plus a secondary side navigation only inside the Admin workspace and long profiles. |
| PH-00-UX-153 | Admin navigation items appear only when the server grants the matching permission. Absence of an item is the control, not a hidden link. |
| PH-00-UX-154 | The restricted workspace is absent from public and ordinary-Admin navigation. A direct visit shows the same neutral "not available" state as a missing page and reveals nothing about its existence. |
| PH-00-UX-155 | Every page has a clear back route or breadcrumbs. Constituency breadcrumbs show state › district › body › ward, with an effective date when historical. |
| PH-00-UX-156 | Global elements: skip link, language switcher (English, Hindi, Marathi), conditional election-period notice region, footer links to Methodology, Funding and independence, Privacy, Accessibility and Corrections contact. |
| PH-00-UX-157 | The footer funding link is present on every page, supporting the no-paid-placement rule. |
| PH-00-UX-158 | Location is optional for browsing. Why it is requested, and how it would be used for eligibility, is explained where it is requested. A selected constituency is labelled differently from a verified one. |
| PH-00-UX-159 | Leaderboards and Compare default to like-for-like cohorts (same office type and term window). Cross-office comparison is blocked with an explanatory state. |
| PH-00-UX-160 | Leaderboards show evidence-based and citizen-assessed views in separate tabs or sections. They are never merged into one ordering. |
| PH-00-UX-161 | Search results are grouped by type and show disambiguating facts (office, body, term dates) for every person result. |

## 5. Content hierarchy for the two key pages

### 5.1 Profile (first viewport)
1. Name, current office and body, current/former label computed from dates.
2. Party history snapshot with dates.
3. Summary of promises by status (counts, with "not yet due" shown separately).
4. Tabs or sections for the remaining areas.

### 5.2 Promise detail (first viewport order)
1. Promise title.
2. Original statement with source cue.
3. Who is responsible (primary and shared).
4. Evidence status (Module A).
5. Citizen assessment (Module B), clearly separate.
6. Milestones, corrections, replies and history below.

| ID | Requirement |
|---|---|
| PH-00-UX-165 | Module A (evidence assessment) and Module B (citizen assessment) are separate labelled regions with separate headings, in a stable order of A then B. They never share one chart, one number, one colour scale or one rank. |
| PH-00-UX-166 | "Not yet due" promises are counted and displayed separately from assessed ones. |
| PH-00-UX-167 | Responsibility is shown before status styling. Shared or other-agency responsibility is displayed explicitly. |

## 6. Trust cues and content rules

| ID | Requirement |
|---|---|
| PH-00-UX-180 | Every material fact shows a provenance cue: source name, issuer type, original date, retrieval date, review status, and a "Report a correction" route reachable in one interaction. |
| PH-00-UX-181 | Dates and effective periods: offices, party memberships, constituencies and disclosures show start and end. "Current" is derived from dates. Past records are labelled "Former" with a range. |
| PH-00-UX-182 | Attribution comes before judgement. Delivery responsibility is shown before any status styling. |
| PH-00-UX-183 | Evidence status vocabulary: Fulfilled, Partially fulfilled, Not fulfilled, Not yet due, Unable to assess, Disputed, Withdrawn, Out of scope. Only an adjudicated Not fulfilled uses a negative treatment. Absence of data is never styled as a warning. |
| PH-00-UX-184 | Sample sizes and windows are always shown next to any citizen percentage. Below the minimum cohort threshold the interface shows "Not enough responses to show" instead of a figure. The threshold value is an owner decision (`PH-00-UX-Q01`). |
| PH-00-UX-185 | Uncertainty is stated in words: confidence level on assessments, "unable to verify" counts, data completeness notes. |
| PH-00-UX-186 | Corrections show a dated notice with a link to the previous version. |
| PH-00-UX-187 | Financial figures show scope, as-of date, source and basis: self-declared, officially recorded, or independently corroborated. The phrase "audited net worth" is never used without proof. No default "richest" ordering. |
| PH-00-UX-188 | Affiliation, protest and social-account entries use precise labels (member, founder, speaker, participant, office-holder, mentioned) with dates and sources. An association is never presented as an allegation. |
| PH-00-UX-189 | Evidence, citizen sentiment and data completeness are visually distinct kinds of information. |
| PH-00-UX-190 | The civic-feedback notice ("not an election, not proof") appears wherever citizen assessments are shown or collected. |
| PH-00-UX-191 | No party colours, symbols or partisan imagery as brand or status treatment. |
| PH-00-UX-192 | No dark patterns: no urgency timers, streaks, sponsored positions or advertising slots. |
| PH-00-UX-193 | Plain language: target reading level about grade 8; every special term has an inline explainer; each page answers one dominant citizen question in its first viewport. |

### 6.1 Copy guardrails

| Avoid | Use instead |
|---|---|
| "Verified citizen vote" | "Evaluation from a constituency-verified resident" |
| "Score" on its own | "Evidence performance" or "Citizen-assessed fulfilment" |
| "Failed promise" | "Not fulfilled (assessed {date})" |
| "Rating", "rank" | "Comparison" (like-for-like only) |
| "Corrupt", "criminal" in the platform's voice | Quote the source verbatim with status and issuer |

## 7. Assumptions
- A-06: The five public navigation labels may change with branding; the structure and the five-item limit remain.
- A-07: A single Admin workspace shell shows different sections by permission rather than separate sites. Whether it is one application or several is a Development decision.

## 8. Dependencies
- `docs/DOMAIN_GLOSSARY.md`, `docs/SCORING_METHODOLOGY.md` (cohort threshold, status vocabulary) and `docs/RBAC_MATRIX.md` (menu permissions).

## 9. Open questions
`PH-00-UX-Q01` (cohort threshold), `PH-00-UX-Q08` (evidence status vocabulary final wording) in `ui-design-handoff.md` §6.
