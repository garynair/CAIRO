# Module 105 — Responsible AI and Ethics

> Module 105 of the Chief AI Risk Officer track. The ethics layer
> on top of the risk, regulatory, and MRM discipline built
> in mod-101 through mod-104. *Ethics* is the part of AI
> governance most prone to soft language and box-checking.
> This module insists on operational specificity.

## What you will leave with

After working through this module you should be able to:

1. Explain why AI ethics is a distinct discipline from
   compliance and risk management — and where the
   boundaries are honest.
2. Navigate the principles landscape (OECD, IEEE 7000,
   UNESCO, Asilomar, NIST, EU HLEG) without treating them
   as interchangeable.
3. Choose bias and fairness metrics with explicit
   awareness of the mathematical impossibility results
   that constrain the choice.
4. Design explainability that is *owed to specific
   audiences*, not just produced for completeness.
5. Build contestability into a deployed system from the
   affected-party's perspective.
6. Translate values into decisions when reasonable people
   disagree — and survive the disagreement.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md),
[`mod-102`](../mod-102-regulatory-landscape/README.md),
[`mod-103`](../mod-103-ai-risk-frameworks/README.md),
[`mod-104`](../mod-104-model-risk-management/README.md).

Particularly relevant:

- mod-103 §2 (taxonomy) — bias and fairness, transparency,
  privacy as categories.
- mod-104 §3 (validation patterns) — subgroup validation,
  counterfactual evaluation.
- mod-101 §6 (failure modes) — *governance theatre* is the
  ever-present risk in ethics work.

## Module layout

```
mod-105-responsible-ai-and-ethics/
├── README.md
├── lecture-notes.md    six lecture sections (~100 minutes)
├── exercises/          five exercises (~15 hours total)
├── quiz.md             20 questions
└── resources.md        annotated reading list
```

## Lecture sections at a glance

| § | Title | Anchor |
|---|---|---|
| 1 | What AI ethics is and is not | OECD AI Principles + IEEE 7000 + NIST AI RMF preamble |
| 2 | The principles landscape | OECD, UNESCO, IEEE 7000 series, Asilomar, EU HLEG, NIST |
| 3 | Bias and fairness beyond demographic parity | FATE literature; impossibility results (Kleinberg, Chouldechova); CFPB and CO Reg 10-1-1 |
| 4 | Transparency and explainability | EU AI Act Arts 13/14; GDPR Art. 22; XAI literature |
| 5 | Contestability and recourse | EU AI Act Art. 14; sector-specific recourse frameworks |
| 6 | Operationalizing ethics | Microsoft RAI Standard (practitioner reference); §6 of mod-101 |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | Compare 3 ethics frameworks; find the operational disagreement | 3 | Analytical | Comparison table + operational-disagreement memo |
| 02 | Define bias metrics for a specific context | 3 | Applied | Metric set + trade-off reasoning + impossibility analysis |
| 03 | Design an explainability standard | 3 | Applied | Standard document covering 3 audiences |
| 04 | Build a contestability process | 3 | Applied | Process design + worked example |
| 05 | Resolve a hard ethics case | 3 | Synthesis | Decision memo with reasoning |

## A note on tone

This module's voice is deliberately direct about a topic
that often invites vagueness. *Ethics theater* (mod-101 §6
governance theatre dressed in ethics vocabulary) is the
single biggest failure mode of CAIRO ethics work. The lecture
notes name it and the exercises are structured to resist
it.

The discipline this module teaches is being able to give
*specific* answers to *hard* questions. Not always
*correct* answers — reasonable people disagree on hard
ethics questions — but specific ones. A CAIRO who can give
specific answers and defend them survives external
scrutiny; a CAIRO who only gives principled answers does
not.

## Paired solutions repo

[`solutions/modules/mod-105-responsible-ai-and-ethics`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-105-responsible-ai-and-ethics)

---

Maintained by [Girish Nair](https://github.com/garynair)
