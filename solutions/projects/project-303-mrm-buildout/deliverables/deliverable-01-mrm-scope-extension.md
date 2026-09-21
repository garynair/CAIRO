# Deliverable 01 — MRM Scope Extension Policy — Reference Solution

## 1. Solution overview

Policy amendment extending Tessera's MRM Policy
v4.2 to cover AI/ML models. Definition of
"model" is **decision-influence-based** (not
technique-based): any quantitative system that
materially informs a decision Tessera makes
falls under MRM. The CAIRO authors AI-specific
methodology; the CRO is MRM policy owner; the
business-line model owners are first-line; MRM
provides second-line independent validation;
Audit is third-line. Vendor LLMs are in-scope
when their output materially informs a
decision (resolving the HR resume-screening
ambiguity in favor of in-scope).

---

## 2. The policy update

> **TESSERA BANK MRM POLICY v4.3 —
> Amendment for AI/ML Models**
> *Effective [date]. Approved by Risk
> Committee.*

### Section 1 — Purpose of this amendment

This amendment extends MRM Policy scope to
encompass artificial intelligence and machine
learning ("AI/ML") models. The amendment
preserves the SR 11-7 frame from MRM Policy
v4.2 and applies it to AI/ML with
proportionality.

### Section 2 — Revised definition of "model"

A **model** for MRM purposes is *a quantitative
system that processes inputs to produce
outputs (predictions, classifications,
recommendations, decisions, or rankings) that
materially inform a Tessera decision*.

This definition encompasses:

- Statistical models (regression, time series,
  scorecards) — already in scope under v4.2.
- Classical machine learning (trees,
  ensembles, kernel methods, etc.).
- Deep learning models (neural networks of
  all architectures).
- Foundation models, language models, and
  fine-tuned variants thereof, whether
  internally developed or vendor-supplied.
- Hybrid systems where an AI/ML component
  materially affects the output (e.g., RPA
  with an ML decision step).
- Rule-based systems that are produced or
  refined through ML (e.g., decision rules
  learned from data).

This definition does **not** encompass:

- Pure heuristic systems (no learned
  parameters; outputs derived solely from
  human-authored rules).
- Reporting systems (descriptive only; no
  recommendations or decisions).
- Production transaction-processing systems
  whose AI/ML components are immaterial to
  the decision (e.g., autocomplete in a
  user form).

### Section 3 — "Materiality of influence" test

A system **materially informs** a Tessera
decision when:

- The output is acted upon by Tessera
  employees, customers, or downstream
  systems in a way that changes the
  outcome from what would occur without
  the system, AND
- The decision being informed is one of:
  - Customer-facing (credit, account,
    pricing, communication content).
  - Risk-relevant (capital, liquidity,
    market position, operational risk).
  - Compliance-relevant (AML, fraud,
    regulatory reporting).
  - Employee-facing in ways that produce
    legally cognisable outcomes (hiring,
    compensation, performance).
  - Vendor / counterparty selection or
    pricing.

### Section 4 — Worked in-scope examples

- The HR resume-screening vendor LLM. The
  system produces ranked candidate lists
  that Sourcing function uses to determine
  which candidates advance. The ranking
  materially influences hiring outcomes.
  **In scope**.
- Treasury "smart cash position" forecasting
  tool. The output drives real Treasury
  decisions (sweep timing, repo positioning,
  etc.). **In scope**.
- Consumer banking next-best-offer model.
  The output determines which customers
  receive which offers. **In scope**.

### Section 5 — Worked out-of-scope examples

- Marketing email campaign-timing
  optimization (optimizes send times within
  an already-authorized campaign; immaterial
  to which campaigns run or who receives
  them). **Out of scope** for MRM (marketing
  ops manages).
- Office productivity LLM use (Copilot,
  ChatGPT for general office work).
  **Out of scope** for MRM under this policy;
  separately governed under Tessera's
  Acceptable AI Use Policy.

### Section 6 — Proportionality principle

Not all in-scope models receive equal MRM
attention. Tiering (per Deliverable 03)
determines per-model treatment intensity.
Tier-3 (low-criticality) models receive
lightweight MRM treatment proportionate to
their materiality; tier-1 models receive
full SR 11-7 treatment with AI-specific
augmentations.

### Section 7 — Roles and accountabilities

Per the SR 11-7 three-lines frame:

- **First line — Business-line model
  owners.** Develop, deploy, and operate
  models. Conduct first-line monitoring.
  Maintain documentation. Submit to MRM
  for validation per tier.
- **Second line — MRM (CRO).** Independent
  challenge of conceptual soundness;
  validation per the methodology
  (Deliverable 04); review of monitoring
  outputs; tracking findings.
- **Second line — CAIRO.** AI-specific
  methodology authorship; AI-specific
  technical expertise to MRM; AI risk
  reporting to the Board; AI regulatory
  engagement. The CAIRO does NOT perform
  MRM validations (preserves MRM
  independence per SR 11-7).
- **Third line — Internal Audit.** Audit
  of the MRM function including AI
  extensions; tests adherence to this
  policy and methodology.

### Section 8 — Approval and amendment process

This policy is approved by the Risk
Committee. Amendments require Risk Committee
approval. The Risk Committee may delegate
specific amendment authority to the CRO for
technical updates; substantive scope changes
require Risk Committee approval.

The CRO is the policy owner. The CAIRO is the
amendment-author for AI/ML-specific updates.

— end policy update —

---

## 3. Reasoning notes

- **Why decision-influence-based rather than
  technique-based definition.** Technique-
  based definitions (e.g., "any neural
  network") leave gaps (e.g., what about a
  decision tree that happens to be ML-
  learned?) and over-include irrelevant
  things (e.g., a neural network used for
  autocomplete UX). Decision-influence-based
  catches what matters — material influence
  on decisions Tessera makes.
- **Why HR vendor LLM is in-scope.**
  Vendor positioning ("it's not a model,
  it's a productivity tool") is not
  controlling. The materiality test is.
  Sourcing function uses the rankings to
  decide which candidates advance —
  material to hiring outcomes — therefore
  in-scope.
- **Why office productivity LLM use is
  out-of-scope of MRM.** Office productivity
  LLM use does not produce material
  decisions to Tessera in the SR 11-7
  sense. It still requires governance (the
  Acceptable AI Use Policy) but that
  governance is not MRM. Putting general
  Copilot use under MRM would swamp the
  function and add no risk benefit.
- **Why the CAIRO does NOT perform
  validations.** SR 11-7 independence
  discipline. If the CAIRO authors
  AI-specific methodology AND validates,
  validators are challenging their own
  methodology. Preserving the split is
  worth the friction.
- **What would change the policy under
  pressure.** If a federal regulator
  demands a different definition of "model"
  for AI/ML specifically, this definition
  may need revision. Current OCC posture is
  decision-influence-aligned, which is why
  this approach holds.

---

Maintained by [Girish Nair](https://github.com/garynair)
