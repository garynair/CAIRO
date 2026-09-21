# Module 108 — Audit Ledgers and Evidence

> Module 108 of the Chief AI Risk Officer track. Tamper-
> evident logging, evidence packages, and signed
> exports — the infrastructure that lets the AI
> program *prove what happened*. Most CAIRO programs
> can describe their controls; programs that survive
> external scrutiny can also produce the evidence
> that the controls operated.

## What you will leave with

After working through this module you should be able to:

1. Distinguish operational logging from audit-grade
   evidence and explain why most production logging
   does not meet the latter standard.
2. Apply the Merkle-tree / hash-chain pattern to AI
   audit ledgers without forcing the cryptographic
   structure to carry organisational expectations it
   was not designed for.
3. Specify an event vocabulary at the right
   granularity for an AI system — comprehensive
   enough to support audit, narrow enough to remain
   maintainable.
4. Author an evidence package for a specific
   regulator or auditor request, including
   completeness, signing, and chain of custody.
5. Design retention, sealing, and chain-of-custody
   policies that survive an adversarial review.
6. Make build / buy / partner decisions for audit-
   ledger infrastructure with the same framework
   applied in mod-106 §6.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-107`](../mod-107-ai-security/README.md).

Particularly relevant:

- mod-106 (Trust Architecture) — defines the
  positive control surface; the audit ledger is
  the *evidence layer* of that surface.
- mod-107 (Security) — defines the threat surface
  the evidence layer must survive.
- mod-103 §6 (GOVERN continuously) — evidence is
  the GOVERN output that lower functions feed
  into.
- mod-102 §2 (EU AI Act) — Art. 12 (record-keeping)
  is one of the article-level obligations evidence
  must satisfy.

## Module layout

```
mod-108-audit-ledgers-and-evidence/
├── README.md
├── lecture-notes.md    six lecture sections (~100 minutes)
├── exercises/          five exercises (~16 hours total)
├── quiz.md             20 questions
└── resources.md        annotated reading list
```

## Lecture sections at a glance

| § | Title | Anchor |
|---|---|---|
| 1 | What evidence is for | EU AI Act Art. 12 + sector incident regimes + audit theory |
| 2 | The tamper-evident ledger pattern | RFC 9162 (transparency logs), Merkle trees, hash chains |
| 3 | Event vocabulary | OpenTelemetry GenAI conventions + practitioner patterns |
| 4 | Evidence packages | Auditor expectations + regulator requirements |
| 5 | Retention, sealing, chain of custody | Records management + cryptographic timestamping (RFC 3161) |
| 6 | Build, buy, or partner | mod-106 §6 framework applied here |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | Design event vocabulary for a system | 3 | Applied | Vocabulary + emission specification |
| 02 | Author an evidence package for a regulator request | 4 | Synthesis | Complete evidence package |
| 03 | Design a Merkle-chained ledger structure | 3 | Synthesis | Ledger design + verification protocol |
| 04 | Author retention and chain-of-custody policy | 3 | Applied | Policy document |
| 05 | Build / buy decision for audit ledger | 3 | Synthesis | Decision matrix + recommendation |

## A note on tone

Evidence work has a deceptive surface — it looks like
administrative work compared to the higher-profile
governance, security, or model topics. In practice the
evidence layer is where most CAIRO programs collapse
under regulator scrutiny. The discipline is taking the
infrastructure seriously even though it is the
quietest part of the program.

## Paired solutions repo

[`solutions/modules/mod-108-audit-ledgers-and-evidence`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-108-audit-ledgers-and-evidence)

---

Maintained by [Girish Nair](https://github.com/garynair)
