# Exercise 02 — Independent Validation Plan — Reference Solution

## 1. Solution overview

A 3-page validation plan for Sentinel Mutual's Tier-1
credit-decisioning gradient boost (Model A). Four
validation patterns: **challenger model** (MRM-led),
**subgroup validation** (joint CAIRO + MRM), **counterfactual
evaluation** (CAIRO-led), and **stress / adversarial
testing** (joint). Subgroup validation is non-negotiable
for the fair-lending posture.

---

## 2. The validation plan

> **Independent Validation Plan — Model A**
> *Sentinel Mutual Bank — Small-business credit gradient boost*
> *Authored: CAIRO + MRM Lead. Date: [date].*

### Section 1 — Validation scope and intended use

**Intended use.** Model A produces a recommended
approval / decline and pricing range for small-business
credit applications at Sentinel. The underwriter retains
decision authority. The validation evaluates whether the
model is fit for that intended use and whether the
intended-use boundary is respected in operation.

**Out of scope.** This validation does not evaluate
(a) consumer-credit applications (handled by a separate
model not covered here), (b) the underwriter's
override patterns (Model B-stream work in mod-103
measurement plan), or (c) the third-party aggregator's
data quality at-source (handled by Vendor Risk).

**Four-element coverage per SR 11-7 §IV:**

- **Conceptual soundness** — challenger model + subgroup
  validation collectively.
- **Ongoing monitoring** — references the production
  measurement plan (mod-103 ex-03 reference) rather than
  re-stating it.
- **Outcomes analysis** — challenger comparison +
  30-day-outcome verification.
- **Benchmarking** — challenger comparison + published
  fair-lending baselines for subgroup validation.

### Section 2 — The validation pattern set

#### Pattern 1 — Challenger model (MRM-led)

- **Evaluates:** Conceptual soundness + outcomes analysis;
  Performance risk category.
- **Method:** MRM constructs an alternative model
  independently using a subset of the same input
  features (excluding the third-party aggregator data
  to test sensitivity). Models score the same 90-day
  application sample. Disagreement cases at decision
  boundaries are reviewed manually.
- **Inputs:** Production model artifact + scoring
  pipeline; raw input data for the 90-day sample
  (with appropriate access controls).
- **Acceptance:** Less than 5% rate of material
  disagreement (defined as cases where challenger and
  production produce different approve/decline outcomes
  at the bank's decisioning threshold) and a
  characterizable pattern in the disagreements.
- **Limitations:** Challenger and production share
  feature engineering and labeling assumptions; truly
  novel error modes may evade detection.

#### Pattern 2 — Subgroup validation (joint CAIRO + MRM)

- **Evaluates:** Conceptual soundness; Bias and fairness
  risk category.
- **Method:** Model A is scored on a stratified sample
  that explicitly includes adequate sample sizes from
  populations identified by Fair-Lending: by industry,
  by business size, by geographic region, and by
  proxied protected-class indicators (where data
  permits). Performance metrics (precision, recall,
  PSI, demographic parity) computed per cohort.
- **Inputs:** Stratified sample; agreed cohort
  definitions (signed off by Head of Fair Lending);
  benchmark thresholds from CO Reg 10-1-1-style
  industry norms.
- **Acceptance:** No cohort shows performance
  degradation greater than 4 percentage points
  relative to overall, on any of the four named
  metrics, *AND* the disparate-impact ratio meets the
  4/5 rule on adverse-decisioning. Failures at the
  margin trigger Fair-Lending review, not automatic
  fail.
- **Limitations:** Proxied protected-class indicators
  are imperfect; subgroup sample sizes for rare
  populations may be too small to draw confident
  conclusions.

#### Pattern 3 — Counterfactual evaluation (CAIRO-led)

- **Evaluates:** Conceptual soundness + transparency;
  Transparency and explainability risk category.
- **Method:** For a sample of 200 production decisions
  (stratified by outcome), produce *counterfactual
  applications* — versions of the input with one
  feature varied at a time across its plausible range.
  Evaluate whether the model's response to feature
  changes is *interpretable per the bank's adverse-
  action notice glossary*.
- **Inputs:** Decision sample; counterfactual generation
  tool (CAIRO-team-built); adverse-action glossary
  (Compliance team).
- **Acceptance:** > 90% of counterfactual transitions
  produce a glossary-interpretable feature change
  explanation. Patterns of un-explainable transitions
  surface in MRM monitoring as findings.
- **Limitations:** Counterfactual generation may miss
  feature interactions; the 90% threshold is a starting
  point and may need calibration after the first
  validation cycle.

#### Pattern 4 — Stress / adversarial testing (joint)

- **Evaluates:** Ongoing monitoring posture; multiple
  risk categories including Privacy (data-leakage probe)
  and Security (adversarial input).
- **Method:** Construct adversarial inputs in three
  classes: (i) economically-implausible-but-syntactically-
  valid applications, (ii) inputs with the third-party
  aggregator data deliberately corrupted, (iii) inputs
  near the decision boundary in ways designed to flip
  outputs. Model A is scored; outputs evaluated for
  robustness.
- **Inputs:** Adversarial input set (~500 cases);
  baseline behaviour reference.
- **Acceptance:** No more than 2% of inputs produce
  outputs that breach the bank's published *no-decisioning-
  with-anomalous-input* policy. Anomaly-detection
  layer must catch all class (ii) inputs.
- **Limitations:** Adversarial set is not exhaustive;
  realistic threat models will evolve.

### Section 3 — Independence and access

- **Pattern 1 (Challenger):** MRM team, independent of
  the model-owner team. No shared performance review or
  OKRs.
- **Pattern 2 (Subgroup):** Joint MRM + CAIRO function;
  Head of Fair Lending defines cohorts. Model owner
  contributes data access but does not influence cohort
  definitions or threshold setting.
- **Pattern 3 (Counterfactual):** CAIRO function leads;
  uses CAIRO-team-built tooling separate from the model
  serving stack. Model owner contributes interpretation
  expertise but does not author counterfactuals.
- **Pattern 4 (Stress / adversarial):** Joint; MRM
  defines economic-implausibility tests; CAIRO defines
  data-corruption and boundary-flip tests.

**Independence test (per §3.3):** Could the validation
team be reasonably accused of bias toward the model owner
if the model fails in production? No, for any of the four
patterns — each has structural independence (different
reporting line, different tooling, different definition
authority) from the model-owner team.

### Section 4 — Re-validation triggers

- **Material change triggers:** Model architecture
  change; training-data refresh shifting input
  distribution material per defined KS-statistic
  threshold (p < 0.01 on any feature); change in
  intended use.
- **ML-specific triggers:** Third-party aggregator
  data-source change or material vendor terms change;
  more than 5% of recent decisions falling in
  characteristically-novel patterns (drift signal).
- **Periodic cadence:** Full re-validation annually;
  monitoring-period reviews quarterly.
- **Trigger on third-party model swap:** N/A for
  Model A (in-house); cited for parity with Model B
  validation plan.

---

## 3. Reasoning notes

- **Why I chose counterfactual evaluation over LIME /
  SHAP-style explainability.** SHAP is in production
  monitoring (per mod-103 ex-03 measurement plan).
  Independent validation needs a *different* angle.
  Counterfactual evaluation tests whether the model's
  behaviour matches the bank's adverse-action notice
  glossary — a different test than feature
  attribution. SHAP and counterfactual evaluation can
  agree or disagree; the disagreement is informative.
- **Why subgroup validation acceptance is "4
  percentage points or trigger Fair-Lending review",
  not a hard fail.** The lecture notes §3.1 emphasised
  that validation evaluates *fitness for purpose*. A
  4pp performance gap may or may not be fair-lending-
  problematic depending on the context. Hard-failing
  the validation forecloses the fair-lending analysis.
  Letting it trigger review preserves discipline while
  allowing context to inform the conclusion.
- **Why no "challenger-only" validation.** Sentinel's
  MRM Lead's default pattern is challenger. The CAIRO
  contribution is precisely *not* to rely on challenger
  alone — that misses the AI-specific risks. The four-
  pattern combination preserves SR 11-7's challenger
  expectation while adding what classical MRM misses.
- **What this plan deliberately under-specifies.** The
  challenger-model's specific construction
  methodology (gradient boost vs. logistic regression
  vs. random forest). MRM owns that choice and
  documents it separately. The validation plan
  specifies the *outcome* expected (independent model;
  disagreement rate threshold), not the *construction
  method*.
- **What I would change in v2.** Add explicit
  evaluation-set provenance discipline — every pattern
  depends on an evaluation set, and the set's currency
  matters per §4.4 of mod-103. The reference compressed
  this for length. A working plan would name each set's
  refresh cadence.

---

Maintained by [Girish Nair](https://github.com/garynair)
