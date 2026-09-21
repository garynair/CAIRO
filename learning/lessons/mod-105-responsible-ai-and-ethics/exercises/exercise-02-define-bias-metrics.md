# Exercise 02 — Define Bias Metrics for a Specific Context

**Estimated time**: 3 hours
**Deliverable**: A bias-metric specification (≤ 2 pages)

---

## Why this exercise exists

§3 of the lecture notes named the impossibility result:
you cannot satisfy all fairness definitions simultaneously
in any context with unequal base rates. This exercise
forces an actual choice in a specific context and
requires you to own the trade-off.

## The scenario

You are the CAIRO at **Cardinal Health Network** (continuity
from mod-104 Exercise 05). The Algorithm Quality Office
is preparing the validation plan for a new in-development
system: an **adult-ICU sepsis-prediction CDSS** (Tier 1
under Cardinal's tiering scheme).

The sepsis predictor:

- Takes vital-sign trends, laboratory values, and
  medication history from the EHR.
- Outputs a 6-hour sepsis-risk score.
- Triggers a workflow: scores above 0.7 generate a
  bedside-nurse alert; scores above 0.85 generate a
  rapid-response-team page.

The Algorithm Quality Office needs the **bias-metric
specification** for this system. The Chief Medical
Officer wants the specification by next Monday and is
prepared to defend it to clinical leadership and to the
state healthcare regulator who has been watching
Cardinal's AI work.

## Your assignment

Produce a bias-metric specification with:

### Section 1 — The protected populations (≤ ½ page)

A list of the protected populations the specification
must address. At minimum:

- Race and ethnicity (per Cardinal's documented
  patient demographics).
- Sex.
- Age strata (consider whether and how to stratify).
- Language of presentation (English / non-English).

For each, name whether self-report or proxy data is
available. Be honest where it is not.

### Section 2 — The metric set (≤ ¾ page)

Choose **two to three** bias metrics that together
characterize the bias surface for this system. For each:

- Name the metric.
- Define it precisely for the sepsis-prediction context
  (what is the positive class, what is the relevant
  outcome).
- State the threshold: at what value does the metric
  trigger concern.
- State the response: what happens when the threshold
  is crossed.

### Section 3 — The trade-off analysis (≤ ½ page)

Explicitly address:

1. **The impossibility result.** Name which of the three
   irreconcilable properties (predictive parity, equal
   false-positive rate, equal false-negative rate) your
   chosen metric set *does* satisfy and which it *does
   not*. Be specific.
2. **The clinical-safety argument.** Why is the metric
   set appropriate for sepsis prediction *clinically*?
3. **The fairness argument.** Why is the metric set
   appropriate for the protected populations *ethically*?
4. **The defensibility statement.** A one-paragraph
   summary that the CMO can use verbatim with
   regulators.

### Section 4 — Subgroup discovery (≤ ¼ page)

Beyond the pre-specified protected populations, name the
subgroup-discovery method(s) the specification requires.
For each, state what it does and what its known
limitations are.

## Constraints

- The metric set must include **at least one false-
  negative-sensitive metric**, because under-detection
  of sepsis in any subgroup is a direct patient-safety
  concern.
- The trade-off analysis must explicitly state which
  impossibility-result properties are *not* satisfied.
  A metric set that claims to satisfy all of them is
  wrong.
- The defensibility statement must be **regulator-
  presentable**. If you cannot imagine the CMO reading
  it verbatim, redraft.
- The specification must address **language of
  presentation** even though it is not a classical
  protected class. The lecture notes §3.5 named
  behavioral and linguistic patterns as effective
  protected groups.

## Rubric

| Criterion | Weight |
|---|---|
| Protected populations — honest about data availability | 15% |
| Metric set — two to three specific metrics with thresholds | 20% |
| Clinical-safety argument — substantive, not generic | 15% |
| Fairness argument — substantive, not generic | 15% |
| Impossibility-result acknowledgment — specific | 20% |
| Defensibility statement — regulator-presentable | 10% |
| Subgroup discovery — addresses beyond classical protected classes | 5% |

## Where to submit

`solutions/modules/mod-105-responsible-ai-and-ethics/exercise-02-define-bias-metrics/SOLUTION.md`

Reference solution uses equalized odds (both sensitivity
and specificity matched across groups) as the central
metric for sepsis prediction, with predictive parity
intentionally not enforced. The trade-off section
explicitly names the irreconcilable properties.

## Reading before you start

- Lecture notes §3 (bias and fairness beyond
  demographic parity) — all of it, especially §3.2
  impossibility result.
- mod-104 Exercise 02 reference (validation patterns,
  subgroup validation).
- Chouldechova (2017) directly — it is short and the
  reasoning is accessible.
