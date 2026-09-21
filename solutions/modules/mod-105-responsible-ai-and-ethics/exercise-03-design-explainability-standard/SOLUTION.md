# Exercise 03 — Design an Explainability Standard — Reference Solution

## 1. Solution overview

A 3-page program-wide explainability standard for
**Tessera Bank**. Covers four audiences (affected
parties, internal validators, regulators, deployers /
underwriters). The four affected-party principles are
the §4.3 three plus a Tessera-specific principle:
*"the explanation is reproducible if challenged."*
SHAP and LIME are bounded as inputs to affected-party
explanations, never as the explanation itself.

---

## 2. The standard

> **Tessera Bank — AI Explainability Standard**
> *Version 1.0. Owned by Chief AI Risk Officer.*
> *Applies to all Tier 1 AI systems per the program tiering.*
> *Reviewed annually.*

### Section 1 — Scope

In scope: every Tier 1 AI/ML system deployed at
Tessera, with the exception of internal-only models
that do not affect customers or employees and that
do not influence any binding decision. The current
in-scope population is: the small-business credit
decisioning system; the fraud-detection anomaly
detector; the customer-service chat agent (with the
deployment-time conditions per its validation file);
the marketing-segmentation model where it influences
fair-lending-relevant decisions. Out of scope: pure
back-office analytical dashboards; experimental models
not yet in any production path.

### Section 2 — Audience-specific requirements

**Audience 1 — Affected parties (loan applicants,
including denied applicants).**

- *Decisions the audience needs to make:* whether to
  modify their application, contest the decision,
  appeal, seek the decision elsewhere, or accept.
- *Content:* the specific factors that drove the
  decision, expressed in the customer's vocabulary;
  the path forward (contestation, recourse, re-
  evaluation cadence); the named human reviewer
  reachable for questions.
- *Depth:* one-page printed letter for denied
  applications; one-paragraph in-app explanation for
  pre-qualification denials; in-person conversation
  available on request.
- *Delivery format:* letter (denials); in-app text
  (pre-qualification); printed packet available on
  request.
- *Cadence:* per-decision (within 5 business days for
  denials per Reg B; immediate for in-app).
- *Owner role:* Adverse-Action Notice Process Owner,
  Compliance team.

**Audience 2 — Internal validators (MRM, internal
audit).**

- *Decisions:* whether the model's behaviour matches
  its design intent; whether independent validation
  has been completed; whether monitoring is
  functioning.
- *Content:* full technical file per the bank's MRM
  standard, including reproducibility documentation;
  validation pattern outputs (challenger, subgroup,
  counterfactual, stress); deployment-time
  configuration; current monitoring metrics.
- *Depth:* full file (typically 30–80 pages per Tier
  1 model).
- *Delivery format:* shared internal documentation
  drive; accessible on request to MRM and Audit roles.
- *Cadence:* updated per material change + annually;
  available on-demand.
- *Owner role:* Model Owner (production); MRM Lead
  (validation file integration).

**Audience 3 — Regulators (OCC, CFPB, NYDFS where
applicable).**

- *Decisions:* whether the bank is meeting SR 11-7
  expectations; whether fair-lending obligations are
  met; whether AI-specific obligations under any
  state-level law are met.
- *Content:* SR 11-7-compliant model inventory entry
  (per mod-104 Ex-03 LLM Supplement pattern); the
  technical file as required by SR 11-7 §III; fair-
  lending evidence package (CFPB / Reg B); any state-
  level disclosure or reporting required.
- *Depth:* on-demand provision; nothing produced
  prophylactically beyond the bank's ongoing
  documentation requirements.
- *Delivery format:* per regulator request; PDF
  packet typical.
- *Cadence:* on-demand; regulator-driven.
- *Owner role:* MRM Lead (for SR 11-7 content); CAIRO
  function (for AI-specific content); GC for the
  cover letter.

**Audience 4 — Internal deployers (underwriters,
fraud-review analysts, customer-experience supervisors).**

- *Decisions:* how to interpret the model's output in
  their decision context; when to override; when to
  escalate concerns.
- *Content:* operating instructions (intended use,
  known limitations, escalation criteria, override
  documentation requirements); ongoing performance
  summary; recent incidents.
- *Depth:* operating-instructions document (≤ 5 pages)
  per system + monthly performance summary (one page).
- *Delivery format:* deployer training materials +
  monthly internal bulletin.
- *Cadence:* training at onboarding + on each material
  model change; monthly summary.
- *Owner role:* Model Owner (operating instructions);
  business-unit Training Lead (delivery).

### Section 3 — Affected-party transparency principles

The standard adopts four principles for affected-party
transparency:

1. **Explainable in actionable terms.**
   *Operational implementation:* the explanation must
   name at least two factors the affected party
   *could change* and one factor that is *structural*
   (e.g., the credit-policy threshold that applied).
   Explanations consisting only of structural factors
   fail the principle. Explanations containing only
   un-actionable factors (e.g., "credit history
   length") also fail; if the only factors are
   un-actionable, the standard requires that the
   explanation also surface the recourse path.

2. **True (not post-hoc rationalisation).**
   *Operational implementation:* attribution outputs
   from explainer tools (SHAP, LIME) must be
   verified against the model's documented behaviour
   on a quarterly basis. Where attribution-based
   explanations and model-behavioural verification
   diverge, the model owner is required to investigate
   and either reconcile the divergence or replace the
   attribution method. Attribution outputs that cannot
   be reconciled with model behaviour are removed
   from affected-party explanations.

3. **Comes with a path forward.**
   *Operational implementation:* every affected-party
   explanation includes (a) the contestation process,
   (b) named human reviewer, (c) timeline for
   re-evaluation if the customer modifies their
   application or waits for natural updates. The
   path forward is mandatory; explanations missing it
   fail the standard.

4. **Reproducible if challenged.** (Tessera-specific
   addition.)
   *Operational implementation:* every affected-party
   explanation provided is logged with the specific
   factors named, the data inputs used, and the model
   version that produced it. If the customer
   subsequently challenges the explanation through
   any channel (contestation, regulator complaint,
   litigation), the bank can reproduce the explanation
   on demand within 5 business days.

### Section 4 — The mechanical-explainability boundary

SHAP, LIME, and similar attribution techniques are
**permitted as inputs** to affected-party
explanations. They are **not permitted as the
explanation itself**.

- **Where appropriate:** as analytical inputs in MRM
  validation; as components of internal-validator
  technical documentation; as the data source for
  attribution-derived natural-language explanations
  delivered to affected parties.
- **Where not sufficient alone:** any direct delivery
  to an affected party. A SHAP chart sent to a denied
  loan applicant does not satisfy this standard.
- **What is required in addition:** natural-language
  translation of the attribution into actionable terms
  (per Principle 1); verification against model
  behaviour (per Principle 2); recourse and timeline
  (per Principle 3); logging for reproducibility (per
  Principle 4).

### Section 5 — Process transparency

In addition to model transparency, the standard
requires *process* transparency:

- For affected parties: the existence of an AI
  system in the decision pathway is disclosed at the
  point of decision (per CA AI Transparency Act
  baseline applied across the bank for consistency).
- For regulators: the bank's overall decision process
  for each in-scope system is documented and made
  available on request, including the human-review
  step, the override path, and the workflow controls.
- For internal deployers: the workflow context the
  model operates within is part of the operating
  instructions (Audience 4).

Process transparency is **not optional** and is treated
as first-class — it is the property that lets affected
parties and regulators understand what the AI is doing
in context, beyond the model output alone.

---

## 3. Reasoning notes

- **Why I added "reproducible if challenged" as the
  fourth principle.** The §4.3 principles are the
  default three. Tessera's posture in the post-Facebook
  growth era is that the bank's AI decisions will be
  challenged — by customers, by regulators, by
  litigators. A program where attribution-based
  explanations cannot be reproduced when challenged
  has a structural weakness that only surfaces under
  challenge. Building reproducibility as a principle
  forces logging discipline at the explanation-
  generation step, not just at the model-output step.
- **Why four audiences and not all eight.** The eight
  audiences from §4.1 are the full taxonomy. For
  Tessera Tier 1 systems, four audiences are the
  operational priority. The other four (curious
  external public, affected communities, board /
  senior management as a distinct audience, etc.) are
  served through other communication channels.
  Standards that try to cover all eight in one
  document fail at length.
- **Why I left SHAP/LIME permitted as inputs but
  bounded.** Mechanical-explainability tools are
  useful. The §4.4 trap is treating them as the
  endpoint, not as the input. The bounding language
  permits their use without permitting the abuse.
- **Why owner roles are explicit.** Standards without
  named owners get ignored. The standard names a role
  for every requirement; mid-tenure organizational
  change might rename the roles but the structural
  ownership pattern persists.
- **What this standard deliberately under-specifies.**
  The *specific* attribution method (SHAP vs. LIME vs.
  newer tools). Method choice is left to the model
  owner with MRM concurrence — the standard requires
  the verification discipline (Principle 2) but does
  not mandate the method. This is the right level for
  a program standard; specific method choice is a
  technical decision that should evolve with the
  toolchain.
- **What I would do differently in v2.** Add an
  *audience-five* section for *affected communities*
  — aggregate-level transparency for the populations
  affected by the bank's AI decisions, beyond
  individual customer explanations. Per §4.1 of the
  lecture notes, this is a legitimate audience.
  Tessera's current scale does not yet justify it; a
  larger bank would.

---

Maintained by [Girish Nair](https://github.com/garynair)
