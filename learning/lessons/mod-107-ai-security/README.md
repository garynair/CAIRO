# Module 107 — AI Security and Adversarial Defense

> Module 107 of the Chief AI Risk Officer track. AI security
> *from the CAIRO perspective* — not engineering depth, but
> program-level fluency. The technical defense work belongs
> to the CISO and the engineering org. The CAIRO's job is
> knowing what good looks like, where the boundary with
> the CISO function sits, and how AI-specific attacks get
> classified, escalated, and reported.

## What you will leave with

After working through this module you should be able to:

1. Distinguish AI-specific attack categories that are
   live threats in 2026 from those that remain
   theoretical, and explain why.
2. Use MITRE ATLAS, OWASP LLM Top 10, and NIST AI 100-2
   E2023 to threat-model an AI system without flattening
   them into a single checklist.
3. Apply defense-in-depth to AI systems beyond the
   classical-perimeter framing.
4. Specify red-teaming and adversarial evaluation as a
   governance practice — what gets done, how often, by
   whom, with what evidence.
5. Operate the CAIRO × CISO boundary cleanly — distinct
   from the CAIRO × MRM boundary (mod-104 §5) but with
   parallel discipline.
6. Author an AI-incident classification taxonomy that
   distinguishes security incidents, AI-program
   incidents, and the joint cases.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-106`](../mod-106-trust-architecture/README.md).

Particularly relevant:

- mod-103 §2 (risk taxonomy — security as a category).
- mod-104 §5 (CAIRO × MRM boundary — the structural
  parallel).
- mod-106 (trust architecture) — defines the positive
  control surface; this module operates on the
  adversarial perspective.

This module **pairs with** `ai-infra-security-learning`,
which carries the engineering-depth treatment of the
same surface. The CAIRO who can engage substantively with
the engineering org on AI security needs both — but the
two modules approach the topic from different angles
and need not be read in either order.

## Module layout

```
mod-107-ai-security/
├── README.md
├── lecture-notes.md    six lecture sections (~100 minutes)
├── exercises/          five exercises (~16 hours total)
├── quiz.md             20 questions
└── resources.md        annotated reading list
```

## Lecture sections at a glance

| § | Title | Anchor |
|---|---|---|
| 1 | The AI threat landscape — real vs hype | Incident base + sector intelligence |
| 2 | Attack taxonomies | MITRE ATLAS, OWASP LLM Top 10, NIST AI 100-2 E2023 |
| 3 | Defense-in-depth for AI systems | NIST SP 800-39 + AI-specific layering |
| 4 | Red-teaming as governance practice | EU AI Act GPAI testing + practitioner patterns |
| 5 | The CAIRO × CISO boundary | mod-104 §5 mirror + AI-security boundary specifics |
| 6 | AI incident classification | EU AI Act Art. 73 + sector incident regimes |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | Threat-model an AI system using MITRE ATLAS | 3 | Applied | ATLAS-aligned threat model |
| 02 | Design a red-team exercise | 4 | Synthesis | Exercise design + scoring rubric |
| 03 | Resolve a CAIRO-vs-CISO boundary dispute | 3 | Analytical | Boundary memo + diagram |
| 04 | Build an AI incident classification taxonomy | 3 | Applied | Taxonomy + routing rules |
| 05 | Author a defense-in-depth program standard | 3 | Applied | Standard document |

## A note on tone

AI security is one of the topics where the CAIRO most
often gets pulled into engineering detail beyond
program-level relevance. The module's voice is
deliberately disciplined about staying at the program
level. Engineering-depth questions go to the security
engineering org and to `ai-infra-security-learning`.
The CAIRO's job is the program structure that the
engineering work delivers against.

## Paired solutions repo

[`solutions/modules/mod-107-ai-security`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-107-ai-security)

---

Maintained by [Girish Nair](https://github.com/garynair)
