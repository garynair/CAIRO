# Deliverable 04 — Article 11 + Annex IV Technical Documentation Summary — Reference Solution

## 1. Solution overview

A navigable summary of the KH-AI-027 technical
file mapping each Annex IV section to where the
substantive documentation lives. The summary is
~6 pages; the full technical file is ~85 pages.
The summary mirrors the Annex IV ordering so the
Notified Body can cross-reference quickly. Three
sections deliberately under-specified at the
summary level (full content in the file): (a)
detailed model architecture; (b) full validation
test plan; (c) configuration management.

---

## 2. The summary

### How this document works

This document summarises KH-AI-027's technical
file per Annex IV of the EU AI Act. Each
section corresponds to one Annex IV item. The
"Where to find it" line per section points to
the file location in the full technical file
(maintained as version-controlled documents
under Kerridge's Quality Management System).

### 1. General description

**Intended purpose.** Adult diabetic-retinopathy
screening from fundus images, supporting
primary-care clinical workflow. Validated
population: adults aged 18+ with diabetes
attending routine screening in European primary-
care settings.

**Provider.** Kerridge Healthcare Ltd., UK
(parent: Kerridge Industries; CAIRO accountable
for AI-side obligations).

**Person responsible for placing on the
market.** Named in declaration of conformity.

**Where to find it:** TF/Section-01.

### 2. Detailed description of system

System architecture: deep convolutional neural
network (ResNet-based architecture); accepts
fundus images normalized to 512x512; outputs
referable / non-referable classification with
confidence score and explainability heatmap.

Integrated with hardware fundus camera (CE-
marked separately under MDR). Software stack:
classification model; integration layer;
clinician-facing UI; audit-trail logging
component.

**Where to find it:** TF/Section-02 (detailed
architecture, hyperparameters, training
methodology); TF/Section-02-Appendix-A (full
model card).

### 3. Information on data

Per Deliverable 03 (Article 10 data and
governance documentation), summarised here.

Training: ~38,000 fundus images, 14 European
sites; validation: ~8,400 images; test: ~3,200
images. Bias examination across ethnicity, age,
cataract presence, image quality. Three honest
data gaps named: South-Asian under-
representation, very-elderly (95+) under-
representation, hand-held-camera images.

**Where to find it:** TF/Section-03 + linked
Deliverable 03 documentation.

### 4. Description of monitoring, functioning, and control

Per Deliverable 06 (post-market monitoring
plan), summarised here.

KH-AI-027's post-market monitoring covers:
sensitivity/specificity monitoring across
deployer sites; subgroup performance
monitoring (the four bias dimensions);
calibration drift monitoring; clinician
override rate monitoring; serious incident
tracking per Deliverable 07.

**Where to find it:** TF/Section-04 + Deliverable
06.

### 5. Risk management system

Per Deliverable 02 (Art. 9 RMS document),
summarised here.

11 risks identified; 9 with explicit treatment
plans; 4 residuals named as material. Bias
treatment uses equalized odds as the primary
fairness conception. RMS operates monthly (AI
Risk Council) and quarterly (Clinical Advisory
Board).

**Where to find it:** TF/Section-05 + Deliverable
02.

### 6. Validation and testing

KH-AI-027 was validated against held-out test
data (~3,200 images, 14-site spread, not
overlapping with training or validation sets).
Validation includes: overall
sensitivity/specificity per intended-use
population; subgroup performance across the
four bias dimensions per Deliverable 03;
calibration evaluation; software-side robustness
testing.

Cross-validation performed with 5-fold approach
during training; final test set held entirely
separate per test/train discipline.

**Where to find it:** TF/Section-06 — full
validation protocol, ~25 pages.

### 7. Cybersecurity measures

Threat model addresses: input integrity
(adversarial inputs to classification);
infrastructure security (deployment environment
hardening); audit log integrity (tamper-evident
logging); model integrity (version control on
the deployed model).

Per Deliverable 02 risk 9 (adversarial inputs),
controls include input-quality validation prior
to classification and confidence-score
thresholding.

**Where to find it:** TF/Section-07.

### 8. Quality management system

Kerridge operates a QMS per ISO 13485 (medical
device) augmented with ISO/IEC 42001 (AI
management system) requirements. The AI-
specific elements include: AI risk management
(RMS per Section 5); data governance (per
Section 3); AI-aware change management; AI
incident response (per Deliverable 07).

QMS responsibilities matrix names: CMO
(clinical safety); CAIRO (AI governance);
Algorithm Quality Office (clinical validation);
CISO (cybersecurity); Data Protection Officer
(privacy).

**Where to find it:** TF/Section-08.

### 9. Standards and conformity assessment

Harmonised standards applied: ISO/IEC 42001;
ISO/IEC 23894 (AI risk management); IEC 62304
(medical device software lifecycle); IEC 82304
(health software); ISO 13485 (medical device
QMS).

Where harmonised standards do not cover, named
alternatives include: NIST AI RMF for risk
framing; equalized-odds methodology for
fairness; statistical practice for sample size.

Conformity assessment route: Annex VII third-
party. Notified Body: [NAMED IN FINAL FILING].

**Where to find it:** TF/Section-09.

### 10. Declaration of conformity

Per Annex V. Includes provider details;
intended purpose; harmonised standards applied;
notified body identification; signature of
authorised representative.

**Where to find it:** TF/Section-10.

### 11. Instructions for use

Per Art. 13. Operating instructions provided
to deployers cover: intended use and validated
population; system performance per Section 6;
known limitations including the three honest
data gaps per Section 3; required workflow
constraints (asymmetric escalation per
Deliverable 05); reporting obligations of
deployers per Art. 26.

**Where to find it:** TF/Section-11.

---

## 3. Reasoning notes

- **Why a navigable summary rather than the
  full file in this deliverable.** The
  technical file's size (~85 pages) does not
  belong in a comparative deliverable.
  Notified Body engagement gets the full
  file; this summary serves the reading-guide
  function plus the cross-reference role.
- **Why the explicit cross-references.** Both
  the Notified Body and competent authorities
  prefer navigable documentation. Buried
  content reads as either disorganization or
  evasion.
- **Why I named the QMS responsibilities
  matrix explicitly here.** Notified Body
  scrutiny of medical-AI QMS focuses on AI-
  specific role assignment. Naming the matrix
  pre-empts the question.
- **What this summary deliberately under-
  specifies.** Detailed model architecture
  (TF/02); full validation test plan (TF/06);
  configuration management procedures. These
  live in the full file because they reward
  depth, not navigability.

---

Maintained by [Girish Nair](https://github.com/garynair)
