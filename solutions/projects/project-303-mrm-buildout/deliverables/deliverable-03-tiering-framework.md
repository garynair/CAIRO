# Deliverable 03 — Model Tiering Framework — Reference Solution

## 1. Solution overview

Three-tier framework. Tier-1 = high
materiality, low reversibility, high
regulatory exposure; full SR 11-7 treatment
plus AI-specific augmentations. Tier-2 =
moderate; periodic validation with reduced
depth. Tier-3 = low materiality, easily
reversible; light-touch with annual review.
The framework includes 5 tiering factors
with clear scoring; ties resolve toward
the higher tier. Initial tier distribution
across 42 models: ~8 Tier-1, ~24 Tier-2,
~10 Tier-3.

---

## 2. The framework

### Tier definitions

**Tier 1 — High criticality.** Models whose
output materially influences customer-facing
decisions with limited reversibility,
regulatory-reportable exposures, or
significant capital implications.

**Tier 2 — Moderate criticality.** Models
whose output influences important decisions
but with greater reversibility or lower
direct customer impact.

**Tier 3 — Lower criticality.** Models
whose output supports decisions but where
errors are easily detected and corrected
and direct customer impact is minimal.

### Tiering factors

Five factors. Each scored 1-3 (1 = low, 3 =
high). Sum of weighted scores produces a
tier recommendation; the highest single-
factor score also forces an escalation (a
single high-severity factor cannot be
washed out by low scores elsewhere).

**Factor 1 — Decision materiality.**
- (3) Decision is customer-facing or
  materially affects capital, liquidity,
  AML, or fundamental-rights outcomes.
- (2) Decision is internal but materially
  affects financial outcomes or
  significant operational decisions.
- (1) Decision supports analysis or
  productivity; immaterial to capital,
  customer, or compliance outcomes.

**Factor 2 — Reversibility of decisions
informed.**
- (3) Decisions are irreversible or very
  difficult to reverse (e.g., credit
  denials communicated; trades executed).
- (2) Decisions are reversible with effort
  (e.g., portfolio re-balancing; pricing).
- (1) Decisions are easily reversed or
  reviewed before action (e.g.,
  recommendation that human decisively
  reviews).

**Factor 3 — Regulatory exposure.**
- (3) Output is directly regulatory-
  reportable or subject to specific
  regulatory frameworks (CRA, ECOA, CFPB,
  AML, capital, etc.).
- (2) Output is in an area of significant
  regulatory interest without specific
  reporting (e.g., consumer-facing
  AI, fair lending adjacent).
- (1) Output is in a low regulatory-
  scrutiny area.

**Factor 4 — Novelty and explainability.**
- (3) Foundation models, LLMs, vendor
  black-box systems with limited
  visibility.
- (2) Deep learning or complex ensembles
  with limited explainability.
- (1) Statistical models, classical ML
  with established interpretability
  techniques.

**Factor 5 — Population breadth.**
- (3) Customer-impacting at scale (many
  customers affected per error).
- (2) Material but limited customer breadth
  or significant internal breadth.
- (1) Limited population impact.

### Scoring and tier assignment

- **Tier 1:** Total score ≥ 12 OR any single
  factor at 3 (forced escalation).
  Exception: a single Factor-4 score of 3
  (novelty) alone does NOT force Tier-1
  if all other factors are 1 (a novel-tech
  productivity tool with low materiality is
  Tier-3).
- **Tier 2:** Total score 8-11 OR Factor-1
  score of 2.
- **Tier 3:** Total score ≤ 7 AND no factor
  at 3.

### Tier-specific treatments

| Treatment | Tier 1 | Tier 2 | Tier 3 |
|---|---|---|---|
| Validation frequency | Annual + on material change | Every 18-24 months | Every 36 months |
| Validation depth | Full per methodology | Reduced (~60% of full) | Light (~30% of full) |
| Ongoing monitoring | Daily/weekly auto + monthly review | Weekly auto + quarterly review | Monthly auto + annual review |
| Independent challenge | Required pre-deployment + annual | Required pre-deployment + biennial | Pre-deployment only |
| Change-management gate | All material changes | Material changes; minor by exception | Annual change review |
| Reporting cadence to RC | Quarterly | Semi-annual | Annual |

### Tiering decision process

- Initial tier assigned by MRM (CRO-side)
  with CAIRO concurrence for AI-specific
  factors.
- Business-line model owner can dispute the
  tier with reasoning. Disputes resolved by
  CAIRO + CRO joint decision. Tier-1
  disputes that fail consensus escalate to
  the Risk Committee.
- Tier assignment recorded in the inventory
  with reasoning.

### Re-tiering triggers

- Material change to model scope or use.
- Material change to the underlying
  business decision the model informs.
- Validation finding that calls into
  question prior tier assignment.
- Incident involving the model.
- Annual review may re-tier; not all
  reviews produce changes.

### Worked tier-assignment examples

**Treasury "smart cash position" forecasting
(Finding 1).**
- Decision materiality: 3 (treasury exposure)
- Reversibility: 2 (sweep timing can be
  adjusted)
- Regulatory exposure: 2 (liquidity reporting
  adjacent)
- Novelty: 2 (custom internally-built
  model, gradient boosting)
- Population breadth: 2 (Tessera-wide
  treasury impact)
- **Total: 11. Forced to Tier-1 by Factor-1
  score of 3.**

**HR resume-screening vendor LLM
(Finding 3).**
- Decision materiality: 2 (employment
  outcomes)
- Reversibility: 2 (candidates can be
  re-evaluated)
- Regulatory exposure: 3 (EEOC, state fair-
  employment, EU AI Act if employees in
  EU)
- Novelty: 3 (vendor LLM, limited
  visibility)
- Population breadth: 3 (all hiring
  candidates)
- **Total: 13. Tier-1.**

**Wealth-management portfolio rebalancing
signal (Finding 2).**
- Decision materiality: 3 (client portfolio
  outcomes)
- Reversibility: 2 (positions can be
  reversed)
- Regulatory exposure: 2 (advisor / fiduciary
  considerations)
- Novelty: 2 (gradient boosting)
- Population breadth: 2 (segment of wealth
  clients)
- **Total: 11. Forced Tier-1 by Factor-1.**

**Two customer-facing consumer-banking
models with complaints (Finding 4).**
- Decision materiality: 3 (consumer credit-
  adjacent)
- Reversibility: 2-3 (depends on the
  specific model)
- Regulatory exposure: 3 (CFPB, ECOA, fair
  lending)
- Novelty: 1-2 (mostly classical ML)
- Population breadth: 3 (broad consumer
  population)
- **Total: 12-14. Tier-1 both.**

**Marketing email campaign-timing
optimizer.**
- (1+1+1+2+2 = 7). **Tier-3.** This is
  the kind of model that benefits from
  the proportionality principle.

**Borderline Tier-1 / Tier-2 case: Small-
business cash-flow modeling for credit
underwriting.**
- Decision materiality: 3 (credit
  decisions)
- Reversibility: 2 (decisions reversible
  with appeal)
- Regulatory exposure: 3 (ECOA, fair
  lending)
- Novelty: 1 (statistical + classical ML)
- Population breadth: 2 (small-business
  segment)
- **Total: 11. Forced Tier-1 by Factor-1
  score of 3. (Borderline to Tier-2 by
  total score; Factor-1 forces Tier-1.)**

### Initial tier distribution

Of the 42 in-scope models, initial tier
distribution per the framework:

- **Tier 1:** ~8 models (consumer-banking
  credit-adjacent, Treasury forecasting,
  HR vendor LLM, two customer-complaint
  models, AML and capital models already
  Tier-1 in v4.2)
- **Tier 2:** ~24 models (most lending,
  CRE, wealth signals, established
  classifiers)
- **Tier 3:** ~10 models (marketing,
  productivity-adjacent, document
  classification)

---

## 3. Reasoning notes

- **Why three tiers rather than four.**
  Four tiers tempts a middle "Tier 2.5"
  that splits the validator-bandwidth
  question in half. Three tiers preserves
  clarity about which models get what
  treatment.
- **Why the forced-escalation rule.**
  Without it, a single regulatory-exposure
  factor at 3 (e.g., fair-lending) could
  be washed out by low scores elsewhere
  and the model could be Tier-3. The
  forced-escalation prevents this for
  high-severity factors.
- **Why I exempted the single-factor-4
  novelty case from forced Tier-1.** A
  novel-tech productivity tool with low
  materiality (e.g., a Tier-3 marketing
  productivity LLM) is the exact kind of
  model the proportionality principle
  protects. Forcing it to Tier-1 would
  swamp the function.
- **Why the dispute process exists.**
  Business-line owners will challenge
  tier assignments; pretending they
  won't is unrealistic. Naming the
  process avoids ad hoc resolution and
  preserves the CRO's final-decision
  posture.
- **What I would do differently.** I
  might have added a sixth factor for
  data-sensitivity (PHI, special-category
  GDPR). It's covered implicitly through
  regulatory exposure but the explicit
  factor would simplify some assignments.

---

Maintained by [Girish Nair](https://github.com/garynair)
