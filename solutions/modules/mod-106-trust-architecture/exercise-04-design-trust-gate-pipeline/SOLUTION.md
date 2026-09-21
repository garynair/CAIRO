# Exercise 04 — Design a Trust-Gate Request Pipeline — Reference Solution

## 1. Solution overview

A **3-gate pipeline** for Tessera's agentic agent:
agent-side fast-path (5ms budget) for routine
authorisation, reverse-proxy gate (30ms budget) for
all operations, and resource-side gate (15ms budget) at
the funds-transfer API specifically. Total interactive
budget ≤ 50ms p99. Step-up triggers when the 4-axis
score's catastrophic-band conditions are met. The
funds-transfer resource-side gate fails closed.

---

## 2. Artifact 1 — Pipeline design

### Gate placement

The design uses **three placements** (per §5.1):

1. **Agent-side** — inside the agent orchestrator
   process.
2. **Reverse-proxy** — between the agent orchestrator
   and downstream services.
3. **Resource-side** — at the funds-transfer API
   specifically.

Defence-in-depth applies: the reverse-proxy gate is
the structural backstop; the agent-side gate is the
fast-path optimisation; the resource-side gate is the
catastrophic-operation hard stop.

### Pipeline stages

For an operation initiated by the agent:

```
[Agent orchestrator decides to invoke a tool]
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│ Gate 1 — Agent-side fast-path                            │
│ Placement: in-process (orchestrator)                     │
│ Inputs: cached manifest + last-known revocation status  │
│ Latency budget: 5ms p99                                  │
│ Decisions: ALLOW (routine) / passthrough (else)         │
│ Failure mode: fail-passthrough — if gate fails, route   │
│   to Gate 2 (does not allow on its own)                 │
└─────────────────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│ Gate 2 — Reverse-proxy gate                              │
│ Placement: separate service between orchestrator and    │
│   downstream resources                                   │
│ Inputs: full manifest verification + 4-axis trust score │
│   (Ex-02) + fresh revocation check                       │
│ Latency budget: 30ms p99                                 │
│ Decisions: ALLOW / DENY / STEP_UP                       │
│ Failure mode: fail-closed — if gate is unavailable,     │
│   all operations DENY                                    │
└─────────────────────────────────────────────────────────┘
                     │
                     ▼
[For non-transfer operations: operation reaches resource]
[For transfer operations:]
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│ Gate 3 — Resource-side gate (transfer API only)         │
│ Placement: inside the transfer API service              │
│ Inputs: re-verify capability constraint specifically:   │
│   - amount within signed limit                           │
│   - destination account is customer-owned                │
│   - daily transfer count within limit                    │
│ Latency budget: 15ms p99                                │
│ Decisions: ALLOW / DENY                                 │
│ Failure mode: fail-closed — transfers DENIED if gate    │
│   unavailable                                            │
└─────────────────────────────────────────────────────────┘
                     │
                     ▼
[Transfer executes; signed audit event emitted]
```

### Per-gate specification

**Gate 1 — Agent-side fast-path.**

- *Placement:* In-process library imported into the
  agent orchestrator.
- *Inputs:* (a) Cached manifest from session start
  (TTL: 60 seconds for routine ops, 0 seconds for
  catastrophic ops — fast path doesn't apply to
  catastrophic). (b) Last-known revocation status
  (TTL: 30 seconds).
- *Decisions:* ALLOW if (operation class is "read"
  AND identity score is fresh AND capability matches
  AND no recent denial events for this session).
  Otherwise passthrough to Gate 2.
- *Latency budget:* 5ms p99.
- *Failure mode:* **Fail-passthrough.** If Gate 1
  itself errors (e.g., library crash), the request
  proceeds to Gate 2. Gate 1 does NOT authorise on
  its own without successful operation.

**Gate 2 — Reverse-proxy gate.**

- *Placement:* Separate service between orchestrator
  and downstream resources.
- *Inputs:* Full W3C VC manifest from Exercise 03
  (verified per Ex-03 protocol); 4-axis trust score
  computed per Exercise 02; fresh revocation check
  (no cache); operation class; principal context.
- *Decisions:* ALLOW / DENY / STEP_UP per the 4-axis
  decision logic.
- *Latency budget:* 30ms p99 (including the manifest
  verification, JWKS fetch, revocation check, and
  trust score computation).
- *Failure mode:* **Fail-closed.** If Gate 2 is
  unavailable (service down, dependencies unreachable),
  all operations are DENIED. The orchestrator
  surfaces a customer-friendly "service temporarily
  unavailable" message.

**Gate 3 — Resource-side transfer gate.**

- *Placement:* Inside the funds-transfer API
  service.
- *Inputs:* The W3C VC manifest's transfer capability
  with its constraints; the current operation
  request; customer's transfer history for the day
  (cached for ≤ 5 seconds).
- *Decisions:* ALLOW (amount within signed limit AND
  destination customer-owned AND daily count within
  limit) / DENY (any constraint violated).
- *Latency budget:* 15ms p99.
- *Failure mode:* **Fail-closed.** Transfers are
  DENIED if Gate 3 cannot verify. The bank does not
  authorise money movement on partial verification.

### Step-up triggers

Step-up is triggered when the 4-axis decision logic
(per Ex-02) returns STEP_UP. Concretely, this
happens when:

- Risk score > 70 AND Autonomy score > 70 AND
  Identity ≥ 80 AND Reliability ≥ 70 (catastrophic
  band with sufficient base trust — escalate to
  customer).
- Funds-transfer amount > 75th percentile of
  customer's 90-day transfer history (specific
  trigger).
- Profile-update on address or contact preferences
  (capability requires step-up flag).

Step-up mechanism:

- Customer push notification to registered device
  with operation summary (amount, destination, etc.).
- Customer confirms or rejects within 60-second
  window.
- Confirmation produces a step-up attestation that
  Gate 2 verifies before allowing.
- Rejection produces an immediate DENY and a
  security event.

---

## 3. Artifact 2 — Latency and availability analysis

### End-to-end latency budget

| Stage | p99 latency budget | Cumulative |
|---|---|---|
| Agent decision (LLM inference) | (out of trust budget — vendor-side) | — |
| Gate 1 (agent-side fast path) | 5ms | 5ms |
| Gate 2 (reverse-proxy) | 30ms | 35ms |
| Network hop to resource | ~5ms | 40ms |
| Gate 3 (resource-side, transfer only) | 15ms | 55ms* |

*For non-transfer operations: cumulative 40ms (Gate 3
skipped).

*For transfer operations: cumulative 55ms, exceeding
the §5.3 interactive target of 50ms. Acceptable
because (a) transfers are not the most-frequent
operation, (b) customer push-notification step-up
adds seconds-of-latency regardless of gate
performance, (c) the 5ms over-budget is in service
of resource-side defence-in-depth.

Routine operations (balance inquiry): 40ms cumulative,
within the §5.3 50ms target.

### Availability dependency

The pipeline introduces three new availability
dependencies for the agent:

1. **Gate 1 library** — in-process, dependency on
   library correctness. Mitigation: fail-passthrough
   posture preserves availability when Gate 1
   itself crashes.
2. **Gate 2 service** — separate service.
   Availability target: 99.95% per fiscal quarter.
   Mitigation: redundant Gate 2 instances behind a
   load balancer; circuit breaker policy in
   orchestrator.
3. **Gate 3 service** — inside transfer API.
   Availability is bounded by the transfer API's
   availability. No new external dependency.

When Gate 2 is unavailable:

- Agent operations DENY (fail-closed).
- Customer-facing experience: "AI assistant temporarily
  unavailable — please try again or contact a banker."
- Internal: incident response triggered if outage
  > 5 minutes.

### Caching strategy

- **Gate 1 caches** the agent's manifest and last
  revocation status. TTLs: 60 seconds for manifest,
  30 seconds for revocation. Cache invalidated on
  revocation events.
- **Gate 2 does not cache** authorisation decisions
  — each operation goes through fresh trust score
  computation. The 4-axis math is fast enough that
  caching is unnecessary.
- **Gate 3 caches** the customer's daily transfer
  count for ≤ 5 seconds. Cache invalidated on each
  successful transfer.

The §5.3 caveat (caching is dangerous when
revocation matters) is respected: catastrophic
operations bypass Gate 1's cache; the revocation
list is checked freshly at Gate 2 for catastrophic
operations.

---

## 4. Artifact 3 — Tradeoff analysis

The five §5.4 costs and their mitigations:

### Cost 1 — Latency

Routine operations: +40ms p99 over the no-gate
baseline. Transfer operations: +55ms p99.

*Mitigation:* The 4-axis math is implemented in
native code (no library calls in the hot path);
Gate 2 is co-located with the orchestrator (sub-ms
network); Gate 1 fast-path eliminates the Gate 2
cost for routine reads.

*Acknowledged residual:* The 55ms transfer latency
is over the §5.3 50ms target. Tessera accepts this
for the defence-in-depth benefit.

### Cost 2 — Availability dependency

Gate 2 is now critical infrastructure for the agent.
Gate 2 outage = agent outage.

*Mitigation:* Active-active Gate 2 redundancy with
sub-second failover; runbook for Gate 2 incident
response; quarterly disaster-recovery exercise of
Gate 2 outage.

*Acknowledged residual:* During the failover window
(typically 100–500ms), operations may experience
elevated latency or transient denials. Customer
experience documentation notes the possibility of
"try again" responses during these windows.

### Cost 3 — Operational complexity

Three gates to monitor, deploy, scale, update. New
roles: Gate 2 SRE on-call; Gate 3 integration with
existing transfer-API runbook; Gate 1 library
release coordination.

*Mitigation:* Phased rollout; integration with
existing Tessera observability stack; documented
runbooks for each gate's common failure modes.

*Acknowledged residual:* The CTO's engineering org
takes on ~3 FTE of ongoing operational burden for
the trust-architecture layer.

### Cost 4 — Developer friction

Agent developers must understand the manifest
format (Ex-03), the capability vocabulary, the
decision logic. Misunderstanding produces operations
that are DENY at Gate 2 with error messages that
need to be debugged.

*Mitigation:* Developer documentation including the
4-axis decision logic and worked-example failure
modes; a "trust-debug" mode in development
environments that explains decision logic in
human-readable terms; agent developer training as
part of onboarding.

*Acknowledged residual:* Initial developer
productivity will be lower; some legitimate
operations may be incorrectly designed and
require iteration.

### Cost 5 — False positives

The trust gates will deny some legitimate operations
— most likely when the 4-axis Risk score crosses
threshold for operations that are routine for a
specific customer but unusual at the agent-class
level.

*Mitigation:* Quarterly review of DENY decisions
broken down by customer cohort; threshold
calibration based on the review; step-up rather
than DENY where possible (per §5.5).

*Acknowledged residual:* The system will be slightly
over-restrictive at launch and will need calibration
based on production data over the first 90 days.
This is the expected behaviour; under-restrictive
at launch would be worse.

---

## 5. Reasoning notes

- **Why three gates and not just one.** A single
  centralised gate is operationally simpler but
  carries single-point-of-failure risk for the
  entire authorization surface. Three gates with
  different placements means the failure modes are
  different — Gate 2 outage doesn't simultaneously
  produce Gate 3 outage, and the resource-side gate
  is the last line of defence for funds movement.
- **Why Gate 1 fails *passthrough* but Gate 2 and 3
  fail *closed*.** Gate 1 is the optimisation
  layer. Its purpose is to make routine operations
  fast; it doesn't *itself* make the authorisation
  decision (it just sometimes shortcuts to ALLOW
  for clearly-routine ops). If Gate 1 crashes,
  Gate 2 still does the real authorisation work.
  Failing Gate 1 closed would prevent the
  optimisation from improving availability rather
  than degrading it. Gates 2 and 3 are real
  authorisation decisions — they fail closed
  because authorising operations under unknown
  authority is worse than denying them.
- **Why the resource-side Gate 3 only protects
  transfers.** Resource-side gates can be added at
  any resource; the marginal benefit is highest
  where blast radius is highest. Transfers are the
  catastrophic case. Adding resource-side gates at
  read APIs would add latency without commensurate
  protection.
- **Why latency budgets are broken out per gate.**
  Per the constraints — the cumulative budget
  doesn't tell you which gate is the bottleneck.
  Per-gate budgets make optimisation tractable.
- **What the design deliberately under-specifies.**
  The specific load-balancer pattern, the exact
  circuit-breaker thresholds, the observability
  dashboard layout. These are engineering choices
  at a lower level than the CAIRO specification.
- **What I would change in v2.** Add an
  *interactive-step-up timeout fallback* — if the
  customer doesn't respond to a step-up
  notification within 60 seconds, what happens?
  The reference implicitly DENIES; a v2 should
  make this explicit and consider whether some
  step-ups should auto-allow after timeout (no)
  vs. some should expire with a soft fail (perhaps
  for low-stakes step-ups).

---

Maintained by [Girish Nair](https://github.com/garynair)
