# Module 103 — AI Risk Frameworks

> Module 103 of the Chief AI Risk Officer track. Takes the
> framework knowledge from mod-101 and mod-102 and makes
> it *operational*. What artifacts NIST AI RMF actually
> produces in a working program, where they live, and how
> they connect back to the enterprise risk appetite the
> CEO and board sign.

## What you will leave with

After working through this module you should be able to:

1. Construct an AI risk taxonomy that fits your
   organization's risk vocabulary and survives review by
   both Risk and Engineering.
2. Author an impact-assessment template that surfaces the
   right risks at the right depth without becoming
   compliance theatre.
3. Design a measurement plan with leading indicators that
   actually lead, not just lagging indicators relabeled.
4. Draft a risk-treatment plan in which residual risk is
   named explicitly and defended.
5. Run a single AI system end-to-end through
   MAP → MEASURE → MANAGE → GOVERN and produce the
   working set of artifacts.
6. Sign off on the enterprise AI risk appetite statement
   at CEO / board scope, coordinating with the
   head-of-ai-governance who operates the risk register.

## Prerequisites

[`mod-101-foundations`](../mod-101-foundations/README.md) and
[`mod-102-regulatory-landscape`](../mod-102-regulatory-landscape/README.md).

mod-101 vocabulary (3LOD, CAIRO scope, operating models,
peer boundaries) is used throughout. mod-102 obligations
(EU AI Act Articles 9 and 27, SR 11-7, sector regimes) and
NIST sub-function references are cited directly.

## Module layout

```
mod-103-ai-risk-frameworks/
├── README.md                                you are here — chapter index
├── 01-framework-vs-program.md               the operational gap
├── 02-ai-risk-taxonomy.md                   taxonomy as the unifying spine
├── 03-map-in-practice.md                    inventory + classification + discipline
├── 04-impact-assessment-template.md         the working artifact of MAP
├── 05-measure-and-leading-indicators.md     MEASURE + the leading-vs-lagging trap
├── 06-manage-and-residual-risk.md           MANAGE + residual-risk discipline
├── 07-govern-and-closing-the-loop.md        GOVERN + the loop closure test
├── 08-risk-appetite-statement.md            CEO/board sign-off + head-of-AI-gov coord
├── exercises/                               five exercises (~16 hours total)
├── quiz.md                                  25 questions covering the chapters
└── resources.md                             annotated reading list, framework-first
```

## Chapters at a glance

| # | Title | Learning objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [From framework to program](./01-framework-vs-program.md) | Frame for the module | NIST AI 100-1, ISO/IEC 23894, ISO/IEC 42001 |
| 2 | [AI risk taxonomy](./02-ai-risk-taxonomy.md) | Objective 1 — the taxonomy | NIST AI 100-1 §3 characteristics; ISO/IEC 23894; COSO ERM |
| 3 | [MAP in practice](./03-map-in-practice.md) | Foundations of Objective 2 and 5 | NIST MAP-1.1 / MAP-2.x / MAP-3.x / MAP-5.1; EU AI Act Art. 9(2)(a) |
| 4 | [The impact assessment template](./04-impact-assessment-template.md) | Objective 2 — the template | NIST MAP-5.1; EU AI Act Arts. 9, 27; Microsoft RAI Standard v2 IA template |
| 5 | [MEASURE and leading indicators](./05-measure-and-leading-indicators.md) | Objective 3 — measurement plan | NIST MEASURE-1.x / MEASURE-2.x / MEASURE-4.x; EU AI Act Art. 9(2)(b) |
| 6 | [MANAGE and residual risk](./06-manage-and-residual-risk.md) | Objective 4 — treatment + residual | NIST MANAGE-1.x / 2.x / 3.x; EU AI Act Arts. 9(2)(d), 9(5), 13; SR 11-7 |
| 7 | [GOVERN and closing the loop](./07-govern-and-closing-the-loop.md) | Objective 5 — end-to-end + loop | NIST GOVERN-1.x / 3.x / 5.x; ISO/IEC 42001 clauses on management review |
| 8 | [The risk appetite statement](./08-risk-appetite-statement.md) | Objective 6 — CEO/board scope | ISO 31000; COSO ERM; enterprise-risk-appetite practice |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Build an AI risk taxonomy](./exercises/exercise-01-build-an-ai-risk-taxonomy.md) | 3 | Synthesis | One-page taxonomy + reasoning note |
| 02 | [Author an impact-assessment template](./exercises/exercise-02-impact-assessment-template.md) | 4 | Applied | Working template + worked example |
| 03 | [Design a measurement plan](./exercises/exercise-03-measurement-plan.md) | 3 | Applied | Leading + lagging indicator design |
| 04 | [Draft a risk-treatment plan](./exercises/exercise-04-risk-treatment-plan.md) | 3 | Applied | Treatment plan for one named risk |
| 05 | [End-to-end loop on one system](./exercises/exercise-05-end-to-end-loop.md) | 3 | Capstone | Linked set of MAP / MEASURE / MANAGE / GOVERN artifacts |

## How this module fits

mod-101 gave you the vocabulary and the operating model.
mod-102 gave you the regulatory map. mod-103 gives you
the *daily work*. Downstream modules build on the loop
this module defines:

- **mod-104 (Model Risk Management)** deepens MANAGE for
  financial-services contexts under SR 11-7 / SR 22-6.
- **mod-105 (Responsible AI & Ethics)** layers the ethics
  dimension over the same loop.
- **mod-108 (Audit Ledgers & Evidence)** hardens the
  evidence trail behind the six-artifact chain.
- **mod-109 (Compliance Operations)** operationalises the
  artifact set against specific regulatory regimes.
- **mod-111 (Board Reporting)** develops Chapter 7's
  board report and Chapter 8's appetite statement in
  more depth.

## A note on artifacts

This module makes you produce more concrete artifacts than
any other in the track. That is deliberate. The discipline
of AI risk management lives *in the artifacts* — not in
the documents *about* the artifacts. If a chapter is
abstract, look at the corresponding exercise for the
working form.

## Paired solutions repo

[`solutions/modules/mod-103-ai-risk-frameworks`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-103-ai-risk-frameworks)

Same conventions as mod-101 and mod-102 — worked
answers, not the answer.

---

Maintained by [Girish Nair](https://github.com/garynair)
