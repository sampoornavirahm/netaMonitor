# DEC-001 — Approved PH-00 UI Experience Baseline

**Date recorded:** 8 November 2026
**Status:** ACCEPTED
**Decision owner:** Human project owner
**Source:** Owner authorization supplied for Agent 2 on 8 November 2026; UI design source: `docs/phases/PH-00/ui-design-handoff.md`
**Review:** Revisit only through a superseding decision; Q01/Q03/Q10/Q11 remain open separately.
**Next review:** Only if a material UX, policy or legal change is proposed.

## Context

The PH-00 UI Design handoff proposed D01–D10. The product owner explicitly approved these decisions and clarified the receipt safety condition and official project name. This record formalizes that approval without treating unrelated UX questions, legal issues, architecture proposals or numerical planning defaults as accepted.

Options considered: (1) accept D01–D10 as proposed, with the owner's D05 condition; (2) defer all proposed UX decisions; (3) accept only a subset. The owner selected option 1.

## Decisions

| ID | Accepted decision |
|---|---|
| D01 | Evidence-based assessment and citizen assessment remain separate; evidence-based assessment is presented first. |
| D02 | Location selection is optional and is clearly distinct from verified constituency status. |
| D03 | Public browsing does not require login. |
| D04 | Explain why an action or information is unavailable and, where safe, the next step. |
| D05 | An evaluation receipt may show only the user's own choice, only to the signed-in user; it has no shareable receipt or link. It must not expose another person's vote or become coercive proof of someone's vote. |
| D06 | Assisted/in-person verification should have equal standing to supported digital verification. |
| D07 | A politician's reply does not replace the original record; factual disputes use the correction process. |
| D08 | Admin navigation may be hidden, but server-side authorization is mandatory. Unauthorized and nonexistent protected areas should not reveal sensitive distinctions. |
| D09 | Negative styling is reserved for adjudicated "Not fulfilled" outcomes. Missing data and not-yet-due promises are not presented as failures. |
| D10 | Offline mode is public read-only, with clear freshness labels and no queued sensitive actions. |

**Product identity:** NetaMonitor is the approved product name (Q13 resolved by owner instruction). This is recorded here for traceability and is not an additional visual-brand decision.

## Consequences

All requirements, data projections, workflows and later acceptance tests must preserve these decisions. A technical conflict is documented and returned to the owner; an agent must not weaken/reinterpret an accepted item. D05 requires privacy and anti-coercion review; a private screen receipt still cannot guarantee that a user will not photograph a screen, and the product must not claim otherwise.

User impact: public access stays open; information and restrictions must be understandable; verification preserves a non-digital route; and private evaluations are not made shareable. These decisions do not by themselves authorize data collection or determine eligibility, legal policy or aggregation thresholds.

## References

- `docs/phases/PH-00/ui-design-handoff.md` (D01–D10)
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/NON_FUNCTIONAL_REQUIREMENTS.md`
- `docs/SCORING_METHODOLOGY.md`
- `docs/PRIVACY_POLICY_REQUIREMENTS.md`
- `docs/TEST_STRATEGY.md`

## Supersession

None.
