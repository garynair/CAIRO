# Exercise 03 — Design an Explainability Standard

**Estimated time**: 3 hours
**Deliverable**: A program-wide explainability standard
(≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank** (continuity from
mod-101 / mod-103). The AI Review Board has approved the
small-business loan-decisioning system for production
deployment. The Compliance team has asked for an
**explainability standard** that the program will hold
to across all Tier 1 systems. Tessera's current pattern
is to invoke SHAP attributions for every model and call
it explainability. Compliance is worried this will not
satisfy the CFPB and is not in line with what mod-105
§4 calls *transparency theater*.

## Your assignment

Author the program-wide explainability standard for
Tessera. The standard must:

### Section 1 — Scope (≤ ¼ page)

Which Tessera systems are in scope, and which are out of
scope with stated reasons.

### Section 2 — Audience-specific requirements (≤ 1½ pages)

For each of **at least three** audiences from §4.1 of
the lecture notes, specify:

- The audience.
- The decisions the audience needs to make based on the
  explanation.
- The content the explanation must include for that
  audience.
- The depth (one paragraph? one page? full technical
  file?).
- The delivery format (printed letter? in-app message?
  shared drive? API response?).
- The cadence (per-decision? per-quarter? on-demand?).
- The owner role.

The three audiences must include:

1. **Affected parties** (loan applicants — including
   denied applicants).
2. **Internal validators** (MRM team, internal audit).
3. **Regulators** (OCC, CFPB, NYDFS if applicable).

You may add additional audiences if relevant (board,
senior management, deployers, etc.).

### Section 3 — The four principles for affected-party
transparency (≤ ½ page)

State the four principles the standard adopts for
affected-party transparency — the standard's specific
operationalization of §4.3 of the lecture notes:

1. Explainable in actionable terms.
2. True (not post-hoc rationalisation).
3. Comes with a path forward.
4. (Add a fourth Tessera-specific principle of your
   choice and defend it.)

For each, name the operational implementation. "True" is
not enough; the implementation must say *how the
standard ensures the explanation is true*.

### Section 4 — The mechanical-explainability boundary (≤ ½ page)

The standard's explicit position on SHAP, LIME, and
similar attribution techniques:

- Where these are appropriate.
- Where they are not sufficient on their own.
- What the standard requires *in addition* when used
  for affected-party explanations.

### Section 5 — Process transparency (≤ ¼ page)

The standard's treatment of *process* transparency
(§4.5 of the lecture notes). What process information
must be made available, to whom, in what form.

## Constraints

- **3 pages, hard limit.** A standard that exceeds 3
  pages will not be applied consistently.
- Each requirement must include the **owner role**.
  Requirements without named owners get ignored.
- The standard must explicitly address the
  *mechanical-explainability trap* (§4.4). Standards
  that allow SHAP charts alone for affected-party
  explanations are not defensible.
- The four affected-party principles must include
  operational implementations, not just restatements.

## Rubric

| Criterion | Weight |
|---|---|
| Scope — explicit and bounded | 10% |
| Audience-specific requirements — three audiences fully specified | 30% |
| Four-principle adoption with operational implementations | 20% |
| Mechanical-explainability boundary — substantive | 15% |
| Process transparency — addressed as first-class | 10% |
| Standard length discipline — ≤ 3 pages | 5% |
| Owner roles — present for every requirement | 10% |

## Where to submit

`solutions/modules/mod-105-responsible-ai-and-ethics/exercise-03-design-explainability-standard/SOLUTION.md`

Reference solution covers four audiences (affected
parties, internal validators, regulators, deployers /
underwriters). The fourth Tessera-specific principle is
*"the explanation is reproducible if challenged"* —
reasoning explains why reproducibility was elevated to
principle status.

## Reading before you start

- Lecture notes §4 (all of it).
- mod-102 §2.4 (EU AI Act Art. 11 + Annex IV — for
  regulator-grade transparency).
- CFPB Circular 2022-03 (the black-box-defense
  rejection).
- Sample published Model Cards (Hugging Face library)
  for format reference.
