# Deliverable 03 — Article 10 Data and Data Governance

**Target:** Days 11-18. **Length:** 4-6 pages.
**Modules:** mod-102 §2.3; mod-105 §3 (bias and
data); mod-103 §2.4 (taxonomy data risk).

## What this deliverable is

The data and data-governance documentation per
Art. 10. Annex IV requires this as part of the
technical file. Notified Body specifically
reviews data documentation for medical-device AI
because data quality drives clinical safety.

## What it should contain

Per Art. 10(2)-(5):

1. **Design choices for training, validation,
   and testing data sets.**
2. **Data origin** (sources of training data).
3. **Annotation processes** (how labels were
   produced; inter-rater reliability for
   referable/non-referable ground truth).
4. **Data preparation processes** (cleaning,
   augmentation, normalisation).
5. **Assumptions** about what the data
   represents.
6. **Examination in view of possible biases**
   that may affect rights or lead to
   discrimination.
7. **Identification of data gaps or
   shortcomings.**
8. **Measures to address bias and data gaps.**

Plus:

9. **Datasheet for the training, validation,
   and test sets** — Gebru et al. (2018)
   pattern adapted for this system.
10. **Lifecycle management** — data refresh
    cadence; provenance; chain of custody;
    representativeness-drift monitoring (per
    mod-110 Ex-01 systemic-cause discussion).

## Constraints

- The bias examination must address **at
  least four** dimensions: age (especially
  70+), ethnicity / retinal pigmentation,
  presence of cataracts, image quality (low-
  light, poor focus).
- For each bias dimension, name **specific
  data-side measures** to address.
- Data-gap identification must be
  **honest** — programs that claim no data
  gaps in a multi-site clinical study are not
  credible.
- The lifecycle section must include the
  refresh-process-review-gate from mod-110
  Ex-01 systemic-cause discipline — the
  training-data refresh process is a known
  failure surface.

## Rubric

| Criterion | Weight |
|---|---|
| All Art. 10(2)-(5) elements addressed | 30% |
| Bias examination across four dimensions | 25% |
| Datasheet addendum substantive | 15% |
| Honest data-gap identification | 15% |
| Lifecycle management with refresh review gate | 10% |
| Length discipline 4-6 pages | 5% |

## Where to find help

- mod-105 §3.5 (subgroup discovery).
- mod-110 Ex-01 reference (training-data
  refresh blind spot).
- Gebru et al. (2018) Datasheets for Datasets.
- EU AI Act Art. 10 (read directly).
