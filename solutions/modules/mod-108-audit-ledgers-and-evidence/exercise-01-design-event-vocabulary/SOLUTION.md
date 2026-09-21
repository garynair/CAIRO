# Exercise 01 — Design Event Vocabulary — Reference Solution

## 1. Solution overview

For **Tessera's agentic customer-service agent**, the
reference defines **12 event types** in 5 categories,
baselined on OpenTelemetry GenAI semantic conventions
with documented Tessera extensions. The granularity
principle: one event per agent action with program-
relevant consequence — explicitly excluding internal
function calls and operational telemetry.

---

## 2. The vocabulary

### Scope and design principles

- **Scope:** All operations of the customer-service
  agent that affect principals, resources, or
  external state. Internal function calls,
  inference-layer messages between agent components,
  and operational telemetry are out of scope.
- **Granularity principle:** One event per agent
  action with program-relevant consequence.
- **Boundary:** If a CAIRO would not need to reconstruct
  the operation at year+3 in a regulator review,
  it does not enter the evidence vocabulary.

### Event types (12 total)

**Authorisation category (3 types):**

- `trust-gate.decision` — Emitted by trust gate at each
  operation; records the gate's allow/deny/step-up
  decision, the 4-axis scores, the reasoning code.
- `manifest.issued` — Emitted by identity service when a
  capability manifest is issued; records the agent, the
  principal, the capability scope.
- `manifest.revoked` — Emitted when a manifest is
  revoked; records the manifest ID, reason, time.

**Tool invocation category (3 types):**

- `tool.invoked` — Emitted when the agent invokes a tool;
  records the tool, the input reference (hash of
  externally-stored input), the manifest reference.
- `tool.result` — Emitted when the tool returns;
  records the tool, the output reference, the success/
  failure status.
- `tool.denied` — Emitted when a tool invocation is
  denied by capability scope; records the tool, the
  reason, the manifest that did not authorise it.

**Model interaction category (2 types):**

- `model.invoked` — Emitted at each LLM inference call;
  records the model identity (vendor, version,
  configuration hash), the prompt-template version,
  the input/output references.
- `model.identity.change` — Emitted when the model's
  runtime identity differs from the expected; records
  the expected and observed identities, the alert
  raised.

**State change category (2 types):**

- `customer.profile.change` — Emitted when the agent
  invokes the profile-update capability; records the
  customer, the field changed, the old/new values
  (with PII handled per output filters).
- `customer.transfer.executed` — Emitted when a funds
  transfer executes; records the customer, the source
  and destination, the amount, the manifest
  authorisation reference.

**Incident-relevant category (2 types):**

- `monitoring.threshold.crossed` — Emitted when any
  measurement plan threshold is crossed (per mod-103
  Ex-03); records the metric, the threshold, the
  observed value, the response triggered.
- `incident.classification.assigned` — Emitted when an
  incident classification is assigned per the mod-107
  Ex-04 taxonomy; records the incident reference, the
  classification, the responding function.

### Field-level standard (common envelope)

Each event includes:

- `id`: UUID v4 (event ID, unique within ledger).
- `type`: kebab-case identifier (one of the 12 above).
- `timestamp`: RFC 3339 datetime in UTC.
- `tsa_timestamp` (optional): RFC 3161 timestamp from
  external TSA, included for catastrophic events.
- `actor`: identifier for the emitting agent / service.
- `subject`: identifier for the entity the event
  concerns.
- `operation`: short string describing the action.
- `result`: one of `success`, `failure`, `deferred`.
- `reason`: short string with context for
  interpretation.
- `references`: object containing pointers to large
  external artifacts (keyed by purpose).
- `signing_key_id`: identifier for the key that signed
  this event.
- `signature`: cryptographic signature over the
  canonicalised event content.
- `prior_event_hash`: hash of the previous event in the
  emitter's sequence (for in-batch hash chain).

### Emission specification

| Emitter | Events emitted | Latency budget | Fail mode |
|---|---|---|---|
| Orchestrator | trust-gate.decision, tool.invoked, tool.result, tool.denied, customer.profile.change, customer.transfer.executed | < 10ms after operation | Fail-closed — operation rejected if emission fails |
| Identity service | manifest.issued, manifest.revoked | < 50ms | Fail-closed |
| Model inference layer | model.invoked, model.identity.change | < 50ms | Fail-open for routine; fail-closed for identity.change |
| Monitoring stack | monitoring.threshold.crossed | < 5 min | Fail-open; retry until acknowledged |
| Incident management | incident.classification.assigned | < 1 hour | Fail-open with audit trail |

Catastrophic-class operations (funds transfer,
profile update) carry **fail-closed** emission —
the operation is rejected if the event cannot be
emitted.

### Vocabulary registry treatment

- The vocabulary registry lives in a Tessera-internal
  service. The registry is itself an append-only
  signed artifact.
- Additions and modifications require CAIRO function
  + CISO + CTO joint approval per the mod-107 Ex-03
  boundary pattern.
- Each event-type definition is versioned. Material
  semantic changes produce a new event type rather
  than mutating the prior; both types may coexist
  during transitions.
- OpenTelemetry GenAI semantic conventions are
  tracked at standards-body level; Tessera extensions
  are documented as a delta against the upstream
  baseline; annual review reconciles drift.

### Worked example

A `customer.transfer.executed` event for a $1,200
transfer between a customer's own accounts:

```json
{
  "id": "01HF9G7Q3MZ2K6X8P4N5W3D8YE",
  "type": "customer.transfer.executed",
  "timestamp": "2026-06-01T18:42:17.831Z",
  "tsa_timestamp": "2026-06-01T18:42:17.952Z",
  "actor": "agent:tessera:customer-service-v2:session:abc123",
  "subject": "customer:tessera:7f9e2d4a-3b1c-4f6e-8c5a-2e8b7c1d4a9e",
  "operation": "transfer_between_own_accounts",
  "result": "success",
  "reason": "customer-initiated transfer within step-up bounds",
  "references": {
    "manifest_jti": "urn:uuid:9c8e2d1a-7b3f-4d6c-9a5f-2e8b7c1d4a9e",
    "model_identity": "VendorX:X-Pro:2026.02",
    "trust_gate_decision_event_id": "01HF9G7Q3MZ2K6X8P4N5W3D8YD",
    "step_up_event_id": "01HF9G7Q3MZ2K6X8P4N5W3D8YA",
    "amount_minor_units": 120000,
    "currency": "USD",
    "source_account_hash": "sha256:e3b0c44298fc1c149a...",
    "destination_account_hash": "sha256:9f86d081884c7d659a..."
  },
  "signing_key_id": "tessera-orchestrator-2026-q2",
  "signature": "MEUCIQDh3eYf2Z3...",
  "prior_event_hash": "sha256:7a4cd8e2..."
}
```

Annotations on non-obvious choices:

- `amount_minor_units` rather than dollar amount — to
  avoid floating-point ambiguity; consistent across
  currencies.
- Account references as hashes, not plaintext —
  account numbers are sensitive; the hashes allow
  later proof of which account was involved
  without exposing the number in the event.
- TSA timestamp included for transfer events
  because they are catastrophic-class; routine
  events would not include the TSA timestamp.
- Multiple references to upstream events (trust-gate
  decision, step-up confirmation) — the event is
  *contextually complete* even though it doesn't
  inline the upstream content.

---

## 3. Reasoning notes

- **Why 12 event types and not 22 or 6.** §3.1 — the
  granularity principle determines the count.
  Tessera's agent has roughly 12 program-relevant
  consequence classes; 22 would over-decompose
  (e.g., separating per-tool events into many
  types); 6 would aggregate categories that
  auditors want to distinguish.
- **Why I baselined on OpenTelemetry GenAI
  semantic conventions.** It is the closest to
  community consensus and is being actively
  developed. Starting from a baseline reduces
  Tessera-specific vocabulary drift and makes
  cross-platform analysis more tractable.
- **Why I separated tool.invoked from tool.result.**
  Tool calls can hang or fail asynchronously. A
  single combined event would either be emitted
  optimistically (before the result is known) or
  delayed indefinitely. The split allows both
  events to be in the evidence stream with the
  right timing.
- **Why model.identity.change is a separate
  event type rather than a field on every
  model.invoked.** Operationally, identity changes
  are rare and important. A separate event type
  surfaces them in queries and supports
  fail-closed semantics for the catastrophic case.
- **What this vocabulary deliberately omits.**
  Internal-agent reasoning steps (the LLM's
  intermediate generation), cache hits, network
  retries, queue depths. All operational; none
  evidence.
- **What I would do differently in v2.** Add a
  `correlation_id` field for cross-event linking
  (an entire session's events share a correlation
  ID; multi-step workflows share theirs). The
  reference uses inter-event references (the
  trust-gate event ID is in the transfer event's
  references); a v2 with explicit correlation IDs
  would be cleaner.

---

Maintained by [Girish Nair](https://github.com/garynair)
