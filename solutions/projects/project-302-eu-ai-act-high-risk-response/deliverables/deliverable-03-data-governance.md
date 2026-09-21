# Deliverable 03 — Article 10 Data and Governance — Reference Solution

## 1. Solution overview

Data governance documentation for KH-AI-027.
Training set: ~38,000 fundus images from 14
European clinical sites; validation set: ~8,400
images; held-out test set: ~3,200 images. Bias
examination covers 4 dimensions (ethnicity, age,
cataract presence, image quality). Three honest
data gaps identified: under-representation of
South-Asian subgroup, very-elderly (95+),
hand-held-camera images. Lifecycle includes the
training-data refresh review gate from mod-110
Ex-01 systemic-cause discipline.

---

## 2. The documentation

### Design choices

Training, validation, and test sets were
designed to support generalisation to the
intended European primary-care screening
context. Cohort-level diversity targets were
set at design time:

- Age strata: 18-44 (15%); 45-64 (40%); 65-79
  (30%); 80+ (15%).
- Ethnic / pigmentation distribution: matched
  to European primary-care diabetes screening
  population per WHO regional data.
- Cataract presence: 12% (matches
  population prevalence in screening cohort).
- Image quality: mix of professional fundus
  cameras (75%) and table-top portable
  cameras (25%).

### Data origin

Training images sourced from 14 European
hospital partners under data-use agreements
permitting AI/ML training use. Data flow:
de-identified at source per HIPAA Safe Harbor
+ GDPR pseudonymisation; transferred to
Kerridge under BAA + DPA. Provenance
documented per-image including originating
site, year of capture, equipment used.

### Annotation processes

Ground truth (referable / non-referable) per
international clinical guidelines (ICDR scale
2+ as referable). Annotation by board-certified
ophthalmologists; 3-rater per image with
disagreement adjudication by senior
ophthalmologist; inter-rater agreement κ = 0.81
(substantial; documented).

### Data preparation

Standard normalisation; augmentation
(rotations, brightness adjustments) for class
balance; outlier removal based on image-quality
score thresholds. Augmentation pipeline
documented and version-controlled.

### Assumptions

The training data represents the European
primary-care diabetes screening population.
Specific assumptions: (a) screening occurs
during typical clinic hours under reasonable
lighting; (b) the device operator follows
standard imaging protocol; (c) patients have
adequate pupil dilation per screening
guidelines.

Use of KH-AI-027 outside these conditions is
out of the intended use; deployer-side
controls (per Deliverable 05 workflow design)
guard against use beyond intended scope.

### Bias examination

Per Art. 10(2)(f), bias examination across four
dimensions:

**Dimension 1 — Ethnicity / retinal
pigmentation.**

Validation outcome: sensitivity matched within
3pp across documented ethnic groups for
referable cases at standard imaging quality.
Specific exception: **South-Asian subgroup**
(only ~6% of training data) shows slightly
lower sensitivity (98.0% vs. 99.2%
benchmark). Below threshold but flagged.

**Dimension 2 — Age strata.**

Validation outcome: sensitivity matched within
2.5pp across age strata. Specific exception:
**80+ subgroup** shows sensitivity 96.5% vs.
99.0% benchmark. Below threshold for the
65-79 group but above the 3pp warning. **95+
subgroup** (very limited n) shows 95.0%
sensitivity — flagged as data gap.

**Dimension 3 — Cataract presence.**

Validation outcome: sensitivity for cataract-
present eyes 95.5% vs. 99.0% benchmark.
Below threshold; hardware-side image-quality
detection (per Deliverable 02 risk treatment)
addresses the most problematic cases by
blocking low-quality images from
classification.

**Dimension 4 — Image quality (handheld vs.
professional).**

Validation outcome: hand-held camera images
show sensitivity 94.0% vs. 99.0% for
professional. **Below threshold; flagged as
data gap.** Mitigation: customer-deployment
contractual language restricts initial
deployment to professional fundus cameras.

### Honest data gaps

Three substantive data gaps:

1. **South-Asian subgroup under-representation**
   (~6% of training data). Mitigation: targeted
   data acquisition for the next training-set
   refresh; clinician guidance highlighting
   the specific subgroup performance.
2. **Very-elderly (95+) under-representation**.
   Mitigation: explicit acknowledgment in the
   operating instructions; clinician workflow
   prompts elevated review for very-elderly
   patients.
3. **Hand-held-camera images
   under-representation**. Mitigation:
   restricted to professional cameras at
   launch; expanded support contingent on
   additional validation work in year 2.

### Lifecycle management

Training data refresh follows a defined
cadence: quarterly review of new clinical
data; annual training-set refresh if material
new data exists.

**Training-data refresh review gate.** Per
mod-110 Ex-01 systemic-cause discipline: no
re-trained model deploys without subgroup-
representation comparison against the prior
training set. The refresh review gate is owned
by the Algorithm Quality Office Clinical
Validation Lead.

Provenance: every training image retains
audit-trail metadata back to source site,
date, equipment. Chain of custody documented
through transfer agreements.

Representativeness drift monitoring: monthly
review of customer-site case-mix data
(authorised customer-side data export) against
training-set composition; substantive drift
triggers data-refresh planning.

---

## 3. Reasoning notes

- **Why I named three honest data gaps.**
  Notified Body specifically looks for data
  gaps in medical-AI training data. Claiming
  no gaps is implausible and damaging when
  the Body finds them anyway.
- **Why the South-Asian under-representation
  was flagged below threshold.** Even
  technically-within-acceptable performance,
  the subgroup deserves explicit
  acknowledgment because the population
  served by Kerridge's customers materially
  includes the subgroup. Programs that
  ignore "within-threshold-but-substantively-
  weaker" subgroups produce post-launch
  bias incidents.
- **Why the lifecycle includes the refresh
  review gate.** mod-110 Ex-01 was about
  exactly this failure pattern; the
  documentation makes it explicit so future
  Kerridge teams cannot accidentally drop
  the gate.

---

Maintained by [Girish Nair](https://github.com/garynair)
