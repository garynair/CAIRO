# Deliverable 05 — Article 14 Human Oversight Design — Reference Solution

## 1. Solution overview

KH-AI-027's oversight is **asymmetric
escalation** (mod-105 Ex-03 pattern adapted
to clinical screening): the AI can prompt
the clinician to refer; the AI cannot
recommend against referral. The natural
person responsible is the screening
clinician (nurse or primary-care physician),
backed by the clinical-quality lead at each
deployer site for escalation. Three measures
implement the four Art. 14(4) oversight
capabilities; two acknowledged tensions are
named (automation bias risk; clinical
workload).

---

## 2. The oversight design

### Workflow and role of the natural person

Workflow: the patient arrives for diabetes
screening; the screening clinician (typically
a nurse) operates the fundus camera; the
imaging hardware captures images; KH-AI-027
classifies; the clinician reviews the
classification, the confidence score, and the
heatmap; the clinician makes the referral
decision.

The screening clinician is the natural person
for Art. 14(1) oversight. The clinical-quality
lead at each deployer site is the
escalation/backstop natural person.

### Art. 14(4)(a) — Understand capacities and limitations

Operating instructions communicate intended
use, validated population, known limitations
(three honest data gaps from Deliverable 03),
required workflow constraints. Mandatory
training for new clinicians covers KH-AI-027
behaviour, the residual risks named in
Deliverable 02, and the workflow constraints.

Refresher training is required annually.

### Art. 14(4)(b) — Remain aware of automation bias

Three controls:

1. **Asymmetric escalation.** The AI can
   prompt referral; the AI cannot recommend
   against referral. A "non-referable"
   classification from the AI does not
   suppress the clinician's option to refer
   based on clinical judgment.
2. **Override-rate monitoring.** Per
   clinician override rates are tracked. A
   clinician whose override rate falls below
   10% (i.e., overrides AI fewer than 10%
   of cases) triggers a clinical-quality
   review.
3. **Per-case confidence and heatmap
   display.** The clinician sees the
   confidence score and explainability
   heatmap, not just a binary
   classification. Heatmaps directing the
   clinician's attention to clinically
   relevant retinal regions reduce blind
   trust.

### Art. 14(4)(c) — Correctly interpret system output

Heatmap design: shows model attention regions
overlaid on the fundus image. Confidence score
displayed numerically and as a colour-coded
band (high / medium / low). Operating
instructions cover how to interpret each.

Clinician UI prevents user error by requiring
explicit confirmation before either
"refer" or "do-not-refer" actions are
recorded.

### Art. 14(4)(d) — Decide not to use; override

Clinicians retain full authority to:

- Refer based on clinical judgment regardless
  of AI classification.
- Refer for follow-up reasons unrelated to the
  AI classification (e.g., systemic
  observations during the screening
  appointment).
- Reject the AI classification entirely if the
  image quality, patient circumstances, or
  the clinician's clinical judgment indicates.

The clinician's referral decision is the
clinical record. The AI classification is a
contributing input, not a binding
recommendation.

### Art. 14(4)(e) — Interrupt or stop

Site-level controls allow the clinical-quality
lead to suspend KH-AI-027 use at the site
level. Kerridge-side controls allow a
provider-level operational pause across all
deployer sites. The pause-criteria are named
in Deliverable 06 (post-market monitoring) and
Deliverable 07 (incident reporting).

### Art. 14(5) — Verification by two natural persons

Annex III(1)(a) requires biometric
identification systems to be verified by two
natural persons. KH-AI-027 is not a biometric
identification system; Art. 14(5) does not
apply. (Documented for completeness.)

### Resourcing implications

Asymmetric escalation produces a workload
shape:

- For non-referable AI classifications: the
  clinician reviews the heatmap, accepts the
  classification, moves on. Average overhead:
  ~30 seconds per patient.
- For referable AI classifications: the
  clinician reviews more carefully, may refer
  or override. Average overhead: ~2 minutes
  per patient.
- For AI's that flag uncertainty (low-
  confidence borderline cases): clinician
  must engage more deeply. ~5 minutes per
  patient.

Total clinical-workload impact is positive
(faster screening overall vs. unaided
ophthalmologist review), but the asymmetric
escalation does not eliminate clinician
engagement.

### Tensions and acknowledged limits

**Tension 1 — Automation bias risk.** Despite
all three controls in Art. 14(4)(b), screening
clinicians may default to accepting AI
classification, particularly in high-throughput
settings. The override-rate monitoring serves
as a tripwire but does not eliminate the
risk. The clinical-advisory-board reviews
this quarterly.

**Tension 2 — Clinical workload trade-off.**
Asymmetric escalation increases per-case
review time for referable cases vs. a system
that simply ratified the AI's classification.
This is intentional (clinical safety) but
deployer sites with high screening throughput
will feel it.

---

## 3. Reasoning notes

- **Why asymmetric escalation rather than full
  symmetric review.** The clinical-safety
  asymmetry — missed referable cases are
  worse than over-referrals — drives the
  workflow design. Symmetric review would
  give equal weight to "AI says
  non-referable, clinician disagrees" and
  "AI says referable, clinician disagrees"
  paths, which mis-prioritizes.
- **Why I tracked the override-rate threshold
  explicitly at 10%.** Specific thresholds
  are more defensible than vague "we will
  monitor". The 10% threshold has clinical
  defensibility for the diabetic-retinopathy
  population (clinical-literature override
  rates for AI-assisted screening tend to be
  15-25%; below 10% suggests automation
  capture).
- **Why I named the two tensions.** Notified
  Body engagement asks "what doesn't work
  here?" Pre-empting the question reads as
  honest discipline rather than missed risk.
- **What this design deliberately doesn't
  include.** A second-clinician sign-off
  requirement (would over-burden screening
  workflow); model-confidence-based forced
  escalation to ophthalmologist (would
  add latency without proportionate safety
  benefit at validation-set rates).

---

Maintained by [Girish Nair](https://github.com/garynair)
