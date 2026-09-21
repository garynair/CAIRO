# Exercise 04 — Risk-Treatment Plan — Reference Solution

## 1. Solution overview

A one-page treatment plan for **Aldwych Health's ED triage
support tool v2**, addressing the demographic-bias-in-
elderly-patients risk. Residual risk is named explicitly
as *Material* and accepted by the AI Risk Council with a
6-month re-evaluation. The plan refuses the temptation to
declare the risk fully mitigated post-rebuild.

---

## 2. The treatment plan

> **Risk Treatment Plan — Aldwych Health**
> *System:* AH-AI-019 — ED Triage Support Tool v2
> *Risk being treated:* Demographic bias in triage
> suggestions, specific to elderly patients (≥ 70)
> *Drafted:* [date]. *Approved:* [date].

### Risk description

The v1 system systematically under-ranked elderly
patients' acuity, contributing to a publicly-reported
incident in 2025. The v2 rebuild applied design-time
mitigations (subgroup oversampling, site-specific
calibration, asymmetric escalation-only workflow). Residual
bias risk remains until monitoring evidence demonstrates
the mitigations hold in production.

**Risk category:** Bias and fairness (taxonomy §2.2; see
mod-101 Exercise 03 reference for the Aldwych
adapted-taxonomy variant).

**Unmitigated likelihood × severity:** **High × High.**
Basis: the v1 incident is direct empirical evidence of
the unmitigated state.

### Controls applied

| # | Control | Catalog reference | Lifecycle | Confirmatory leading indicator |
|---|---|---|---|---|
| C1 | Training-set augmentation with oversampling on under-represented elderly subpopulations | Bias/Pre-deployment/Data-representativeness | Pre-deployment | (one-time pre-deployment) Subgroup-representation report |
| C2 | Site-specific calibration during deployment ramp-up | Bias/Deployment/Calibration | Deployment | (per-site) Calibration-curve agreement per site |
| C3 | Asymmetric escalation-only workflow (AI can suggest escalating ESI, never de-escalating) | Bias+Performance/Deployment/Workflow constraint | Deployment | (continuous) Workflow-constraint adherence (deterministic, audit only) |
| C4 | Monthly demographic-stratified monitoring | Bias/Post-deployment/Monitoring | Post-deployment | Demographic-parity gap on suggestion patterns (from measurement plan) |
| C5 | Per-site pause threshold — single-site divergence > 10pp triggers pause pending Clinical Safety Officer review | Bias/Post-deployment/Trigger | Post-deployment | Pause-trigger rate (target zero; non-zero is informative) |
| C6 | Nurse-level override-rate tracking with retraining trigger if any nurse's override rate falls below 10% | Bias+Workflow capture/Post-deployment/Monitoring | Post-deployment | Override-rate distribution across nurses |

### Residual likelihood × severity

**Material × High → Residual Material.**

Basis: design-time controls (C1–C3) provide bounded
protection. Post-deployment monitoring (C4–C6) detects
recurrence but does not prevent it. The residual is the
window between a bias pattern beginning and the monitoring
threshold being crossed.

The residual is *strictly lower* than unmitigated (the v1
state) because (a) the asymmetric-escalation workflow
prevents the specific failure mode of de-escalating
elderly acuity that drove the v1 incident, and (b) the
post-deployment monitoring would catch a recurrence within
one monthly cycle rather than after public disclosure.

### Residual risk acceptance

- **Accepted by:** AI Risk Council (Chair: CRO).
- **Date of acceptance:** [date].
- **Basis:** The residual is the lowest achievable given
  current technology and operating model. Further
  reduction would require either (a) a different model
  architecture not yet evaluated, or (b) per-nurse
  closed-loop training that has been deferred to a
  later program iteration. The Council judges the
  residual acceptable for a six-month observation
  period.
- **Conditions of acceptance:** Residual returns for
  re-evaluation if any of the re-evaluation triggers
  below fires *or* on the 6-month review.

### Re-evaluation triggers (any of these forces a review)

1. **Pause-trigger fires at any site** (single-site
   divergence > 10pp on a single demographic). This
   triggers immediate Clinical Safety Officer review
   *and* AI Risk Council re-evaluation of this plan
   within 10 business days.
2. **Demographic-parity gap > 5pp at two consecutive
   monthly cycles at any site** — triggers AI Risk
   Council re-evaluation within 30 days.
3. **Nurse-level override rate < 10% for any nurse on
   sustained basis (3 months)** — triggers workflow-
   capture review; treatment plan re-evaluated for
   adequacy.
4. **Material model update** (training data refresh,
   architecture change, calibration re-fit) — triggers
   full re-evaluation regardless of prior trigger
   history.
5. **6-month scheduled review** — Council re-evaluates
   based on monitoring evidence accumulated.

### Exception status

**Not an exception.** This treatment fits within the
program's standard pattern for high-risk-system bias
treatment: design-time mitigation + workflow constraint +
post-deployment monitoring + named residual acceptance.

---

## 3. Reasoning notes

- **Why I refused "fully mitigated".** The v1 incident is
  on the public record. A treatment plan that claimed the
  v2 rebuild had fully mitigated the risk would be both
  implausible to the regulator and dishonest to the AI
  Risk Council. Naming the residual as *Material* is the
  honest position. It is also the position that survives
  external scrutiny.
- **Why six controls and not three.** The temptation in
  treatment plans is to consolidate ("we have monitoring
  and workflow constraint, that's enough"). The reference
  names the controls separately because each carries a
  separate failure mode if removed — removing C3
  (asymmetric workflow) eliminates the bounded protection
  even if monitoring remains, for instance. The granular
  naming protects against silent control degradation.
- **Why C5's pause-trigger rate is informative even when
  zero.** The target is zero pauses — pauses indicate the
  system is misbehaving. But *sustained zero* across many
  months in a system where the residual is Material is
  *also* informative: either the monitoring is not
  sensitive enough, or the controls are working better
  than expected. The Council reviews both extremes.
- **Why the residual is accepted by the Council, not the
  CAIRO alone.** For a High-residual risk in a high-risk
  system at a healthcare org, single-executive
  acceptance is the wrong governance posture. The
  Council's collective acceptance distributes the
  decision and signals seriousness to the Board Quality
  Committee.
- **Re-evaluation trigger #4** (material model update).
  This is the one most often forgotten. Every model
  update silently re-evaluates the residual; programs
  that do not name this trigger end up with stale
  treatment plans referencing a model that no longer
  exists.
- **What I would do differently in v2 of the plan.** Add
  a *control adequacy* indicator: a periodic test of
  whether the monitoring controls (C4-C6) would have
  caught the v1 incident if it occurred today. This is
  the closest thing to a real residual-risk measurement.
  The reference omits for one-page discipline.

---

Maintained by [Girish Nair](https://github.com/garynair)
