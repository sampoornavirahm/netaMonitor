# ADR-003 — Versioned Provenance and Tamper-Evident Audit

**Date:** 8 November 2026
**Status:** PROPOSED
**Decision owner:** Human project owner
**Supersedes:** None

## Context

Public claims and promise assessments may be challenged or corrected. The product must preserve what was known, by whom, from which source and when. Privileged actions require accountability, but a database alone cannot guarantee absolute immutability.

## Options considered

1. Update records in place and keep conventional mutable logs.
2. Keep versioned public records, append-oriented decision/audit events, provenance and correction links; evaluate independent integrity checkpoints.
3. Claim immutable/blockchain storage for all records.

## Proposed decision

Use explicit record versions and source lineage; corrections create dated versions/notices rather than silent replacement. Maintain append-oriented, access-controlled audit events for material decisions and privileged actions. Evaluate hash chaining and independent checkpoints for tamper evidence; document trust assumptions, retention and recovery limits. Do not claim absolute immutability or adopt a blockchain by default.

## Rationale and consequences

Option 2 supports contestability, corrections, reproducibility and proportionate auditability without claiming technical properties beyond evidence. It requires storage/retention design, privacy minimization, integrity verification and recovery procedures. Corrections and legally required deletion may require carefully reviewed redaction/tombstone patterns.

## Security and privacy implications

Audit logs can themselves expose personal information. Restrict access, avoid vote choice/identity evidence, minimize event fields and decide retention/legal holds. A privileged database operator may still tamper absent independent controls; external checkpoints only increase detection.

## Implementation impact

PH-01/04/08/10 must define version identifiers, actor attribution, event schema, access review, checkpoint operator, alerting, recovery and retention. No schema or migration is created in PH-00.

## References

- `docs/DATA_MODEL.md`
- `docs/SECURITY_MODEL.md`
- `docs/MODERATION_POLICY.md`
- `AGENTS.md` non-negotiable audit rule
