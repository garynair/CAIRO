# Exercise 02 — Design a 4-Axis Trust Score with Explicit Math

**Estimated time**: 4 hours
**Deliverable**: A trust-scoring specification (≤ 3 pages)

---

## Why this exercise exists

§4 of the lecture notes argued for deterministic,
multi-axis trust scoring as the right posture for
authorisation decisions. This exercise makes you do the
work: define the axes, define the inputs, define the
math, define the thresholds, and defend the choices
against the alternatives.

## The scenario

You are advising **Tessera Bank's** CTO on the trust-
scoring component of the agentic customer-service
agent (continuity from Exercise 01). The CTO has asked
you for a **4-axis trust score specification** that the
trust gate will use to authorise operations.

## Your assignment

Produce a trust-scoring specification with:

### Section 1 — The four axes (≤ 1 page)

For each of four axes, specify:

- **Axis name** and one-line definition.
- **What the axis measures** for an agent operation
  in this context.
- **Input signals** — specifically, what signed events
  or attestation artifacts the axis consumes.
- **Math** — the function that produces the score
  from inputs. Be specific. "Weighted sum of inputs"
  is not specific; "0.4 × identity_attestation_age_score +
  0.3 × revocation_status + 0.3 × delegation_depth_penalty,
  bounded [0, 100]" is.
- **Range** — what the output range is.
- **Refresh cadence** — how often the score is
  re-computed.

You may use the §4.4 starting axes (Identity, Risk,
Reliability, Autonomy) or adapt them. If you adapt,
justify in the reasoning notes.

### Section 2 — The decision logic (≤ ½ page)

The trust gate's decision logic on top of the four
axes:

- **Allow** — what combination of axis scores produces
  an allow decision.
- **Deny** — what combination produces a deny.
- **Step up** — what combination triggers step-up
  authentication (per §5.5).
- **Pause for human** — what combination triggers
  human-in-the-loop.

Be specific. "If trust is high, allow" is not specific.
"If Identity ≥ 80 AND Risk ≤ 30 AND Reliability ≥ 60
AND Autonomy ≤ 50, allow without step-up" is.

### Section 3 — Three worked examples (≤ ¾ page)

For three specific operations, show the axes' inputs
and outputs:

1. **A routine balance inquiry** (low-stakes,
   well-established agent).
2. **A first-time funds transfer** (higher-stakes,
   moderate confidence).
3. **A funds transfer above the agent's normal
   pattern** (e.g., $4,900 transfer when the
   customer's median is $200).

For each, show: input signals collected; per-axis
scores; decision logic output; what additional
evidence (if any) is required.

### Section 4 — Trade-off and defence (≤ ¾ page)

Address:

1. **Why deterministic, not heuristic.** Defend the
   posture per §4.3 for this context.
2. **Why these four axes, not others.** What
   alternatives did you reject?
3. **The auditability statement.** A one-paragraph
   summary you could use with a regulator or
   internal auditor explaining how a specific
   authorisation decision can be reproduced and
   defended.
4. **One limitation** of the scoring approach.
   Programs that claim no limitations are not
   credible.

## Constraints

- The math for each axis must be **specific enough
  that a developer could implement it**. Do not
  leave it as "a function of signals".
- The decision logic must be **rule-based, not
  ML-based**. The §4.3 posture is deterministic for
  authorisation.
- At least one axis must have an **explicit time
  decay** — the score declines if recent signals
  are not refreshed. Trust without freshness is
  not trust.
- The three worked examples must produce **different
  decisions**. A specification where every example
  results in "allow" is not exercising the design.

## Rubric

| Criterion | Weight |
|---|---|
| Four axes — specific inputs, specific math, specific ranges | 30% |
| Decision logic — rule-based, multi-threshold | 20% |
| Worked examples — three with different decisions | 20% |
| Trade-off and defence — substantive, regulator-presentable | 15% |
| Time decay on at least one axis | 5% |
| Limitation acknowledged | 10% |

## Where to submit

`solutions/modules/mod-106-trust-architecture/exercise-02-design-four-axis-trust-score/SOLUTION.md`

Reference solution uses Identity / Risk / Reliability /
Autonomy with specific math: each on a 0–100 scale,
decision matrix with four bands, explicit step-up
trigger between bands 2 and 3.

## Reading before you start

- Lecture notes §4 (trust scoring) — all of it,
  especially §4.4 (axes) and §4.5 (event vocabulary).
- mod-103 §4.1 (leading-vs-lagging) — applies here:
  trust signals can be leading or lagging.
- Exercise 01 reference solution (for the operation
  context).
