# Exercise 03 — Design a Measurement Plan

**Estimated time**: 3 hours
**Deliverable**: A measurement plan for one system, ≤ 2 pages

---

## The scenario

You are the CAIRO at **Tessera Bank** (continuity from
mod-101 Exercise 04). The AI-assisted small-business
loan-decisioning system has cleared MAP — the impact
assessment is complete and the AI Review Board has
classified the risks. You now need to design the
**measurement plan**.

The relevant risks from the impact assessment (use the
taxonomy from Chapter 2 or Exercise 01):

1. **Performance risk** — model recommendation accuracy
   drifts as the small-business economy changes.
2. **Bias and fairness risk** — recommendation patterns
   show disparate impact across protected classes.
3. **Transparency risk** — adverse-action notices cannot
   meaningfully explain individual decisions.
4. **Privacy and data risk** — the cash-flow aggregator
   (third-party data source) exposes data beyond intended
   purpose.
5. **Operational risk** — the third-party aggregator goes
   down, model loses input.
6. **Compliance risk** — fair-lending obligations not
   continuously demonstrable.

## Your assignment

Produce a measurement plan that includes, for each of the
six risks:

1. **At least one *leading* indicator** (per Chapter 5's
   leading-vs-lagging discipline — true leading, not
   relabeled lagging).
2. **At least one *lagging* indicator** for verification.
3. **Threshold** — a specific numeric or categorical
   threshold, set *before* you have production data on it.
4. **Data source** — where the data comes from.
5. **Cadence** — how often the indicator is computed and
   reviewed.
6. **Response when threshold is crossed** — concrete,
   not "we discuss it".
7. **Owner** — named role.

## Required structure

A table per risk:

```
### Risk N — (taxonomy category)

Leading indicator
  - Metric:
  - Data source:
  - Cadence:
  - Threshold:
  - Response:
  - Owner:

Lagging indicator
  - Metric:
  - Data source:
  - Cadence:
  - Threshold:
  - Response:
  - Owner:
```

Followed by a short *plan-level* section:

- **Dashboard design** — what audience sees what, on what
  cadence.
- **Eval-set inventory** — for any leading indicator that
  depends on an eval set, name the eval set, its
  provenance, refresh cadence.
- **Cross-cutting concerns** — anything that affects
  multiple risks (e.g., the third-party aggregator's
  reliability indicator covers both privacy and
  operational risk).

## Constraints

- **2 pages.** Hard limit.
- Each leading indicator must be *substantively* leading.
  If your "leading" indicator is "number of complaints
  in last 7 days", it is lagging-relabeled and the
  exercise has not been done.
- Each threshold must be defined **without reference to
  current production values**. If your threshold is "20%
  worse than current", that is acceptable only as a
  starting threshold; the absolute value must also be
  given.
- Every threshold must have a **specific named response**
  — what gets done, by whom, on what timeline.
- The plan must explicitly **name the eval set** for any
  metric depending on one and acknowledge its
  refresh cadence.

## Rubric

| Criterion | Weight |
|---|---|
| Coverage — leading + lagging per risk | 15% |
| Leading indicators — substantively leading | 25% |
| Thresholds — defined absolutely, not just relatively | 15% |
| Responses — concrete, owned, time-bounded | 15% |
| Eval-set discipline — named, provenance, refresh cadence | 15% |
| Cross-cutting concerns — surfaced | 10% |
| Length discipline — ≤ 2 pages | 5% |

## Where to submit

`solutions/modules/mod-103-ai-risk-frameworks/exercise-03-measurement-plan/SOLUTION.md`

Reference solution provides a working measurement plan
for the Tessera scenario.

## Reading before you start

- Chapter 5 (MEASURE and Leading Indicators) end to end,
  especially the leading-vs-lagging table, the four
  metric-design principles, and the eval-set problem.
- Chapter 8 §*Where the appetite sits in the loop* — the
  thresholds you set here must be coherent with the
  appetite tolerances the CEO signs. If the appetite has
  not yet been signed for the taxonomy category, note
  the assumption you made.
- mod-101 Exercise 04 reference solution (Tessera RACI)
  — for the role-naming context.
