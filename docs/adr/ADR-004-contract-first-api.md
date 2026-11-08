# ADR-004 — Contract-First API and Public Data Projections

**Date:** 8 November 2026
**Status:** PROPOSED
**Decision owner:** Human project owner
**Supersedes:** None

## Context

The product needs browser and future public API access, with portable client/server contracts and strict separation between public records and personal, verification, administrative and individual evaluation data.

## Options considered

1. Expose persistence models directly and let clients infer behavior.
2. Define versioned language-neutral API contracts and explicit allowlisted projections, with runtime validation and authorization.
3. Design all endpoints and public API scope during PH-00 without accepted domain/policy decisions.

## Proposed decision

Use contract-first API design for implementation phases: versioned OpenAPI (or an owner-approved equivalent), runtime validation at trust boundaries, explicit public and privileged projections, and adapter/service contracts independent of the UI framework. Do not treat UI `capability` labels as endpoints. Final routes, payloads, authentication scheme and public-data commitments are deferred to owning phases.

## Rationale and consequences

Option 2 improves interoperability, contract testing, independent clients and privacy review. It adds contract maintenance/versioning work and requires discipline not to leak persistence details. It allows API scope to be determined only after requirements and policy gates are accepted.

## Security and privacy implications

Every operation requires server-side authentication/authorization/eligibility and output allowlisting. Public contract review must consider enumeration, scraping, rate limits, linkage and small-cohort disclosure. No privileged credential or identity/vote record appears in browser-facing contracts.

## Implementation impact

PH-01 establishes contract tooling and checks; PH-15 defines evaluation operations; PH-23 defines public API/open data after privacy and source-license review.

## References

- `docs/SYSTEM_ARCHITECTURE.md`
- `docs/RBAC_MATRIX.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md`
- `docs/TEST_STRATEGY.md`
