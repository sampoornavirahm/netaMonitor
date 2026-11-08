# NetaMonitor Data Source Register

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Template only; no sources registered
**Decision owner:** Human project owner · No real datasets or personal records belong in this template.

## 1. Source onboarding gate

Do not ingest, copy, scrape, republish or rely on a source until a responsible reviewer documents provenance, authority, jurisdiction, licence/terms, allowed use, personal-data exposure, update and correction process, and a safe acquisition method. This register is not permission to access a source. Voter-roll scraping and Aadhaar biometric/eKYC are prohibited.

## 2. Register template

Create one row per source/dataset/version. Leave unknown fields explicitly `UNASSESSED`; do not infer them.

| Field | Required information |
|---|---|
| Source ID / version | Stable internal reference; version or snapshot identifier |
| Source name / URL or locator | Publisher, issuing body, document/dataset name, durable public locator if permitted |
| Source owner / contact | Responsible publisher and correction/contact route |
| Jurisdiction / subject | Geographic and office/data scope; effective boundary/version |
| Source type / authority | Official primary, credible secondary, community-submitted, other; basis for classification |
| Original publication / effective date | Date of source and period the facts apply to |
| Retrieved / captured date | Timestamp and retrieval context |
| Licence / terms / permitted uses | Licence text/version, attribution, reproduction, redistribution and derivative conditions |
| Personal/sensitive content | Categories present, minimization/redaction decision, legal/privacy review |
| Provenance / integrity | File/content hash, archive reference, transformation steps and chain of custody |
| Update cadence / freshness | Expected update schedule, last checked date, stale condition |
| Acquisition method | Manual, official download, documented API or other approved method; no scraping unless separately authorized |
| Quality / confidence assessment | Completeness, known limitations, validation and reviewer rationale |
| Import mapping / version | Proposed entity mapping, normalization and duplicate/reconciliation rules |
| Review and approval | Editor, independent reviewer, decision, dates and conflicts declared |
| Correction / appeal path | Publisher correction process and internal correction route |
| Retention / deletion | Retention class, source terms, backup/cache treatment and decision owner |
| Publication projection | Fields proposed for public release and privacy/linkage review outcome |
| Status | `PROPOSED`, `IN_REVIEW`, `APPROVED_FOR_USE`, `REJECTED`, `SUSPENDED`, `SUPERSEDED` |
| Next review / owner | Review due date, accountable source steward and escalation |

## 3. Empty register

No source records are populated in PH-00. A future source steward should add reviewed entries only after the onboarding gate is satisfied. Each import must also record its input hash, mapping version, reconciliation results, rejected rows, reviewer and resulting published-record versions.
