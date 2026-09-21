# Exercise 01 — Tier Five ML Models per SR 11-7

**Estimated time**: 3 hours
**Deliverable**: A tiering table for five models + reasoning
per model (≤ 1 page total)

---

## The scenario

You are the CAIRO at **Sentinel Mutual Bank**, a $25B regional
US bank. The MRM function (under the CRO) has historically
tiered actuarial and credit-decisioning models. Sentinel's
MRM policy uses a three-tier scheme broadly aligned with
§2.2 of the lecture notes. You are now responsible for
extending the tiering to AI/ML systems.

The MRM Lead has asked you to **tier five candidate ML
models** that have surfaced from a recent inventory sweep.
For each, you will assign a tier and defend the assignment.

## The five models

### Model A — Credit-decisioning gradient boost

The bank's primary small-business credit-decisioning
model. Inputs: applicant business data, cash-flow signals
from a third-party aggregator, an internal industry-risk
index. Output: a recommended approval / decline +
recommended pricing range. Underwriter retains final
authority but follow-through has been ~80% on the
recommendation. Re-trained quarterly on a 24-month
rolling window. 1,200 decisions / month.

### Model B — Customer-service LLM agent

LLM-based chat agent on the bank's website. Handles
balance inquiries, transaction explanations, and dispute
initiation. Does not approve credit or make adverse
decisions. Identifies itself as AI. Vendor-hosted; the
vendor occasionally swaps the underlying foundation
model with 30-days advance notice. 600,000 sessions /
quarter.

### Model C — Marketing-segmentation model

ML model that segments retail customers into 14
behavioral segments to drive marketing communications.
Inputs: account activity, demographic data, past
campaign response. Output: a segment label per customer
+ a propensity-to-respond score for each campaign.
Re-trained twice per year. Outputs drive email and direct-
mail send decisions.

### Model D — Fraud-detection anomaly detector

In-house ML model that scores incoming transactions for
fraud probability. Inputs: transaction stream + customer
history + device fingerprint. Output: a fraud score that
triggers (i) automatic blocking above 0.95, (ii) manual
review between 0.75 and 0.95, (iii) passes below 0.75.
Re-trained monthly on a 90-day rolling window. ~15
million transactions / month.

### Model E — Internal-document LLM assistant

LLM-based assistant for internal employees to query
internal policy and procedure documents (HR policy,
operations manuals, compliance guidance). Cited in
employee training as authoritative. Vendor-hosted (same
vendor as Model B). Not customer-facing. ~50 employee
sessions / day.

## Your assignment

For each model, produce:

1. **Recommended tier** (Tier 1 Critical / Tier 2
   Important / Tier 3 Standard).
2. **The criteria from §2.2 you are applying** (be
   specific: which (i) / (ii) / (iii) criterion
   triggered tier).
3. **Any ML-specific tiering input you are using**
   (data freshness, inscrutability, vendor provenance —
   from §2.3).
4. **One sentence of reasoning** for the assignment.
5. **What would change the tier** — a specific change
   to the model description that would move it up or
   down a tier.

## Required structure

A table:

| Model | Tier | §2.2 criteria triggered | ML-specific input | One-line reasoning |
|---|---|---|---|---|
| A — Credit boost |  |  |  |  |
| B — LLM chat |  |  |  |  |
| C — Marketing segmentation |  |  |  |  |
| D — Fraud anomaly |  |  |  |  |
| E — Internal LLM assistant |  |  |  |  |

Followed by a "what would change the tier" section, one
line per model.

## Constraints

- **Tiers must be defensible against the MRM Lead.**
  Be ready to defend against the "this should be Tier 1
  to be safe" objection (per §2.4 anti-patterns).
- **Tiering must be consistent.** If Model A is Tier 1 on
  the basis of customer-facing decision-making, Model D
  (which also drives binding decisions) must also be
  Tier 1 unless you can name a substantive difference.
- **Vendor-hosted is not automatically Tier 1.** Vendor
  provenance is an input, not a determinant.
- Internal-only models (Model E) are **in scope** for SR
  11-7 if their outputs influence binding employment or
  operational decisions.

## Rubric

| Criterion | Weight |
|---|---|
| Tier choices — defensible | 30% |
| §2.2 criteria — specifically identified per model | 20% |
| ML-specific inputs — applied where relevant | 15% |
| Consistency across the five — like-risk like-tier | 15% |
| "What would change the tier" — surfaces a real alternative | 10% |
| Restraint — anti-patterns from §2.4 avoided | 10% |

## Where to submit

`solutions/modules/mod-104-model-risk-management/exercise-01-tier-five-ml-models/SOLUTION.md`

Reference solution available. The reference's hardest call
is Model E (internal LLM assistant) — tiering reasoning
explains the choice.

## Reading before you start

- Lecture notes §1 (what SR 11-7 actually says) and §2
  (model tiering).
- mod-102 §4 (sector-specific — financial services).
