# ADR-001 — Provider-Neutral Modular Architecture

**Date:** 8 November 2026
**Status:** PROPOSED
**Decision owner:** Human project owner
**Supersedes:** None

## Context

NetaMonitor needs a portable baseline across web delivery, API/runtime, relational persistence, authentication, object storage, notifications, maps and imports. The handbook proposes React/TypeScript/Vite, Hono/TypeScript, PostgreSQL, Cloudflare and Supabase. Provider-specific business logic or a premature service split could create lock-in and complicate security.

## Options considered

1. Adopt the proposed vendors directly throughout domain/application logic.
2. Use a provider-neutral modular application with explicit ports/adapters; choose initial adapters after PH-00 approval and PH-01 evaluation.
3. Begin with distributed services and independent persistence for every domain.

## Proposed decision

Start with clearly bounded domain/application modules behind provider-neutral interfaces. Keep API and domain behavior runtime-independent; use adapters for identity, relational repositories, object storage, notifications, maps, import sources and hosting. PostgreSQL with documented migrations is the proposed relational baseline. Treat every named vendor/runtime as replaceable and not yet selected.

## Rationale and consequences

Option 2 is a proportionate portability boundary with fewer operational moving parts than a distributed design. It requires stable interface/contract tests and explicit management of any provider-specific capabilities. It does not require separate physical databases or microservices. PH-01 must evaluate deployment, cost, data processing, failure modes, local development and exit/export plans before accepting implementation choices.

## Security and privacy implications

Adapters must not bypass server-side authz, expose provider secrets, leak sensitive fields, or make provider claims equivalent to identity/residence. Data region, subprocessors, key handling, backups and legal terms remain open. Provider substitution does not itself establish privacy or compliance.

## Implementation impact

PH-01 should document dependency direction, contracts, migration/export path, adapter testing and clean-clone commands. Do not build an application during PH-00.

## References

- `AGENTS.md` architecture baseline
- `docs/SYSTEM_ARCHITECTURE.md`
- `docs/NON_FUNCTIONAL_REQUIREMENTS.md`
- `docs/decisions/DEC-002-open-product-and-policy-questions.md`
