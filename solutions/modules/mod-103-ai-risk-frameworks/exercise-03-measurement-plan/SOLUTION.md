# Exercise 03 — Measurement Plan — Reference Solution

## 1. Solution overview

This reference is a 2-page measurement plan for **Tessera
Bank's small-business loan-decisioning system**. Each of
the six risks has a leading and a lagging indicator with
defined absolute thresholds, owned responses, and named
eval-set provenance. One indicator (third-party aggregator
reliability) is cross-cutting and is called out separately.

---

## 2. The plan

> **Measurement Plan — Tessera Bank**
> *System:* TB-AI-007 — Small-business loan-decisioning workbench
> *Owner of plan:* AI Risk Lead, with model-owner concurrence
> *Cadence of plan review:* quarterly + on material change

### Risk 1 — Performance (model recommendation accuracy)

**Leading indicator:** KS-statistic on input feature
distribution, daily.
- Data source: streaming feature pipeline.
- Threshold: KS p < 0.01 on any single feature against
  the training reference distribution.
- Response: Model Owner investigates within 5 business
  days; if drift confirmed material, AI Review Board
  notified within 10 business days.
- Owner: Model Owner.

**Lagging indicator:** Recommendation precision on the
30-day post-decision outcome set.
- Data source: outcome-labeled batch.
- Threshold: precision < 0.83 in any rolling 30-day
  window (absolute threshold; baseline at pilot close
  was 0.89).
- Response: AI Review Board reviews; model considered
  for retraining or pause.
- Owner: Model Owner.

### Risk 2 — Bias and fairness

**Leading indicator:** Demographic parity gap on the
*proposed* recommendations stratified by underwriter-
inferred customer cohort.
- Data source: monthly stratified batch.
- Threshold: > 4 percentage-point gap between any two
  cohort groups in recommendation *positive rate*
  (absolute threshold; benchmark of 4pp picked from CO
  Reg 10-1-1 industry-norm proxies).
- Response: Head of Fair Lending convenes review within
  5 business days; if confirmed, pause + investigation.
- Owner: Head of Fair Lending.

**Lagging indicator:** Disparate-impact ratio on
*actual* underwriting outcomes (after underwriter
decision) quarterly.
- Data source: quarterly fair-lending analysis.
- Threshold: 4/5 rule violation in any
  protected-class group.
- Response: GC + Compliance review; potential
  fair-lending corrective action plan.
- Owner: Head of Fair Lending.

### Risk 3 — Transparency

**Leading indicator:** Fraction of recommendations
where the top-3 SHAP feature contributions are
human-interpretable per a pre-defined glossary.
- Data source: nightly explainer over model decisions.
- Threshold: < 90% interpretable in any rolling 7-day
  window.
- Response: Model Owner reviews opaque cases; opaque-
  case patterns escalated to AI Review Board.
- Owner: Model Owner.

**Lagging indicator:** Number of adverse-action notices
that failed to satisfy Reg B's "specific reasons"
requirement on independent legal review.
- Data source: sampled monthly legal review.
- Threshold: > 0 per month.
- Response: Immediate corrective notice; pattern
  surfaced to GC + CAIRO.
- Owner: GC.

### Risk 4 — Privacy and data

**Leading indicator:** Number of cash-flow-aggregator
calls whose payload exceeds the documented data-minimization
schema.
- Data source: aggregator-API logging (Tessera-side).
- Threshold: > 0.
- Response: Vendor Risk Lead investigates within 3
  business days; aggregator notified.
- Owner: Vendor Risk Lead.

**Lagging indicator:** Number of customer privacy
complaints attributable to the system (per quarter).
- Data source: customer complaints register.
- Threshold: > 1 / quarter.
- Response: Privacy office investigation; pattern
  surfaced to AI Risk Council.
- Owner: Chief Privacy Officer.

### Risk 5 — Operational (third-party aggregator dependency)

**Leading indicator:** Aggregator API success rate
(rolling 1-hour window).
- Data source: aggregator API monitoring.
- Threshold: < 99.5% success rate sustained for >
  15 minutes.
- Response: Operational fallback engaged (degrade to
  underwriter-only mode); Model Owner notified; Vendor
  Risk Lead notified within 24h.
- Owner: SRE on-call + Model Owner.

**Lagging indicator:** Number of underwriting decisions
delayed by aggregator unavailability (per month).
- Data source: workflow logs.
- Threshold: > 50 / month.
- Response: AI Review Board reviews; vendor-redundancy
  evaluation if pattern persists.
- Owner: Head of Underwriting.

### Risk 6 — Compliance (fair-lending continuous demonstrability)

**Leading indicator:** Fair-lending evidence-package
*currency* — days since last evidence-package update.
- Data source: AI compliance dashboard.
- Threshold: > 35 days.
- Response: Compliance team produces updated package;
  pattern surfaced to CAIRO.
- Owner: Head of Fair Lending + Compliance Lead.

**Lagging indicator:** Fair-lending regulator inquiry
turnaround time (when an inquiry arrives).
- Data source: legal docket.
- Threshold: > 10 business days to first substantive
  response.
- Response: Internal review of fair-lending evidence
  pipeline; CAIRO + GC.
- Owner: GC.

### Plan-level

**Dashboard design.**

- *Model Owner dashboard* (daily): leading indicators
  for Risks 1, 3, 5 + lagging for Risk 1.
- *AI Risk Council deck* (monthly): all leading + all
  lagging, plus current threshold status.
- *Board Risk Committee report* (quarterly): rolled-up
  threshold-crossing counts per risk category +
  significant events.

**Eval-set inventory.**

| Eval set | Purpose | Provenance | Refresh cadence |
|---|---|---|---|
| TB-EVAL-LOAN-30D | Risk 1 lagging — 30-day outcomes | Production-decision sample | rolling 30 days |
| TB-EVAL-FAIR-Q | Risk 2 lagging — disparate-impact | Quarterly stratified random sample | quarterly |
| TB-EVAL-EXPLAIN-WK | Risk 3 leading — interpretability | Decision-batch sample | weekly |
| TB-EVAL-PRIVACY-Q | Risk 4 lagging — privacy complaint context | Customer-service tickets | quarterly |

All eval sets are documented with curation methodology;
contamination check is run quarterly against the
training set.

**Cross-cutting concerns.**

- The aggregator dependency (Risk 5) cuts across Risk 4
  (privacy of aggregator data). One incident in the
  aggregator may surface evidence in both. The
  AI Risk Lead is responsible for maintaining a single
  view of aggregator events across both risks.
- The fair-lending package currency (Risk 6 leading) is
  driven by Risk 2 lagging output. Stale Risk 2
  evaluations automatically degrade Risk 6 readiness.

---

## 3. Reasoning notes

- **Why the bias leading indicator is set at 4pp
  *absolute*.** Defining bias thresholds is the hardest
  call in any AI program. The reference picks 4pp based
  on the CO Reg 10-1-1 industry-norm proxies — explicitly
  citing an external anchor protects the threshold from
  motivated drift. A defensible alternative would set it
  at 5pp (slightly more permissive) or 2pp (more
  conservative). The point is *justifying the absolute
  threshold against an external anchor*, not the
  specific number.
- **Why "KS-statistic" for the performance leading
  indicator.** A simple statistical test on feature
  distribution drift is the canonical leading indicator
  for performance. Setting p < 0.01 is conventional but
  aggressive; p < 0.001 would be more conservative.
  The reference picks 0.01 because of the volume of
  features being tested (multiple-testing-corrected
  thresholds get aggressive faster than expected).
- **Why the aggregator success-rate window is short.**
  15-minute sustained-failure threshold matches the
  underwriting workflow's tolerance — most decisions can
  wait 15 minutes; sustained outages beyond that produce
  customer-experience harm.
- **Why Risk 6's leading indicator is "days since update"
  rather than a model metric.** Compliance demonstrability
  is fundamentally a *process* property, not a model
  property. The leading indicator measures the *process*
  is on cadence, which is what predicts the lagging
  indicator (regulator response time).
- **What the next iteration should add.** A meta-
  indicator: the *fraction of thresholds crossed in the
  last quarter that produced the documented response.*
  This is the §4.5 dashboard discipline check; the
  reference omits it for length but it is the highest-
  leverage addition.

---

Maintained by [Girish Nair](https://github.com/garynair)
