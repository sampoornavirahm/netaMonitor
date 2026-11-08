# NetaMonitor Non-Functional Requirements

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review
**Decision owner:** Human project owner · Targets below are proposals unless stated in an accepted decision.

| ID | Quality attribute | Requirement and verification intent | Status / owner |
|---|---|---|---|
| NFR-SEC-001 | Authorization | Enforce authentication, authorization, eligibility and business rules at trusted server boundaries; client visibility is not a security control. Verify allow and deny cases for every permission. | Baseline; security owner |
| NFR-SEC-002 | Secrets | No provider secret, service-role key or privileged credential is shipped to the browser or committed. Verify build artifacts and secret-scanning results in implementation phases. | Non-negotiable |
| NFR-SEC-003 | Secure development | Use threat modelling, input validation, output encoding, secure session practices, rate limiting, dependency review and security tests proportionate to risk. OWASP ASVS is a reference, not a compliance claim. | Proposed; security owner |
| NFR-SEC-004 | Audit | Privileged and material editorial actions have attributable, append-only application records and integrity monitoring; limitations and recovery are documented. | Baseline; audit design proposed |
| NFR-PRV-001 | Minimisation | Collect only data necessary for a documented purpose; prefer derived eligibility facts over retained identity documents. No identity/vendor or retention decision is implied. | Non-negotiable; legal review |
| NFR-PRV-002 | Confidentiality | Restrict identity evidence and account data by purpose and permission; separate them from public domain projections and vote choice. Verify with access-control and data-flow tests. | Non-negotiable |
| NFR-PRV-003 | Evaluation privacy | Private confirmation is authenticated-voter-only, shows only that voter's own submitted choice, and is non-shareable/non-exportable; it is distinct from public results/aggregates. No public individual choice or third-party-verifiable receipt; public aggregate disclosure awaits Q01, including differencing/re-identification review. | Non-negotiable; Q01 open |
| NFR-PRV-004 | Retention | Each data class needs an approved retention, deletion, backup-expiry and legal-hold rule before production collection. No durations are approved in PH-00. | Blocked; Q03/legal |
| NFR-AVA-001 | Availability | Define service availability and recovery objectives during PH-01/operational design based on pilot risk, provider plans and cost approval. Do not promise an SLA now. | Open; product/operations |
| NFR-AVA-002 | Failure handling | Provider outages, timeouts, retries, rate limits and partial failure must be explicit. No failure may be presented as a successful vote, verification or publication. | Required |
| NFR-AVA-003 | Recovery | Document backup scope, restore testing, recovery-point/time objectives, ownership, encryption and vendor dependency before production. | Open; PH-01/operations |
| NFR-PERF-001 | Performance | Establish measurable page/API budgets, workload and percentile targets from pilot journeys before implementation; measure on representative low-bandwidth devices. | Open; PH-01 |
| NFR-PERF-002 | Efficiency | Public discovery is paginated, text-first and avoids unnecessary large media transfers; use caching only for allowlisted public content. | Required |
| NFR-A11Y-001 | Accessibility | Target WCAG 2.2 AA across public, account and admin journeys; keyboard, screen reader, contrast, zoom/reflow and non-colour cues are tested. This is a target, not a legal-conformance claim. | UX-approved target |
| NFR-A11Y-002 | Alternatives | Charts have equivalent text/table representations; maps have a list alternative; verification has an assisted route. | UX-approved |
| NFR-UX-001 | Responsive | Core journeys work at 320 CSS px through desktop without loss of content or function; exceptions must include an accessible alternative. | UX-approved |
| NFR-UX-002 | Offline | Only previously accessed, allowlisted public information may be cached; freshness is visible. No private data or action queue; cache policy requires security review. | UX-approved |
| NFR-I18N-001 | Localization | Support English, Hindi and Marathi for core journeys; preserve original source language and label translations. Plan for text expansion and locale-specific dates/numbers. | Product target |
| NFR-I18N-002 | Search | Search must handle script, transliteration/spelling variants and ambiguous people/office terms without silently selecting an entity. Exact ranking/normalization remains design work. | Proposed |
| NFR-PORT-001 | Portability | Domain rules are provider-neutral behind documented boundaries; database migrations, API contracts and export strategy are portable. | Proposed; ADR-001 |
| NFR-PORT-002 | Portability | Provider adapters cover authentication, object storage, notifications, maps/geocoding, imports and hosting. Vendor-specific features require documented exit/impact assessment. | Proposed; ADR-001 |
| NFR-DATA-001 | Integrity | Temporal records, source provenance, adjudication history, corrections and import reconciliation preserve prior states and effective dates. | Required |
| NFR-DATA-002 | Consistency | Stable identifiers, explicit lifecycle constraints and deterministic versioned score inputs are required. Concurrency and idempotency are tested in the owning phases. | Required |
| NFR-OBS-001 | Observability | Use structured operational telemetry with access controls and minimised/redacted personal data; do not log secrets, identity evidence or vote choices. | Required |
| NFR-OBS-002 | Incident response | Define security/privacy incident escalation, containment, preservation, notification assessment and recovery before collection of sensitive data. | Open; legal/operations |
| NFR-MNT-001 | Maintainability | Document domain boundaries, state machines, decision status and traceability; use clean-clone commands and automated checks in PH-01. | Required |
| NFR-TEST-001 | Testability | Implement deterministic synthetic fixtures, contract tests, accessibility/security tests, and risk-based E2E tests; no real personal or political data in fixtures. | Required |
| NFR-COST-001 | Cost | Re-check vendor quotas, retention, backup, inactivity and egress terms at decision/deployment time; alert on usage and obtain explicit paid-service approval. | Required |
| NFR-NEUT-001 | Neutrality | No paid rankings, paid vote weighting or political advertising in MVP. Content rules and editorial decisions apply viewpoint-neutral criteria. | Non-negotiable |

## Open target decisions

Availability/SLO and RTO/RPO, performance budgets, cache staleness, accessibility audit method, retention schedules, telemetry retention, abuse-rate limits, evaluation suppression, and deployment cost thresholds require named owner decisions in the appropriate phases. PH-00 proposes no numerical target for these unresolved matters.
