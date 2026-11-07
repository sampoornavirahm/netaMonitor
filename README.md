# NetaMonitor — Project Repository

NetaMonitor is an India-first, non-partisan, evidence-led civic accountability platform. It helps people inspect elected representatives, dated political and public records, promises and evidence, and confidential verified-citizen evaluations. It is not an official election system or a substitute for electoral processes.

## Source of truth

The Git repository is the source of truth. LLM conversations, memory and generated summaries are not authoritative. Every agent must read `AGENTS.md` and the relevant project documents before working.

## Repository contents

- `AGENTS.md` — mandatory operating instructions for every AI and human contributor.
- `IMPLEMENTATION_HANDBOOK.md` — product vision, architecture baseline, policies, phase roadmap and shared standards.
- `phase-register.csv` — phase index and dependencies. Dependencies, not numeric order alone, determine execution order.
- `prompts/PH-XX/` — three role-specific, copy-ready prompts per phase.
- `docs/phases/` — phase briefs, deliverables, QA reports, handoffs and acceptance records.
- `docs/adr/` — Architecture Decision Records (why technical/architectural choices were made).
- `docs/decisions/` — Product, policy and governance decisions (why the product behaves as it does).

## Initial setup

1. Keep the repository private during development.
2. Add the starter-pack files at the repository root, preserving folders.
3. Create `CHANGELOG.md` (included in this pack) and commit the initial baseline.
4. Create PH-00 branches only after the baseline commit exists.
5. Run PH-00 in this order: UI Design → human review/merge → Development → human review/merge → Independent QA → human acceptance.

## Phase workflow

Each phase has three prompts: UI Design, Development + Unit/Integration Testing, and Independent E2E/QA. For PH-00 specifically, there is no application to run: UI produces product/UX specifications, Development produces product and technical specification documents only, and QA independently audits those documents and creates the future executable test catalogue. No production code, database migrations, API implementation or browser E2E execution belongs in PH-00.

For implementation phases after PH-00, the E2E agent tests the running application against approved requirements. A phase is not accepted merely because a coding agent says it is complete. The phase owner records acceptance after reviewing QA results and all blocking defects.

## Branch workflow

Use the phase-specific branches: `ph00/ui-design`, `ph00/development`, and `ph00/qa`. Create each branch from the latest approved `main`, sequentially. Each agent commits only to its own branch and opens a Pull Request. Merge approved work into `main` before creating the next branch so the next agent receives the prior accepted deliverables. Protect `main` from direct pushes. Human approval is required for every merge.

At phase completion, record acceptance in `docs/phases/PH-XX/acceptance-record.md` and create a Git tag such as `ph00-approved`. Future phases branch from the latest accepted `main`.

## Naming and scope

The official project name is **NetaMonitor**. Do not reintroduce the previous working title. The product is non-partisan. No paid ranking, vote weighting or political advertising is allowed in the MVP.
"# netaMonitor" 
