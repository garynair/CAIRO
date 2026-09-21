# Exercise 03 — Article 9 RMS Summary — Reference Solution

## 1. Solution overview

The reference RMS summary is the single page that goes into
Aldwych's deployment proposal for the rebuilt ED triage
support tool. It addresses every Art. 9(2) element with
specificity, names the prior bias failure mode explicitly in
the risk identification, and is honest about residual risk.

---

## 2. The one-page RMS summary

> **Risk Management System Summary**
> *Aldwych Health — ED Triage Support Tool v2*
> *EU AI Act Art. 9 (high-risk under Annex III(5)(a))*
> *Version 1.0, prepared for AI Review Board + Board
> Quality Committee*

### 1. System scope and classification

- ED triage support tool used at intake by triage nurses
  across Aldwych's 14 hospitals to suggest an Emergency
  Severity Index (ESI) level based on incoming patient
  vitals and chief complaint.
- High-risk under EU AI Act Art. 6(2) via Annex III(5)(a).
  Art. 6(3) exemption considered and rejected (mod-102
  Exercise 01 §E for reasoning).
- Subject to EU AI Act for any EU-resident patient
  encounters; subject to MHRA / CQC oversight as a
  clinical-decision-support tool.

### 2. Article 9(2)(a) — Identification of risks

Known and reasonably foreseeable risks:

- **Demographic bias in triage suggestions** (the failure
  mode of the v1 system, decommissioned 2025). Specific to
  age, sex, language-of-presentation. Highest-priority
  risk; treated as not-yet-residual until
  monitoring evidence supports otherwise.
- **Over-triage** (ESI level pulled inappropriately high)
  causing ED resource misallocation and patient harm via
  delayed care of higher-acuity patients.
- **Under-triage** (ESI level pulled inappropriately low)
  causing direct patient harm to the under-triaged person.
- **Workflow capture** (nurses defaulting to the AI
  suggestion without independent assessment) — the
  Art. 6(3) failure mode that drives the high-risk
  classification.
- **Reasonably foreseeable misuse**: substitution for
  clinical judgement in high-acuity edge cases; misuse
  outside the intended ED-intake context; deployment
  across hospital sites with materially different
  population characteristics without site-specific
  validation.

### 3. Article 9(2)(b) — Estimation and evaluation

- **Per-hospital evaluation**: monthly evaluation of
  agreement between AI suggestion and final clinician ESI,
  stratified by ESI level and by protected demographic
  characteristics where consented data permits.
- **Threshold for re-evaluation**: any month in which
  demographic stratification shows > 5 percentage points
  divergence in agreement between subgroups for a single
  hospital triggers automatic clinical-team review.
- **Threshold for system pause**: any month in which the
  pattern repeats across two consecutive months at a
  single hospital, or in which a single demographic shows
  divergence > 10 percentage points anywhere, triggers
  system pause at the affected site pending Clinical
  Safety Officer review.
- **Reasonably foreseeable misuse evaluated quarterly** by
  the AI Review Board against the named misuse scenarios.

### 4. Article 9(2)(c) — Data risks (Art. 10 cross-reference)

- Training data per Art. 10 obligations: documented
  provenance, representativeness review, missing-value and
  protected-class handling documented.
- Specific data risks: under-representation of
  paediatric, elderly, and non-English-presentation
  populations in the training set. Per the v1 incident
  post-mortem, elderly under-representation was the
  proximate cause of the prior failure.
- Mitigations: augmented training set with explicit
  oversampling on under-represented subgroups; site-
  specific calibration applied during deployment
  ramp-up.

### 5. Article 9(2)(d) — Risk management measures + residual risk

| Risk | Measure | Residual risk |
|---|---|---|
| Demographic bias | Site-specific calibration + monthly demographic monitoring + pause threshold | **Material**. Treated as not-yet-residual until 6 months of monitoring evidence. |
| Over-triage | ESI conservatism ceiling — system cannot pull from ESI 4/5 to ESI 1 without flagging | Low. Bounded by design. |
| Under-triage | Workflow constraint: AI suggestion appears only after the nurse selects an initial ESI candidate; suggestion can only *escalate*, never de-escalate | Low. Bounded by design. |
| Workflow capture | Workflow constraint (above) + monthly tracking of nurse-AI agreement / override rate per nurse | Material. Tracked. Threshold for retraining if individual override rate falls below 10%. |

### 6. Iterative governance and deployer communication

- **Iterative governance**: the RMS is reviewed quarterly
  by the AI Review Board and annually by the Board Quality
  Committee. Each demographic monitoring threshold breach
  triggers an unscheduled review.
- **Deployer communication** (Art. 13): operating
  instructions to clinical teams state explicitly that
  (a) the AI suggestion is an input to nurse judgement,
  not a replacement; (b) the AI suggestion can only
  escalate ESI, never de-escalate; (c) any nurse who
  follows the AI suggestion contrary to their initial
  judgement must record the reason; (d) the named
  Clinical Safety Officer at each site is the escalation
  path for any concern about the AI's behaviour.

> *Authorised by:* Chief AI Risk Officer + Chief Medical
> Officer (co-sign per mod-101 exercise-03 reference
> structure). *Date:* [date].

---

## 3. Reasoning notes

- **Why the prior failure mode is named first.** Two
  reasons. First, regulatory: the v1 incident is on the
  public record, and any Art. 73 review of v2 will start
  with the question "what did you do differently?" The
  RMS must answer that question on its first page.
  Second, board-level: the Board Quality Committee
  approved the v1 decommissioning. Hiding the prior
  failure from the v2 RMS is a structural insult to the
  Board's prior decision.
- **Why the residual-risk column says "Material" twice.**
  Because it is. A program that names every residual risk
  as "Low" by month one of redeployment is not credible.
  Bias monitoring is a live concern until evidence
  supports otherwise; workflow capture is a live concern
  by construction of the AI–human workflow. Naming this
  honestly costs nothing and gains substantial credibility
  with the regulator.
- **The asymmetric escalation/de-escalation design.** This
  is the single most important design choice in the rebuild.
  An AI that can de-escalate ESI suggestions creates the
  exact failure mode of v1 (elderly patients pulled to
  lower acuity). An AI that can only escalate is bounded
  on the catastrophic-failure side at the cost of being
  noisier (more over-triage suggestions). The trade-off
  is the right one for an ED context. It is documented
  here for both the regulator and for the v3 designers
  who will be tempted to remove it.
- **What this RMS deliberately under-specifies.** The
  re-training cadence. The reference does not commit to a
  re-training frequency; that decision belongs in a
  separate model-update-control document that the
  Predetermined Change Control Plan (FDA-style) will
  formalize. Forcing it into the RMS would couple two
  artifacts that should evolve at different cadences.
- **What I would do differently next iteration.** Add a
  bench-test row to §3 — Aldwych should run a static
  bench-test of the v2 model against the v1 failure
  cases *before* deployment. The reference omits this for
  one-page discipline, but a v1.1 of the RMS should
  include it explicitly.

---

Maintained by [Girish Nair](https://github.com/garynair)
