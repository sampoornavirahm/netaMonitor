# NetaMonitor Privacy Policy Requirements and Threat Model

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft requirements; no legal compliance claim
**Decision owner:** Human project owner · **Required review:** Qualified Indian privacy/legal counsel

## 1. Purpose and notice requirements

This is a product/privacy specification, not a public legal privacy notice or legal opinion. Before collection, counsel and the owner must determine applicable law, commencement, roles, lawful grounds, notice/consent duties, rights, cross-border/provider terms, retention, breach and grievance obligations. Verify current law at the relevant phase; do not rely on handbook dates as legal advice.

For each processing purpose, provide plain-language notice covering controller/operator identity as legally determined, data categories, purpose, basis/choice, recipients/processors, location/transfers where relevant, retention/deletion, user choices/rights, complaint/contact route, minors/accessibility and consequences of refusal. Consent must be specific and withdrawable where applicable; service-essential and optional purposes must not be conflated.

## 2. Data inventory and privacy boundaries

| Category | Examples | Classification | Default exposure |
|---|---|---|---|
| Public sourced records | Office terms, promises, source metadata, adjudications, published replies | Public after review | Public allowlisted projections |
| Account/contact | Provider subject, contact confirmation, recovery and preferences | Personal | Account holder and minimum support/auth service |
| Identity/constituency material | Evidence, address/identity attributes, reviewer notes | Restricted | Assigned verification role/service only |
| Eligibility assertion | Tier, constituency reference, validity, decision | Restricted | Eligibility service; public sees no evidence or detailed denial reason |
| Citizen evaluation | Choice, revision and evaluation time | Highly restricted | Vote-choice boundary; no staff individual-choice view |
| Identity-choice mapping | Opaque eligibility subject-to-account mapping | Highest restriction | Narrow separate service/key boundary |
| Private voter confirmation | Confirmation available only to the authenticated voter, showing only their own submitted choice | Highly restricted / private | Non-shareable and non-exportable; not a public result, third-party receipt or proof |
| Public results/aggregates | Counts, percentages, distributions and cohort statistics | Derived; may remain sensitive | Separate disclosure product; public only after Q01 and re-identification review |
| Submission/moderation | Contact details, uploads, reports, abuse signals | Personal/restricted | Assigned moderation/editorial workflow |
| Security/audit/telemetry | Session, admin events, IP/abuse indicators, correlation data | Restricted | Operational/security roles with purpose and expiry |
| Aggregate/derived | Counts, scores, analytics | Derived; may remain sensitive | Public only after Q01 and re-identification review |

Do not treat pseudonymous or aggregated data as automatically anonymous. Joining, timing, differencing and external datasets can re-identify individuals.

## 3. Privacy threat model

Threat model is a starting point, not a completed DPIA or legal assessment.

| Threat / affected data | Example abuse or failure | Proposed control | Residual risk / owner |
|---|---|---|---|
| Identity-to-evaluation linkage | Insider or query joins account, constituency evidence and choice | HIGH-PRIORITY gate: resolve physical separation or an equivalently strong isolation boundary before voting implementation; document data flows and permitted cross-boundary operations; obtain independent review | Correlation, collusion and provider compromise remain; SEC-01/ADR-002 |
| Small-cohort disclosure | Public result reveals likely choice in a small area | Q01 suppression, no cross-tabs, minimum query controls, privacy review and aggregate-only API | Differencing, external knowledge, threshold insufficiency; Q01 owner |
| Coercive proof | User is pressured to demonstrate a submitted choice | Distinguish the private authenticated-voter confirmation (own submitted choice only, non-shareable, non-exportable) from public aggregates. No public lookup, third-party verification, signed attestation or exportable/shareable receipt | A person may still photograph/show their own screen; never claim coercion is impossible; UX/security owner |
| Raw verification exposure | Misconfigured storage, support access, backup or logs reveal documents | Avoid raw retention, segregated encrypted storage, scoped short-lived access, redaction, audit, backup expiry | Insider/provider compromise; Q03/legal/security |
| Purpose creep | Verification/account data reused for analytics/targeting | Purpose tags, separate permissions, no political profiling/advertising, review of new use | Future organizational pressure; governance owner |
| Account recovery takeover | Attacker resets account and changes evaluation | Risk-based recovery, re-authentication, notifications and controlled change policy | SIM/email compromise; PH-03/security |
| Support impersonation misuse | Staff views or changes personal records | Justification, time limit, visible banner, actor attribution, restricted actions and review | Colluding staff or victim-device exposure; PH-04 |
| Logs/telemetry leak | Tokens, contact, document or vote choice logged | Structured allowlisted logging, redaction, no secrets/choice/evidence, access and retention limits | Vendor-level telemetry; PH-01/operations |
| Cache/shared-device disclosure | Private receipt or account data persists offline | Public-only allowlist, no private cache, sign-out cleanup, shared-device notice | OS screenshots/other device access; PH-24 |
| Import/source overcollection | Bulk records include personal data beyond use | Source/licence review, field minimization, quarantine and human reconciliation | Misleading source terms/inaccurate data; PH-22 |
| Data correction/deletion conflict | User request conflicts with public history or legal hold | Explicit retention/legal review, correct public facts with provenance, restrict personal identifiers | Legal and trust trade-off; Q03 |
| Cross-provider exposure | Provider access, region or subprocessor conflicts with expectations | Vendor due diligence, data-flow inventory, contract/security review, portability plan | Provider/jurisdiction risk; PH-01 and counsel |

## 4. Required privacy controls

- Maintain a data-flow inventory with purpose, classification, source, recipients, storage, region, access roles, retention and deletion state.
- Minimize collection; do not scrape voter rolls or process Aadhaar biometric/eKYC.
- Before voting implementation, resolve and independently review the HIGH-PRIORITY physical-separation or equivalently strong isolation decision between identity mapping and vote-choice records.
- Distinguish the private, non-shareable/non-exportable confirmation showing only the authenticated voter's own submitted choice from public results/aggregates. Public outputs never expose individual choices and remain Q01-gated.
- Encrypt sensitive data in transit and at rest; restrict key access, rotate keys and keep secrets outside source/browser. Exact cryptographic implementation is PH-01.
- Exclude identity evidence, vote choices, credentials and unnecessary PII from logs, analytics, notifications, exports and caches.
- Gate new use, disclosure, third-party access and public dataset fields through privacy/security review.
- Define access request, correction, deletion/closure, retention exception, legal hold, breach triage and user complaint workflows after legal review.
- Do not imply perfect anonymity; describe residual risks in consent and methodology without overstating guarantees.
- Use synthetic test identities; never use real political/electoral identity records as fixtures.

## 5. Privacy review gates

Before PH-05 collection: Q03 legal basis, privacy notice, route/vendor, retention, deletion and breach owner. Before any PH-15 voting implementation: resolve SEC-01 and independently review the identity-mapping/choice isolation boundary. Before public results: Q01 threshold, query/differencing risk, evaluation revision/audit trade-off, re-identification and coercion review. Before PH-22 imports: licensing, provenance and minimization. Before public API/open data: field-by-field release and linkage review. Before production: incident plan, subprocessor/region review, access audit, restore/expiry test and counsel approval.

## 6. Open issues

Q01 minimum aggregation/suppression policy; Q03 privacy/legal/retention/identity route; data controller/operator roles, applicable legal basis, user rights and grievance process; retention periods; minors; contact details; cross-border/processor handling; breach notification and audit duration remain unresolved. Do not label NetaMonitor compliant with a statute absent counsel review.
