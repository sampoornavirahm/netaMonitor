# ADR-002 — Restricted Verification and Evaluation Data Boundaries

**Date:** 8 November 2026
**Status:** PROPOSED
**Decision owner:** Human project owner
**Supersedes:** None

## Context

The platform may process identity/constituency evidence and confidential civic evaluations. If joined directly in public records, general staff tooling, telemetry or exports, this data can expose political opinion, enable coercion or permit re-identification.

## Options considered

1. Store account, verification and evaluation choice in one broadly accessible domain model.
2. Apply logical data boundaries, least-privilege services, opaque evaluation subjects and aggregate-only projections; decide whether physical separation is necessary after threat/privacy review.
3. Avoid all citizen evaluations/verification permanently.

## Proposed decision

Adopt logical separation as a minimum design requirement: verification evidence and decisions are restricted; evaluation choices are held behind a narrow privacy boundary; identity-to-opaque-subject mapping is separate from the choice view; public output is aggregate-only. Do not expose individual choice to ordinary staff, public APIs, logs, analytics or offline caches. Physical separation, key custody and retention remain implementation gates.

## Rationale and consequences

Option 2 supports the product purpose while reducing routine linkage paths. It adds operational complexity, requires careful eligibility/revision design, and does not guarantee anonymity. The owner must approve the Q01 aggregate policy and Q03 legal/retention policy before relevant collection or publication.

## Security and privacy implications

Residual risks include timing correlation, insider collusion, endpoint misconfiguration, small-cohort inference, coercion through screenshots, backup/log leakage and provider compromise. Threat model and privacy review must test these risks; thresholds alone are insufficient.

## Implementation impact

Future APIs, repositories, audit design, analytics, cache, backups and role grants must preserve separation. A PH-01/PH-05/PH-15 design decision must determine storage/key boundary and prove denial paths.

## References

- `docs/DATA_MODEL.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md`
- `docs/SECURITY_MODEL.md`
- `docs/VERIFICATION_POLICY.md`
- `docs/decisions/DEC-001-ui-experience-baseline.md` (D05)
- `docs/decisions/DEC-002-open-product-and-policy-questions.md` (Q01/Q03)
