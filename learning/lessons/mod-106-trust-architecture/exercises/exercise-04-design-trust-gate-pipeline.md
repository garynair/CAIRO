# Exercise 04 — Design a Trust-Gate Request Pipeline

**Estimated time**: 3 hours
**Deliverable**: A trust-gate pipeline design + a
tradeoff analysis (≤ 3 pages)

---

## The scenario

You are advising **Tessera Bank** on the placement and
design of the trust gates for the agentic customer-
service agent (Exercises 01–03). Specifically: where
the gates sit, what they do at each stage, and what
the design breaks. The CISO and CTO will use this as
input to the production architecture decision.

## Your assignment

Produce three artifacts.

### Artifact 1 — Pipeline design (≤ 1½ pages)

A design specifying:

1. **Gate placement.** Use the §5.1 placement taxonomy
   (agent-side / reverse-proxy / resource-side /
   gateway-mediated). State which placements the
   design uses and why.

   *The design must use at least two placements* —
   defence-in-depth applies. Single-placement designs
   are not robust.

2. **Pipeline stages.** For each operation the agent
   attempts, the sequence of gates and the actions at
   each:

   ```
   Operation initiated by agent
   → Gate 1 (placement, function, latency budget)
   → Gate 2 (placement, function, latency budget)
   → ...
   → Operation reaches resource
   → Resource response
   → Return path: any post-operation gates
   ```

3. **Per-gate specification.** For each gate:
   - Placement.
   - Inputs (what attestation / manifest / trust-score
     it consumes).
   - Decisions (allow / deny / step-up / log).
   - Latency budget (per §5.3).
   - Failure mode (what happens if the gate itself
     fails — fail-closed or fail-open, and the
     defence of that choice).

4. **Step-up triggers.** Specific conditions under
   which the pipeline invokes step-up (per §5.5).

### Artifact 2 — Latency and availability analysis (≤ ¾ page)

Address:

1. **End-to-end latency budget.** For an interactive
   operation (customer asks balance), what is the
   cumulative trust-gate latency, and how does it
   compare to the §5.3 targets (50ms p99
   interactive)?

2. **Availability dependency.** Each gate added is a
   potential failure point. State the design's
   availability assumption and the recovery posture
   when a gate is unavailable.

3. **Caching strategy.** Does the design cache any
   authorisation decisions? If yes, address the
   §5.3 caveat (revocation invalidates the cache).
   If no, defend the latency cost.

### Artifact 3 — Tradeoff analysis (≤ ¾ page)

Per §5.4 of the lecture notes, name what the design
breaks:

1. **Latency.** How much, on whose request?
2. **Availability dependency.** What is now
   dependent on the trust infrastructure that was
   not before?
3. **Operational complexity.** What new operational
   work is required?
4. **Developer friction.** How will agent developers
   experience the gates? What error messages,
   documentation, debugging paths are required?
5. **False positives.** Where is the design most
   likely to reject legitimate operations? How
   will this be detected and addressed?

For each, state the *cost* and the *mitigation*. A
design with no acknowledged costs is not credible.

## Constraints

- The pipeline must use **at least two placements**
  from §5.1.
- At least one gate must **fail closed** for
  catastrophic operations. Defend the choice.
- The latency budget must be **broken out per gate**
  — not just the cumulative total.
- The tradeoff analysis must name at least **five**
  specific costs (the five categories above).
- Step-up triggers must be **specific** — not "for
  unusual operations" but "when the funds-transfer
  amount exceeds 75th percentile of the customer's
  90-day transfer history".
- No vendor name appears as *the* answer. The design
  may use Cloudflare, IBM watsonx.governance, or roll-your-own
  components; if it does, the choice is defended on
  its own merits, not on vendor reputation.

## Rubric

| Criterion | Weight |
|---|---|
| Gate placement — at least two, defended | 15% |
| Per-gate specification — complete for each gate | 25% |
| Latency budget — broken out per gate | 15% |
| Availability dependency — addressed substantively | 10% |
| Step-up triggers — specific | 10% |
| Tradeoff analysis — at least five costs, with mitigations | 20% |
| Fail-closed defence on at least one gate | 5% |

## Where to submit

`solutions/modules/mod-106-trust-architecture/exercise-04-design-trust-gate-pipeline/SOLUTION.md`

Reference solution uses a **3-gate pipeline**:
agent-side fast-path gate (5ms budget) for routine
authorisations + reverse-proxy gate (30ms budget) for
all operations + resource-side gate at the funds-
transfer API (additional 15ms). Total budget 50ms p99
for interactive operations. Step-up triggers on
funds-transfer above 75th percentile of customer's
90-day history.

## Reading before you start

- Lecture notes §5 (trust gates in the request
  path) — all of it.
- Exercises 01–03 reference solutions (for the
  operation context, the 4-axis score, and the
  manifest format).
- mod-104 §3 (validation patterns) — the gates'
  posture against gaming applies here.
