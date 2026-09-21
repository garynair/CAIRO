# Exercise 03 — Place the CAIRO on the Org Chart

**Estimated time**: 2 hours
**Deliverable**: A one-page org chart + a one-page defense memo

---

## The scenario

You are advising **Aldwych Health**, a 12,000-person regional
healthcare system in the UK. Aldwych operates 14 hospitals and
a growing telehealth practice. The board has decided that
Aldwych needs a Chief AI Risk Officer. They have asked you, as an
external advisor, to recommend *where the role should report*
and to defend the recommendation in a one-page memo to the
board.

The constraints:

- Aldwych is regulated by the MHRA (medical devices), the CQC
  (care quality), the ICO (data protection), and is subject to
  the EU AI Act for AI systems on its EU-resident-patient
  flows.
- Aldwych's existing executive structure:
  - CEO (chief executive)
  - Chief Medical Officer (clinical authority, signs off on
    clinical-decision-support systems)
  - CIO (operates the EHR and clinical IT)
  - CTO (newer role; owns data platform and AI/ML capability)
  - Chief Quality Officer (owns clinical safety and patient
    safety incidents)
  - General Counsel
  - Chief Risk Officer (owns enterprise risk, including
    information governance)
  - There is no CISO; the CIO covers information security.
- Aldwych has had **one publicly reported AI-related
  incident**: a triage support tool that was found to
  systematically under-rank elderly patients. The
  recommendation system was decommissioned. The Chief Medical
  Officer led the response; the board is dissatisfied with
  how long it took to identify and act on the bias.

## Your assignment

1. **Choose a reporting line for the CAIRO** from the viable
   options described in
   [Chapter 4](../04-when-to-appoint-a-cairo.md). You may
   propose a *dotted-line + solid-line* arrangement if you
   think it improves the structure.
2. **Draw the resulting org chart.** Markdown is fine
   (indented bullet structure) — the visual is less important
   than the relationships. Include the CAIRO, the CAIRO's direct
   reports (you may invent reasonable ones), and the CAIRO's
   peer executives.
3. **Write a one-page memo to the board** defending the
   reporting line. Address:
   - Why this reporting line over the alternatives.
   - How 3LOD independence is preserved.
   - Specifically how the boundary with the Chief Medical
     Officer is managed (clinical authority vs. AI risk).
   - Specifically how the boundary with the CIO is managed
     (clinical IT operations vs. AI governance).
   - What the **most likely failure mode** of your chosen
     structure is, and how you will detect it.

## Constraints

- Pick a reporting line that is **viable per
  [Chapter 4](../04-when-to-appoint-a-cairo.md)**. If you
  propose CAIRO → CTO, you must explicitly rebut the 3LOD
  concern; the bar is high.
- "Report to the CEO" is not a free lunch. Defend it as
  rigorously as any other choice (executive bandwidth,
  visibility into operations, board interface).
- The board will see this memo. Write for executives, not for
  framework specialists. Use plain language. One acronym per
  sentence, maximum.

## Rubric

| Criterion | Weight |
|---|---|
| Reporting-line choice — coherent with Chapter 4; alternatives explicitly considered | 25% |
| 3LOD independence — preserved, or trade-off explicitly defended | 25% |
| CMO boundary — handled with specific decision rights, not vague "collaboration" | 15% |
| CIO boundary — handled with specific decision rights | 10% |
| Failure-mode prediction — concrete, observable, with a detection mechanism | 15% |
| Memo quality — executive-readable, defensible, short | 10% |

## Where to submit

`solutions/modules/mod-101-foundations/exercise-03-place-the-cairo-on-the-org-chart/SOLUTION.md`

contains a reference org chart and memo. The reference picks
CAIRO → CRO with a dotted line to the Chief Medical Officer for
clinical-decision-support oversight; the memo defends that
choice. **This is not the only correct answer.** You should
score yourself on whether your defense is as rigorous as the
reference's, not on whether your structure matches.

## Reading before you start

- [Chapter 3](../03-three-lines-of-defense.md) (3LOD) and
  [Chapter 4](../04-when-to-appoint-a-cairo.md) (reporting-line
  options and viability), plus
  [Chapter 5](../05-peer-boundaries.md) for peer scope
  (especially the CMO-adjacent CAE and GC boundaries).
- The reporting-line viability list in Chapter 4 is the
  structural map.
- For the clinical-authority boundary: MHRA *Software and AI
  as a Medical Device* guidance, and the CQC's *Right
  Support, Right Care, Right Culture* digital framework. (Out
  of scope for this exercise to read; cite them only if your
  defense rests on them.)
