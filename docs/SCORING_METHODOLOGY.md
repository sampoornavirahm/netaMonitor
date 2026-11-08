# NetaMonitor Scoring and Citizen Assessment Methodology

**Phase:** PH-00 · **Version:** 0.1 · **Status:** PROPOSED; owner approval required
**Decision owner:** Human project owner · **Policy/legal review:** as applicable

## 1. Purpose and non-combination rule

Three different questions must never be collapsed into one score, common rank or opaque composite:

1. **Evidence-based Promise Performance:** what reviewed sources support about eligible commitments.
2. **Citizen assessment:** how eligible citizens evaluate an individual promise, summarized only under approved disclosure controls.
3. **Evidence/data coverage:** how complete, current and reviewable the platform's information is.

No payment, popularity, partisan identity, gamification, vote count or admin privilege changes an editorial outcome or score weight. An editor cannot type over a computed value. Formulae, inputs, exclusions and methodology version must be public and reproducible.

## 2. Evidence-based Promise Performance (proposal)

### Inclusion gate

Include a promise only when it is published, sufficiently sourced, measurable, due by the assessment cut-off, within a documented responsibility/influence scope, and has a current reviewed adjudication. Exclude from the denominator with a visible reason if not yet due, withdrawn, duplicate, unverifiable, out of scope, unattributable, disputed without resolved assessment, or not sufficiently evidenced. Do not silently drop a negative outcome.

### Proposed per-promise values and formula

For an included promise, proposed values are: `Fulfilled = 1`, `Partially fulfilled = 0.5`, `Not fulfilled = 0`. If `N` is the count of included promises and `v_i` is its reviewed value:

`Evidence Performance (%) = 100 × (sum(v_i) / N)`

If `N = 0`, show "insufficient assessable commitments", not 0%. Equal weighting is a transparent baseline proposal, not owner approval. Multi-part commitments, changed deadlines, promise splitting/merging, and partial completion criteria require documented methodology and reviewer rationale before inclusion.

### Time, attribution and change

Use an explicit as-of date, term/campaign scope, due rule and methodology version. Do not score not-yet-due promises as failures. Shared or agency-controlled outcomes require a documented attribution rule; absent evidence of the representative's role, exclude with reason rather than assign blame/credit. Corrections/adjudication changes create a new score snapshot; retain the old input/version trail and communicate material recalculation.

## 3. Citizen assessment (proposal, Q01-blocked)

The evaluation is a private civic opinion, not evidence, official election outcome or representative endorsement. Proposed response options are fulfilled, partially fulfilled, not fulfilled and unable to verify. The last option is included in a clearly labelled distribution but excluded from the fulfilment percentage denominator.

For a promise, let `F`, `P`, and `N` be active eligible counts for fulfilled, partially fulfilled and not fulfilled. Proposed illustrative percentage:

`Citizen-assessed fulfilment (%) = 100 × (F + 0.5 × P) / (F + P + N)`

No percentage is calculated if the denominator is zero. The authenticated voter may receive a private, non-shareable, non-exportable confirmation showing only their own successfully submitted choice; this is not a public result, receipt for third-party verification or coercive proof. **Public results, aggregates, counts, percentages, cohorts, windows and suppression thresholds may not be published until Q01 is decided after privacy/re-identification review.** The handbook's planning threshold of 20 is not an approved policy and is not adopted here. Q01 governs public disclosure, not the private voter-only confirmation.

Changes must replace the active choice under an explicit, audited revision policy; aggregate outputs use the active choice per eligible person/promise, not revision event counts. Do not expose per-user vote history, receipt sharing, demographic cross-tabs or small cohorts. Even with aggregation, linkage, differencing, coercion and inference risks remain; thresholding alone does not guarantee anonymity.

Any representative-level index (for example an equal-weighted mean of promise-level citizen percentages) is only an option for future owner review. No such index/ranking is approved in PH-00.

## 4. Evidence/data coverage (proposal)

Report coverage as a separate vector or explanatory panel, not as performance. Candidate dimensions: published promises with primary source; due promises with current reviewed adjudication; source-date currency; milestones with evidence; attributed responsibility; and records with open disputes/corrections. Show counts, denominators, as-of date and missingness reasons. Do not convert a coverage gap into a neutral/negative fulfilment value or hide it in a score. Metric selection and presentation need editorial/product approval.

## 5. Confidence, comparison and display

- Confidence/strength describes evidence quality and uncertainty, not a probability that a person is good/bad. A possible future ordinal evidence-quality rubric (for example source authority, corroboration, recency and attribution) is **PROPOSED only**; no numeric confidence score or automatic adjustment is defined. Define criteria, reviewer guidance and calibration before use.
- Display numerator, denominator, eligible/excluded counts with reasons, date window, responsible scope, method version, last review, source links and known limitations.
- Do not rank unlike offices, jurisdictions, incomplete term windows or materially different commitment sets as equivalent.
- Show "not enough information" or "not comparable" instead of an invented value.
- Citizen display, including sample size and window, is blocked on Q01.
- No score is a statement of legal guilt, truth beyond sources, general competence, popularity, or future voting advice.

## 6. Manipulation and governance controls

Threats include coordinated submissions/voting, duplicate or compromised accounts, brigading, selective promise publication, denominator gaming, review conflicts, source poisoning and strategic timing. Controls to evaluate: eligibility checks, anomaly monitoring with restricted access, import review, versioned inclusion/exclusion logs, independent reviewers, appeal/correction, safe rate limiting and aggregate privacy controls. Anti-abuse signals are not proof of manipulation and must not silently change a score or target a viewpoint.

Changes to formulas, weights, cohort windows, labels or suppression behavior require a versioned proposal, public rationale, impact assessment, human approval and migration/recalculation plan. No admin score override is permitted.

## 7. Open decisions

Q01 publication threshold and anti-differencing policy; promise inclusion/partial-credit rules; multi-authority attribution; evidence-confidence vocabulary; score cohort/window; minimum assessable promise count; coverage dimensions; correction/recalculation notice; and legal/election-period display restrictions are open. Owners and due phases are in [DEC-002](./decisions/DEC-002-open-product-and-policy-questions.md).
