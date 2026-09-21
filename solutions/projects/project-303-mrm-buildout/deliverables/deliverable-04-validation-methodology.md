# Deliverable 04 — AI/ML Validation Methodology — Reference Solution

## 1. Solution overview

Adapts SR 11-7's three-pillar validation
to AI/ML. Conceptual soundness extends to
training data, feature engineering, model
architecture choice, bias examination,
explainability where applicable. Ongoing
monitoring adds drift detection, subgroup
performance, and calibration. Outcomes
analysis includes proxy outcomes for cases
where ground truth lags. Validator
independence is preserved by maintaining a
separation between MRM (validates) and CAIRO
(authors methodology and provides
AI-specific technical expertise but does
not validate).

---

## 2. The methodology

### Pillar 1 — Conceptual soundness for AI/ML

Adapted from SR 11-7. The validator's job is
to assess whether the model is theoretically
sound for its intended use.

For AI/ML, conceptual soundness includes:

1. **Use-case appropriateness.** Is the
   chosen technique appropriate to the
   decision being informed? Linear
   regression for a non-linear problem,
   classification for a regression problem,
   or AI/ML where a simple rule would
   suffice are all soundness concerns.
2. **Training data appropriateness.** Does
   the training data represent the
   intended-use population? Are there
   selection effects? What's the time-
   period coverage? Is the data sufficient
   in volume for the chosen technique?
3. **Feature engineering.** Are the
   features used appropriate? Any features
   that are illegal under fair-lending
   (race, age in protected ways) or
   problematic by proxy?
4. **Architecture choice.** For deep
   learning: is the architecture choice
   justified vs. simpler alternatives?
5. **Bias examination.** Has the model
   been examined for differential
   performance across protected subgroups?
   What fairness conception was used?
   What were the findings? How were
   they addressed?
6. **Explainability assessment.** For
   models that influence decisions
   subject to "right to explanation"
   regulatory requirements (consumer
   credit, ECOA, EU AI Act high-risk):
   what explainability techniques are
   employed? Are explanations faithful
   to the model's actual reasoning?
7. **Documentation.** Does the model
   documentation enable independent
   challenge?

### Pillar 2 — Ongoing monitoring for AI/ML

Drift types specific to ML:

- **Data drift.** Distribution of input
  features changes over time.
- **Concept drift.** Relationship between
  features and outcomes changes.
- **Performance drift.** Model
  performance metrics degrade over time.
- **Subgroup performance drift.** Aggregate
  performance stable but subgroup
  performance changes.
- **Calibration drift.** Probability
  estimates no longer match outcome
  frequencies.

Per-tier monitoring intensity per
Deliverable 03.

### Pillar 3 — Outcomes analysis for AI/ML

For models where ground truth is available
in reasonable time: backtest comparison
of predictions to outcomes; analysis of
errors and error patterns; subgroup
outcome analysis.

For models where ground truth lags
substantially or is not observable for some
cases (e.g., credit-denial cases where the
counterfactual is not observed):

- **Proxy outcomes.** Carefully chosen
  proxies with documented assumptions.
  Validator examines proxy validity.
- **Reject inference.** Where credit-denial
  cases are not observed: reject-inference
  techniques per industry practice; the
  technique used must be documented and
  the validator examines its appropriateness.
- **Held-out evaluation.** Where backtest
  is feasible: independent test data
  not used in training or validation.

### AI-specific validation elements

Beyond the pillars:

**Training data documentation review.** Per
SR 11-7 documentation discipline. Validator
reviews training data source, sampling,
representativeness, quality metrics, and
any documented gaps.

**Bias / subgroup performance analysis.**
Per the chosen fairness conception
(equalized odds, demographic parity,
predictive parity, etc. per mod-105 §3.2).
The validator examines whether the
conception is appropriate to the use case
and whether subgroup performance has been
adequately analyzed.

**Explainability assessment.** Where
applicable: validator examines whether
explanation methods are faithful to model
reasoning. SHAP / LIME for tabular models;
attention or attribution analysis for
deep learning. The validator does NOT
require explainability when the use case
does not demand it.

**Vendor / black-box model validation.**
Where Tessera does not have full model
access:
- Document what is known about the model
  (vendor documentation, model card if
  available).
- Validation focuses on the input
  preparation, the output use, and the
  monitoring layer Tessera operates.
- Hold-out performance testing against
  Tessera-curated test data.
- Specific attention to fairness outcomes
  where applicable (the HR vendor LLM
  case).
- Document explicitly what cannot be
  validated due to vendor information
  asymmetry.

### Validation depth per tier

**Tier-1 validation.** Full validation
covering all three pillars and all
AI-specific elements. Conceptual soundness
analysis is independent; not just review
of model-developer documentation. Validator
constructs independent challenger
benchmarks where feasible. Findings rated
per existing MRM finding-severity
framework. Validation report: typically
30-60 pages.

**Tier-2 validation.** Reduced depth.
Conceptual soundness assessment may rely
more on developer documentation with
spot-check independent analysis. Subgroup
performance and drift analysis required.
Validator does not generally construct
challenger benchmarks. Validation report:
typically 10-25 pages.

**Tier-3 validation.** Light-touch.
Documentation review + ongoing-monitoring
review. Focus on whether the model is
operating within documented boundaries.
Validation report: typically 3-8 pages.

### Validator independence

Per SR 11-7. Validators are independent of:
- Model development teams.
- The business line whose decisions the
  model informs.
- The financial outcomes the model affects.

For AI/ML, additional independence concerns:
- The CAIRO does NOT validate. The CAIRO
  authors AI-specific methodology and
  provides AI-specific technical expertise
  to MRM validators but does not perform
  validations. This preserves
  independence.

### Validation reporting

Per existing MRM reporting framework:
- Report to model owner and business-line
  head.
- Findings tracked in GRC tool with
  severity, owner, remediation date.
- Risk Committee receives summary; Tier-1
  validations summary every quarter; Tier-
  2 semi-annually; Tier-3 annually.

### Re-validation cadence

Per Deliverable 03 tiering. Re-validation
also triggered by:
- Material change to the model.
- Material change to the decision being
  informed.
- Incident involving the model.
- Drift exceeding established thresholds.
- Annual review concluding that re-
  validation is warranted.

### Exam-readiness posture

This methodology is the documented approach
for OCC February examination. Choices made
with examination in mind:
- Three-pillar SR 11-7 frame preserved.
- AI-specific augmentations documented as
  explicit additions to the pillars, not
  replacements.
- Validator independence explicitly
  preserved (the CAIRO/CRO/MRM relationship
  was the natural place for exam
  scrutiny; the design pre-empts the
  question).
- Validation reports follow established
  MRM reporting framework (the OCC has
  examined these for years; familiarity
  is helpful).

### Acknowledged limits

This methodology does not fully address:

- **Vendor LLMs at the foundation-model
  layer.** Validation under deep
  information asymmetry has structural
  limits. The methodology documents the
  attempt; full validation is not
  achievable.
- **Long-tail subgroup performance.**
  Subgroups too small for adequate
  statistical power cannot be reliably
  validated. The methodology requires the
  validator to document which subgroups
  fall below the power threshold.
- **Emergent behavior in LLM-based
  systems.** Behavior under prompts the
  validator did not anticipate. The
  methodology requires the validator to
  document attempts at adversarial probing
  but cannot guarantee coverage.

---

## 3. Reasoning notes

- **Why I preserved the three-pillar frame
  rather than re-architecting.** The OCC
  knows the three-pillar frame; departing
  from it would have invited extensive
  examination dialogue about the
  alternative. Adapting it preserves the
  exam-readiness posture while addressing
  the AI specifics.
- **Why the CAIRO does not validate.**
  Independence discipline. SR 11-7 is
  serious about validator independence;
  the CAIRO authoring methodology AND
  validating would compromise it.
  Friction is worth it.
- **Why vendor / black-box validation is
  explicit about its limits.** A
  methodology that pretends to fully
  validate vendor LLMs would be examined
  honestly by the OCC and fail. The
  explicit-limits framing reads as
  discipline rather than weakness.
- **Why I named subgroup-power limits.**
  Programs that claim full subgroup
  validation when sample sizes don't
  support it produce post-launch bias
  findings. Documenting the power
  limitation is honest and survives
  scrutiny.
- **Why outcomes analysis includes proxy
  outcomes.** Credit-denial cases where
  the counterfactual is not observed are
  pervasive in banking AI/ML; ignoring
  them would leave a major class of
  models with no outcomes pillar.
- **What I would do differently.** I might
  have separated explainability into its
  own pillar rather than folding into
  conceptual soundness. For high-impact
  consumer credit, explainability is its
  own substantive question.

---

Maintained by [Girish Nair](https://github.com/garynair)
