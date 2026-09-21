# Exercise 03 — SR 11-7-Compliant Inventory Entry for an LLM

**Estimated time**: 2 hours
**Deliverable**: A model-inventory entry + a completeness
audit (≤ 2 pages combined)

---

## The scenario

You are the CAIRO at **Sentinel Mutual Bank** (same context
as Exercises 01 and 02). Model B from Exercise 01 — the
customer-service LLM chat agent — has been tiered (Tier 2
in the reference solution). The MRM Lead now needs an
SR 11-7-compliant inventory entry. The MRM model inventory
template was built for classical models and has fields
that do not naturally fit an LLM. The MRM Lead asks you
to **author the entry for Model B** and identify which
fields need extension.

## Your assignment

Produce two artifacts.

### Artifact 1 — The inventory entry

A complete model inventory entry for Model B. The MRM
template requires:

| Field | Classical-model populated form |
|---|---|
| Model ID | Sequential ID |
| Model name | Descriptive |
| Model type | Statistical / econometric / mixed |
| Model owner (role) | Named role |
| Model purpose | Business use |
| Inputs (named) | Data sources, refresh cadence |
| Outputs (named) | Specific quantitative outputs |
| Methodology summary | High-level description |
| Implementation environment | Where it runs |
| Development date | When built |
| Last validation | Date + outcome |
| Tier | Tier per MRM policy |
| Material limitations | Known model limitations |
| Performance metrics | Currently-tracked metrics |
| Material changes since last validation | Log |
| Vendor (if any) | Vendor + product |

Author the entry for Model B. Where a classical field does
not map cleanly, **use the field with adapted content**
(e.g., "Model type" → "LLM (vendor-hosted)") and **note in
Artifact 2** that the field had to be adapted.

### Artifact 2 — Completeness audit

A half-to-one-page note that addresses:

1. **Which fields required adaptation** to fit an LLM
   shape. Be specific.
2. **Which fields the classical template *misses* for an
   LLM**. Examples to consider: prompt template
   version, model-provider version-pinning policy,
   output-filter configuration, evaluation set
   provenance, deployment-time guardrails. For each
   missed field: what it is, why it matters, where to
   add it.
3. **A single recommendation** to the MRM Lead about
   how to extend the inventory template for LLM-class
   models without breaking compatibility with classical
   models.

## Constraints

- Inventory entry must be **complete** — no field left
  blank with "n/a". If a field genuinely does not apply,
  populate with "n/a — reason".
- The completeness audit must propose **at least three**
  missing fields specific to LLM inventory.
- The recommendation in Artifact 2 must be **operational**
  — not "add LLM-specific fields" but a concrete
  proposal (e.g., "add an LLM Supplement section with
  fields X, Y, Z that classical models leave blank").
- Combined length: 2 pages.

## Rubric

| Criterion | Weight |
|---|---|
| Inventory entry — every field populated honestly | 30% |
| Adaptation notes — explicit about where classical fields were stretched | 20% |
| Missing-fields list — at least three concrete additions | 25% |
| Recommendation — operational, compatible with classical models | 15% |
| Length discipline — ≤ 2 pages | 10% |

## Where to submit

`solutions/modules/mod-104-model-risk-management/exercise-03-sr-11-7-inventory-entry-for-llm/SOLUTION.md`

Reference solution available. The reference's
recommendation is the "LLM Supplement" pattern — five
LLM-specific fields appended to the classical inventory
template.

## Reading before you start

- Lecture notes §1.3 (what counts as a model) and §4
  (lifecycle — implementation review for LLMs).
- mod-103 §3.1 (inventory attributes).
