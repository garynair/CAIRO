# Deliverable 05 — Ongoing Monitoring Framework — Reference Solution

## 1. Solution overview

Six monitoring streams (data quality, output
distribution, performance, subgroup
performance, operational, material change).
First-line execution by business-line model
owners; second-line independent review by
MRM. Thresholds set per-model with documented
methodology; breaches escalate through three
tiers (investigation, pause, revalidation).
Worked example: how this framework would have
caught the wealth-management retrain
degradation in week 1 rather than week 3.

---

## 2. The framework

### Six monitoring streams per tier

| Stream | Tier-1 cadence | Tier-2 | Tier-3 |
|---|---|---|---|
| Input data quality / distribution | Real-time auto + daily review | Daily auto + weekly review | Weekly auto + monthly review |
| Output prediction distribution | Daily auto + weekly review | Weekly auto + monthly review | Monthly review |
| Performance vs. ground truth | Daily where available + monthly trend | Weekly + quarterly trend | Quarterly |
| Subgroup performance | Monthly | Quarterly | Annual |
| Operational (latency, availability) | Real-time | Real-time | Real-time |
| Material-change detection | Continuous (CI gate) | Continuous | Continuous |

### Stream-specific design

**Stream 1 — Input data quality and
distribution.**

- Schema and type checks (does the input
  match what the model was trained on).
- Distribution comparison to training-set
  distribution (PSI, KL divergence per
  feature).
- Missingness rates per feature.
- Outlier rates.

Threshold examples: PSI >0.2 on any tier-1
feature flags warning; PSI >0.3 flags
critical.

**Stream 2 — Output prediction distribution.**

- Distribution of predicted scores or
  classifications.
- Comparison to baseline (training-set
  output distribution; recent rolling
  baseline).
- Confidence score distribution if
  applicable.

Threshold examples: prediction-distribution
shift >2σ from baseline rolling-window
flags warning.

**Stream 3 — Performance vs. ground truth.**

- Where ground truth is observable: standard
  metrics (precision, recall, AUC, calibration).
- Where ground truth is delayed: time-lagged
  performance tracking.
- Where ground truth is partial: proxy
  outcomes per Deliverable 04.

Threshold examples: AUC drop >5% from
validation baseline flags warning; >10%
flags critical.

**Stream 4 — Subgroup performance.**

- Per the bias dimensions identified in
  validation per Deliverable 04.
- Performance metric per subgroup vs.
  overall.
- Specifically: differential performance
  trends (subgroup A degrading faster than
  subgroup B).

Threshold examples: subgroup performance
gap widening >3pp over baseline flags
warning.

**Stream 5 — Operational signals.**

- Latency, availability, error rates.
- Resource consumption.
- Integration-layer signals.

Threshold examples: availability <99.9%
for tier-1, <99% for tier-2 flags warning.

**Stream 6 — Material change detection.**

- Detection of any change to: training data,
  model parameters, software stack, input
  schema, output use.
- Continuous CI gate; changes flagged for
  MRM review per Deliverable 04 re-validation
  triggers.

### Roles

**First-line (business-line model owner).**
- Owns the monitoring stream operation.
- Reviews monitoring scorecards per cadence.
- Escalates per the escalation framework.
- Maintains monitoring documentation.

**Second-line (MRM).**
- Independent review of monitoring outputs.
- Validates that monitoring is actually
  operating (the wealth-management failure
  pattern was a monitoring-not-operating
  pattern).
- Triggers re-validation per Deliverable 04.

**CAIRO oversight.**
- Reviews aggregate monitoring picture for
  AI-specific concerns.
- Reports to Board per Deliverable 06.

### Thresholds methodology

Per-model thresholds set at validation time
and revised per re-validation. Methodology:

- Initial thresholds derived from training
  / validation variation (3σ rule by
  default; tighter for tier-1 where
  appropriate).
- Threshold review at re-validation; can
  be tightened or relaxed with reasoning.
- Threshold changes go through change
  control (material-change detection).

### Escalation paths

**Tier-A — Warning breach.** Business-line
model owner investigates within 5 business
days; reports to MRM. No automatic action.

**Tier-B — Critical breach or repeated
warnings.** Model owner pauses model use
pending investigation OR continues with
documented residual risk acceptance.
Decision requires MRM concurrence. Risk
Committee notified.

**Tier-C — Systemic breach (multiple
streams or subgroup-specific harm).**
Mandatory pause. Investigation per
mod-110 systemic-cause discipline. Risk
Committee notified within 48 hours.
Potential customer notification per
incident-response procedures.

### Re-validation triggers from monitoring

- Three consecutive tier-A warnings on a
  single stream.
- One tier-B critical breach.
- Material change to the model.
- Subgroup performance gap widening
  sustained over two review cycles.
- 12 months since last validation (annual
  trigger).

### Worked example — Wealth-management
rebalancing degradation

Given the failure pattern from Finding 2:
the model was retrained 3 weeks ago without
pre/post performance comparison; production
performance has degraded.

**How this framework would have caught it
earlier.**

- **Stream 6 (material-change detection)**
  would have triggered MRM review at the
  retrain. MRM concurrence on the retrain
  would have been required before
  deployment per the change-management
  gate; the pre/post comparison would have
  been required by the methodology. The
  retrain would not have deployed without
  this evidence.
- **Stream 3 (performance vs. ground truth)**
  would have flagged AUC drop or proxy
  outcome degradation within the first
  week of deployment.
- **Stream 4 (subgroup performance)** would
  have flagged if degradation was
  concentrated in particular client
  segments.

**Forward correction.** Going forward, the
rebalancing model is Tier-1 per the
tiering framework; full monitoring stack is
in place; the retrain failure cause (the
post-launch validation gate was not
operating after the latest training data
refresh) is the systemic cause per
mod-110 Ex-01 pattern. Systemic correction:
the change-management gate must execute
even when the change is a retrain (not
just architecture changes); MRM has been
brought in to audit the gate operation
weekly for the next quarter.

### Vendor-model monitoring

Vendor models pose specific challenges:
- Tessera does not control model parameters
  or retraining cadence.
- Vendor may not disclose model changes.
- Performance monitoring must rely on
  Tessera-observable inputs and outputs.

Framework approach:
- Vendor contracts require notification of
  material model changes (Stream 6
  surrogate).
- Tessera-side monitoring of Streams 1, 2,
  3, 4 from input/output flows operates
  regardless.
- Vendor-side disclosed monitoring is a
  supplement, not a substitute.

### Phased capability buildout

Honest acknowledgment: not all 42 models
have the full monitoring stack on Day 90.
The capability buildout sequencing:

- **Days 0-90:** Streams 1, 2, 5, 6 for all
  Tier-1 and Tier-2 models. Stream 3 for
  Tier-1 where ground truth is available.
- **Days 91-180 (Q1):** Stream 3 for
  remaining Tier-1 and Tier-2 (with proxy
  outcomes documented); Stream 4 for all
  Tier-1.
- **Days 181-365 (full year):** Stream 4
  for Tier-2; full capability for Tier-3.

### Inputs to Board reporting

The monitoring framework feeds the Q4 board
package (Deliverable 06) via:
- Aggregate monitoring scorecard.
- Stream-specific breach summary.
- Material-change activity.
- Subgroup performance trends.

---

## 3. Reasoning notes

- **Why six streams rather than fewer.**
  Each stream catches a distinct failure
  pattern. Folding them produces opacity
  about which type of issue is actually
  present.
- **Why the change-management gate is
  separate (Stream 6).** The wealth-
  management failure (Finding 2) was a
  change-management failure, not a
  performance failure. Without a separate
  stream, the change-management failure
  mode is invisible until performance
  degrades — which is downstream and
  slower.
- **Why phased buildout is named honestly.**
  Programs that claim full monitoring on
  Day 1 invite Audit and OCC scrutiny on
  the gap between claim and reality.
  Phased buildout with named timelines is
  the defensible posture.
- **Why vendor-model monitoring is explicit
  about its limits.** Same logic as
  Deliverable 04 vendor validation
  discussion. Pretending to monitor what
  cannot be monitored is worse than
  documenting the asymmetry.
- **Why the worked wealth-management
  example.** The Risk Committee will read
  this framework with the wealth-management
  incident on their minds. The worked
  example demonstrates the framework is
  designed against actual Tessera failure
  modes, not generic best practice.
- **What I would do differently.** Threshold
  methodology might benefit from per-tier
  default thresholds (rather than per-
  model) to reduce validator burden. The
  trade-off: per-model thresholds are more
  defensible but more work. Defensibility
  won here.

---

Maintained by [Girish Nair](https://github.com/garynair)
