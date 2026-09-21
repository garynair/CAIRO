# Deliverable 03 — Model Tiering Framework

**Target:** Days 20-40. **Length:** 4-6 pages.

## What this deliverable is

A tiering framework that determines the
intensity of MRM treatment per in-scope
model. The framework determines how often a
model is validated, how deeply, what level of
ongoing monitoring it gets, what level of
review for changes. The 42 in-scope models
get tiered using this framework.

## What it should contain

1. **Tier definitions.** Three or four tiers;
   each tier defined by criteria, not by
   examples.
2. **Criteria for tiering.** Drawn from
   factors like materiality of decisions
   informed by the model; reversibility of
   those decisions; customer impact;
   regulatory implications; novelty of the
   technique; vendor vs. internal
   development; oversight workflow.
3. **Tier-specific treatments.** For each
   tier: validation depth, validation
   frequency, ongoing-monitoring intensity,
   change-management requirements,
   independent challenge requirements,
   reporting cadence.
4. **Tiering decision process.** Who decides;
   how disputes are resolved (typical
   business-line vs. MRM tier disagreements
   exist).
5. **Re-tiering triggers.** When a model
   needs to be re-tiered (substantive use
   change, expansion, incident, etc.).
6. **Worked tier-assignment examples.** Six
   to eight specific Tessera models, with
   reasoning. Including: at least one
   borderline tier-1/tier-2 case; the
   Treasury cash forecasting tool; the HR
   vendor LLM.

## Constraints

- Tiering must be defensible without
  business-line negotiation per model.
  Subjective criteria are allowed but the
  reasoning must be reproducible.
- The framework should align with how
  Tessera's existing traditional-model
  tiering works, but cannot inherit
  traditional-model criteria wholesale (AI
  models have different failure modes).
- The framework will be tested against the
  proportionality principle (Deliverable 01)
  — tier-3 treatment must be light enough
  to be feasible for the bulk of low-
  criticality classifiers.

## Rubric

| Criterion | Weight |
|---|---|
| Tier definitions clear and decidable | 20% |
| Tiering criteria substantive | 20% |
| Tier-specific treatments proportional | 20% |
| Decision process named | 10% |
| Worked examples (6-8 specific) | 20% |
| Re-tiering triggers explicit | 10% |

## Where to find help

- mod-106 §3 (SR 11-7 tiering / materiality).
- mod-103 §4 (risk categorization for AI/ML).
- mod-104 Ex-03 (CAIRO/MRM joint decision
  patterns).
