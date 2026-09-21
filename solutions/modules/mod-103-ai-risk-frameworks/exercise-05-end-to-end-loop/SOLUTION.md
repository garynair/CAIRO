# Exercise 05 — End-to-End Loop — Reference Solution

## 1. Solution overview

This reference walks **Kerridge Healthcare's pre-submission
retinal-imaging AI/ML algorithm** through the full
MAP → MEASURE → MANAGE → GOVERN loop. Compressed (one to
one-and-a-half pages per artifact) but complete; each
artifact references the previous ones. Total length: ~7
pages.

---

## 2. Artifact 1 — Inventory row

| Attribute | Value |
|---|---|
| System ID | KH-AI-027 |
| Name + description | Retinal-imaging diabetic-retinopathy screener; CNN producing referable-vs-non-referable classification + heatmap |
| Owner (first line) | Head of Imaging Algorithms, Kerridge Healthcare |
| Business unit | Kerridge Healthcare |
| Use case | Pre-submission to FDA (SaMD) + EU MDR + AI Act high-risk |
| In-scope per program scope rules | Yes |
| Regulatory classifications | EU AI Act: high-risk via Art. 6(1) (safety component of regulated medical device); FDA: De Novo SaMD pre-submission; EU MDR: Class IIa |
| Risk categories applicable (taxonomy §2.2) | Performance; Bias and fairness; Transparency; Privacy and data; Operational; Compliance; Strategic |
| Status | Pre-submission (clinical validation in progress) |
| Last impact assessment | [date] |

---

## 3. Artifact 2 — Classification

**Regulatory.**

- **EU AI Act:** High-risk via Art. 6(1) — safety component
  of a product regulated under EU MDR. Conformity-
  assessment route: third-party (Annex VII) because the
  device class triggers Notified Body involvement.
- **FDA:** AI/ML Software as a Medical Device.
  Predetermined Change Control Plan to be filed alongside
  the De Novo submission to enable continuous-learning
  within a pre-cleared envelope.
- **EU MDR:** Class IIa — body-part-specific, non-active
  device with diagnostic claim.

**AI risk taxonomy.** From §2.2 starting taxonomy, with
Aldwych-style addition of *Clinical safety* as a top-
level category:

- Performance — material (diagnostic accuracy directly
  affects clinical outcome).
- Bias and fairness — material (subgroup performance
  disparities are common in retinal imaging).
- Transparency and explainability — material (clinicians
  need to read the heatmap; regulators need the
  reasoning to be auditable).
- Privacy and data — material (training data is patient
  imaging).
- Security — moderate (clinical-network deployment; not
  internet-exposed but supply-chain matters).
- Operational — material (clinical workflow integration).
- Compliance — material (FDA + EU MDR + EU AI Act +
  GDPR data-handling).
- Strategic — material (this is the first SaMD product
  for Kerridge Healthcare; reputational and strategic
  stakes are high).
- *Clinical safety* (Kerridge-added top-level) — material
  (this is a clinical-decision-support system).

---

## 4. Artifact 3 — Impact assessment (compressed)

Using the template from Exercise 02.

### 1 — System summary

KH-AI-027 produces a referable / non-referable
classification for retinal images in primary-care
diabetic-retinopathy screening, with an attention heatmap
overlay. Affected parties: patients screened (primary),
ophthalmologists receiving referrals (secondary),
primary-care clinicians performing screening (operating
user). Decisions affected: ophthalmologist referral
decision. Pre-submission status.

### 2 — Risk categories applicable

All nine taxonomy categories above are Y.

### 3 — Failure modes per applicable category (compressed; 1 example per category)

- **Performance.** Model may under-detect referable disease
  in low-light or low-contrast images, especially in
  patients with cataracts. Likelihood: Medium. Severity:
  High.
- **Bias.** Model may under-detect referable disease in
  populations under-represented in the training set
  (specifically: darker-pigmented retinas, ages > 75).
  Likelihood: Medium. Severity: High.
- **Transparency.** Heatmap may highlight regions that do
  not correspond to clinically meaningful features,
  reducing trust without rejecting the classification.
  Likelihood: Medium. Severity: Medium.
- **Privacy.** Patient imaging in training set may be
  re-identifiable by combination with metadata.
  Likelihood: Low. Severity: High.
- **Security.** Supply-chain compromise of the inference
  container at deployment. Likelihood: Low. Severity:
  High.
- **Operational.** Workflow integration failure causes
  delays in screening; site-level dependency on
  vendor-supported camera hardware. Likelihood: Medium.
  Severity: Medium.
- **Compliance.** Failure of the Predetermined Change
  Control Plan to anticipate a needed update; FDA may
  require new submission rather than within-envelope
  update. Likelihood: Medium. Severity: Medium.
- **Strategic.** Product underperforms in commercial
  deployment, damaging Kerridge Healthcare's go-to-
  market position. Likelihood: Medium. Severity:
  Medium.
- **Clinical safety.** False-negative classification
  delays referral; patient's untreated disease
  progresses. Likelihood: Low (given workflow design)
  but Severity: Very High.

### 4 — Existing controls (compressed)

- Multi-site clinical validation in progress (Performance).
- Subgroup performance evaluation on validation set
  (Bias).
- Bounded heatmap algorithm with documented attention
  source (Transparency).
- Imaging de-identification per HIPAA + GDPR (Privacy).
- Signed-container deployment via internal artifact
  registry (Security).
- Clinical workflow integration tested at pilot sites
  (Operational).
- PCCP drafted for FDA pre-submission review (Compliance).

### 5 — Gaps

- Subgroup validation does **not yet cover** patients
  > 75 with cataracts at sufficient sample size.
- No external red-team of the heatmap (Transparency).
- PCCP currently anticipates training-data refresh but
  **not architecture changes** — a planned upgrade may
  fall outside the envelope.
- No second-source camera-hardware support; operational
  single-point-of-failure.

### 6 — Reasonably foreseeable misuse

- Clinical use beyond the validated population
  (e.g., glaucoma screening); workflow controls do not
  currently prevent.
- Deployment in lower-quality imaging settings (handheld
  fundus cameras) outside the validated hardware
  envelope.

### 7 — Recommendations to MEASURE and MANAGE

(Compressed, top 3.)

For MEASURE:

- Measure subgroup performance specifically in > 75 +
  cataract subpopulation (Bias).
- Measure heatmap-attention agreement with clinician-
  annotated regions (Transparency).
- Measure PCCP-envelope adherence — track whether
  proposed model updates fit the envelope (Compliance).

For MANAGE:

- Consider whether second-source camera support is
  needed pre-launch (Operational F gap).
- Consider whether a clinical-population restriction
  should be enforced at the workflow level rather than
  via documentation (Misuse 1).

---

## 5. Artifact 4 — Measurement plan (compressed)

For the top three risks from §4:

**Performance — top risk.**

- Leading: model-confidence-score distribution shift on
  weekly batches vs. training reference.
- Threshold: > 2σ shift in mean.
- Response: Model Owner investigates; if shift confirms
  drift, halt new-site deployment.
- Owner: Model Owner.

- Lagging: subgroup-stratified sensitivity on rolling 30-
  day labeled outcome set.
- Threshold: sensitivity < 0.87 in any age × pigmentation
  cell.
- Response: AI Review Board reviews; clinical advisory
  panel consulted; model considered for re-training.
- Owner: Model Owner + Clinical Director.

**Bias and fairness.**

- Leading: pre-deployment subgroup-stratified validation
  delta against committed thresholds.
- Threshold: > 5pp delta in sensitivity between any
  subgroup pair.
- Response: AI Review Board reviews; deployment in
  affected sites paused.
- Owner: Head of Imaging Algorithms.

- Lagging: post-deployment site-level disparity report
  quarterly.
- Threshold: > 4pp sustained over 2 quarters.
- Response: Clinical Safety Officer + AI Review Board
  review; treatment plan re-evaluated.
- Owner: Clinical Safety Officer.

**Clinical safety.**

- Leading: heatmap-attention disagreement rate with
  clinician annotation (sampled weekly).
- Threshold: > 15% disagreement.
- Response: Transparency review; clinical advisory
  panel.
- Owner: Clinical Director + Model Owner.

- Lagging: clinically-confirmed false-negative rate from
  longitudinal patient follow-up (semi-annual).
- Threshold: any clinically-significant case.
- Response: Adverse event report under MDR / FDA
  channels; immediate AI Review Board.
- Owner: Clinical Director.

(Plan also covers privacy, security, operational,
compliance, strategic — omitted here for compression.)

---

## 6. Artifact 5 — Treatment plan for the most material risk

The most material risk is **Bias in > 75 + cataract
subpopulation** (Bias category; specific failure mode
from §4-Bias). Treatment plan (compressed; same shape as
Exercise 04):

**Controls applied:**

- C1: Targeted subgroup augmentation in the next training
  data refresh; quantified target sample size = 2x
  current.
- C2: Pre-launch validation gate: deployment cannot
  proceed until > 75 + cataract subgroup sensitivity
  reaches > 0.85 on the augmented validation set.
- C3: Post-deployment clinical-flag rule: clinician
  receiving a non-referable classification for a > 75
  patient with documented cataract must explicitly
  confirm the AI's classification rather than passive-
  accept.
- C4: Quarterly subgroup-stratified disparity report
  with hard threshold trigger (per measurement plan).

**Residual:** Material × High → **Material residual.**
Strictly lower than unmitigated (controls C2 and C3
provide bounded protection at the decision point;
controls C1 and C4 reduce systematic drift) but real
because the subgroup is intrinsically under-imaged in
the training distribution.

**Accepted by:** Kerridge Healthcare's AI Review Board,
with concurrence from the Chief Medical Officer.

**Re-evaluation triggers:** Threshold crossing in C4;
clinical incident; > 6 months without subgroup data
refresh; FDA / Notified Body request.

**Exception status:** Not an exception — this is the
program's standard pattern.

---

## 7. Artifact 6 — GOVERN summary

**Risk register placement.** KH-AI-027 enters the
Kerridge Healthcare risk register as a *high-material-
risk system in pre-submission state*. The system carries
nine taxonomy categories at material level (per §3 above);
the register tracks status per category.

**Board roll-up.** In the next quarterly Board Risk
Committee report, KH-AI-027 appears as the *most
significant new entrant to the risk register this
quarter*. The roll-up will note the strategic significance
(first SaMD product), the pre-submission timeline, and
the material residual on the Bias category. Asked of the
Board: a ratification of the AI Review Board's
acceptance of the Material residual on the > 75 +
cataract Bias risk, pending the post-launch monitoring
results.

**GOVERN review cadence.**

- Pre-submission phase: AI Review Board reviews
  monthly; AI Risk Council reviews quarterly.
- Post-submission, pre-launch: AI Review Board
  bi-weekly.
- Post-launch: AI Review Board monthly; AI Risk Council
  quarterly; Board Risk Committee quarterly.

**One concrete loop-closing pattern.** If post-launch
MEASURE shows the C4 subgroup-disparity threshold
crossing in two of any three quarters at any site, the
program's **bias-treatment standard** is updated to
require an additional pre-launch validation gate (rather
than just the post-deployment monitoring used here).
That standard update — visible in the next policy
revision — is the *evidence* that the loop closed.
A failure to update the standard despite two threshold
crossings would be a *failure-to-close* signal that the
CAIRO would surface to the AI Risk Council and the Board.

---

## 8. Reasoning notes

- **Why this system.** Retinal-imaging SaMD sits at the
  intersection of two regulatory regimes (FDA + EU MDR
  + EU AI Act) and exercises every taxonomy category
  including Clinical safety. It is the most demanding
  shape of system Kerridge operates, which is the right
  shape for this capstone.
- **Why the artifacts are tightly linked.** The linkage
  is the *whole point* of the exercise. A program where
  the impact assessment, measurement plan, and treatment
  plan describe the same risk with subtly different
  vocabularies has failed at the integration that this
  module is teaching.
- **Why I called out a Material residual rather than
  Low.** Pre-submission FDA / Notified Body review will
  read every claim of fully-mitigated risk skeptically.
  A program that names Material residual where Material
  residual exists builds trust with the regulator from
  the first interaction. Programs that systematically
  claim Low residual draw harder questions throughout
  the review process.
- **Why the loop-closing example is so specific.**
  Programs that fail at the loop-closing stage do so
  because they cannot name *what good would look like*
  in concrete terms. The reference's "if pattern X
  occurs in MEASURE, then standard Y gets updated"
  framing is the operational form of loop closure. The
  CAIRO who runs this loop is the one whose program
  survives external review.
- **The Kerridge-added "Clinical safety" taxonomy
  category** demonstrates §2.4 — adapting the taxonomy
  for context. Without that addition, the failure mode
  most likely to surface a serious incident would have
  been buried under "Performance" and given inadequate
  prominence.
- **What would change in v2 of this exercise.** A
  cross-system view: most CAIROs operate dozens of systems
  simultaneously; the loop closes (or fails to close)
  across the portfolio, not just per-system. The
  reference compresses to one system for length but the
  portfolio-level loop is the next stage.

---

Maintained by [Girish Nair](https://github.com/garynair)
