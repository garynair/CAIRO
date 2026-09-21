# Exercise 04 — Decide What to Automate

**Estimated time**: 3 hours
**Deliverable**: Automation framework + decisions (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank**. The CTO has
proposed adopting a comprehensive compliance
platform (one of OneTrust, Vanta, IBM
watsonx.governance) to "automate AI compliance".
The platform would cost $0.8M annually. Before
endorsing, the CRO has asked you for an
**automation framework** that decides what
Tessera should automate, what it should not, and
where the platform would actually add value.

## Your assignment

Produce a framework with:

### Section 1 — Decision criteria (≤ ¾ page)

State the criteria Tessera will use to decide
whether an activity should be automated:

- **Volume.** Is the activity high-frequency
  enough that automation amortises?
- **Judgment.** Does the activity require human
  judgment per §4.2?
- **Maturity.** Is the underlying practice mature
  enough that automation amplifies the right
  thing (per §4.3)?
- **Standardisation.** Is the activity uniform
  enough to automate consistently?
- **Vendor independence.** Does the activity tie
  Tessera to a vendor in problematic ways?

For each criterion, explain how it weighs in.

### Section 2 — The decisions (≤ 1½ pages)

For at least **eight** specific compliance
activities at Tessera, apply the criteria and
decide:

- Evidence aggregation (across the program).
- Crosswalk maintenance (regulatory mappings).
- Incident classification (per mod-107 Ex-04).
- Quarterly board pack preparation.
- Vendor risk assessment for AI vendors.
- Adverse-action notice generation.
- Bias-monitoring threshold-crossing detection.
- Training completion tracking.

For each, give a clear decision (automate / don't
automate / partially automate) with the reasoning.

### Section 3 — Platform recommendation (≤ ¾ page)

Given the decisions above, address:

- **Whether** to adopt a compliance platform at
  all.
- **Which** of the three named platforms (if
  any) fits Tessera best.
- **What** to use the platform for (specifically
  — the activities decided "automate" in §2).
- **What** to keep outside the platform.
- **Cost-benefit** analysis at the $0.8M / year
  price point.

## Constraints

- The decisions in §2 must use the criteria from
  §1 consistently — for each activity, show how
  each criterion applied.
- At least **two** of the eight activities must
  be "don't automate" — reflecting §4.2.
- The platform recommendation must address the
  §4.3 trap (do not adopt a platform before
  practice maturity).
- The recommendation must address Tessera's
  multi-LOB structure (where applicable).

## Rubric

| Criterion | Weight |
|---|---|
| Decision criteria — five named, weighted | 15% |
| Activities — eight addressed with criteria-applied reasoning | 35% |
| "Don't automate" decisions — at least two | 15% |
| Platform recommendation — substantive | 20% |
| §4.3 trap addressed | 10% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`solutions/modules/mod-109-compliance-operations/exercise-04-compliance-automation-framework/SOLUTION.md`

Reference solution recommends a *partial* platform
adoption — automate evidence aggregation,
crosswalk maintenance, and quarterly report
generation; do not automate incident
classification, adverse-action notice generation,
or bias-monitoring threshold-crossing detection
(all judgment-laden). Recommends OneTrust as the
best fit but explicitly conditions on
demonstrated practice maturity.

## Reading before you start

- Lecture notes §4 (compliance automation).
- mod-107 Ex-04 (incident classification — the
  judgment that should not be automated).
- mod-105 §3.3 (bias metric specification — the
  threshold detection that requires care).
