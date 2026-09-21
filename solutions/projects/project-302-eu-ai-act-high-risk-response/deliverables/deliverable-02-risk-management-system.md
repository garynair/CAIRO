# Deliverable 02 — Article 9 RMS — Reference Solution

## 1. Solution overview

The full RMS document for KH-AI-027. 11 risks
identified per Art. 9(2)(a); estimation
methodology per (b); cross-reference to data
risks per (c); treatment plans per (d) with 4
residuals explicitly named and accepted. Bias
treatment uses **equalized odds** as the
primary fairness conception (matching
sensitivity AND specificity across protected
subgroups); predictive parity is not
simultaneously enforced (mod-105 §3.2
impossibility result acknowledged). The
continuous-iterative process is operated
through monthly AI Risk Council reviews and
quarterly clinical-advisory-board reviews.

---

## 2. The RMS document

> **KERRIDGE HEALTHCARE — KH-AI-027 RISK
> MANAGEMENT SYSTEM v1.0**
> *Per EU AI Act Art. 9.*

### Section 1 — System scope and classification

KH-AI-027 (adult diabetic-retinopathy screening
SaMD) is high-risk under EU AI Act Art. 6(1)
and Art. 6(2) via Annex III(5)(a). Conformity
assessment route: Annex VII third-party.

### Section 2 — Art. 9(2)(a) — Identification of risks

Per Kerridge's AI risk taxonomy (mod-103 §2),
11 risks identified:

**Performance risks:**

1. *Sensitivity degradation in low-light
   images.* Likelihood: Medium. Severity:
   High (clinical-safety; missed referable
   cases).
2. *Sensitivity degradation in cataract-
   present eyes.* Likelihood: Medium.
   Severity: High.
3. *Calibration drift after training data
   refresh.* Likelihood: Medium (per
   mod-110 Ex-01 systemic-cause pattern).
   Severity: High.

**Bias and fairness risks:**

4. *Differential sensitivity by ethnicity /
   retinal pigmentation.* Likelihood:
   Medium. Severity: High.
5. *Differential sensitivity by age 80+.*
   Likelihood: Medium. Severity: High.
6. *Workflow capture — clinicians defaulting
   to AI classification without
   independent judgment.* Likelihood: High
   (per mod-105 §4.5). Severity: Medium-
   High.

**Transparency / explainability:**

7. *Heatmap regions not corresponding to
   clinically meaningful features.*
   Likelihood: Medium. Severity: Medium.

**Privacy and data:**

8. *Patient image re-identifiability via
   metadata combination.* Likelihood: Low.
   Severity: High.

**Security:**

9. *Adversarial inputs causing classification
   errors.* Likelihood: Low (limited
   incentive). Severity: Medium.

**Operational:**

10. *Integrated imaging hardware fails;
    silent degradation of input quality.*
    Likelihood: Medium. Severity: Medium.

**Clinical safety (Kerridge-added category):**

11. *Vendor-side model swap during deployed
    operation.* Likelihood: N/A (in-house
    model). Mark as not applicable.

### Section 3 — Art. 9(2)(b) — Estimation and evaluation

**Estimation methodology.** Likelihood is
estimated from validation-cohort outcomes plus
clinical-literature base rates; severity is
estimated from clinical-impact analysis.

**Evaluation thresholds.** Per-risk thresholds
that warrant treatment per Art. 9(2)(d). Risks
with Medium-or-higher likelihood AND
High-severity warrant explicit treatment plans.
9 of the 11 risks meet this bar.

**Reasonably foreseeable misuse.** Includes:
clinical use beyond the validated population
(e.g., glaucoma screening); use in lower-
quality imaging settings (handheld fundus
cameras); use without the required clinician
oversight workflow. Workflow controls (per
Deliverable 05) and customer-deployment
contractual language address these.

### Section 4 — Art. 9(2)(c) — Data risks

Per Deliverable 03. KH-AI-027's data risks
include training-set ethnic and age-stratum
representativeness; cataract-present eye
representation; image-quality distribution.
Data-side measures address these per Deliverable
03.

### Section 5 — Art. 9(2)(d) — Risk management measures

For each of the 9 risks meeting the treatment
threshold, a treatment plan. Examples (full
plans in the appendix; summarized here for the
RMS document):

**Risk 1 — Low-light sensitivity.**

- Controls: Hardware-side image-quality
  detection blocks low-quality images before
  classification; software-side flag prevents
  classification confidence above 0.7 for
  low-light samples.
- Residual: **Material**. Some borderline-
  light images still classified; clinician
  override is the failsafe.
- Acceptor: AI Risk Council with CMO
  designee concurrence.

**Risk 4 — Ethnicity bias.**

- Controls: Training-set augmentation with
  oversampled darker-pigmented retinas;
  subgroup performance validation (per
  Deliverable 03 datasheet); per-site
  monitoring with stratified outcomes.
- Residual: **Material**. Statistical power
  on the rarest pigmentation subgroup is
  limited.
- Acceptor: AI Risk Council.

**Risk 5 — Age 80+ bias.**

- Controls: Similar pattern. Oversampling;
  validation; monitoring.
- Residual: **Material** for very elderly
  patients (95+) due to limited training
  data.
- Acceptor: AI Risk Council with explicit
  re-evaluation trigger at the end-of-year
  monitoring review.

**Risk 6 — Workflow capture.**

- Controls: Asymmetric escalation (the AI
  can prompt referral; cannot recommend
  against). Clinician override documentation.
  Nurse-level override-rate monitoring.
- Residual: **Material**. Tracked. Threshold
  for retraining if any clinician's override
  rate falls below 10%.

(Risks 2, 3, 7, 8, 10 follow similar pattern;
full treatment plans in technical-file
appendix.)

### Section 6 — Continuous iterative process

The RMS operates continuously:

- **Monthly AI Risk Council review** of the
  risk register and treatment plan status.
- **Quarterly clinical advisory board
  review** of clinical-safety risks.
- **On material change** of the system or
  data: full RMS re-evaluation.
- **Annual full review** of the RMS
  document.

### Section 7 — Deployer communication

Per Art. 13, the RMS is communicated to
deployer hospitals via the operating
instructions document. The instructions cover:

- The system's intended use and validated
  population.
- The residual risks named in this RMS.
- The workflow constraints (asymmetric
  escalation; required clinician oversight).
- The reporting obligations of deployers
  back to Kerridge for monitoring purposes.

— end RMS document —

---

## 3. Reasoning notes

- **Why I picked equalized odds as the
  fairness conception.** Clinical-safety
  argument: false negatives in screening
  (missed referable cases) are the primary
  clinical concern; false positives drive
  workflow burden. Equalized odds matches
  both. Predictive parity is not enforced; the
  reference is explicit per mod-105 §3.2.
- **Why I named risk 11 (vendor swap) as N/A
  rather than omitting.** Completeness
  discipline. The Notified Body will look for
  the question; explicit N/A with reasoning
  is the right posture.
- **Why I named the 4 residuals as
  Material.** §6 honesty discipline.
  Programs that claim full residual mitigation
  for sensitive medical-AI risks are not
  credible. Naming residuals honestly survives
  Notified Body scrutiny.
- **What this RMS deliberately under-
  specifies.** The detailed treatment-plan
  documentation (lives in the technical-file
  appendix); the specific monitoring metric
  thresholds (per Deliverable 06).
- **What I would do differently.** I might
  have separated bias risks 4 and 5 into
  three risks rather than two (ethnicity;
  age 80+; intersectional). The 2-risk
  framing under-counts intersectional cases.

---

Maintained by [Girish Nair](https://github.com/garynair)
