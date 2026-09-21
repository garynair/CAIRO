# Exercise 02 — Author an Impact-Assessment Template

**Estimated time**: 4 hours
**Deliverable**: A working impact-assessment template + a
worked example using the template

---

## The scenario

You are the CAIRO at **Northfield Mutual** (continuity from
mod-101 Exercise 02). The first-90-day deliverables include
*the AI policy hierarchy and four standards*. One of those
standards — the Development Standard — requires that every
AI deployment go through a documented impact assessment.

You need to author the **impact-assessment template** the
standard will require. The template will be used by:

- Model owners in the first line (who fill it out).
- The AI Review Board (who approve deployments based on
  it).
- Internal Audit (who sample-test that it was filled out
  consistently).
- Eventually regulators (who will read it during
  examinations).

## Your assignment

Produce two artifacts.

### Artifact 1 — The template

A working impact-assessment template based on Chapter 4
(the seven-section template) — but adapted, with named
fields, with constraints, and with prose guidance for each
field.

The template should include, for each section:

- Section title and purpose (one sentence).
- The specific fields to fill in (named).
- For each field, a one-sentence prompt to the author.
- A constraint or two ("at least 2 failure modes per risk
  category", "be specific not generic", etc.).
- An example excerpt of what *good* fills look like for
  one or two fields.

Total length cap on the template: 4 pages (template
prose). A template longer than 4 pages will not get
filled out faithfully.

### Artifact 2 — The worked example

Use the template to assess one of Northfield's existing
systems: **the LLM-based customer-service chat agent**
(currently in pilot — same context as mod-101 Exercise 02).
The worked example is the template, filled in.

The worked example should be:

- **Honest** — flag real gaps in the chat agent, not just
  positive findings.
- **Specific** — use the specificity discipline from
  Chapter 4 ("the model under-rates X" not "the model
  could be biased").
- **A demonstration of the template** — every section
  filled in, in the form the template prescribes.

## Constraints

- Template length cap: 4 pages.
- Worked-example length cap: 4 pages.
- Both artifacts must use the AI risk taxonomy from
  Exercise 01 (or, if you have not done Exercise 01, the
  starting nine-category taxonomy from Chapter 2).
- The template must include guidance to **not** propose
  controls in the impact assessment (per Chapter 3
  §*What MAP is not* and Chapter 4 §*What the template
  must not do* — MAP names risks; MANAGE names
  controls).
- The worked example must include **at least one residual
  risk that cannot be fully mitigated by an existing
  control**. Real impact assessments have these; templates
  that produce only-mitigable risks are decorative.

## Rubric

| Criterion | Weight |
|---|---|
| Template — all seven sections covered (per Chapter 4) | 20% |
| Template — fields named and prompted, not just titled | 15% |
| Template — constraints discourage vague entries | 15% |
| Template — explicitly does not blur into MANAGE | 10% |
| Worked example — specific failure modes per risk category | 20% |
| Worked example — honest gaps named | 10% |
| Worked example — at least one un-fully-mitigable risk surfaced | 10% |

## Where to submit

`solutions/modules/mod-103-ai-risk-frameworks/exercise-02-impact-assessment-template/SOLUTION.md`

Reference solution includes both the template and a worked
example for Northfield's chat agent.

## Reading before you start

- Chapter 3 (MAP in Practice), especially the *What MAP
  is not* section — the template must resist the
  MAP-collapses-into-MANAGE mistake.
- Chapter 4 (The Impact Assessment Template) end to end.
- Chapter 2 (the starting nine-category taxonomy) — if
  you have not done Exercise 01.
- EU AI Act Article 27 (fundamental-rights impact
  assessment) — comparison for the fundamental-rights
  framing in the template.
- Microsoft Responsible AI Standard impact-assessment
  template (public) — useful as comparison material. Do
  not copy; observe pattern range.
