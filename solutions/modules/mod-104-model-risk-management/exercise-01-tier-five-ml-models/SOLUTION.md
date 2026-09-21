# Exercise 01 — Tier Five ML Models — Reference Solution

## 1. Solution overview

Two Tier 1s, two Tier 2s, one Tier 3. The hardest call is
Model E (internal LLM assistant) — the reference tiers it
**Tier 2**, against the intuitive "internal-only =
Tier 3" temptation. Reasoning in §3.

## 2. Tiering table

| Model | Tier | §2.2 criteria triggered | ML-specific input | One-line reasoning |
|---|---|---|---|---|
| A — Credit boost | **Tier 1** | (i) externally binding decision; (ii) material customer / regulatory consequence | Quarterly retrain; third-party data dependency | Direct credit decisioning with ~80% recommendation-follow-through; CFPB / Reg B exposure |
| B — LLM chat | **Tier 2** | (ii) bounded operational impact (dispute initiation); some compliance exposure | Vendor-hosted; foundation-model swap pattern; LLM inscrutability | Influences dispute initiation but does not make adverse decisions; vendor change exposure raises one tier above the equivalent in-house chat |
| C — Marketing segmentation | **Tier 3** | None of (i)-(iii) at material level | Semi-annual retrain; in-house | Drives marketing channel choice; no adverse customer impact; modest operational exposure |
| D — Fraud anomaly | **Tier 1** | (i) automatic blocking is a binding decision; (ii) material customer + regulatory (false positive = customer harm; false negative = bank loss + regulator concern) | Monthly retrain; in-house; high volume | Auto-blocking customer transactions is a binding adverse decision at scale; SR 11-7's misuse framing applies |
| E — Internal LLM assistant | **Tier 2** | (ii) bounded operational impact; *cited as authoritative in employee training* | Vendor-hosted; same vendor-swap exposure as B | Internal use, but cited as authoritative — employees making operational decisions on its outputs creates real downstream risk |

## 3. What would change the tier

- **A** moves to Tier 2 if and only if Sentinel changes the
  workflow to require the underwriter to formulate an
  independent decision before seeing the model's
  recommendation (eliminates the de-facto-decisioning
  follow-through). Unlikely to happen; political
  difficulty of removing a deployed efficiency.
- **B** moves to Tier 1 if Sentinel adds adverse-
  decisioning capability (credit pre-qualification,
  dispute auto-resolution, account restriction). Moves
  to Tier 3 only if the vendor-swap exposure is
  eliminated by contractual model-version pinning, which
  the vendor has refused.
- **C** moves to Tier 2 if marketing decisions affect
  fair-lending posture (e.g., the segmentation drives
  which products are advertised to which customer
  groups). The model description says "segments and
  campaigns" without specifying fair-lending sensitivity;
  the reference assumes none.
- **D** stays Tier 1 across plausible variations. Could
  move to Tier 1 with a specific catastrophic-risk
  designation in a four-tier scheme.
- **E** moves to Tier 3 if Sentinel removes the
  "authoritative" framing in training material and adds
  a clear disclaimer in the assistant's responses
  (employees must verify against the source documents).
  Moves to Tier 1 only if the assistant gains
  decision-making authority (which currently it does not).

## 4. Reasoning notes

- **Why Model E is Tier 2, not Tier 3.** The
  *authoritative in employee training* framing is what
  moves it. An LLM assistant that an employee is told to
  rely on for compliance, HR, or operational questions
  has downstream decision influence even though it does
  not make decisions itself. SR 11-7's misuse framing
  is the right lens — the model is being used in ways
  the designers may not have validated. A Tier 3
  posture would let the program ignore this, and most
  programs do, and most programs eventually have an
  incident on it.
- **Why Model D is Tier 1, not Tier 2.** Fraud
  models in some banks are tiered as Tier 2 on the
  reasoning that "fraud is not customer-facing in the
  way credit is." The reference rejects this: a
  false-positive automatic block *is* customer-facing
  and materially affects customer experience and trust.
  The volume (15M transactions / month) amplifies the
  risk. Tier 1 is the right posture.
- **Why I did not tier Model B as Tier 1.** Model B
  influences dispute initiation but does not make
  binding adverse decisions. The bank's existing
  dispute-handling processes are the binding-decision
  surface; Model B is upstream of those processes. A
  reasonable alternative position would Tier 1 on
  vendor-swap exposure alone. The reference takes the
  more lenient position because the bank can offset
  vendor risk through monitoring (per Exercise 02
  validation patterns) more cheaply than through full
  Tier 1 treatment.
- **Why Model C is Tier 3.** Marketing-segmentation
  models in retail banking are a frequent regulator
  concern when they touch fair-lending; the description
  here did not establish fair-lending exposure. The
  reference is explicit that this assumption could
  change the tier (see §3 "what would change").
- **The general principle.** Tier is a *function of
  use*, not of model technology. The same model used
  differently gets different tiers. The hardest part of
  tiering is being honest about how the model is
  *actually* used, not how it was designed.

---

Maintained by [Girish Nair](https://github.com/garynair)
