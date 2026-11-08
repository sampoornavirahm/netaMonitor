# AGENTS.md — NetaMonitor

## 1. Source of truth and mandatory reading
The Git repository is authoritative. Never rely on chat history or model memory. Before work, read: `README.md`, `IMPLEMENTATION_HANDBOOK.md`, `phase-register.csv`, this file, the assigned `prompts/PH-XX/` prompt, the current `docs/phases/PH-XX/` brief and all relevant accepted specifications, ADRs and decisions. For PH-00 Development, also read all eight UI source deliverables and `docs/phases/PH-00/README.md`. If a referenced file is missing, identify whether it is expected to be created in this phase; do not silently invent it.

## 2. Project identity
- Product name: **NetaMonitor**.
- Product: India-first, non-partisan, evidence-led civic accountability platform.
- Current initial phase: PH-00 — product definition, governance and decision baseline.
- Repository source of truth: this Git repository.

## 3. Architecture baseline (subject to PH-00 approval)
- Web: React + TypeScript + Vite.
- API: TypeScript + Hono initially, behind provider-neutral application/domain layers.
- Database: PostgreSQL with committed SQL migrations.
- Initial hosting adapters: Cloudflare Pages/Workers, Supabase Auth/Postgres, Cloudflare R2.
- Tests: Vitest, Playwright and axe-core.
- Contracts: OpenAPI, shared types and runtime validation.
- Treat this as a proposed baseline until PH-00 accepts the relevant ADRs.

## 4. Non-negotiable trust, security and privacy rules
- Enforce authentication, authorisation, eligibility and business rules server-side.
- Never put service-role keys or provider secrets in frontend code.
- Separate registered/contact-confirmed, identity-verified and constituency-verified states. OTP is not identity or residence proof.
- Do not scrape voter rolls or implement Aadhaar biometric/eKYC. Any identity method requires privacy/legal review and data minimisation.
- Separate voter identity mapping from ballot choices; public APIs expose aggregates only and suppress small cohorts. No public individual vote history.
- No voting while Admin/SuperAdmin impersonation is active. Impersonation must be explicit, time-limited, visible to the operator and fully audited.
- Admins must not approve their own verification or content submissions.
- Keep editorial evidence assessment separate from citizen evaluations. Citizen votes are not proof and are not official election ballots.
- Preserve historical office terms, candidacies, party memberships, affiliations and financial disclosures; never overwrite temporal history.
- Every material public fact requires provenance, attribution, date/status and a correction/reply path.
- Do not turn an association into proof of wrongdoing. Clearly label self-declared, official and independently corroborated financial facts.
- SuperAdmin is hidden from ordinary navigation but is not secured by obscurity; enforce permissions server-side.
- Audit events must be append-only and tamper-evident, with documented limitations; never claim a single database is absolutely immutable.
- No paid rankings, paid vote weighting or political advertising in the MVP.
- Offline mode must not submit votes or cache identity evidence, admin data or private records.
- Use synthetic test persons and records only. Never commit secrets, identity documents or personal data.
- Prefer provider adapters, documented migrations and portable contracts.

## 5. Required agent workflow
1. Confirm phase dependencies are marked ACCEPTED.
2. UI Design agent produces the assigned design/product artifacts.
3. Human reviews and merges those artifacts.
4. Development agent works from the updated `main`, implementing only the assigned phase and running unit/integration tests where code exists.
5. Human reviews and merges.
6. Independent E2E/QA agent tests the running application for implementation phases. For PH-00, QA audits specifications only; no running application exists.
7. Human phase owner records the gate decision. Do not start dependent phases before acceptance.

## 6. PH-00 special boundary
PH-00 is documentation and specification work only. Do not scaffold the runtime application, add database migrations, implement APIs, write application code or attempt browser E2E execution. Produce product requirements, user journeys, domain and data specifications, security/privacy/governance policies, proposed architecture and ADRs, acceptance criteria, requirement traceability and a future test strategy. Flag open decisions clearly.

## 7. Required documentation updates
Update the relevant phase folder, `AGENTS.md`, `CHANGELOG.md`, and impacted product/architecture/domain/schema/API/security/design/test documents and ADRs/decisions. A handoff must include: summary, changed files, decisions, open questions, tests/checks and exact outcomes, defects, risks, next steps and phase readiness.
Decision status is recorded in canonical files under `docs/adr/` and `docs/decisions/`; only explicitly owner-approved items may be marked `ACCEPTED`. For PH-00, keep UI source documents in `docs/phases/PH-00/` and link to them rather than creating duplicate root copies. The QA report is independent; the human owner alone records phase acceptance.

## 8. Branching rules
- `main` is the only accepted source of truth.
- Never commit directly to `main`. Use a phase/role branch and Pull Request.
- For PH-00 use `ph00/ui-design`, `ph00/development`, and `ph00/qa`.
- Create branches sequentially from the latest approved `main`; do not create all three from an outdated base.
- Each agent works in its own isolated checkout/workspace. Do not share a mutable working directory between agents.
- Only the human project owner approves merges and phase acceptance. QA must not approve its own report or edit implementation to hide defects.
- Record important technical choices as ADRs and product/policy choices as decisions. Supersede records; do not erase history.

## 9. Free-tier and deployment discipline
Do not assume free tiers are permanent or unlimited. Record quotas, data retention, backups, inactivity pauses and service dependencies. Do not deploy publicly, incur paid services or use production personal data without explicit approval.

## 10. Commands
Do not invent package-manager or test commands. Before PH-01, there may be no runnable app. PH-01 must document exact clean-clone setup, lint, typecheck, test, build and migration commands in `README.md`.
