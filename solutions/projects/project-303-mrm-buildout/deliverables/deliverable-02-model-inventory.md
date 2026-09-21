# Deliverable 02 — AI/ML Model Inventory — Reference Solution

## 1. Solution overview

Inventory: 42 models in scope per Deliverable
01; 14 already under MRM (carry through); 28
newly in-scope. Four substantive findings
named — including the uncomfortable Treasury
forecasting tool. Sequencing puts the two
customer-facing consumer-banking models with
recent complaints first, followed by Treasury
and wealth-management retrain issue, with
lower-criticality classifiers backfilled
through Q1.

---

## 2. The inventory and memo

### Inventory snapshot

> **Tessera AI/ML Model Inventory v1.0**
> *Maintained in GRC tool;
> ID/name/tier/owner/validator/status fields.
> Below is the Risk Committee summary
> presentation; the operational inventory
> contains the per-model fields per
> Deliverable 02 spec.*

| Business line | Models | Existing MRM | New to MRM |
|---|---|---|---|
| Consumer banking | 11 | 4 | 7 |
| Small-business lending | 9 | 5 | 4 |
| Commercial real estate | 7 | 4 | 3 |
| Wealth management | 8 | 1 | 7 |
| Shared services | 7 | 0 | 7 |
| **Total** | **42** | **14** | **28** |

### The four findings

**Finding 1 — Treasury "smart cash position"
forecasting tool.** A treasury-side ML model
that forecasts intraday cash position has
been driving real Treasury decisions for
approximately 8 months without formal MRM
governance. The model was developed by a
Treasury analyst as a productivity tool;
adoption was organic; documentation is
minimal; no validation has been performed.
The model has not produced losses to date.
**This is material.** Treasury exposure
sizing in a $25B bank is consequential. The
inventory work surfaced the system; the
findings include the lack of governance
itself.

Action: Treasury places the system on
operational pause within 14 days pending
provisional validation. Provisional Tier-1
treatment. Full validation by Day 60.
Communicated to CRO and CEO immediately upon
discovery.

**Finding 2 — Wealth-management portfolio
rebalancing signal.** The signal model that
contributes to rebalancing recommendations
was retrained 3 weeks ago without pre/post
performance comparison. Production
performance has degraded — sharpe ratio of
recommendations is down ~22%. The wealth-
management team has not noticed. (CAIRO
discovered through inventory work.)

Action: rollback to prior model parameters
within 5 days pending investigation.
Investigation per mod-110 systemic-cause
discipline. Suspected systemic cause:
post-launch validation gating was not
operating after the latest training data
refresh (the failure pattern from mod-110
Ex-01).

**Finding 3 — HR resume-screening vendor
LLM.** Vendor-supplied system used by
Sourcing to rank candidates. Per Deliverable
01, materiality-based in-scope determination
applies. The system has been in production
for 6 months without MRM treatment.

Action: Provisional Tier-2 treatment.
Vendor-model validation per the methodology
adapted for information asymmetry. Subgroup
performance analysis specifically — protected-
class outcome examination required. Initial
report to MRM by Day 75.

**Finding 4 — Two customer-facing consumer-
banking models.** Of the 7 new-to-MRM
consumer-banking models, two have produced
customer complaints in the last quarter
through the bank's consumer-relations
function (complaints related to credit-line
decisions affected by the next-best-offer
recommendations). The complaints are not
formal CFPB complaints yet but the trend is
real.

Action: Priority validation. Tier-1
provisional. Validation by Day 45.

### Sequencing for the 28 outside-MRM models

90-day sequencing prioritises by risk:

- **Days 0-45 (highest priority):** the two
  customer-facing consumer-banking models
  with complaints (Finding 4); the wealth-
  management rebalancing model (Finding 2)
  rollback first, then validation.
- **Days 45-75:** Treasury forecasting tool
  full validation (Finding 1); HR vendor
  LLM (Finding 3); 4 wealth-management
  signals (lower priority within the
  business line).
- **Days 75-120 (post-90-day arc; into Q1):**
  Remaining lower-tier consumer-banking,
  commercial-real-estate, small-business
  lending, shared-services models.

### Discovery methodology

The inventory was constructed by:

- Tessera's existing MRM inventory (the 14
  models already under MRM) as starting
  point.
- Surveys to business-line leadership (CRO
  co-signed the request for accuracy).
- Procurement-data cross-reference (vendor
  software with AI/ML capability).
- IT data-flow mapping (any system
  consuming material model artifacts).
- Conversations with specific high-judgment
  individuals (heads of analytics, data
  science, ops).

### What we may have missed

Two known unknowns:

1. **Shadow AI use.** Individual employees
   using ChatGPT / Copilot to produce
   analysis that informs decisions. These
   are out-of-MRM-scope per Deliverable 01
   but represent a separate AI Acceptable
   Use governance question. Tessera does
   not have full visibility.
2. **Vendor models we don't know about.**
   Vendor software may include AI/ML
   components not disclosed to Tessera at
   procurement time. Vendor risk management
   has been asked to surface these in
   their next vendor review cycle.

### Resourcing implications

MRM has 4 validators today. The pre-90-day-
arc plan called for ~14 traditional-model
validations per year (current capacity is
roughly matched to that). The new 28 AI/ML
models require validation, tracked
proportionally:

- Tier-1 estimated: 6-8 models. Full
  validation per model: ~6-8 weeks of
  validator time.
- Tier-2 estimated: 14-16 models. Per model:
  ~3-4 weeks.
- Tier-3 estimated: ~10 models. Per model:
  ~1-2 weeks.

Total: roughly 100-130 validator-weeks of
new work over 12 months. Current capacity:
~140 weeks/year for AI-side work assuming
no augmentation. **Implication: MRM is
+2 validators short for the steady-state
need.** CAIRO and CRO joint recommendation to
the CFO: hire 2 senior AI/ML-capable
validators by end of Q1.

---

## 3. Reasoning notes

- **Why I named Finding 1 (Treasury) honestly.**
  The CRO will not enjoy seeing this. But:
  (a) it surfaced via the inventory work, so
  burying it would be a worse story when
  Audit or the OCC finds it independently;
  (b) the CRO will appreciate finding out
  from the CAIRO before finding out from the
  exam; (c) honesty discipline is what the
  CAIRO × CRO relationship needs at the
  outset.
- **Why immediate pause on Treasury.**
  Treasury exposure sizing is material to
  the bank. Continuing operation while
  validation occurs is not defensible if
  the model later produces a loss. Pause
  costs Treasury some operational
  efficiency; that's the right trade.
- **Why provisional Tier-1 on the customer-
  facing models with complaints.** CFPB
  risk if complaints escalate. Tier-1
  treatment surfaces issues; defensive
  posture for Tessera.
- **Why the resourcing ask in this
  deliverable rather than later.** Early
  resourcing ask is durable; late ask
  ("we ran out of capacity") is not.
- **What I would do differently.** I might
  have separated Findings 1 and 2 from
  Findings 3 and 4 — first two are
  incidents requiring immediate action;
  second two are governance gaps requiring
  programmatic action. The memo could read
  more clearly with the distinction.

---

Maintained by [Girish Nair](https://github.com/garynair)
