# NetaMonitor Security Model and Threat Register

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review
**Decision owner:** Human project owner · Use OWASP ASVS as a reference, not a certification claim.

## 1. Security objectives and trust boundaries

Protect confidentiality of identity, account and evaluation data; preserve integrity/provenance of public records and decisions; maintain availability of safe public reading; and make privileged actions attributable and reviewable. Trust boundaries are client, API edge, application/domain, public-record persistence, restricted verification, evaluation privacy, admin/audit, object storage and external providers. See [proposed architecture](./SYSTEM_ARCHITECTURE.md).

## 2. Threat scenarios and proposed controls

| ID | Threat | Abuse case / impact | Proposed control and future test |
|---|---|---|---|
| TH-01 | Authentication/account takeover | Credential/session theft enables account or evaluation changes | Secure provider adapter, session lifecycle, recovery controls, step-up for sensitive actions, anomaly response; test expiry, replay and recovery |
| TH-02 | Broken authorization / privilege escalation | User accesses editor, verifier, SuperAdmin or another user's object | Deny-by-default server-side permission/scope/object checks; enumerate allow/deny matrix and direct-object tests |
| TH-03 | Self-approval / collusion | Staff approves own record or verification, or two roles bypass separation | Independent reviewer assignment, immutable actor attribution, dual control for designated actions; test self and conflict paths |
| TH-04 | Impersonation misuse | Support alters user data or casts as target | Explicit reason/target/expiry/banner, true-actor audit, prohibit vote/verification/role changes; test every forbidden action |
| TH-05 | Vote duplication or manipulation | Duplicate identities, replay, automation, brigading or revision abuse | Eligibility service, opaque subject, idempotency, anomaly triage and one-active-choice invariant; tests use synthetic accounts |
| TH-06 | Vote linkage/re-identification | Insider or public queries link identity to choice or infer a small cohort | Resolve and independently review physical separation or an equivalently strong isolation boundary before voting implementation; public aggregates remain Q01-gated; no individual-choice access, third-party receipt verification or exportable/shareable receipt |
| TH-07 | Data breach/exfiltration | Verification documents, contacts or records exposed via API/object/log/backup | Minimize and classify data, encryption, scoped credentials, allowlisted responses, access logging, backup review and incident response |
| TH-08 | Insider misuse | Privileged staff accesses or exports sensitive data without purpose | Least privilege, just-in-time access, dual control, audit alerts, periodic review and sanctions/appeal governance |
| TH-09 | Import poisoning | Malicious or inaccurate source data corrupts public facts | Staging/quarantine, source/licence review, input hash, validation, human reconciliation, reversible publication; malicious-file tests |
| TH-10 | Scraping/harassment | Bulk collection of sensitive data or targeted abuse | No public personal evaluation data; rate limits, privacy-safe public projections, abuse handling and lawful access review |
| TH-11 | Content poisoning/defamation | Fabricated or misleading claims published as fact | Provenance, issuer labels, review, confidence/uncertainty, right of reply, corrections, sensitive escalation and appeal |
| TH-12 | Spam/automated abuse | Flooded submissions, account creation or evaluation endpoints | Per-action abuse controls, rate limits, moderation queue capacity and neutral response; test throttling and no false success |
| TH-13 | Denial of service/provider failure | Public/API or sensitive workflow unavailable or inconsistent | Rate limits, bounded work, timeouts, resource controls, graceful public degradation; fail closed for authz/evaluation |
| TH-14 | Audit tampering | Privileged actor alters/deletes event chain | Append-only application policy, external checkpoints proposal, integrity verification and documented recovery; tamper simulation |
| TH-15 | Supply-chain/provider compromise | Dependency or vendor access exposes users or alters data | Dependency review, secret management, adapter isolation, vendor/term review, incident and exit plans |
| TH-16 | Offline/shared-device exposure | Private state survives cache or is exposed to household user | Public-only cache allowlist, sign-out clearing, no private offline view/action queue; inspect storage and offline scenarios |
| TH-17 | Election-period misuse | Public evaluation is mistaken for poll, campaign or election result | Explicit copy boundaries and counsel-approved jurisdiction configuration; test default-safe mode and no unapproved activation |

## 3. Baseline controls

- Enforce authentication, authorization, eligibility and business rules server-side. The frontend and hidden navigation are not security controls.
- Never expose service-role keys, signing keys or provider secrets in browser bundles, logs or source control.
- Validate inputs, encode outputs, apply CSRF/session protections as appropriate, protect uploads, rate-limit sensitive actions, and return neutral errors for protected-resource discovery.
- Separate public projections from personal and restricted models; use deny-by-default storage and API policies. Database row-level controls are defense in depth, not the only control.
- Use secure administrative accounts, MFA/step-up authentication proposal, scoped access, access review and incident alerts.
- Before voting implementation, resolve the HIGH-PRIORITY security decision to physically separate voter identity mapping from vote-choice records or establish an equivalently strong, independently reviewed isolation boundary. Logical labels or a separate service alone are not assumed sufficient without evidence.
- No individual choice is exposed to staff or the public. A private, authenticated-voter-only confirmation may show only that voter's own submitted choice; it is non-shareable/non-exportable and is not coercive proof. Public results/aggregates are separate outputs, subject to Q01, and cannot link a choice to a voter. Aggregation cannot be called perfectly anonymous.
- Maintain source lineage, immutable version references, reviewer identity, reason and correction path for material records.
- Secure backups and object lifecycle; test restore and deletion/expiry. No production service/retention values are selected here.
- Use synthetic people/records only. Never commit secrets, identity documents or real user/politician test data.

## 4. Audit, integrity and non-repudiation limits

Record material administrative, authorization, verification-decision, publication, adjudication, evaluation-write (without exposing choice in general audit views), export and configuration actions. Capture actor, action, target, time, reason, correlation and result, with data minimization. Restrict access to sensitive audit fields.

Append-only application design, chaining and independent checkpoints are proposed controls. They do not make a single database absolutely immutable, prove who controlled an account, or eliminate collusion/provider compromise. Define key ownership, checkpoint frequency, retention, verification, alerting and recovery in later phases.

## 5. Security response and residual risk

Before sensitive data collection, name an incident owner and define containment, credential/key revocation, evidence preservation, privacy/legal notification assessment, user support, recovery and post-incident review. Provider outage/compromise, insider collusion, coercion, re-identification, biased source coverage and denial-of-service remain residual risks.

## 6. Open security decisions

The physical-separation or equivalently strong isolation boundary between voter identity mapping and vote-choice records is a HIGH-PRIORITY decision, unresolved and blocking all voting implementation until owner decision and independent security/privacy review (SEC-01/ADR-002). Auth provider/session architecture; key management; admin MFA and dual-control scope; rate limits/anti-abuse signals; audit checkpoint operator/retention; security contact and incident SLAs; vendor/data-region assessments; upload scanning; and Q01/Q03 remain open for their phase owners. No production-ready security assertion is made.
