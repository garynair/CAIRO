# Exercise 05 — Operating-Model Recommendation Memo

**Estimated time**: 3 hours
**Deliverable**: A 3-page memo to a fictional board

---

## The scenario

You are advising **Kerridge Industries**, a $14 billion
diversified industrial holding company. Kerridge operates
four business units:

- **Kerridge Aerospace** — components and avionics; heavy
  use of ML for predictive maintenance on aircraft engines;
  customers are regulated airframers; subject to FAA / EASA.
- **Kerridge Healthcare** — medical-imaging devices; one
  FDA-cleared AI/ML algorithm in market; two more in
  pre-submission; subject to FDA, EU MDR + AI Act.
- **Kerridge Materials** — industrial coatings; minimal AI
  exposure; one supply-chain forecasting model.
- **Kerridge Financial** — captive insurance and a small
  fintech-adjacent leasing arm; subject to state insurance
  regulation and SR 11-7-flavored MRM expectations.

Kerridge's board has approved establishing an enterprise AI
governance function with a Chief AI Risk Officer reporting to the
Chief Risk Officer. The CAIRO has been appointed. The CAIRO's
first major decision is the **operating model**: centralized,
federated, or hub-and-spoke.

The CEO has asked the CAIRO to prepare a board memo with a
recommendation and the reasoning. The memo will be discussed
at the next risk-committee meeting in three weeks.

## Your assignment

You are the CAIRO. Write the board memo.

The memo should:

1. **Recommend one operating model** — centralized,
   federated, or hub-and-spoke. State the recommendation in
   the first sentence.
2. **Justify the recommendation** in the context of
   Kerridge's specific profile (the four business units, the
   regulatory diversity, the existing functional structures).
3. **Explicitly consider the alternatives.** For each of the
   two you did not pick, state in one paragraph why it was
   rejected for *this* organization.
4. **Address the strongest objection** to your
   recommendation. Steel-man it. Then respond.
5. **Describe the first-year roadmap.** What does the
   operating model look like in 90, 180, and 365 days? What
   is the order of operations?
6. **Identify the leading indicators** you will report to the
   board at the 12-month mark to demonstrate that the
   operating model is working (or that it needs to change).

## Constraints

- **Three pages, hard limit.** Boards do not read four-page
  memos.
- Every paragraph must do work. No throat-clearing.
- Cite at least one **authoritative** framework. ISO 42001
  §5 (Leadership) is a strong anchor.
- Practitioner references (Anthropic RSP, Microsoft RAI,
  Google SAIF) may be used as *range*, not as the answer.
  See [Chapter 6](../06-operating-models.md) for the framing.
- The memo will be read by a risk committee that includes
  the board chair (background: industrial CEO) and two
  external directors (background: one large-firm GC, one
  former audit-committee chair of a Fortune 500). Write for
  them, not for AI specialists.

## Rubric

| Criterion | Weight |
|---|---|
| Recommendation — stated up front, unambiguous, defensible | 20% |
| Context-fit — justification ties to Kerridge's specific structure | 20% |
| Alternatives — both not-chosen options addressed substantively | 15% |
| Steel-manned objection — strongest counter, fairly stated, answered | 15% |
| Roadmap — concrete artifacts at 90 / 180 / 365 days, not aspirational | 15% |
| Leading indicators — observable, defensible, not vanity metrics | 10% |
| Writing — executive-readable, three pages, no acronym soup | 5% |

## Where to submit

`solutions/modules/mod-101-foundations/exercise-05-operating-model-recommendation-memo/SOLUTION.md`

The reference solution recommends **hub-and-spoke** for
Kerridge, with the hub in the CRO's risk function and spokes
in each business unit's existing risk team. As with prior
exercises, that is *one* defensible position. Centralized is
also defensible for Kerridge (especially given the small
size of Materials and the very different regulatory regimes).
Federated is the hardest case to defend for Kerridge and is
the most instructive to argue.

If your recommendation differs from the reference, the
question is whether your memo would survive the risk-committee
meeting. Score yourself on the rubric.

## Reading before you start

- [Chapter 6](../06-operating-models.md) (operating models)
  and [Chapter 8](../08-failure-modes.md) (failure modes).
- ISO 42001 §5 (Leadership) — required reading for the
  framework anchor.
- Skim ONE of: Anthropic RSP, Microsoft RAI Standard, or
  Google SAIF. The point is range; you only need a working
  feel for one.
