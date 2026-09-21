# Module 106 — Trust Architecture

> Module 106 of the Chief AI Risk Officer track. Trust
> architecture — the technical and operational machinery
> by which an organisation decides what an AI agent is
> permitted to do, on whose behalf, and with what
> evidence. The discipline lives at the intersection of
> identity, capability scoping, and runtime enforcement.

## What you will leave with

After working through this module you should be able to:

1. Define "trust" for AI systems in operational terms,
   not metaphorical ones.
2. Apply NIST SP 800-207 (Zero Trust Architecture) to
   agentic AI without forcing the source framework to
   carry assumptions it was not designed for.
3. Distinguish deterministic from heuristic trust
   scoring, and choose the approach that fits the
   stakes.
4. Author an agent identity and capability manifest
   (signed, verifiable, scoped) using current standards.
5. Design a trust-gate request pipeline that sits
   between AI agents and the resources they touch.
6. Make build-vs-buy-vs-partner decisions for trust
   architecture with a structured framework.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-105`](../mod-105-responsible-ai-and-ethics/README.md).

Particularly relevant:

- mod-103 §2 (taxonomy) — security risk + transparency
  risk as categories.
- mod-104 §3 (validation patterns) — how trust scoring
  validates.
- mod-105 §4 (transparency by audience) — what trust
  decisions owe to whom.
- mod-107 (AI Security) follows directly; trust
  architecture is the *positive* control surface that
  security operates within.

## Module layout

```
mod-106-trust-architecture/
├── README.md
├── lecture-notes.md    six lecture sections (~105 minutes)
├── exercises/          five exercises (~16 hours total)
├── quiz.md             20 questions
└── resources.md        annotated reading list
```

## Lecture sections at a glance

| § | Title | Anchor |
|---|---|---|
| 1 | What "trust" means for AI systems | NIST AI RMF + NIST SP 800-207 + working definitions |
| 2 | Zero-trust adapted for AI agents | NIST SP 800-207 |
| 3 | Identity and capability scoping | W3C Verifiable Credentials, JWT/JOSE, OAuth 2.1, agent passports |
| 4 | Trust scoring — deterministic vs heuristic | Trust calculus + scoring math + practitioner examples |
| 5 | Trust gates in the request path | Where they sit; what they do; what they break |
| 6 | Build, buy, or partner | Decision framework + landscape of options |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | Map trust boundaries using NIST 800-207 | 3 | Applied | Annotated boundary diagram + memo |
| 02 | Design a 4-axis trust score with explicit math | 4 | Synthesis | Scoring spec with weights, thresholds, math |
| 03 | Author an agent identity + capability manifest | 3 | Applied | Signed manifest + verifier code-sketch |
| 04 | Design a trust-gate request pipeline | 3 | Applied | Pipeline design + tradeoff analysis |
| 05 | Build-vs-buy-vs-partner decision | 3 | Synthesis | Decision matrix + recommendation memo |

## A note on practitioner references

This module is the one most often discussing specific
vendor or open-source implementations. **Source policy
applies in full**: Cloudflare AI Gateway, IBM
watsonx.governance, Anthropic agent attestation
patterns, and roll-your-own with
NIST + W3C standards are all *practitioner patterns*.
None is the canonical answer. The lecture notes draw on
several and the exercises require you to compare them
without picking one as the default.

If a passage of this module reads like it is
recommending a vendor, file an issue.

## Paired solutions repo

[`solutions/modules/mod-106-trust-architecture`](https://github.com/garynair/CAIRO/tree/main/solutions/modules/mod-106-trust-architecture)

---

Maintained by [Girish Nair](https://github.com/garynair)
