# NetaMonitor Authorization and Separation-of-Duties Matrix

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review
**Decision owner:** Human project owner · Enforce server-side; UI visibility is not authorization.

## 1. Authorization model

Permissions are explicit actions scoped to resources/jurisdictions/queues. Account and verification states are attributes, not roles; a person can hold multiple states and staff grants, but citizen evaluation is prohibited in staff/impersonation contexts. Deny by default. Every request re-checks authentication, permission, scope, object ownership, workflow state and separation-of-duty rules server-side. The table is a draft minimum policy, not an implementation grant.

“Admin” is a restricted workspace, not a blanket grant; it carries no operation unless a named permission profile authorizes it. “Data reviewer” maps to the scoped Content Reviewer profile for the applicable content domain.

Legend: **Y** allowed subject to policy; **Own** own object only; **Scoped** granted jurisdiction/resource; **N** denied; **Gate** unresolved policy/legal approval.

| Capability | Anonymous | Registered/contact confirmed | Identity verified | Constituency verified | Contributor/claimant | Moderator | Data Editor | Content Reviewer | Verification Officer | Support Admin | Analytics Viewer | SuperAdmin |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Read published public records/methodology | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y |
| Read restricted/private data | N | N | N | N | N | N | N | N | Scoped evidence only | N | Aggregate only | Gate, audited |
| Create correction/report | Y, rate-limited | Y | Y | Y | Y | Y | Y | Y | Y | Y | N | Y |
| Submit evidence/comment | Limited/policy | Y | Y | Y | Y | Y | Y | Y | Y | Y | N | Y |
| Read/modify own submission | Own | Own | Own | Own | Own | Scoped | Scoped | Scoped | N | Own support scope | N | Scoped, audited |
| Vote/evaluate promise | N | N | N | Eligible scope only | N | N | N | N | N | N | N | N |
| Edit draft public record | N | N | N | N | N | N | Scoped | N | N | N | N | Gate, audited |
| Review/publish public record | N | N | N | N | N | N | N | Scoped | N | N | N | Gate, dual control |
| Review/approve own authored item | N | N | N | N | N | N | N | N | N | N | N | N |
| Review verification evidence | N | N | N | N | N | N | N | N | Assigned cases only | N | N | Break-glass proposal, dual control |
| Decide own verification case | N | N | N | N | N | N | N | N | N | N | N | N |
| Moderate/report resolution | N | N | N | N | N | Scoped | N | Scoped editorial | N | N | N | Gate, audited |
| Claim profile / submit reply | N | Own claim | Own claim | Own claim | Scoped claimant only | N | N | Review only | N | N | N | N |
| Start/stop impersonation | N | N | N | N | N | N | N | N | N | Scoped, reason, expiry | N | Break-glass controls |
| Vote/verify/change role while impersonating | N | N | N | N | N | N | N | N | N | N | N | N |
| View aggregate analytics | N | N | N | N | N | Scoped | Scoped | Scoped | N | Minimal support metrics | Aggregate only | Scoped, audited |
| Manage roles/global settings | N | N | N | N | N | N | N | N | N | N | N | Explicit grant, MFA, audit |
| View audit records | N | Own activity where approved | Own activity where approved | Own activity where approved | Own activity where approved | Scoped | Scoped | Scoped | Own-case scope | Own/admin scope | N | Scoped, audited |
| Trigger/approve export or deletion | N | Own request | Own request | Own request | Own request | N | N | N | N | Restricted support | N | Dual control where sensitive |

## 2. Permission profiles (proposed)

| Profile | Minimum permission family | Explicit exclusions |
|---|---|---|
| Data Editor | Create/edit drafts, source registry, import staging for assigned scope | Cannot approve/publish own work; no identity evidence or vote data |
| Content Reviewer | Review, adjudicate and publish assigned content/corrections; appeal queue with independent assignment | Cannot review own authored work; no verification evidence or individual votes |
| Verification Officer | View minimum assigned verification evidence; decide/appeal with reviewer separation | No content editing, vote choice or browsing history |
| Moderator | Triage reports, apply proportionate action, route appeals | Cannot change editorial adjudication or access identity evidence |
| Support Admin | Account-support workflow; guarded impersonation when approved | No evaluation, verification decision, role/security mutation during impersonation |
| Analytics Viewer | Disclosure-safe aggregate dashboards | No individual identity, evaluation, verification or raw anti-abuse signals |
| Profile claimant | Submit authority evidence and labelled reply | No record deletion, status editing, voter data or editorial controls |
| SuperAdmin | Explicit restricted permission grants, global settings and break-glass actions | Not exempt from server policy, audit, dual-control or no-voting rules |

## 3. Separation of duties and elevated access

- A creator cannot approve/publish their own record, source adjudication, correction decision or verification case.
- An appeal must be assigned to a different reviewer; if staffing prevents this, the case remains pending/escalated rather than self-approved.
- Sensitive publication and break-glass operations may require a second authorized person. Exact classes and thresholds require owner approval.
- Impersonation requires a stated support reason, target, time limit, visible persistent banner, true actor attribution, start/stop events and reviewable audit. The target's own authority is not inherited for prohibited actions.
- While impersonating: deny votes/evaluations, verification approval, security-role changes, and any action that would make support staff appear to be the user.
- SuperAdmin is not hidden security: every privileged endpoint checks explicit permissions; MFA/step-up authentication and independent review are proposed controls.
- Emergency access is time-limited, minimum scope, reasoned, alerted, reviewed after use and unable to bypass data-class restrictions without a separately approved control.
- Suspensions/revocations, access recertification cadence, emergency approvers and audit retention are open governance decisions.

## 4. Authorization decision order

1. Authenticate subject (except intentionally public read).
2. Reject invalid/expired/revoked sessions and restricted account state.
3. Resolve explicit permission and resource/jurisdiction scope.
4. Enforce object-level privacy and workflow state.
5. Enforce self-approval and separation-of-duty rules.
6. Enforce identity/constituency eligibility for evaluation.
7. Apply impersonation, election-period and safety restrictions.
8. Record material allow/deny decisions without leaking sensitive distinctions to an unauthorized requester.

No client, cached token claim alone, hidden navigation item or provider default is sufficient authorization.

## 5. Open governance decisions

Owner must define grant approvers, permission catalogue, dual-control actions, staff vetting, access-review cadence, appeals for account sanctions, incident/break-glass authority, audit visibility and retention, claimant proof standard (Q10), and legal review. No role should be granted solely because a user claims an office.
