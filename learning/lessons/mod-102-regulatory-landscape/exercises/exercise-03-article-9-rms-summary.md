# Exercise 03 — Draft an Article 9 Risk-Management-System Summary

**Estimated time**: 2 hours
**Deliverable**: A one-page RMS summary for a specific
high-risk system

---

## The scenario

You are the CAIRO at a fictional **Aldwych Health** (the same
healthcare system from mod-101 Exercise 03). Aldwych is
re-introducing an AI triage support tool — the rebuild of the
previous tool that was decommissioned after the bias incident.
The rebuild has been classified internally as **high-risk
under EU AI Act Annex III(5)(a)** (access to and enjoyment
of essential private services and public services — health
services) and is subject to EU AI Act provisions for any
EU-resident patient encounters.

The Chief Medical Officer has asked you for a **one-page
risk-management-system summary** to attach to the deployment
proposal that will go to the AI Review Board and to the
Board Quality Committee.

## Your assignment

Produce a one-page Article 9 RMS summary that addresses each
of the four Art. 9(2) elements:

1. **Identification and analysis** of known and reasonably
   foreseeable risks (Art. 9(2)(a)).
2. **Estimation and evaluation** of risks that may emerge
   from intended use and reasonably foreseeable misuse
   (Art. 9(2)(b)).
3. **Evaluation of other risks** arising from data collection
   and analysis under Art. 10 (Art. 9(2)(c)).
4. **Risk-management measures** with explicit attention to
   residual risk after measures are applied (Art. 9(2)(d)).

The summary must also briefly address:

- **Continuous-iterative nature** of the RMS (it is a process,
  not a document).
- **Communication of residual risks to deployers** — for
  Aldwych the deployers are the clinical teams in the
  individual hospitals.

## Required structure

A one-page document with the following sections:

```
### 1. System scope and classification
### 2. Article 9(2)(a) — Identification of risks
### 3. Article 9(2)(b) — Estimation and evaluation
### 4. Article 9(2)(c) — Data risks (Art. 10 cross-reference)
### 5. Article 9(2)(d) — Risk management measures + residual risk
### 6. Iterative governance + deployer communication
```

## Constraints

- **One page.** Hard limit. The Board members will not read
  a longer document at this stage.
- Each section is **two to four bullets**, not paragraphs.
- The risks in §2 (Art. 9(2)(a)) **must include the bias
  failure mode** from the previous tool's incident.
  Pretending the prior failure did not happen is the worst
  possible posture.
- Residual risk in §5 is **named explicitly**. Do not write
  "all residual risk has been mitigated" — that is
  defensible only for trivial systems.
- The deployer-communication note (§6) is concrete: what,
  specifically, will the deployer-facing operating
  instructions say?

## Rubric

| Criterion | Weight |
|---|---|
| Art. 9(2)(a) — risks identified include bias failure mode + at least four other concrete risks | 20% |
| Art. 9(2)(b) — estimation and evaluation method named, not just asserted | 15% |
| Art. 9(2)(c) — Art. 10 data risks explicitly cross-referenced | 10% |
| Art. 9(2)(d) — risk-management measures are concrete and tied to specific risks; residual risk explicitly named | 25% |
| Iterative + deployer notes — substantive, not boilerplate | 15% |
| One page — discipline maintained | 10% |
| Honesty about prior failure — present, not hidden | 5% |

## Where to submit

`solutions/modules/mod-102-regulatory-landscape/exercise-03-article-9-rms-summary/SOLUTION.md`

Reference solution available. As elsewhere, defensible
authored RMS summaries vary; score yourself on the rubric.

## Reading before you start

- [Chapter 3 — Article 9 and the NIST crosswalk](../03-article-9-and-nist-crosswalk.md).
- EU AI Act Art. 9 + Art. 10 + Art. 13 (operating
  instructions to deployers).
- mod-101 Exercise 03 reference solution (for the Aldwych
  scenario context).
