# ADR-002 — Restricted Verification and Evaluation Data Boundaries

**Date:** 8 November 2026
**Status:** PROPOSED
**Decision owner:** Human project owner
**Supersedes:** None
**Priority:** HIGH — unresolved security decision; must be resolved and independently reviewed before any voting implementation.

## Context

The platform may process identity/constituency evidence and confidential civic evaluations. If joined directly in public records, general staff tooling, telemetry or exports, this data can expose political opinion, enable coercion or permit re-identification.

## Options considered

1. Store account, verification and evaluation choice in one broadly accessible domain model.
2. Require physical separation, or an equivalently strong isolation boundary, between voter identity mapping and vote-choice records; define and review the exact boundary, access paths and evidence before voting implementation.
3. Avoid all citizen evaluations/verification permanently.

## Proposed decision

Require a design decision that provides physical separation or an equivalently strong isolation boundary between voter identity mapping and vote-choice records. The boundary, threat model, access paths, key/access controls, failure behavior and independent review must be documented and approved before any voting implementation begins. The particular architecture and what evidence demonstrates equivalent strength remain unresolved; this ADR remains PROPOSED and does not approve an implementation.

At minimum, the eventual design must prevent ordinary identity/mapping access from revealing choices and prevent choice-record access from resolving voter identity; any eligibility operation crossing the boundary must use a narrowly scoped, explicitly authorized and auditable interface. These are review criteria, not a selection of physical topology or a claim that a particular service split is sufficient.

Distinguish two outputs:

- **Private voter confirmation:** after a successful submission, an authenticated voter may see a non-shareable, non-exportable confirmation showing only that voter's own submitted choice. It must not expose another person's vote and must not be designed or represented as coercive proof.
- **Public results:** any published results, aggregates, counts or percentages are separate disclosure products, never receipts. They may expose aggregates only after the Q01 policy and privacy review are resolved; they must never identify a voter or link an individual choice.

Do not expose individual choice to ordinary staff, public APIs, logs, analytics or offline caches.

## Rationale and consequences

The required isolation gate reduces routine linkage paths but adds operational complexity and does not guarantee anonymity. The owner must resolve and review the isolation design before voting implementation, and approve the Q01 aggregate policy and Q03 legal/retention policy before relevant collection or public publication. Private voter confirmation is distinct from public aggregate disclosure; Q01 governs the latter.

## Security and privacy implications

Residual risks include timing correlation, insider collusion, endpoint misconfiguration, small-cohort inference, coercion through screenshots, backup/log leakage and provider compromise. A private confirmation cannot prevent a person from photographing or showing their own screen; the product must not make it exportable, verifiable by a third party or suitable as proof. Threat model and privacy review must test these risks; thresholds alone are insufficient.

## Implementation impact

Future APIs, repositories, audit design, analytics, cache, backups and role grants must preserve separation. Before any voting implementation, a high-priority security decision must determine physical separation or demonstrate an equivalently strong isolation boundary, pass independent security/privacy review, and prove denial paths. Q01 and Q03 remain separate gates; this clarification does not change their status or accept this ADR.

## References

- `docs/DATA_MODEL.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md`
- `docs/SECURITY_MODEL.md`
- `docs/VERIFICATION_POLICY.md`
- `docs/decisions/DEC-001-ui-experience-baseline.md` (D05)
- `docs/decisions/DEC-002-open-product-and-policy-questions.md` (Q01/Q03)
