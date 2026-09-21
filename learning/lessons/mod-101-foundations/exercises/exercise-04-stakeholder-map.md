# Exercise 04 — Stakeholder Map for an AI Initiative

**Estimated time**: 2 hours
**Deliverable**: A RACI matrix + an influence/interest map

---

## The scenario

**Tessera Bank**, a 25,000-person US regional bank, is about
to launch an AI-assisted small-business loan-decisioning
system. The system uses a gradient-boosted model trained on
five years of historical underwriting decisions, augmented
with three external data sources (cash-flow signals from a
fintech aggregator, public business filings, and a
proprietary industry-risk index). The model produces a
*recommendation* — the human underwriter makes the final
decision but must record their reason if they overturn the
recommendation.

The bank's AI governance program has been operational for six
months. The program is anchored on NIST AI RMF, with an AI
Review Board (chaired by the CAIRO) that approves all
high-impact AI deployments. This is the second deployment to
come through the board; the first was a fraud-detection model
that everyone agreed was straightforward.

This deployment is **not** straightforward. It touches:

- Fair-lending obligations (ECOA, Reg B).
- Model risk management (SR 11-7).
- Third-party-data governance (the cash-flow aggregator and
  the industry-risk index are vendors).
- Consumer notice obligations.
- Internal sales-and-service incentives — underwriters who
  follow the model recommendation close more loans, faster.

## Your assignment

Produce two artifacts.

### Artifact 1 — RACI matrix

A RACI for the decision *to deploy this model to production*.
Rows are activities, columns are roles. Activities, at
minimum:

1. Model selection (the modeling approach itself).
2. Training-data curation (including the inclusion of the
   external data sources).
3. Bias / fair-lending evaluation.
4. Model validation (independent challenge).
5. Consumer-notice language.
6. Vendor due diligence (cash-flow aggregator, industry-risk
   index).
7. Operational monitoring plan.
8. Go / no-go deployment decision.
9. Incident-response plan.

For each activity, identify:

- **R** — Responsible (does the work)
- **A** — Accountable (signs off; only one A per activity)
- **C** — Consulted (substantive input required)
- **I** — Informed (kept aware)

Roles to consider (you may add others): CAIRO, CRO, CDO, CTO,
CISO, GC, Chief Compliance Officer, Head of Underwriting,
Head of Fair Lending, MRM Lead, Model Owner (ML
engineering), Vendor Risk Lead, AI Review Board, Board Risk
Committee.

### Artifact 2 — Influence/Interest Map

A simple 2×2 quadrant map with **influence** on one axis and
**interest** on the other. Place each role from the RACI on
the grid. Use the standard four labels:

- **High influence, high interest** — manage closely
- **High influence, low interest** — keep satisfied
- **Low influence, high interest** — keep informed
- **Low influence, low interest** — monitor

Add a one-paragraph note for each quadrant explaining your
placement.

## Constraints

- Every activity must have exactly **one A**.
- Independent challenge (MRM validation) is **not** the
  responsibility of the model owner — if your RACI puts them
  on the same row as R, you have broken 3LOD.
- The board risk committee is **I** for everything except the
  go / no-go decision, where it is **C** (the executive
  function is A).
- If you find yourself with more than three C's on an
  activity, you have over-consulted. Reduce.

## Rubric

| Criterion | Weight |
|---|---|
| RACI — exactly one A per activity, no R/A collisions on MRM-style validation | 25% |
| RACI — fair-lending obligations have an *accountable* owner (not just consulted) | 15% |
| RACI — vendor due diligence is fully populated; the external data sources are not orphans | 15% |
| Influence/interest map — placements are defensible; no roles missing | 15% |
| Quadrant rationales — each quadrant has a substantive note | 10% |
| Boundary discipline — the model owner is not validating their own work | 10% |
| Restraint — no row has more than three C's | 10% |

## Where to submit

`solutions/modules/mod-101-foundations/exercise-04-stakeholder-map/SOLUTION.md`

contains a reference RACI and influence/interest map for the
Tessera scenario. **The reference is not the only correct
answer.** Defensible RACIs vary by institutional culture.
Score yourself on the constraints (exactly one A, MRM
independence, etc.), not on row-by-row match.

## Reading before you start

- [Chapter 3](../03-three-lines-of-defense.md) (3LOD) and
  [Chapter 5](../05-peer-boundaries.md) (peer-role boundary
  grid).
- OCC SR 11-7 §III (Model Risk Management Framework) and §IV
  (Independent Validation). Required context for
  understanding why MRM is its own accountable function.
