# Exercise 02 — Define Bias Metrics for a Specific Context — Reference Solution

## 1. Solution overview

For **Cardinal Health Network's sepsis-prediction CDSS**,
the reference adopts **equalized odds** (matched
sensitivity AND specificity across protected subgroups)
as the central metric, supplemented by **demographic
calibration** (matched calibration curves). The
impossibility result is explicit: predictive parity is
*not* enforced, because clinical-safety arguments
require false-negative-rate parity, which conflicts
with predictive parity in any context with unequal base
rates.

---

## 2. The specification

> **Cardinal Health Network — Bias Metric Specification**
> *System: Adult-ICU sepsis-prediction CDSS (in development)*
> *Tier: 1 (Critical, per Cardinal's Algorithm Quality
> Office tiering)*
> *Authored by: CAIRO function in consultation with
> Chief Medical Officer and Chief Quality Officer*

### Section 1 — Protected populations

| Population dimension | Data source | Notes on availability |
|---|---|---|
| Race and ethnicity | Self-reported in EHR demographics; ~88% completeness | Missing data common; sub-population sizes for some categories small |
| Sex (recorded biological sex) | EHR demographics; ~99% completeness | Distinguish from gender; both relevant but reported differently |
| Age strata | EHR demographics; ~100% completeness | Stratify: 18–44, 45–64, 65–79, ≥ 80 |
| Language of presentation | EHR primary-language field + chart context; ~70% completeness | Proxy where unrecorded |
| Insurance status | EHR + billing data; ~99% completeness | Included because it correlates with care patterns; necessary covariate for honest analysis |

Honest acknowledgment: race / ethnicity self-report
completeness creates a measurement floor on disparity
analysis. Stratification by missing-vs-reported is
included.

### Section 2 — The metric set

**Metric 1 — Equalized odds (central metric).**

Definition for sepsis prediction:

- **Sensitivity** = P(score ≥ 0.7 | true sepsis within 6h),
  computed per protected subgroup.
- **Specificity** = P(score < 0.7 | not sepsis within 6h),
  computed per protected subgroup.

The system satisfies equalized odds at a subgroup pair
(A, B) when *both* the sensitivity gap and the
specificity gap are within their respective thresholds.

**Threshold for sensitivity gap:** ≤ 3 percentage points
between any two protected subgroups. Sensitivity
disparity is patient-safety-critical: under-detection of
sepsis in any subgroup is direct harm.

**Threshold for specificity gap:** ≤ 5 percentage
points between any two protected subgroups. Specificity
disparity is operationally important (alert fatigue,
clinical workflow burden) but lower-severity than
sensitivity.

**Response when threshold is crossed:**

- *Sensitivity gap > 3pp:* Algorithm Quality Office
  convenes urgent review within 24 hours; Chief Medical
  Officer notified; deployment paused at affected sites
  pending review.
- *Specificity gap > 5pp:* AI Review Board reviews at
  next scheduled meeting; Clinical Quality Council
  consulted; affected-subgroup pattern documented;
  pause not automatic but available as a treatment
  option.

**Owner:** Algorithm Quality Office's Clinical Validation
Lead.

**Metric 2 — Demographic calibration (secondary).**

Definition: for each protected subgroup, plot the
predicted probability of sepsis vs. the empirical
probability of sepsis (calibration curve). The system
satisfies demographic calibration when the calibration
curves across subgroups do not differ by more than 5%
in any decile.

**Threshold:** Calibration curves diverging by > 5% in
any decile triggers AI Review Board review.

**Response:** Investigation of why calibration differs;
potential subgroup-specific re-calibration during
deployment.

**Owner:** Algorithm Quality Office.

### Section 3 — The trade-off analysis

#### The impossibility result and our position

The Chouldechova / Kleinberg impossibility result is
explicit: with unequal base rates of sepsis across
protected subgroups (which is documented in clinical
epidemiology — sepsis incidence varies by age and by
several other dimensions), we cannot simultaneously
satisfy:

(i) **Predictive parity** — equal positive predictive
    value (precision) across subgroups
(ii) **Equal false-positive rates** (component of
     equalized odds)
(iii) **Equal false-negative rates** (component of
      equalized odds)

Our chosen metric set satisfies (ii) and (iii) — the
two components of equalized odds. It does **not** satisfy
predictive parity (i).

The operational implication: at a given alert threshold,
the *precision* of "score ≥ 0.7" — meaning the fraction
of alerts that turn out to be true sepsis — will be
different across subgroups. Subgroups with higher
true-sepsis base rates will have higher alert precision;
subgroups with lower base rates will have lower alert
precision.

This is a real consequence the program accepts.

#### The clinical-safety argument

False-negative-rate parity is non-negotiable for
sepsis prediction. Under-detection of sepsis in any
subgroup is direct patient harm — the system's reason
to exist is timely detection. A patient missed because
their subgroup has a worse sensitivity is a clinical-
safety failure, not a fairness question.

False-positive-rate parity matters for the same reason
but lower-severity: clinical-workflow burden affects
care quality across the system. The 5pp threshold (vs.
3pp for sensitivity) reflects the asymmetry.

Predictive parity is *desirable* but not the highest
priority. Subgroups with different base rates will
necessarily have different alert precision when
sensitivity is matched; clinicians manage this by
incorporating subgroup-base-rate context in clinical
interpretation of alerts. (Cardinal's clinical-
education materials for the system explicitly cover
this.)

#### The fairness argument

Equalized odds satisfies a specific fairness
conception: *every patient, regardless of subgroup,
has the same probability of being correctly identified
when they have sepsis, and the same probability of
being correctly not-flagged when they do not.*

This is the fairness conception that *clinical patient
care* most clearly maps onto. Other fairness conceptions
(predictive parity, demographic parity) are also
legitimate but center different concerns
(communication of risk; group representation in alerts).
Equalized odds centers the clinical event, which is the
right center for sepsis prediction.

We document that we are *not* enforcing predictive
parity. A program that claims to enforce all fairness
conceptions simultaneously is wrong; we explicitly do
not.

#### Defensibility statement (for CMO regulator use)

> *Cardinal's sepsis-prediction CDSS is monitored for
> equalized odds across protected populations —
> sensitivity and specificity are matched across race,
> ethnicity, sex, age strata, language of presentation,
> and insurance status, within bounded thresholds.
> Sensitivity parity is held to a 3-percentage-point
> threshold because under-detection of sepsis in any
> subgroup is a direct patient-safety concern.
> Predictive parity — equal positive predictive value
> across subgroups — is not separately enforced; this
> is a deliberate choice grounded in the mathematical
> result that predictive parity and equalized-odds
> cannot be simultaneously satisfied where base rates
> differ, and in clinical reasoning that
> sensitivity-parity better serves patient outcomes.
> The trade-off is documented in the algorithm's
> validation file and is reviewed annually by the
> Clinical Quality Council.*

### Section 4 — Subgroup discovery

Beyond the pre-specified protected populations, the
specification requires:

- **Slice-finding analysis** using open-source slice-
  finding tools (e.g., SliceFinder) on a quarterly
  basis. Output: subgroups (defined by feature-value
  combinations) where the system's performance deviates
  meaningfully from overall. Limitation: identifies
  statistically-significant slices but does not
  distinguish ethically-meaningful from
  ethically-trivial subgroups.
- **Clinical-population stratification review** —
  Cardinal's clinicians review the system's behaviour
  against clinically-meaningful population groupings
  (immunocompromised patients, recently-discharged
  patients, etc.) annually. Limitation: clinician
  attention is limited; not all clinically-meaningful
  subgroups will be reviewed.

Both methods are required; their findings are merged
into the analysis space.

---

## 3. Reasoning notes

- **Why equalized odds, not predictive parity.** Both
  are defensible for clinical-decision-support tools.
  The reference picks equalized odds because of the
  clinical-safety argument. A clinically-defensible
  alternative would be to add a predictive-parity
  component for the rapid-response-team-paging
  threshold (0.85) specifically, because false-positive
  rapid-response activations have operational and
  patient-experience consequences. The reference
  considered this and decided the 5pp specificity
  threshold sufficiently addresses it without adding
  metric-set complexity.
- **Why a 3pp threshold and not 5pp.** Sensitivity
  parity for a Tier 1 patient-safety system must be
  tight. Lower thresholds would be defensible (1pp,
  2pp) but practically may produce constant threshold
  crossings due to sampling variation in small
  subgroups. 3pp is the operationally tight value that
  signal-distinguishes from noise. Calibration to this
  threshold should be reviewed after the first six
  months of monitoring.
- **Why insurance status is included.** Insurance
  status correlates with care patterns, treatment
  intensity, and length-of-stay — all of which
  potentially affect sepsis-prediction model outputs.
  Including it as a covariate in the analysis is
  necessary for honest disparity assessment; excluding
  it makes the analysis less interpretable.
- **The hardest decision.** Whether to enforce
  sensitivity parity at the rapid-response-team
  threshold (0.85) at all. The case for *not* enforcing
  is that very high scores represent a clinically
  unambiguous signal and the model's behaviour at the
  extreme tail may be unstable. The case for enforcing
  is that the rapid-response page is the most
  consequential action and disparity here has the
  largest harm. The reference enforces both threshold's
  sensitivity but acknowledges potential measurement
  noise at the 0.85 threshold.
- **What this specification deliberately under-
  specifies.** The intersectional analysis (e.g.,
  *elderly + non-English-speaking* as a combined
  subgroup). Subgroup-discovery analysis surfaces
  combinations but intersectional analysis of pre-
  specified protected populations is omitted for one-
  page discipline. A v2 of the specification should
  add it explicitly.
- **What I would do differently next iteration.** Add
  an explicit *handoff-to-clinician* metric — when an
  alert fires, what fraction of cases the clinician
  acts on (clinical-acceptance rate). Disparity in
  clinical-acceptance rate by subgroup is a separate
  bias surface from model output disparity and may
  reveal patterns the model alone does not show.

---

Maintained by [Girish Nair](https://github.com/garynair)
