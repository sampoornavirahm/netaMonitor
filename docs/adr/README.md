# Architecture Decision Records (ADRs)

Use ADRs for technical/architectural decisions that affect boundaries, providers, data integrity, security, scalability or portability. Suggested filename: `ADR-NNN-short-title.md`.

Each ADR must include: title, date, status, decision owner, context/problem, options considered, decision, rationale, consequences/trade-offs, security/privacy implications, implementation impact, references and supersedes/superseded-by links. Status values: PROPOSED, ACCEPTED, REJECTED, SUPERSEDED. LLMs may propose; only the human project owner may accept. Never delete an accepted ADR; supersede it with a new record.

## PH-00 proposals

| ADR | Topic | Status |
|---|---|---|
| [ADR-001](./ADR-001-provider-neutral-modular-architecture.md) | Provider-neutral modular architecture | PROPOSED |
| [ADR-002](./ADR-002-sensitive-data-boundaries.md) | Restricted verification and evaluation data boundaries | PROPOSED |
| [ADR-003](./ADR-003-versioned-provenance-and-audit.md) | Versioned provenance and tamper-evident audit | PROPOSED |
| [ADR-004](./ADR-004-contract-first-api.md) | Contract-first API and public data projections | PROPOSED |
