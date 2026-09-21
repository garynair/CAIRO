# Exercise 04 — Build an AI Incident Classification Taxonomy

**Estimated time**: 3 hours
**Deliverable**: A classification taxonomy + routing
rules + worked examples (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Northfield Mutual** (the
context from mod-101 / mod-103 / mod-105).
Northfield has experienced rapid growth in AI
deployment over the last 18 months and has had **3
AI-related incidents** in the trailing 6 months:

1. The claims-triage system flagged elderly insureds
   for fraud review at materially elevated rates
   for two weeks before being detected.
2. The customer-service chat agent disclosed account
   information from another customer's session due
   to a context-handling bug in the orchestrator.
3. The fraud-detection model was found to have
   been trained partly on a corrupted dataset; the
   model had been producing inappropriate
   false-positive patterns for three weeks before
   detection.

None of these had a clean classification path; the
CISO and CAIRO function had to negotiate ownership
for each case in real time. The Board Risk
Committee has asked you to **build a classification
taxonomy** that will determine routing without
real-time negotiation.

## Your assignment

Produce three artifacts.

### Artifact 1 — The taxonomy (≤ 1 page)

The classification categories Northfield will use.
At minimum:

1. **Security incident** — definition + Northfield-
   specific examples.
2. **AI-program incident** — definition + Northfield-
   specific examples.
3. **Joint incident** — definition + Northfield-
   specific examples.

Northfield may want **sub-categories** within each
top-level (e.g., AI-program incident → bias /
transparency / capability / etc.). Include the sub-
categories Northfield needs.

For each category, name:

- The defining characteristics.
- Two or three concrete Northfield-context examples.
- The default lead function.
- The default escalation path.

### Artifact 2 — Routing rules (≤ 1 page)

For each category, the **routing decision tree**:

- Who detects the incident.
- Who classifies it (initial classification + who
  can re-classify if facts change).
- Lead function and stream lead.
- Notification recipients within Northfield.
- External notification obligations checklist
  (regulator + framework reference).
- AI Risk Council escalation threshold (which
  incidents auto-escalate vs. which require
  judgement).

### Artifact 3 — Worked examples (≤ 1 page)

Apply the taxonomy to the three Northfield incidents
above. For each:

- Classification at hour 0 (when first detected).
- Classification at hour 24 (as more facts
  emerged) — and whether the classification
  changed.
- Final classification.
- Lead function and the path the incident took.
- One regulatory notification obligation triggered
  (or not) and the reasoning.

## Constraints

- The taxonomy must be **operationally usable**.
  A taxonomy too abstract to determine routing is
  not a taxonomy.
- Sub-categories must be **small enough to remember**
  (mod-103 §2.1 discipline — taxonomies with too
  many sub-categories are consulted, not used).
- Routing rules must include **specific named
  roles** at Northfield, not "the appropriate
  function."
- External notification obligations must cite
  **specific** regulations (EU AI Act Art. 73,
  NYDFS Part 500 §500.17, GDPR Art. 33, sector
  rules) where they apply.
- Worked examples must include the **re-
  classification dynamic** (per §6.5) — at least
  one of the three should have its classification
  evolve between hour 0 and 24.

## Rubric

| Criterion | Weight |
|---|---|
| Taxonomy — three top-level + appropriate sub-categories | 25% |
| Definitions and examples — Northfield-specific | 15% |
| Routing rules — specific named roles, escalation thresholds | 25% |
| Worked examples — re-classification dynamic addressed | 20% |
| External notification — specific regulation citations | 10% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`solutions/modules/mod-107-ai-security/exercise-04-ai-incident-classification/SOLUTION.md`

Reference solution uses 3 top-level categories with
4 sub-categories within each. The bias incident
(claims-triage) starts as AI-program but escalates
to joint at hour 24 when the IR investigation
discovers an external-data-source manipulation
component. The data-corruption incident starts as
joint and converges to AI-program with security
notification.

## Reading before you start

- Lecture notes §6 (AI incident classification) —
  all of it.
- mod-102 §2.7 (EU AI Act Art. 73 timelines).
- mod-105 Exercise 04 reference (Northfield
  contestability process) — for the claims-triage
  context.
- mod-103 §6.5 (loop closure) — incident
  classification feeds program-level change.
