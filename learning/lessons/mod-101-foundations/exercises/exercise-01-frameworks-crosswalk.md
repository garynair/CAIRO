# Exercise 01 — Frameworks Crosswalk

**Estimated time**: 3 hours
**Deliverable**: A one-page crosswalk table (Markdown or PDF) +
a short reflection (≤ 1 page)

---

## Why this exercise exists

Three frameworks dominate AI governance work in 2026: the
**NIST AI RMF**, **ISO/IEC 42001**, and the **EU AI Act**. You
will encounter all three repeatedly. The frameworks are not
contradictory, but they organize the work differently and
emphasize different things. A working CAIRO is fluent in moving
between them.

This exercise forces that fluency by making you build the
crosswalk yourself. Pre-built crosswalks exist; you should not
use one. The point is *internalizing* the structure.

## Your assignment

Produce a single-page crosswalk that maps key concepts across
the three frameworks. Use whatever rows and columns work for
you; you will be evaluated on the *defensibility of the
mapping*, not on matching any specific template.

A starting structure that works:

| Concept | NIST AI RMF | ISO/IEC 42001 | EU AI Act |
|---|---|---|---|
| Role of leadership / governance |  |  |  |
| AI system inventory / scope |  |  |  |
| Risk identification |  |  |  |
| Risk treatment |  |  |  |
| Continuous monitoring |  |  |  |
| Documentation requirements |  |  |  |
| Incident reporting |  |  |  |
| External assurance / audit |  |  |  |

For each cell:

- Give the **specific** locator: NIST AI RMF sub-function
  (e.g. `GOVERN-1.1`), ISO 42001 clause (e.g. §5.1), EU AI
  Act article (e.g. Art. 9).
- Quote 5–15 words from the framework so the mapping is
  inspectable.
- Mark cells that are **partial matches** with a `~` and
  cells that **have no equivalent** with `—`.

## Reflection (≤ 1 page)

After completing the crosswalk, write a short reflection
addressing:

1. Which framework gave you the most concrete obligations? The
   most flexibility?
2. Identify one concept that is **central to one framework but
   absent or marginal in another**. Explain why you think the
   asymmetry exists.
3. If you had to choose *one* framework to anchor a governance
   program for a global SaaS company, which would you pick and
   why?

## Constraints

- Cite at least one **authoritative** source per row. NIST AI
  100-1 (the framework body), the NIST AI RMF Playbook, ISO
  42001:2023, and the EU AI Act final text are the
  authoritative sources here.
- Do **not** substitute a vendor's mapping for the
  authoritative sources. If a vendor's mapping disagrees with
  the framework text, the framework text wins.
- If you cannot find an authoritative source for a claim, mark
  the row `<!-- needs-research: explain -->` rather than
  inventing one.

## Rubric

| Criterion | Weight |
|---|---|
| Specificity — locators (sub-function / clause / article) for every populated cell | 25% |
| Faithful quoting — short quotes that an evaluator can verify against the source text | 25% |
| Honest gaps — partial matches and absences explicitly marked | 20% |
| Reflection — answers all three reflection questions with a defensible position, not a hedge | 20% |
| Source policy — all authoritative claims are sourced authoritatively | 10% |

## Where to submit

In a real program, this would go to the AI risk function for
review. For self-study, compare against the reference solution
at:

`solutions/modules/mod-101-foundations/exercise-01-frameworks-crosswalk/SOLUTION.md`

The reference solution is one *defensible* crosswalk, not the
only correct one. If your mapping differs from the reference,
the question is whether you can defend it from the source text.
