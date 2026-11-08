# Changelog — NetaMonitor

All notable project changes are recorded here. This file tracks repository/specification changes as well as later product releases.

## [Unreleased]
### Added
- PH-00 development specification pack (documentation only): product/NFR requirements, domain and logical data model with ERD, proposed architecture, RBAC, scoring, verification, privacy, security, moderation, election-period safeguards, source-register template, traceability, future test catalogue and developer handoff.
- PH-00 owner-approved UI decisions D01–D10 and an open-question register; four proposed ADRs for architecture review.

### Notes
- The eight UI Design source deliverables were merged into `main` by PR #1. Their handoff's pending-review statement is historical; D01–D10 are now explicitly owner-approved in DEC-001.
- Specification reconciliation records the eight evaluation eligibility outcomes (including the election-period pause) and keeps UI sources in their phase folder rather than duplicating them at `docs/` root.
- PH-00 voting privacy clarification: SEC-01 is a HIGH-PRIORITY, unresolved security decision requiring physical separation or an equivalently strong, independently reviewed isolation boundary before any voting implementation. Private voter-only confirmations are distinguished from Q01-governed public results/aggregates; confirmations are non-shareable/non-exportable and cannot expose or prove another person's vote. No ADR or open/legal decision was newly approved.
- No application code, package manifests, executable tests, API endpoints, database migrations, deployment configuration or real personal/political data were added. Independent QA and human PH-00 acceptance remain outstanding.

## [0.1.0] — 2026-11-08
### Added
- Initial NetaMonitor starter pack, 27-phase register and 81 role-specific prompts.
- Repository operating instructions and branch workflow.
- PH-00 documentation-only phase brief and corrected UI, Development and independent QA prompts.
- Documentation folders for phases, ADRs and product/policy decisions.

### Notes
- No application code, production infrastructure or migrations are included in this release.
- PH-00 must be accepted before PH-01 begins.
