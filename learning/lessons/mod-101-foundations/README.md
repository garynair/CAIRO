# Module 101 — AI Governance Foundations

> Module 101 of the Chief AI Risk Officer track. The first stop.
> Sets up the vocabulary, the operating model, and the role
> boundaries every subsequent module assumes you already
> have.

## What you will leave with

After working through this module you should be able to:

1. State, in two sentences, what "AI governance" is and how
   it differs from AI ethics, AI compliance, and IT
   governance.
2. Name the four NIST AI RMF functions and place each one
   on a real org chart.
3. Apply the IIA Three Lines Model to an AI organization
   without it collapsing into theater.
4. Decide whether your org needs a Chief AI Risk Officer now,
   and if so, where the role should report.
5. Position the CAIRO defensibly against nine peer roles —
   CRO, CCO, CPO, CAE, GC, CISO, CIO, CTO, CDO.
6. Pick a governance operating model (centralized,
   federated, hub-and-spoke) and defend the choice against
   the two strongest objections.
7. Author the engagement contracts the CAIRO owes upward
   (CEO / board) and downward (Head of AI Governance).

## Prerequisites

This is an entry module. The only assumed background is:

- Familiarity with at least one regulated industry
  (financial services, healthcare, public sector, or a
  sector covered by the EU AI Act).
- Comfort reading a control framework — you do not need to
  have implemented one.
- Some prior exposure to AI/ML products in production (you
  have shipped one, advised on one, or audited one).

The full track prerequisite chain is in the top-level
[`PREREQUISITES.md`](../../PREREQUISITES.md).

## Module layout

```
mod-101-foundations/
├── README.md                       you are here — chapter index
├── 01-what-ai-governance-is.md     defines the discipline
├── 02-nist-ai-rmf-functions.md     the operating-system framework
├── 03-three-lines-of-defense.md    who does what
├── 04-when-to-appoint-a-cairo.md     readiness + reporting line
├── 05-peer-boundaries.md           nine peer-role scope grid
├── 06-operating-models.md          centralized / federated / hub-spoke
├── 07-engagement-contracts.md      upward (CEO/board) + downward (HoAIG)
├── 08-failure-modes.md             the negative-space catalog
├── exercises/                      five exercises (12–14 hours total)
├── quiz.md                         20 questions covering the chapters
└── resources.md                    annotated reading list, framework-first
```

## Chapters at a glance

| # | Title | Learning objective it anchors | Anchor framework |
|---|---|---|---|
| 1 | [What AI governance is](./01-what-ai-governance-is.md) | Governance vs. ethics / compliance / IT gov / MRM / safety | OECD AI Principles, NIST AI RMF preamble |
| 2 | [NIST AI RMF as the operating system](./02-nist-ai-rmf-functions.md) | Four functions, placed on an org chart | NIST AI 100-1 + Playbook |
| 3 | [Three Lines of Defense](./03-three-lines-of-defense.md) | 3LOD applied to AI without theater | IIA Three Lines Model (2020), ISO 42001 §5 |
| 4 | [When to appoint a CAIRO](./04-when-to-appoint-a-cairo.md) | Readiness heuristic + viable reporting lines | Practitioner synthesis grounded in COSO ERM |
| 5 | [CAIRO peer boundaries](./05-peer-boundaries.md) | Position the CAIRO against nine peer roles | ISO/IEC 38507, COSO ERM AI Supplement |
| 6 | [Governance operating models](./06-operating-models.md) | Centralized / federated / hub-and-spoke + defense | ISO 42001 §5 + practitioner case studies |
| 7 | [Engagement contracts](./07-engagement-contracts.md) | Contracts up (CEO/board) and down (Head of AI Governance) | IIA 3LM + practitioner synthesis |
| 8 | [Failure modes](./08-failure-modes.md) | The negative-space catalog | Synthesis across framework literature |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Frameworks crosswalk](./exercises/exercise-01-frameworks-crosswalk.md) | 3 | Analytical | One-page crosswalk: NIST AI RMF × ISO 42001 × EU AI Act |
| 02 | [Draft a governance charter](./exercises/exercise-02-draft-a-governance-charter.md) | 3 | Applied | 2–3 page charter for a fictional insurer |
| 03 | [Place the CAIRO on an org chart](./exercises/exercise-03-place-the-cairo-on-the-org-chart.md) | 2 | Applied | Org chart + one-page reporting-line defense memo |
| 04 | [Stakeholder map](./exercises/exercise-04-stakeholder-map.md) | 2 | Analytical | RACI matrix + influence/interest map for a lending model |
| 05 | [Operating-model recommendation memo](./exercises/exercise-05-operating-model-recommendation-memo.md) | 3 | Synthesis | 3-page memo to a fictional board |

## Module ownership

This module owns the vocabulary, the org-design vocabulary,
and the "who does what" mapping for the CAIRO track. Later
modules cite this one rather than re-defining terms. If you
encounter a term in a later module and want a refresher,
the canonical definition lives in
[Chapter 1](./01-what-ai-governance-is.md).

## Paired solutions repo

[`solutions/`](https://github.com/garynair/CAIRO/tree/main/solutions)
carries the reference solutions for every exercise. Each
is a *worked answer*, not the answer — there is no single
correct governance program. Reference solutions are
written to show one defensible path and the reasoning
behind the trade-offs.

## A note on sources

Modules in this track cite **regulations and standards as
authoritative** (EU AI Act, NIST AI RMF, ISO/IEC 42001,
OECD AI Principles, IIA Three Lines Model, OCC SR 11-7,
and so on). Where a practitioner reference appears —
Anthropic's RSP, Microsoft's RAI Standard, Google's SAIF,
IBM watsonx.governance — it is one
implementation pattern, never the canonical answer. If a
passage of this module reads like it is recommending a
vendor, treat that as a defect and file an issue.

---

Maintained by [Girish Nair](https://github.com/garynair)
