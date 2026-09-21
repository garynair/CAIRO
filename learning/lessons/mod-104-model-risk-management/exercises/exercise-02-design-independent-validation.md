# Exercise 02 — Design an Independent Validation for an ML Model

**Estimated time**: 4 hours
**Deliverable**: A validation plan (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Sentinel Mutual Bank** (continuity
from Exercise 01). The credit-decisioning gradient-boost
model (Model A from Exercise 01) has been tiered **Tier 1
Critical** and is due for independent validation. The MRM
Lead asks you to *contribute to the validation plan* — not
to author it (MRM owns the validation), but to define the
AI-specific validation patterns the plan must include.

Sentinel's MRM function has done independent validation
on actuarial and classical credit models for over a decade.
Their default validation pattern is **challenger model**:
build a separate model independently and analyse
disagreements. That pattern is workable for a gradient-
boost credit model but does not cover the AI-specific
risks (bias, transparency, third-party data dependency)
the CAIRO function has identified.

## Your assignment

Produce a 3-page validation plan that combines the
challenger-model approach (which MRM will execute) with
**three additional validation patterns** that address the
AI-specific risks. The plan must address:

### Section 1 — Validation scope and intended use (½ page)

A short statement that pins down what the validation is
evaluating. Includes:

- The model's intended use (specific decision being
  influenced).
- The validation's scope boundary — what is *not* being
  validated.
- The four elements of validation from SR 11-7 §IV — for
  each, a one-line statement of how this plan addresses
  it.

### Section 2 — The validation pattern set (1½ pages)

For each of **four** validation patterns (challenger
plus three additional), describe:

- **Pattern name** (from §3.2 of the lecture notes or a
  reasoned alternative).
- **What it evaluates** (which validation element +
  which risk category from the mod-103 taxonomy).
- **Method** — concrete steps a validator could execute.
- **Required inputs / artifacts** — data, code, access.
- **Acceptance criteria** — what *passing* looks like.
- **Limitations** — what the pattern cannot tell you.

At least one of the three additional patterns must
address **bias and fairness**. At least one must address
**transparency** or **third-party data dependency**. The
fourth is your choice.

### Section 3 — Independence and access (½ page)

How the validation team is independent of the model owner:

- Who performs each pattern (MRM, CAIRO function, external,
  joint).
- What access is needed and how it is granted.
- The "independence test" application (per §3.3): is
  the validation team independent of the model owner
  in a way that would survive an after-failure review?

### Section 4 — Re-validation triggers (½ page)

What triggers re-validation:

- Material change triggers (per §3.4).
- ML-specific triggers (training data refresh threshold,
  third-party data source change, prompt template
  changes if relevant).
- Periodic cadence.

## Constraints

- **3 pages, hard limit.**
- The challenger model must be **one** of the four
  patterns. Designing without one breaks the SR 11-7
  posture for a Tier 1 credit model.
- Subgroup validation must be **explicitly** included as
  a pattern element. CFPB and fair-lending oversight
  make this non-negotiable.
- "We will validate" without a *concrete method* is not
  a validation pattern. Each pattern needs steps a real
  validator could execute.
- Validation patterns must be **independently executable**
  by a person who does not know the model internals.

## Rubric

| Criterion | Weight |
|---|---|
| Scope statement — specific, bounded | 10% |
| Four patterns — at least one bias, at least one transparency/data | 25% |
| Pattern detail — method + inputs + acceptance + limitations per pattern | 25% |
| Independence statement — passes the §3.3 test | 15% |
| Re-validation triggers — concrete, ML-specific included | 15% |
| Length discipline — ≤ 3 pages | 10% |

## Where to submit

`solutions/modules/mod-104-model-risk-management/exercise-02-design-independent-validation/SOLUTION.md`

Reference solution available. The reference uses
challenger + subgroup + counterfactual + stress/adversarial
as the four patterns, with explicit reasoning for the
selection.

## Reading before you start

- Lecture notes §3 (independent validation).
- mod-103 §2 (AI risk taxonomy) for risk-category
  vocabulary.
- mod-102 §4 (sector — CFPB and fair-lending).
- SR 11-7 §IV directly.
