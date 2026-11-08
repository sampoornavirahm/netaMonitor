# DEC-002 — Open PH-00 Product and Policy Questions

**Date recorded:** 8 November 2026
**Status:** OPEN / BLOCKED items as noted
**Decision owner:** Human project owner; named accountable persons remain to be assigned
**Required reviewers:** Qualified counsel for legal/privacy/election matters

## Purpose

This register preserves questions raised by the UI Design work and Agent 2 specification. An entry marked `PROPOSED` is not accepted. The owner must record an explicit decision, rationale, effective date and supersession link before closing it. The planning default of 20 for citizen results is not approved.

| ID | Question / context | Why it matters / risk if unresolved | Recommended options for owner review (not decisions) | Owner / required reviewer | Target / status |
|---|---|---|---|---|---|
| Q01 | What minimum cohort and additional anti-differencing rules govern citizen-result publication, and is a representative-level minimum needed? | Small groups or repeated queries may reveal participation/choice; an arbitrary threshold can create false privacy assurance. | Suppress all results until privacy review; approve threshold plus query controls; publish limited distributions without percentages. | Product/privacy owner; privacy counsel | Before PH-15/16; **BLOCKED** |
| Q02 | Are comment reactions included in MVP? | Reactions may incentivize brigading/popularity and affect moderation load. | Exclude; allow only non-ranked acknowledgement; defer to later phase. | Product/moderation owner | Before PH-14; **OPEN** |
| Q03 | What notice, lawful basis, identity route, retention/deletion periods, legal holds and breach processes apply? | Sensitive political opinion, contact, identity and constituency data; unlawful or unexpected collection/exposure. | Minimize and avoid raw document retention; defer identity-dependent service until counsel-approved route; define per-class schedule. | Product owner; qualified privacy/legal counsel | Before PH-03/05 collection and PH-15; **BLOCKED** |
| Q04 | How will assisted/in-person verification operate (staffing, location, accessibility, evidence transfer and secure handling)? | Equal access cannot be promised without safe and funded operations. | Pilot partner; appointment/help-desk route; defer verification until route exists. | Phase owner/operations | Before PH-05; **OPEN** |
| Q05 | Validate synthetic personas with pilot-area research and confirm Hindi/Marathi translation capacity. | Persona assumptions may not represent users; translation quality affects access and trust. | Conduct research; recruit language reviewers; revise personas with consent and privacy safeguards. | Product/UX owner | Before PH-02/20; **OPEN** |
| Q06 | What offline stale-data threshold applies, and may any non-sensitive draft be stored offline? | Stale facts can mislead; local drafts may expose sensitive content on shared devices. | Public-only cache with visible timestamp and no drafts; define per-record age; evaluate public draft exception later. | Product/security owner | Before PH-24; **OPEN** |
| Q07 | Is audio or other assisted-literacy support in scope? | Affects inclusive design, language support, cost and content operations. | Audio guidance; assisted help route only; defer until research. | Product/accessibility owner | Before PH-02/20; **OPEN** |
| Q08 | What are final evidence-status labels in English, Hindi and Marathi? | Labels can imply blame or lose nuance across languages. | Editorial glossary with reviewed translations and user testing. | Editorial/localization owner | Before PH-02/10/20; **OPEN** |
| Q09 | Are public reviewer bylines used, or role-only attribution? | Byline increases transparency but creates safety/privacy/pressure risks. | Role and date only; voluntary byline; named-byline policy with safety exception. | Editorial/privacy owner | Before PH-08/10; **OPEN** |
| Q10 | What evidence establishes a representative/delegate's authority to claim a profile, and how is it renewed/revoked? | Impersonation, unauthorized speech or excessive collection; no claimant should edit/suppress public facts. | Official contact/authorization evidence; reviewed delegated authority; defer claims until approved process. | Product/moderation owner; qualified legal review | Before PH-10; **BLOCKED** |
| Q11 | What election-period wording/restrictions apply by jurisdiction, election and time? | Civic evaluations may be mischaracterized; incorrect suppression may be unlawful or partisan. | Counsel-approved jurisdiction configuration; feature-specific pause; status notice while preserving records. | Product owner; qualified election counsel | Before PH-25 activation; **BLOCKED** |
| Q12 | What pilot geography and initial office cohort should be covered? | Determines data/source availability, staffing, boundary modeling and safe rollout. | One limited pilot area with reliable sources; staged cohort after source review. | Human phase owner | Before PH-06/07 data scope; **OPEN** |
| Q13 | What is the final product name? | Consistent product identity and documentation. | NetaMonitor. | Human project owner | **ACCEPTED / RESOLVED:** NetaMonitor |

## Additional specification decisions left open

The following are not resolved merely because a related UX decision was accepted:

- Evidence confidence vocabulary; minimum assessable promise count; partial/multi-part promise treatment; shared-authority attribution and score-comparison windows (FR-016/017).
- Identity/constituency evidence, eligibility criterion, validity/expiry and account recovery policy (Q03).
- Comment scope, moderator actions, notice/appeal timeframes, conflict-of-interest and sensitive-claim escalation.
- Audit-event visibility, retention, integrity checkpoint operator and emergency access.
- Hosting/authentication/object-storage/notification/map/source providers, deployment region, cost thresholds, SLO/RTO/RPO and technical controls (all proposed in ADRs).
- Public API/open data field allowlist, source licenses and deletion/correction behavior.

Each needs a named owner and target phase before implementation. Do not infer acceptance from the initial handbook or a proposed ADR.

## Change record

This register clarifies the UI handoff status: the eight source documents were merged into `main` by PR #1 and the product owner has now explicitly approved D01–D10. The handoff's “pending review/not merged” line is a historical statement. It is not edited in-place.
