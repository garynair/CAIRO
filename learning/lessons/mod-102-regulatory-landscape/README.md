# Module 102 — Regulatory Landscape

> Module 102 of the Chief AI Risk Officer track. The map of AI
> rules as they actually exist in 2026. Where the rules
> come from, how they stack, and how to operate when half
> of them disagree with each other.

## What you will leave with

After working through this module you should be able to:

1. Explain the four lineages of modern AI regulation
   (rights-based, sector-based, capability-based,
   jurisdiction-based) and name a current regulation in
   each.
2. Classify any AI system against EU AI Act Annex III and
   defend the classification.
3. Translate the four NIST AI RMF functions into a
   defensible EU AI Act Article 9 risk-management-system
   summary.
4. Map a product's obligations across at least three
   simultaneous regulatory regimes without double-counting
   and without missing anything load-bearing.
5. Read a regulator letter and reverse-engineer what the
   regulator actually wants — not what the letter literally
   asks for.
6. Build a 90-day regulatory-monitoring cadence that
   catches meaningful change without consuming the team.
7. Position OMB M-25-21 federal CAIRO designation and the
   AI Governance Board equivalence at private-sector CAIRO
   scope.

## Prerequisites

[`mod-101-foundations`](../mod-101-foundations/README.md).
The vocabulary defined there — governance, three lines,
operating models, peer boundaries — is used throughout
this module.

## Module layout

```
mod-102-regulatory-landscape/
├── README.md                                 you are here — chapter index
├── 01-four-lineages-of-ai-regulation.md      the map of AI regulation
├── 02-eu-ai-act-risk-tiers.md                risk tiers + Annex III classification
├── 03-article-9-and-nist-crosswalk.md        RMS authoring against Article 9
├── 04-sector-specific-regulation.md          SR 11-7, SaMD, NAIC, NYDFS
├── 05-us-state-patchwork.md                  CA, CO, NY, IL, UT state layer
├── 06-multi-regime-obligations-mapping.md    one product, one merged register
├── 07-reading-a-regulator-letter.md          reverse-engineering a probe
├── 08-regulatory-monitoring-cadence.md       the 90-day cadence
├── 09-omb-m-25-21-federal-caio.md             the federal CAIO shape
├── exercises/                                five exercises (~14 hours total)
├── quiz.md                                   20 questions covering the chapters
└── resources.md                              annotated reading list, framework-first
```

## Chapters at a glance

| # | Title | Learning objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [Four lineages of AI regulation](./01-four-lineages-of-ai-regulation.md) | Objective 1 — the map | OECD AI Principles, NIST AI 100-1 preamble |
| 2 | [EU AI Act: risk tiers and Annex III](./02-eu-ai-act-risk-tiers.md) | Objective 2 — classification | Reg. (EU) 2024/1689, Arts 5–6, 50, Annex III |
| 3 | [Article 9 and the NIST crosswalk](./03-article-9-and-nist-crosswalk.md) | Objective 3 — Article 9 RMS | Reg. (EU) 2024/1689, Arts 9–13, 72; NIST AI RMF Playbook |
| 4 | [Sector-specific regulation](./04-sector-specific-regulation.md) | Part of Objective 4 — sector layer | SR 11-7, SR 22-6, NYDFS Part 500, FDA SaMD, EU MDR, NAIC bulletin |
| 5 | [The US state patchwork](./05-us-state-patchwork.md) | Part of Objective 4 — state layer | CA AI Transparency Act, CO AI Act, NYC LL 144 |
| 6 | [Multi-regime obligations mapping](./06-multi-regime-obligations-mapping.md) | Objective 4 — synthesis | Practitioner synthesis grounded in the four lineages |
| 7 | [Reading a regulator letter](./07-reading-a-regulator-letter.md) | Objective 5 — regulator letters | Practitioner synthesis; SR 11-7 as the framing lens |
| 8 | [Regulatory monitoring cadence](./08-regulatory-monitoring-cadence.md) | Objective 6 — monitoring discipline | Practitioner synthesis; EU AI Act Art. 72 as motivator |
| 9 | [OMB M-25-21 federal CAIRO designation](./09-omb-m-25-21-federal-caio.md) | Objective 7 — federal shape | OMB M-25-21 |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Classify five systems against EU AI Act Annex III](./exercises/exercise-01-classify-against-eu-ai-act.md) | 3 | Applied | Classification table + reasoning per system |
| 02 | [Multi-framework obligations map](./exercises/exercise-02-multi-framework-obligations-map.md) | 3 | Applied | Single product, three regimes, one merged obligations register |
| 03 | [Draft an Article 9 RMS summary](./exercises/exercise-03-article-9-rms-summary.md) | 2 | Synthesis | One-page risk-management-system summary |
| 04 | [Reverse-engineer a regulator letter](./exercises/exercise-04-reverse-engineer-regulator-letter.md) | 3 | Analytical | What-they-actually-want memo + response plan |
| 05 | [90-day regulatory monitoring playbook](./exercises/exercise-05-regulatory-monitoring-playbook.md) | 3 | Applied | Playbook spec: sources, cadence, triggers, escalation |

## How this module fits

mod-101 owns the vocabulary and the operating model.
mod-102 owns the **map of rules** the operating model has
to navigate. The two read together. Several later modules
cite mod-102 directly:

- mod-104 (Model Risk Management) cites Chapter 4 for
  SR 11-7 and SR 22-6 context.
- mod-107 (AI Security) cites Chapters 4 and 5 for
  NYDFS Part 500 intersection.
- mod-110 (Incident Response) cites Chapter 2 for EU AI
  Act Art. 73 reporting timelines.
- Capstone 302 (EU AI Act high-risk response) is a
  direct application of Chapters 2 and 3.

## A note on currency

Regulations change. This module was written against the
AI regulatory state of 2026. The chapters name the source
documents and the article / section numbers so you can
verify against current text. If a citation in this module
disagrees with the current regulation, **the regulation
wins**. File an issue.

Chapters flag `<!-- needs-research: ... -->` where a
specific detail should be re-verified against the current
statute before being relied on for a filing or brief.

## Paired solutions repo

[`solutions/modules/mod-102-regulatory-landscape`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-102-regulatory-landscape)

Same convention as mod-101 — worked answers, not the
answer.

---

Maintained by [Girish Nair](https://github.com/garynair)
