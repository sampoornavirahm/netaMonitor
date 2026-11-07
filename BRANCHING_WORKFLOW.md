# NetaMonitor Git Branching Workflow

## Ground rules
- `main` is the only accepted source of truth. Protect it from direct pushes.
- Every agent works in a separate branch and isolated local checkout/workspace.
- Human project owner approves every PR merge and the final phase gate.
- Create the next role branch from the latest approved `main` after the previous role's PR is merged.

## PH-00 branch names and order
1. `ph00/ui-design` — branch from `main`; UI agent adds personas, journeys, information architecture, service blueprint and low-fidelity flows. Open PR; human reviews and merges.
2. `ph00/development` — only after step 1 merges, branch from the updated `main`; Developer agent creates technical/product specifications and ADR/decision proposals. Open PR; human reviews and merges.
3. `ph00/qa` — only after step 2 merges, branch from the updated `main`; QA independently audits all artifacts and writes findings/recommendation. Open PR; human reviews and merges.
4. Human owner resolves findings, records `docs/phases/PH-00/acceptance-record.md`, and tags accepted commit `ph00-approved`.

## Future phases
Use `ph01/ui-design`, `ph01/development`, `ph01/qa`, and similarly for each phase. A phase may start only when every dependency in `phase-register.csv` is accepted. Each branch must be based on the current accepted `main`, not an earlier branch.

## Branch creation examples (Git CLI)
```bash
git switch main
git pull origin main
git switch -c ph00/ui-design
# make changes, then commit and push
git add .
git commit -m "docs(ph00): add UX and product experience specifications"
git push -u origin ph00/ui-design
```
After the PR is merged, create the next branch from the updated `main`:
```bash
git switch main
git pull origin main
git switch -c ph00/development
```
Repeat for `ph00/qa`. Do not create all three branches at the start from the same outdated commit.

## Pull Request checklist
- [ ] Correct phase/role branch and latest `main` base
- [ ] Scope limited to assigned role and phase
- [ ] Stable requirement IDs used and traced
- [ ] No secrets, real identity data or production data
- [ ] Relevant docs, handoff and changelog updated
- [ ] Tests/checks reported honestly; blocked is not passed
- [ ] No unresolved Critical/High issues hidden
- [ ] Human owner reviewed and approved
