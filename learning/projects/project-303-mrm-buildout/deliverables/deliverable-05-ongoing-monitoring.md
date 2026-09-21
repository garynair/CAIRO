# Deliverable 05 — Ongoing Monitoring Framework

**Target:** Days 35-65. **Length:** 4-6 pages.

## What this deliverable is

The framework that defines what monitoring
production AI/ML models receive on an ongoing
basis. Distinct from periodic validation
(Deliverable 04) and from incident response
(handled separately). Goes to business-line
model owners (they execute most of the
monitoring); to MRM (independent oversight);
to Risk Committee for governance.

## What it should contain

1. **Monitoring streams.** What kinds of
   monitoring per tier. Likely streams:
   - Input data quality and distribution.
   - Output prediction distribution and
     drift.
   - Performance against ground truth (where
     available).
   - Subgroup performance per fairness
     dimensions in scope.
   - Operational availability / latency.
   - Material change detection (model
     parameter changes, training data
     refresh, software stack changes).
2. **Roles and accountabilities.** Who
   monitors what. Business-line model
   owners typically own first-line
   monitoring; MRM provides independent
   review of monitoring outputs.
3. **Thresholds.** How thresholds are set;
   how they are revised; how breaches are
   escalated.
4. **Escalation paths.** When monitoring
   surfaces something concerning, what
   happens.
5. **Re-validation triggers.** Specific
   monitoring patterns that trigger
   re-validation by MRM.
6. **The wealth-management rebalancing
   model.** A worked example using one of
   the inventory findings — what monitoring
   would have caught the post-retrain
   degradation; how it gets corrected
   going forward.

## Constraints

- Monitoring framework cannot demand
  capabilities the business lines do not
  have. Phased capability buildout is
  acceptable; what's deferred must be
  named.
- Vendor models pose specific monitoring
  challenges; framework must address them
  honestly.
- Monitoring outputs feed Q4 board reporting
  (Deliverable 06) — framework must produce
  the right inputs.

## Rubric

| Criterion | Weight |
|---|---|
| Monitoring streams substantive | 25% |
| Roles / first vs. second line | 15% |
| Thresholds and escalation | 20% |
| Re-validation triggers | 15% |
| Worked example (wealth management) | 15% |
| Vendor-model handling | 10% |

## Where to find help

- mod-106 §5 (ongoing-monitoring framework).
- mod-110 Ex-01 (systemic-cause discipline;
  the wealth management example).
- mod-111 (board-reporting cadence; what
  feeds it).
