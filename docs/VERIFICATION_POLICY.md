# NetaMonitor Account and Eligibility Verification Policy

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft; identity route and legal decisions blocked
**Decision owner:** Human project owner · **Required review:** Qualified privacy/legal counsel

## 1. Purpose and governing distinctions

Verification exists only to support specified account security and eligibility purposes. The platform must represent separately:

1. **Registered/contact-confirmed:** control of a registered contact method was confirmed. OTP proves only contact control.
2. **Identity-verified:** an approved process supports a limited identity/uniqueness claim.
3. **Constituency-verified:** an approved process supports eligibility association with a named constituency for a stated period.

None implies political support, public identity disclosure or another tier. A selected constituency for browsing is not verified residence. Verification status is private and is not published on a public profile.

## 2. Verification lifecycle

Proposed case states: `not_started → draft → submitted → in_review → needs_information ↔ in_review → approved/declined → appealed → appeal_decided → expired/revoked`. Every transition records reason code, actor, time, policy version and next step. No reviewer may approve their own case. Appeal is assigned to a different reviewer; if unavailable, escalate/hold rather than self-review.

Identity and constituency decisions are distinct; a constituency case may require an identity decision first. Expiry/re-verification may be required by a future policy; no validity period is selected. Notify a user before expiry where operationally possible and avoid silent eligibility changes mid-action.

## 3. Evidence and routes

An evidence route must be approved only after purpose, authority, necessity, accessibility, fraud, exclusion, security, cost and legal review. Do not select an identity vendor in PH-00. Do not scrape, bulk-copy or query voter rolls without separately approved authority; this project explicitly prohibits voter-roll scraping. Do not implement Aadhaar biometric/eKYC.

Digital and assisted/in-person routes should have equal standing where offered. Assisted use must not let a helper choose an evaluation or impersonate the applicant. Specify staff training, private handling, identity of helper, evidence transfer, appointment/outage route and appeal before operating a physical route.

For any proposed evidence item, the future design must state:

- Purpose and exact claim it supports.
- Minimum necessary attributes; prefer review of a fact and deletion over retaining a raw document.
- Accepted alternatives, accessibility, language, rural/low-connectivity and exclusion impacts.
- Reviewer role, conflict check, separation, decision reasons and appeal.
- Storage, encryption/key access, malware/privacy handling, access logs, retention/deletion and breach response.
- Legal authority, provider terms and notice/consent review by qualified counsel.

This list is a design gate, not permission to collect a document.

## 4. Constituency eligibility

The approved process must establish only the constituency relation required for a stated civic-evaluation eligibility purpose. It must handle boundary versions and effective dates, overlapping jurisdictions, moves, expiry and disputed/ambiguous addresses. Public display must not reveal evidence, exact address, reviewer notes or why another person's eligibility failed. Location selection is optional for public browsing.

Whether eligibility is based on current residence, another lawful criterion, constituency boundaries, age or any other rule is unresolved and must be decided by the owner with legal review before PH-05 implements it.

## 5. Reviewer and account controls

- Verification Officer can access only assigned minimum evidence; no vote-choice, browsing-history, content-editor or analytics access by default.
- Reviewer cannot approve own account, case or evidence; access is logged and periodically reviewed under an owner-approved schedule.
- Account recovery does not itself upgrade identity/constituency verification; support must not request passwords or impersonate a user to bypass recovery.
- Account suspension, suspected fraud, duplicate-account treatment, correction, appeal and restoration require reasoned, proportionate policy and privacy review.
- Verification status changes are server-side inputs to eligibility and are not exposed as a detailed public response.

## 6. Retention and deletion gates

No evidence types, providers, retention durations, identity proofing route, legal basis or privacy-notice language are approved here (Q03). Before any collection: document necessity, schedule for raw evidence and derived decisions, access and audit retention, backup/replica expiry, legal hold, export/deletion effect, cryptographic key lifecycle and user appeal. Avoid keeping a raw document after a decision unless a documented, legally reviewed necessity exists.

## 7. Required future assurance

Test tier transitions, invalid OTP assumptions, reviewer self-approval denial, role isolation, expiry/revocation, appeal assignment, assisted route parity, account recovery, duplicate signals, failure/outage handling and deletion/backup behavior using synthetic identities only. Conduct privacy and threat assessment before selecting a route. The test strategy contains the future catalogue.

## 8. Open gates

Q03 privacy notice/retention/identity route; legal authority; accepted evidence and assisted operations (Q04); constituency criterion/boundary authority; reviewer qualifications; expiry; appeals; fraud signals; account recovery; and data breach response owner. None is presumed resolved by a UX flow.
