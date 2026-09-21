# Module 104 — Model Risk Management

> Module 104 of the Chief AI Risk Officer track. Model Risk
> Management — the discipline financial services has been
> running for over a decade — applied to AI / ML. SR 11-7 is
> not just an obligation; it is one of the few sources of
> *concrete operational standards* for how to validate,
> monitor, and govern a model. This module makes that
> discipline usable in any context.

## What you will leave with

After working through this module you should be able to:

1. Explain what SR 11-7 actually requires (vs. what people
   say it requires) and why it works.
2. Tier ML models within an SR 11-7-style MRM framework
   without forcing ML into financial-model assumptions.
3. Design an independent validation for an ML model where
   classical challenger-model approaches do not directly
   apply.
4. Author a model inventory entry — including for an LLM —
   that satisfies both SR 11-7 and the CAIRO program.
5. Resolve the recurring boundary disputes between the
   CAIRO function and an established MRM function.
6. Apply the MRM discipline outside banking — healthcare,
   insurance, public sector, industrial.

## Prerequisites

[`mod-101-foundations`](../mod-101-foundations/README.md),
[`mod-102-regulatory-landscape`](../mod-102-regulatory-landscape/README.md),
and [`mod-103-ai-risk-frameworks`](../mod-103-ai-risk-frameworks/README.md).

Particularly relevant:

- mod-102 §4 (sector-specific: SR 11-7 + SR 22-6 + NYDFS).
- mod-103 §5 (MANAGE in practice; treatment plans).
- mod-101 §4 (CAIRO peer-role boundaries, esp. MRM under CRO).

## Module layout

```
mod-104-model-risk-management/
├── README.md
├── lecture-notes.md    six lecture sections (~110 minutes)
├── exercises/          five exercises (~15 hours total)
├── quiz.md             20 questions
└── resources.md        annotated reading list
```

## Lecture sections at a glance

| § | Title | Anchor |
|---|---|---|
| 1 | What SR 11-7 actually says (and why it works) | OCC/FRB SR 11-7 — *all of it*, not the summary |
| 2 | Model tiering for ML / AI | SR 11-7 §III; sector adaptations |
| 3 | Independent validation when challenger models break | SR 11-7 §IV; SR 22-6; EBA Model Risk Mgmt GL |
| 4 | The model lifecycle with ML-specific stops | SR 11-7 §III–§VI; FDA PCCP guidance for analog |
| 5 | The CAIRO × MRM boundary | mod-101 §4 + program-level integration |
| 6 | MRM beyond banking | (synthesis) |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | Tier 5 ML models per SR 11-7 | 3 | Applied | Tier table + reasoning |
| 02 | Design an independent validation for an ML model | 4 | Synthesis | Validation plan (≤ 3 pp) |
| 03 | SR 11-7-compliant inventory entry for an LLM | 2 | Applied | Inventory row + completeness audit |
| 04 | Resolve a CAIRO-vs-MRM-lead boundary dispute | 3 | Analytical | Memo + boundary diagram |
| 05 | Apply MRM outside banking | 3 | Synthesis | MRM-equivalent program for a non-bank context |

## A note on the source material

SR 11-7 is short (about 21 pages). It is also dense; every
sentence is doing work. The lecture notes summarise it but
**you should read the actual document**. The Playbook-style
guidance most people cite is downstream of the source. When
the citation and the source disagree, the source wins.

## Paired solutions repo

[`solutions/modules/mod-104-model-risk-management`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-104-model-risk-management)

---

Maintained by [Girish Nair](https://github.com/garynair)
