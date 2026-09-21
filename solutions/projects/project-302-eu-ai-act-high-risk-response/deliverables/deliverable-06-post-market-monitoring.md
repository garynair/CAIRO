# Deliverable 06 — Article 72 Post-Market Monitoring Plan — Reference Solution

## 1. Solution overview

The PMM plan is a separable artifact (per
mod-102 §2.6) — designed for the EU AI Act
Notified Body but structurally aligned with
EU MDR and FDA post-market surveillance
requirements. Six monitoring streams cover
performance, subgroup performance, calibration
drift, clinician override patterns, deployer
operational signals, serious incidents (cross-
reference to Deliverable 07). Monitoring
operates monthly (operational), quarterly
(advisory board), annually (full review).
Pause/withdraw decision criteria are explicit;
trigger ownership is named.

---

## 2. The PMM plan

### Purpose and scope

This plan defines KH-AI-027 post-market
monitoring per Art. 72. It is the EU AI Act
artifact; equivalent content satisfies EU MDR
PMS obligations and substantively addresses FDA
post-market reporting expectations.

Scope: monitoring KH-AI-027 in all deployer
clinical settings within the EU.

### Six monitoring streams

**Stream 1 — Overall performance.**
Sensitivity and specificity against confirmed
clinical outcomes (referable cases verified by
ophthalmologist; non-referable cases tracked
for downstream confirmation). Monthly
aggregation from deployer-site data export.

**Stream 2 — Subgroup performance.** The four
bias dimensions from Deliverable 03
(ethnicity, age strata, cataract presence,
image quality). Monthly aggregation; trigger
review if any subgroup performance falls
below the validation-set baseline by more
than 3pp for two consecutive months.

**Stream 3 — Calibration drift.** Monitoring
that the confidence-score-to-outcome
relationship matches validation. Quarterly
analysis with explicit gating: re-calibration
warranted if the calibration error exceeds
defined thresholds (per the model card).

**Stream 4 — Clinician override patterns.**
Per-clinician override rates (per Deliverable
05). Site-level override-rate aggregations.
Monthly review. Triggers for low override
rate (automation bias risk) and high override
rate (model performance concern).

**Stream 5 — Deployer operational signals.**
Hardware fundus camera failure rates;
software stability metrics; image-quality
distribution at deployer sites; clinician
training completion rates.

**Stream 6 — Serious incidents.** Cross-
reference to Deliverable 07. Serious
incidents are reported to the relevant
authorities per Art. 73; the PMM plan
maintains the integrated picture.

### Cadence

- **Operational (monthly).** Algorithm Quality
  Office and Clinical Validation Lead review
  Streams 1, 2, 4, 5. Outputs: monitoring
  scorecard.
- **Advisory board (quarterly).** Clinical
  Advisory Board reviews integrated picture
  across all six streams; reviews calibration
  (Stream 3). Outputs: quarterly
  recommendations.
- **Provider-level (annually).** Full PMM
  review by AI Risk Council. Outputs:
  technical-file refresh; risk-register
  update; PMM plan update.

### Pause / withdraw criteria

Three escalation tiers:

**Tier 1 — Stream-level investigation.** Any
single stream metric breaches a defined
warning threshold. Algorithm Quality Office
investigates within 5 business days.

**Tier 2 — Site-level pause.** Site-level
performance deteriorates below the validated
performance threshold; or site-level subgroup
performance deteriorates materially. The
clinical-quality lead at the site, supported
by the Algorithm Quality Office, can pause
KH-AI-027 use at that site pending
investigation.

**Tier 3 — Provider-level withdrawal.** Per-
site investigations escalate to provider-
level if the underlying cause is system-side
rather than site-specific. The CAIRO, with CMO
concurrence, can pause KH-AI-027 operation
across all deployer sites and trigger
incident reporting per Deliverable 07.

### Reporting flow

- Internal: monthly scorecard → quarterly
  advisory board report → annual full review.
- External: Art. 72 reporting to relevant
  competent authorities per the defined
  cadence (annual report at minimum;
  immediate reporting for serious incidents
  per Deliverable 07); EU MDR PMS reporting
  in parallel; FDA post-market reporting via
  the relevant pathway.

### Data sources and quality

KH-AI-027 deployer sites provide structured
data export via secure authenticated
endpoint. Data quality is monitored via
completeness checks (% of cases reported);
deployer-side data quality is the deployer's
responsibility per the operating instructions.

### Resourcing

PMM execution is owned by the Algorithm
Quality Office Clinical Validation Lead with
3 FTE supporting (data analyst, clinical
quality specialist, regulatory affairs liaison
to Compliance). Quarterly Clinical Advisory
Board engagement is contracted with external
clinical experts.

---

## 3. Reasoning notes

- **Why six streams rather than the EU MDR
  PMS-standard three.** KH-AI-027 is novel
  enough that subgroup performance and
  override-rate monitoring deserve their own
  streams. Folding them into "overall
  performance" would obscure the specific
  failure modes the system is most exposed
  to.
- **Why explicit thresholds (3pp for subgroup;
  10% for override rate).** Specific
  thresholds defensible against the
  alternative (vague "we will monitor").
  Specific thresholds can be challenged
  substantively; vague ones evade scrutiny
  while providing no actual discipline.
- **Why the tier-3 pause/withdraw authority
  rests jointly with CAIRO + CMO concurrence.**
  Either alone would be one-sided: CAIRO
  alone misses clinical-safety nuance; CMO
  alone misses AI-system-specific
  judgement. Joint concurrence is the right
  posture.
- **Why this PMM plan is structurally aligned
  with MDR PMS and FDA post-market.** mod-102
  §2.6 separable-artifact principle: build
  for the strictest regime, use across the
  others. Substantially reduces total
  reporting burden vs. parallel separate
  monitoring programs.
- **What this PMM plan deliberately doesn't
  include.** Real-time monitoring dashboards
  for end-users (would be premature for a
  first deployment); A/B testing of model
  variants in production (clinical safety
  precludes); customer-side custom
  thresholds (operational discipline favors
  uniform thresholds).

---

Maintained by [Girish Nair](https://github.com/garynair)
