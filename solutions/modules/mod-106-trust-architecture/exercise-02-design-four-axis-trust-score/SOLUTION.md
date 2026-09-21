# Exercise 02 — Design a 4-Axis Trust Score — Reference Solution

## 1. Solution overview

A trust-scoring specification for **Tessera Bank's
agentic customer-service agent**. Four axes: Identity,
Risk, Reliability, Autonomy. Each on a 0–100 scale,
with specific deterministic math. Decision logic is a
multi-threshold rule-set: routine operations allow at
moderate scores, catastrophic operations require all
axes high. The Identity axis carries explicit time
decay; the auditability statement is regulator-
presentable.

---

## 2. The specification

> **Tessera Bank — 4-Axis Trust Score Specification**
> *Version 1.0.*
> *Owned by: CTO (technical implementation);
> CAIRO (program requirements); CISO (security review).*
> *Applies to: agentic customer-service agent
> authorisation decisions.*

### Section 1 — The four axes

#### Axis 1 — Identity (range 0–100; higher is more
trusted)

*What it measures:* the strength of the agent's
identity attestation at this moment of operation.

*Inputs:*

- **signature_valid** ∈ {0, 1} — JWT/VC signature
  verification result.
- **attestation_age_seconds** — current time minus
  attestation issuance time.
- **revocation_status** ∈ {valid, revoked,
  unknown} — JWKS revocation lookup.
- **delegation_chain_valid** ∈ {0, 1} — all
  delegation hops verify.

*Math:*

```
if not signature_valid: return 0
if revocation_status == "revoked": return 0
if not delegation_chain_valid: return 0

# Freshness decay: full credit if attestation < 60s old,
# linear decay to 0 credit at 5 minutes.
age = attestation_age_seconds
if age <= 60:
    freshness_score = 100
elif age <= 300:
    freshness_score = 100 - ((age - 60) * 100 / 240)
else:
    freshness_score = 0

# Revocation-unknown penalty.
if revocation_status == "unknown":
    freshness_score *= 0.7

return round(freshness_score)
```

*Refresh cadence:* per-operation.

#### Axis 2 — Risk (range 0–100; lower is more
trusted — higher number means more risky)

*What it measures:* the risk profile of the requesting
principal, the requested operation, and the operation
context.

*Inputs:*

- **operation_class** — categorical (read /
  send_message / dispute_initiate / transfer / profile_update).
  Lookup table assigns base risk: read=10,
  send_message=15, dispute_initiate=30, profile_update=55,
  transfer=70.
- **operation_amount** (transfers only) — dollar
  amount. Adds 0–30 to base based on amount
  relative to customer's 90-day median.
- **principal_risk_score** — customer's existing
  fraud-risk score from Tessera's existing fraud
  systems, normalized 0–100.
- **session_age_seconds** — long sessions add a
  small risk increment (mid-session adversarial
  takeover concern).

*Math:*

```
risk = operation_class_base_risk[operation_class]

if operation_class == "transfer":
    ratio = operation_amount / max(customer_90d_median_transfer, 100)
    if ratio <= 1: amount_risk = 0
    elif ratio <= 5: amount_risk = (ratio - 1) * 5  # up to 20
    else: amount_risk = 20 + min((ratio - 5) * 2, 10)  # cap at 30
    risk += amount_risk

# Principal risk overlay: blend with 0.3 weight.
risk = 0.7 * risk + 0.3 * principal_risk_score

# Session age penalty: +1 per hour beyond 1 hour, cap at 10.
if session_age_seconds > 3600:
    risk += min((session_age_seconds - 3600) / 3600, 10)

return min(round(risk), 100)
```

*Refresh cadence:* per-operation.

#### Axis 3 — Reliability (range 0–100; higher is
more trusted)

*What it measures:* the track record of the agent
class on operations similar to this one.

*Inputs:*

- **agent_class** — the agent's class identifier
  (e.g., customer-service-agent-v2).
- **operation_class** — same categorical as Axis 2.
- **historical_success_rate** — fraction of
  operations of this class by this agent class that
  completed without incident in the trailing 30 days.
- **incident_count_recent** — number of incidents
  involving this agent class in the trailing 30 days.

*Math:*

```
if historical_operation_count < 100:
    # Insufficient data; conservative default
    return 50

success_score = historical_success_rate * 100

# Recent incident penalty: each incident in trailing 30d
# reduces reliability by 10, floor at 0.
reliability = success_score - (incident_count_recent * 10)
return max(round(reliability), 0)
```

*Refresh cadence:* daily (recomputed in batch nightly).

#### Axis 4 — Autonomy (range 0–100; lower is more
trusted — higher number means more autonomous /
less-supervised operation)

*What it measures:* how much of the decision is being
made by the AI vs. the human.

*Inputs:*

- **human_review_present** ∈ {0, 1} — is a human
  reviewing this operation before it commits?
- **operation_class** — same categorical.
- **customer_step_up_pending** ∈ {0, 1} — has the
  customer been asked to confirm?

*Math:*

```
if human_review_present == 1:
    return 10  # Human-supervised; low autonomy
if customer_step_up_pending == 1:
    return 30  # Customer confirmation requested; bounded autonomy

# Pure-agent operations
autonomy_by_class = {
    "read": 40,
    "send_message": 60,
    "dispute_initiate": 75,
    "profile_update": 85,
    "transfer": 90
}
return autonomy_by_class[operation_class]
```

*Refresh cadence:* per-operation.

### Section 2 — Decision logic

Apply the four axes to authorisation decisions
according to these bands:

```
def authorise(identity, risk, reliability, autonomy):
    # Hard failures
    if identity == 0:
        return DENY, "identity attestation failed"
    if reliability < 30:
        return DENY, "agent class reliability below threshold"

    # Catastrophic operations (Risk > 70 AND Autonomy > 70)
    if risk > 70 and autonomy > 70:
        if identity >= 80 and reliability >= 70:
            return STEP_UP, "high-risk autonomous operation; customer confirmation required"
        else:
            return DENY, "high-risk autonomous operation; insufficient trust"

    # High-risk operations (Risk > 50)
    if risk > 50:
        if identity >= 60 and reliability >= 50 and autonomy <= 75:
            return ALLOW, "high-risk operation within bounded autonomy"
        elif identity >= 70 and reliability >= 60:
            return STEP_UP, "high-risk operation with elevated autonomy; step-up"
        else:
            return DENY, "high-risk operation; trust insufficient"

    # Moderate-risk operations
    if risk > 30:
        if identity >= 50 and reliability >= 40:
            return ALLOW, "moderate-risk; baseline trust"
        else:
            return STEP_UP, "moderate-risk; identity or reliability below baseline"

    # Routine operations
    if identity >= 40:
        return ALLOW, "routine operation; baseline trust"
    return STEP_UP, "routine operation; identity below baseline"
```

### Section 3 — Worked examples

**Example A — Routine balance inquiry.**

- Operation class: `read` (base risk 10).
- Customer's session: established 3 minutes ago, MFA used.
- Agent class: customer-service-agent-v2, 99.7%
  historical success on read operations.
- Attestation age: 30 seconds.
- Revocation status: valid.

Axes:

- Identity: 100 (fresh attestation, valid signature,
  no revocation).
- Risk: 0.7 × 10 + 0.3 × 25 (customer's principal
  risk) = 7 + 7.5 = ~15.
- Reliability: 99.7 × 100 - 0 incidents = ~97.
- Autonomy: 40 (read operation, pure-agent).

Decision: ALLOW (routine; routine band, identity ≥ 40).

**Example B — First-time funds transfer ($1,200,
customer's median transfer is $200).**

- Operation class: `transfer`.
- Operation amount: $1,200; ratio to median = 6 →
  amount_risk = 20 + min((6-5)*2, 10) = 22.
- Attestation age: 60 seconds.
- Principal risk score: 25 (normal).
- Reliability: 99.5% on transfer operations, 0
  incidents.
- Human review: no.
- Customer step-up: not yet requested.

Axes:

- Identity: 100.
- Risk: 70 + 22 = 92, blended: 0.7 × 92 + 0.3 × 25 =
  64.4 + 7.5 = ~72.
- Reliability: ~95.
- Autonomy: 90 (transfer, pure-agent).

Decision: Risk > 70 AND Autonomy > 70 → catastrophic
band. Identity ≥ 80 AND Reliability ≥ 70 → STEP_UP.
Customer confirmation requested via push notification.

**Example C — Unusual funds transfer ($4,900,
customer's median is $200).**

- Operation class: `transfer`.
- Operation amount: $4,900; ratio to median = 24.5
  → amount_risk = 20 + min((24.5-5)*2, 10) = 30 (cap).
- Principal risk score: 40 (elevated; customer has
  one recent disputed transaction).
- Attestation age: 90 seconds.
- Reliability: 99.5% on transfer operations.
- Human review: no.
- Customer step-up: not yet.

Axes:

- Identity: 100 - ((90-60) * 100/240) = 100 - 12.5 =
  ~88.
- Risk: 70 + 30 = 100, blended: 0.7 × 100 + 0.3 × 40 =
  70 + 12 = 82.
- Reliability: ~95.
- Autonomy: 90.

Decision: Risk > 70 AND Autonomy > 70 → catastrophic
band. Identity = 88, Reliability = 95. STEP_UP, but
with a more rigorous step-up: customer push
notification *with the transfer amount and
destination visible*, requiring active acknowledgment
(not just tap-to-confirm).

### Section 4 — Trade-off and defence

**Why deterministic, not heuristic.** Tessera operates
in a regulator-watched environment (SR 11-7 + CFPB +
NYDFS). When an authorisation decision is challenged
— by a customer disputing an unauthorised transfer,
by a regulator examining the bank's AI controls —
the bank must reproduce the decision exactly and
explain why. A heuristic score would require
explaining a model; a deterministic score explains
itself. The reproducibility cost of heuristic scoring
is unacceptable for high-stakes banking
authorisations.

**Why these four axes.** Identity covers the
verification question; Risk covers the operation
and principal context; Reliability covers the
historical posture of the agent class; Autonomy
covers the human-in-the-loop dimension. Alternative
axes considered:

- *Capability fit* (whether the operation matches
  the agent's claimed capability scope) — rejected
  because this is a *prerequisite* to scoring, not
  a score. The trust gate must verify capability
  before scoring; failed capability check is DENY
  regardless of score.
- *Network origin* (where the request originated) —
  rejected because Tessera handles this at a
  pre-trust-score layer (network-level access
  controls). Including it would mix layers.
- *Temporal context* (time of day, day of week) —
  rejected because for a 24/7 banking system, this
  is a heuristic concern that doesn't deterministic
  differentiate.

The four chosen axes are *orthogonal* — a strong
score on one does not compensate for a weak score on
another in the decision logic. This is the §4.4
discipline.

**Auditability statement (regulator-presentable):**

> *Tessera's agentic customer-service agent is
> authorised at each operation by a four-axis
> deterministic trust score. Each axis (Identity,
> Risk, Reliability, Autonomy) is computed from
> signed signals (cryptographic attestations,
> capability assertions, the customer's existing
> risk profile, the agent class's historical
> reliability data) by a published function. Given
> the inputs to a specific authorisation decision,
> the score and the decision can be reproduced
> exactly at any time after the fact. Decision logic
> is a published rule-set that determines allow,
> deny, or step-up based on the combination of
> axes. The score and decision are logged with the
> operation; the audit ledger preserves the inputs
> for any subsequent review.*

**One limitation.** The Reliability axis depends on
*historical* performance of the agent class on
operations of the type in question. For a new agent
class or a new operation class, historical data is
sparse and the axis defaults to 50 (insufficient
data conservative). This means new agent capabilities
get treated as moderately-reliable from launch —
which is the right posture but means the system is
not optimally calibrated until 100+ operations
accumulate. A future iteration could substitute a
class-similarity heuristic for the cold-start period;
the reference does not for simplicity and
defendability.

---

## 3. Reasoning notes

- **Why I put time decay on Identity, not on
  Reliability.** Identity attestations are *fresh
  inputs at each operation* — staleness directly
  weakens the verification. Reliability is a
  *historical* aggregate — staleness of historical
  signals is not the right concept. A long history
  of clean reliability is stronger evidence than a
  short one; that's the opposite of decay.
- **Why the Risk axis includes a principal-risk
  blend.** The agent's blast radius is partially a
  function of *who* the principal is. A customer
  with a clean profile and a long history is lower
  risk than a new customer or a customer with
  recent disputes. The 30% weight is a compromise
  — high enough to matter, low enough that a high
  principal risk doesn't dominate operations the
  customer is asking for in good faith.
- **Why catastrophic operations require step-up
  even with high trust.** The §5.5 step-up pattern
  applied: where blast radius is high but
  legitimate use is also expected, the right
  posture is *additional evidence*, not allow-
  or-deny. Customer push-notification confirmation
  is the cheapest additional evidence available.
- **Why I bounded amount-risk at 30.** Above 5x
  median, the additional risk-per-dollar diminishes
  rapidly — a $50,000 transfer is not 250x as risky
  as a $200 transfer; it's an unusual transfer that
  is already at the top of the risk scale. Bounding
  prevents the axis from saturating in ways that
  would distort the decision logic.
- **The hardest design choice.** Whether to include
  the customer-side step-up in the Autonomy axis
  computation (autonomy = 30 when step-up pending)
  vs. handling it purely in the decision logic.
  Both work. The reference's approach lets the
  Autonomy axis reflect the *effective* autonomy at
  the moment of decision, which is what matters
  for the rule-set evaluation. The alternative
  would make Autonomy a pure-agent property.
- **What this specification deliberately under-
  specifies.** The exact JWKS endpoint, the
  specific cryptographic algorithm choice (ES256
  vs Ed25519 vs RS256). Engineering chooses.
- **What I would do differently in v2.** Add an
  *operations-per-session* counter to the Risk axis
  — many operations in a single session correlate
  with adversarial probing. The reference omits
  for simplicity; a v2 specification would include
  it.

---

Maintained by [Girish Nair](https://github.com/garynair)
