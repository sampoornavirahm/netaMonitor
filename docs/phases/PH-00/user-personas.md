# NetaMonitor PH-00 — User Personas

**Phase:** PH-00 · **Role:** Agent 1 (Product Experience and UI Design) · **Status:** Draft for human review
**ID range:** `PH-00-UX-001` to `PH-00-UX-049`

> All personas are **synthetic**. Names, places and circumstances are invented for design purposes and do not describe real people, politicians or parties. Personas are decision aids, not research findings. Replace or validate them with pilot research before PH-02 (see `PH-00-UX-Q05`).

## 1. How to use this document
- Journeys (`user-journeys.md`) cite persona IDs.
- Accessibility needs here feed `accessibility-and-responsive-principles.md`.
- Access states (anonymous, registered, identity verified, constituency verified, Admin sub-roles, SuperAdmin) follow the handbook §5 baseline. This file does not define permissions; permissions are owned by the Development agent's `docs/RBAC_MATRIX.md`.

## 2. Access-state model used by personas

| ID | Access state | What the person has done | What it does NOT prove |
|---|---|---|---|
| PH-00-UX-001 | Anonymous | Nothing. Reads public records. | Nothing about identity or location. |
| PH-00-UX-002 | Registered (contact confirmed) | Created an account and confirmed a contact method. | Not identity. Not residence. OTP is not identity proof. |
| PH-00-UX-003 | Identity verified | A reviewer or approved route confirmed they are a real, distinct person. | Not where they live. |
| PH-00-UX-004 | Constituency verified | Evidence of residence in a named constituency was accepted. | Not that they support anyone. |
| PH-00-UX-005 | Profile claimant (delegate) | Authority to respond for a representative's profile was approved. | Not permission to edit or hide sourced records. |
| PH-00-UX-006 | Admin (scoped sub-role) | Holds named permissions: Data Editor, Content Reviewer, Verification Officer, Moderator, Support Admin or Analytics Viewer. | Not unlimited access. Cannot approve own work. |
| PH-00-UX-007 | SuperAdmin (restricted workspace) | Holds the highest permission set with MFA. | Not an invisible bypass. Cannot vote, and cannot decide verifications while impersonating. |

## 3. Public personas

### PH-00-UX-010 — P1 Anita Deshmukh, the Curious Browser (synthetic)
- **Context:** 34, nurse. Mid-range Android phone, intermittent mobile data, Marathi first, some English. Low political engagement, wary of being profiled.
- **Top tasks:** find her local representative; see what they promised and what happened; share a page with a neighbour.
- **Needs:** no login wall; Marathi; low data use; plain language; reassurance that browsing is not tracked politically.
- **Digital literacy:** moderate on messaging apps, low with forms and uploads.
- **Risks:** abandons at first sign of an account wall or jargon.
- **Design implications:** public browsing without account; text-first pages; each term has an inline explainer.

### PH-00-UX-011 — P2 Rahul Iyer, the Verified Participant (synthetic)
- **Context:** 41, school teacher, shares a family phone, English and Hindi.
- **Top tasks:** verify once; evaluate promises in his own constituency; change an evaluation later.
- **Needs:** clear reason when he cannot evaluate; privacy confidence; a verification route that does not depend on owning a smartphone or uploading documents.
- **Risks:** shared device exposes his evaluation to family; fears retaliation.
- **Design implications:** receipt visible only inside his signed-in session, with shared-device warning and prompt sign-out; eligibility explained without revealing verification data.

### PH-00-UX-012 — P3 Farida Sheikh, the Evidence Contributor (synthetic)
- **Context:** 29, local journalist, uses laptop and phone, English and Hindi.
- **Top tasks:** submit a correction or evidence with sources; track the outcome; appeal a decline.
- **Needs:** a reference number; named next step; visible outcome on the record; appeal to a different reviewer.
- **Risks:** feels ignored if outcomes are not explained.
- **Design implications:** tracker with role-level reviewer, decision and reason; no silent edits.

### PH-00-UX-013 — P4 the Office Delegate (synthetic)
- **Context:** staff of a synthetic ward councillor. Desktop, English.
- **Top tasks:** claim the profile; reply to a record; dispute a factual error.
- **Needs:** a visible, moderated reply; a separate route to dispute facts.
- **Risks:** attempts to hide critical but correctly sourced records.
- **Design implications:** reply sits beside the record under a distinct label and never replaces it.

### PH-00-UX-014 — P5 Kavita Rao, the Assistive-Technology User (synthetic, cross-cutting)
- **Context:** 52, low vision, uses a screen reader with large text; also keyboard-only on desktop. Hindi and English.
- **Top tasks:** every public task plus verification.
- **Needs:** WCAG 2.2 AA; text alternatives for charts and maps; no colour-only meaning; predictable focus; correct Devanagari rendering.
- **Design implications:** drives `accessibility-and-responsive-principles.md`.

### PH-00-UX-015 — P6 Suresh Pawar, the Low-Literacy / Assisted User (synthetic)
- **Context:** 58, farmer, feature-phone history, new to smartphones. Marathi only. Often helped by a family member or a help-desk volunteer.
- **Top tasks:** find a promise about local water supply; understand the status; ask for help to verify.
- **Needs:** short sentences; icons plus words; audio or assisted option is a **question for the owner** (`PH-00-UX-Q07`); a non-digital verification route.
- **Risks:** being excluded by digital-only verification; being coached into a particular evaluation by a helper.
- **Design implications:** assisted-verification route stated up front; assisted users must still make their own evaluation choice.

## 4. Staff personas

### PH-00-UX-020 — A1 Meera Kulkarni, Data Editor (synthetic)
Creates and updates sourced records and drafts. Desktop, long sessions. Needs source-completeness checks, version history, and no ability to publish own drafts.

### PH-00-UX-021 — A2 Imran Qureshi, Content Reviewer (synthetic)
Reviews drafts, evidence and corrections; records adjudications. Needs side-by-side diff, a checklist, and a required reason. Cannot review own submissions.

### PH-00-UX-022 — A3 Dev Malhotra, Verification Officer (synthetic)
Reviews minimal identity and constituency evidence. Restricted workspace. Needs evidence expiry, reason codes, and a view that excludes vote data and browsing history.

### PH-00-UX-023 — A4 Lata Bhosale, Moderator (synthetic)
Handles reports on comments, submissions and replies. Needs report context, graduated actions, appeal route, and exposure limits for upsetting content.

### PH-00-UX-024 — A5 Nikhil Verma, Support Admin (synthetic)
Helps users with account problems. May impersonate only in a guarded mode. Needs a conspicuous banner, true-actor display and an exit control. Cannot vote, decide verifications or change roles while impersonating.

### PH-00-UX-025 — A6 Zoya Ali, Analytics Viewer (synthetic)
Reads aggregate operational and anti-manipulation insight. Needs aggregate-only views with small-cohort suppression. Sees no individual votes or identities.

### PH-00-UX-026 — S1 Priya Nair, SuperAdmin (synthetic)
Rare, high-risk use: global settings, role administration, election-period mode, break-glass. Needs MFA prompts, confirmation steps that restate effect and audit logging, and dual control where required.

## 5. Anti-persona

### PH-00-UX-030 — The Coordinated Manipulator
Organised actors trying to brigade evaluations, flood submissions or intimidate individuals.
- **Design implications:** no public per-user vote visibility; no public engagement counters on opinion; neutral, non-accusatory rate-limit messages; no hint about which signals trigger review.

## 6. Cross-persona accessibility and digital-literacy considerations

| ID | Consideration | Requirement |
|---|---|---|
| PH-00-UX-040 | Language | Every public task is completable in English, Hindi and Marathi (see `accessibility-and-responsive-principles.md`). |
| PH-00-UX-041 | Connectivity | Public reading must work on slow, intermittent connections; text before images. |
| PH-00-UX-042 | Device | Primary target is a mid-range Android phone at narrow width; desktop is secondary for public users and primary for staff. |
| PH-00-UX-043 | Literacy | Plain language, short sentences, inline explainers for special terms, icon plus text for key states. |
| PH-00-UX-044 | Assisted use | The design must not assume a person completes tasks alone; assisted routes must not allow a helper to choose for the user. |
| PH-00-UX-045 | Shared devices | Sensitive confirmations warn about shared sessions; sign-out clears private screen state. |
| PH-00-UX-046 | Fear of exposure | Reassurance copy about confidentiality is shown at the point of concern (verification, evaluation), not only in a policy page. |
| PH-00-UX-047 | Staff fatigue | Admin queues are dense but legible, with clear ownership and no hidden state. |

## 7. Assumptions
- A-01: Pilot users are mostly mobile-first and include Marathi and Hindi readers.
- A-02: Some users will verify through an assisted or non-digital route.
- A-03: Staff work on desktop or tablet.

## 8. Dependencies
- Accepted `docs/RBAC_MATRIX.md` and `docs/VERIFICATION_POLICY.md` (Development agent) to confirm sub-role scopes and routes.
- Privacy/legal review of any assisted-verification process.

## 9. Open questions
See `ui-design-handoff.md` §6 for the consolidated list: `PH-00-UX-Q05`, `PH-00-UX-Q07`.
