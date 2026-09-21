# Chapter 5 — MEASURE and Leading Indicators

## Why this chapter exists

MEASURE is the NIST AI RMF function that says *given what
we know about the risks, are they actually present, and at
what magnitude*. It is the function that most programs
over-invest in and under-design — the dashboards proliferate
while the number of *actionable* signals stays flat.

The failure is almost always the same: metrics that look
like leading indicators but function as lagging ones, so
the program discovers each risk when it materialises rather
than before. This chapter names the trap, gives the metric-
design discipline that avoids it, and defines the
measurement plan as the working artifact.

Chapter 4 handed MEASURE a list of failure modes to
detect. Chapter 5 turns that list into instruments.
Chapter 6 turns instrument readings into treatment.

## What MEASURE produces

Three artifacts. Each is small and named.

1. **A measurement plan** per system — what is measured,
   how, how often, by whom.
2. **A metric set** with thresholds and responses — what
   level of each metric triggers what action.
3. **The dashboards and reports** that surface metrics to
   the roles that act on them.

The three are linked: the plan enumerates metrics; the
metric set names their thresholds and responses; the
dashboards render the metrics to specific audiences. A
program with dashboards but no plan has metrics no one
chose; a program with a plan but no dashboards has metrics
no one sees.

## The leading-vs-lagging trap

The single most common mistake in MEASURE design is
labeling a lagging indicator as a leading one.

- A **leading indicator** tells you a risk is becoming
  more likely *before* it materialises. It gives the
  program time to act.
- A **lagging indicator** tells you a risk has already
  materialised. It gives the program time only to
  respond.

Both are useful. Programs need both. But programs that
have only lagging indicators discover incidents at the
incident, and no amount of dashboarding fixes that.

Examples, worked:

| Indicator | Leading or lagging? | Why |
|---|---|---|
| Number of bias complaints from affected users | **Lagging** | The bias has manifested to the point that users noticed |
| Number of overturned model decisions in the last week | **Lagging** (mostly) | The decisions were made, then overturned |
| Rate of change in overturned-decision frequency | **Leading-ish** | The trend is early; the individual decisions still lagged |
| Demographic parity score on the latest eval set | **Depends** — leading if the eval set is refreshed and representative, lagging if it is stale |
| Drift in input feature distribution (KS test on production vs training) | **Leading** | Drift usually precedes performance degradation |
| Confidence-score distribution shift on production traffic | **Leading** | Miscalibration signals often precede accuracy drop |
| Customer complaint rate | **Lagging** | Complaints are downstream of harm |
| Customer complaint rate *rate of change* | **Leading-ish** | The derivative catches acceleration before absolute numbers do |
| Number of red-team findings in the last quarter | **Leading** | Findings precede exploitation |

The discipline is: **at least one true leading indicator
per applicable risk category**, per system. If a category
has only lagging indicators, name the gap and put it on
the MANAGE list.

## Metric design principles

Four principles. A metric that fails any of them should be
retired.

- **Tie each metric to a risk category from the
  taxonomy.** A metric without a named risk is decoration.
  If the metric owner cannot say *which Chapter 2
  category this metric addresses*, it is not in scope.
- **Define the threshold before you have data on it.**
  Setting a threshold after seeing a distribution invites
  motivated thresholds. *"Anything above 0.78 is
  concerning"* is motivated reasoning when 0.78 is your
  current maximum. The discipline: threshold-first,
  data-second.
- **Pair every metric with a response.** What happens
  when the threshold is crossed? *"We discuss it at the
  next AI Review Board"* is acceptable as a response if
  the policy says so; *"we revisit"* is not.
- **Drop metrics no one acts on.** A measurement function
  with more metrics than responses is producing
  wallpaper. Regular pruning is a health signal.

The four principles together produce a metric set that is
smaller than the program initially wants and more useful
than the program initially expects.

## The measurement plan as artifact

A working measurement plan for one system is one or two
pages, structured as a table.

| Risk category | Metric | Data source | Cadence | Threshold | Response when crossed | Owner |
|---|---|---|---|---|---|---|
| Performance | Accuracy on labeled holdout (v2 eval set) | nightly batch | weekly | < 0.92 | AI Review Board review at next meeting | Model Owner |
| Bias & fairness | Demographic parity gap on approvals | quarterly fair-lending eval | quarterly | > 5 pp | Model paused; fair-lending review | Head of Fair Lending |
| Bias & fairness (leading) | Drift in cash-flow OCR error rate on non-English receipts | production log | weekly | > 2× 90-day baseline | Investigation ticket to Data Eng | Data Eng Lead |
| Drift | KS statistic on input feature distribution | streaming | daily | p < 0.01 | Model Owner notified; investigation within 5 days | Model Owner |
| Transparency | Adverse-action notice individual-explanation coverage rate | monthly sample audit | monthly | < 95% | Compliance review; sample audit expanded | CCO |
| ... | ... | ... | ... | ... | ... | ... |

A plan longer than two pages is not a plan; it is an
aspirational document. If you cannot fit the system's
measurement plan into two pages, either the system is
over-instrumented or the plan is diluted.

## The eval-set problem

Most measurement plans depend on **eval sets** — labeled
datasets used to compute metrics. Eval sets carry their
own risks. If the eval set is broken, every metric that
depends on it is broken silently.

Three eval-set risks that show up in practice:

- **Staleness.** The eval set was built six months ago;
  production has drifted; metrics computed on it are no
  longer predictive of production performance.
- **Contamination.** The eval set was used during
  training (intentionally or via leakage). Metrics on it
  overstate production performance — sometimes by a lot.
- **Coverage.** The eval set under-represents populations
  that production over-represents. Metrics on it
  under-estimate risks in the under-represented
  populations — which is where fair-lending findings
  usually live.

A working MEASURE function treats every eval set as a
**tracked artifact**:

- Name and version.
- Provenance (how it was built, from what source data).
- Coverage analysis (how it stratifies against production).
- Refresh cadence (how often it is regenerated).
- Contamination check (evidence it was not in training).

Without these, the metrics are unverifiable. NIST AI RMF
MEASURE-2.5 asks specifically for demonstrable
representativeness and validity of the eval set; if you
cannot answer that sub-function, you cannot defend the
metrics that depend on it.

## The dashboard discipline

Dashboards are the *rendering* of the metric set to a
specific audience. Working dashboards share five
properties.

- **Show leading indicators above lagging ones.** Reading
  order signals priority. If a board dashboard leads with
  customer-complaint volume, the program has told the
  board it is in reactive mode.
- **Show thresholds explicitly.** Not just current values.
  A metric shown without its threshold is a number
  without meaning.
- **Show the response for each threshold.** A viewer
  should not need to consult a separate document to know
  what happens when a threshold breaches.
- **Have a named primary audience.** A specific role, not
  *"the AI team"*. Roles have calendars; teams do not.
- **Are reviewed by that audience on a defined cadence.**
  Weekly, monthly, quarterly — named in the operating
  rhythm (Chapter 7).

A dashboard nobody reads on a defined cadence is not a
dashboard; it is wallpaper. Treat it as such and remove it.
The program is stronger with fewer dashboards actually
used.

## Article 9(2)(b) and reasonably foreseeable misuse

For any high-risk EU AI Act system, the measurement plan
is the substrate for Article 9(2)(b) — *estimation and
evaluation* of risks under intended use *and* reasonably
foreseeable misuse. mod-102 Chapter 3 has the crosswalk.

Practical consequence for the measurement plan: at least
one metric per applicable category is scoped to *misuse*,
not just intended use. Examples:

- A jailbreak-success-rate metric on a customer service
  agent (Security + Transparency categories).
- A prompt-injection-attempt detection rate on an
  email-processing agent (Security).
- A hallucinated-recommendation frequency on any
  generative system (Performance + Transparency).

If the measurement plan cannot answer *"how would we know
if this system were being misused"*, it is not Art. 9(2)(b)
compliant.

## What MEASURE does *not* do

MEASURE does not decide whether a threshold breach is
acceptable. MEASURE surfaces the breach; MANAGE decides
what to do; GOVERN decides whether the appetite covered
this class of breach at all.

A common failure: MEASURE owners escalate breaches to
themselves and quietly acknowledge them. This is a
governance failure that looks like a measurement problem.
Fix by writing the response column into the plan and
routing breaches to the named owner, not to the dashboard.

## Concrete example — one metric worked through

Small-business loan decisioning, bias-and-fairness category,
leading indicator.

- **Metric.** Drift in the OCR error rate for cash-flow
  receipts in non-English languages, week over week.
- **Data source.** Aggregator ingestion logs, filtered by
  detected receipt language.
- **Cadence.** Weekly, reviewed by Data Engineering.
- **Threshold.** Absolute: OCR error rate exceeds 8%.
  Relative: exceeds 2× the trailing 90-day baseline.
  Both trigger.
- **Response.** Investigation ticket to Data Eng with
  5-business-day SLA; if error rate is confirmed, model
  is retrained-blocked pending a data-quality fix and the
  Head of Fair Lending is notified.
- **Owner.** Data Engineering Lead (metric), Head of Fair
  Lending (response).

The metric is *leading* because OCR degradation precedes
biased approval-rate outcomes by weeks. If the program
only measured the approval-rate outcome, it would discover
the bias at the CFPB inquiry.

## Summary

- MEASURE produces three artifacts: the measurement plan,
  the metric set with thresholds and responses, and the
  dashboards.
- The leading-vs-lagging trap is the most common failure:
  programs relabel lagging indicators and discover
  incidents at the incident. Every applicable risk
  category needs at least one true leading indicator.
- Metrics must tie to a taxonomy category, have
  thresholds set before data is collected, be paired with
  a named response, and be pruned when no one acts on
  them.
- The measurement plan is a two-page table. Longer is
  worse.
- Eval sets are tracked artifacts with named provenance,
  coverage, refresh cadence, and a contamination check.
  Metrics that depend on eval sets are only as credible
  as the eval sets themselves.
- Dashboards have a named audience, a defined review
  cadence, and thresholds and responses displayed
  in-line. Everything else is wallpaper.
- For high-risk EU AI Act systems, the plan must include
  at least one metric scoped to reasonably foreseeable
  misuse per applicable category (Art. 9(2)(b)).
- Exercise 03 designs a measurement plan for one system
  with true leading indicators and named responses.
