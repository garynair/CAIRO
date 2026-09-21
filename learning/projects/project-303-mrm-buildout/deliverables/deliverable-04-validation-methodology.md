# Deliverable 04 — AI/ML Validation Methodology

**Target:** Days 25-55. **Length:** 6-8 pages.

## What this deliverable is

The methodology that MRM validators will use
to assess AI/ML models. Adapts SR 11-7's
three-pillar validation (conceptual soundness,
ongoing monitoring, outcomes analysis) to AI/ML
specifics. Goes to MRM team for execution; to
Risk Committee for governance; to OCC
February examination as the documented
approach.

## What it should contain

1. **The three SR 11-7 pillars adapted.**
   - **Conceptual soundness for AI/ML.** What
     it means; what evidence validators look
     for; how it differs from traditional
     model validation.
   - **Ongoing monitoring for AI/ML.** Drift
     types specific to ML (data drift,
     concept drift, distribution shift,
     performance drift); subgroup
     performance monitoring; calibration.
   - **Outcomes analysis for AI/ML.** When
     decision-outcomes lag the model
     (typical in many AI/ML applications);
     proxy outcomes; backtest discipline.
2. **AI-specific validation elements.** Items
   that don't fit traditional MRM:
   - Training data documentation review.
   - Bias / subgroup performance.
   - Explainability assessment where
     appropriate to use case.
   - For vendor / black-box models:
     validation under information
     asymmetry.
3. **Validation depth per tier.** What a
   tier-1 validation looks like vs. tier-2
   vs. tier-3.
4. **Validator independence.** Per SR 11-7.
   Specific application to AI/ML:
   independence from model development AND
   from the business-line incentives.
5. **Validation reporting.** Format and
   distribution of validation reports.
6. **Periodic re-validation.** Cadence and
   triggers. Re-training as a trigger.
7. **The exam-readiness posture.** This
   methodology will be examined; design
   choices reflect that.

## Constraints

- Methodology must produce defensible
  validations within reasonable bandwidth
  (MRM has 4 validators today; cannot scale
  arbitrarily).
- Methodology must accommodate vendor
  models where Tessera does not have full
  access to the underlying model.
- Methodology must be honest about its
  limits — what AI/ML risks it does NOT
  fully address.

## Rubric

| Criterion | Weight |
|---|---|
| Three pillars adapted to AI/ML | 25% |
| AI-specific elements substantive | 20% |
| Tier-proportional depth | 15% |
| Vendor / black-box handled | 15% |
| Independence preserved | 10% |
| Exam-ready framing | 10% |
| Limits acknowledged | 5% |

## Where to find help

- mod-106 §4 (SR 11-7 validation framework).
- mod-105 (fairness / subgroup performance —
  feeds the bias validation element).
- mod-110 §3 (incident causes inform what
  validators look for).
- mod-104 §6 (CAIRO × MRM joint development of
  AI-specific methodology).
