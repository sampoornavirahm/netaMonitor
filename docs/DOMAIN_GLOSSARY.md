# NetaMonitor Domain Glossary

**Phase:** PH-00 · **Version:** 0.1 · **Status:** Draft for human review

| Term | Definition and boundary |
|---|---|
| Account | Platform identity and settings record. It is not proof of legal identity, residence, eligibility or political preference. |
| Contact-confirmed | Account state showing control of an email/phone contact was confirmed; not identity or residence proof. |
| Identity-verified | Restricted verification decision that an approved process established the required uniqueness/identity claim. Method and legal basis remain open. |
| Constituency-verified | Time-bounded decision associating an identity-verified account with a named constituency for a defined eligibility purpose. It is not a public profile fact. |
| Person | Public-domain individual entity, distinct from an account, candidacy, office or term. Identity resolution and publication require evidence and review. |
| Office type | Defined public office category (for example MP, MLA or local representative), with jurisdiction and level. The exact supported taxonomy is a phase decision. |
| Constituency | Geographic/electoral unit with type, jurisdiction and effective-dated boundaries. A manually selected unit is not verified residence. |
| Boundary version | Immutable/effective-dated representation of a constituency boundary and its source. |
| Election event | Dated election context for a jurisdiction and office type. It is not the platform's citizen evaluation. |
| Candidacy | A person's participation as a candidate in a particular election; distinct from winning or holding office. |
| Election result | Attributed official or sourced outcome of an election, with source and verification state; never inferred from candidacy alone. |
| Term | Effective-dated appointment/elected service in an office, linked to person, office type, constituency and election context where applicable. |
| Party membership | Effective-dated relationship of a person to a political party. A past affiliation is retained, not overwritten. |
| Organisation / affiliation | Dated, sourced relationship to an organisation or group with a precise relationship type. Association alone is not wrongdoing. |
| Public activity | Dated, sourced event (such as speech, protest or public action); participation and role must not be inferred beyond evidence. |
| Promise | A source-backed public commitment with original wording/context, ownership/attribution, measurable criteria, due date and lifecycle. |
| Responsibility attribution | Documented link between a promise/outcome and the actor/authority's evidenced role or influence; shared responsibility is explicit. |
| Milestone | Dated, measurable intermediate event associated with a promise or project. |
| Source | A document, record, dataset, person or publication from which a claim/evidence item derives; includes terms, provenance and quality review. |
| Provenance | Origin, issuer, publication/retrieval dates, transformations, attribution, licensing/terms and review history for a record or assertion. |
| Evidence | Material bearing on a claim or promise; may be official, secondary, submitted or unverified. It is not automatically conclusive. |
| Editorial adjudication | Reasoned, attributable reviewer decision about evidence/status, independent of citizen opinion. |
| Evidence performance | Versioned, reproducible measure of editorially assessed eligible promises. Its formula remains a proposal until accepted. |
| Citizen evaluation | One eligible person's confidential civic opinion on a promise. It is not proof, an election ballot or a government certification. |
| Citizen assessment | Aggregate description of eligible citizen evaluations, subject to privacy review and suppression rules. |
| Evidence/data coverage | Measure or explanation of available, missing, current and reviewed information; never an implicit performance score. |
| Financial disclosure | Dated, scoped statement about assets/liabilities/business interests with source and declared/recorded/corroborated basis. |
| Profile claim | A request by a person/delegate to establish authority to speak for an office's profile; does not grant record-editing or suppression rights. |
| Correction | Request to rectify a factual or contextual error in a published record; retains prior version and a decision trail. |
| Right of reply | A labelled response associated with a record, not a replacement or deletion of that record. |
| Appeal | Request for independent reconsideration of a specified decision, ordinarily by a reviewer other than the original decision-maker. |
| Submission | User-provided content/evidence pending moderation/editorial review; not a verified public fact until accepted and properly attributed. |
| Moderation action | Proportionate action under published conduct/content rules, separate from factual adjudication. |
| Verification case/evidence | Restricted information and decision workflow for identity/constituency status; never part of a public profile or vote choice. |
| Evaluation eligibility | Server-side determination that an account may submit/change an evaluation for a particular promise at a particular time. |
| Identity-choice mapping | Highly restricted association used to enforce eligibility/one-active-evaluation rules; logically separated from the choice store. |
| Aggregate result | Disclosure-safe statistics for a cohort and time window; not a per-person response or receipt. Publication rules remain gated by Q01. |
| Score snapshot | Versioned result computed from immutable/identified inputs, methodology version, and computation time. |
| Audit event | Attributable record of material actions, integrity protected and subject to documented retention/access limits. |
| Import job | Tracked ingestion/reconciliation operation with source, licence, input hash, mapping, errors, reviewer and outcome. |
| Effective time | Period during which a fact/relationship is true in the domain, distinct from when the platform learned or recorded it. |
| Recorded time | Time an assertion or change entered the platform, retained for audit/provenance. |
| Restricted data | Personal, verification, security, vote-linkage or unpublished operational data requiring purpose-limited access. |

## Controlled vocabulary note

Use "citizen evaluation" or "citizen assessment" in public-facing product language, not "poll", "mandate" or official election terminology. The legacy `PH-00-UX` capability token `ballot.*` is a traceability label only and does not define a product API.
