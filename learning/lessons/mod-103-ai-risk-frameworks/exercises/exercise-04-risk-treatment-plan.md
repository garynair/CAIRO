# Exercise 04 — Draft a Risk-Treatment Plan

**Estimated time**: 3 hours
**Deliverable**: A risk-treatment plan for one specific
risk, ≤ 1 page

---

## The scenario

You are the CAIRO at **Aldwych Health** (continuity from
mod-101 Exercise 03 and mod-102 Exercise 03). The ED
triage support tool (v2 rebuild) has cleared MAP and
MEASURE design. The AI Review Board is now drafting
treatment plans for each material risk surfaced.

The risk you are treating in this exercise:

> **Demographic bias in triage suggestions**, specific
> to elderly patients (≥ 70). The v1 incident showed
> that the model systematically under-ranked elderly
> patients' acuity. The v2 rebuild has applied
> design-time mitigations (oversampling, site-specific
> calibration) but residual risk remains until 6 months
> of monitoring evidence support the mitigations.

(This is risk #1 from the mod-102 Exercise 03 reference
RMS summary.)

## Your assignment

Produce a one-page risk-treatment plan with:

1. **Risk description** — the specific failure mode
   (from the impact assessment).
2. **Risk category** — from the taxonomy.
3. **Unmitigated likelihood × severity** — rating with
   one-line justification.
4. **Controls applied** — referenced from the control
   catalog (you may invent one if not yet built;
   Chapter 6 §*The control catalog* gives the
   structure). For each control:
   - What it does.
   - Where it sits in the lifecycle (pre-deployment,
     deployment, post-deployment).
   - The leading indicator from your measurement plan
     that confirms the control is working.
5. **Residual likelihood × severity** — rating after
   controls, with one-line justification.
6. **Residual risk acceptance** — named role that has
   accepted residual; date of acceptance; basis for
   acceptance.
7. **Re-evaluation trigger** — what would force a re-
   review of this treatment plan.
8. **Exception status** — is this treatment within the
   program's standard pattern, or is it an exception?
   If exception, the basis.

## Constraints

- **One page.** Hard limit.
- Residual risk must be **named explicitly** — not "fully
  mitigated" (per Chapter 6 §*Residual risk
  discipline*).
- Residual risk must be rated **strictly lower** than
  unmitigated risk. If the residual is the same as the
  unmitigated, the controls are not working and the plan
  should not be approved.
- Residual must be accepted by a **named role at the
  appropriate level**. For a high-residual risk in a
  high-risk system, the appropriate level is the AI Risk
  Council or higher.
- Re-evaluation trigger must be **observable**. "If
  things change" is not a trigger.
- Controls must be linked to leading indicators (per
  Chapter 6 §*The treatment plan*, the six-property
  list). A control without a confirmatory indicator is
  decoration.

## Rubric

| Criterion | Weight |
|---|---|
| Risk description — specific, from impact assessment | 10% |
| Controls — named, lifecycle-classified, indicator-linked | 25% |
| Residual risk — explicitly named, rated lower than unmitigated | 25% |
| Residual acceptance — named role, appropriate level, dated, basis given | 15% |
| Re-evaluation trigger — observable, specific | 15% |
| Exception status — addressed | 5% |
| Length discipline — one page | 5% |

## Where to submit

`solutions/modules/mod-103-ai-risk-frameworks/exercise-04-risk-treatment-plan/SOLUTION.md`

Reference solution provides a working treatment plan for
this risk. The reference explicitly names *Material*
residual risk, accepted by the AI Risk Council with a
6-month review trigger, and explains why it is honest
to do so.

## Reading before you start

- Chapter 6 (MANAGE and Residual Risk) end to end,
  especially the treatment-plan example, the four
  residual-risk disciplines, and the *treat everything*
  trap.
- Chapter 8 §*Category-level tolerances* — the appetite
  line for the Bias-and-Fairness category is what makes
  *acceptable level* observable when you name the
  residual accepter.
- mod-102 Exercise 03 reference SOLUTION — for the
  Aldwych ED triage context.
