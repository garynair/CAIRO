# Exercise 01 — Design Event Vocabulary for a System

**Estimated time**: 3 hours
**Deliverable**: A vocabulary specification + emission
specification (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank** (continuity from
mod-106 + mod-107). The agentic customer-service
agent is going into production. The CISO and CTO
have asked you for the **event-vocabulary
specification** that the agent's emission layer
will use. The vocabulary will go into Tessera's
audit ledger (the choice of which is the subject of
Exercise 05).

## Your assignment

Produce a vocabulary specification with:

### Section 1 — Scope and design principles (≤ ¼ page)

State:

- The scope of the vocabulary (what system, what
  operations).
- The granularity principle being applied (per
  §3.1).
- The boundary between this vocabulary and
  operational logging (what is *not* an evidence
  event).

### Section 2 — The event types (≤ 1½ pages)

Define **8–15** event types covering the categories
from §3.2: authorisation, capability assertions,
tool invocations, model interactions, state
changes, configuration changes, incident-relevant
events.

For each event type:

- **Type name** — kebab-case identifier.
- **Description** — what the event represents.
- **When emitted** — the precise trigger.
- **Required fields** — the data the event must
  contain (per §3.3).
- **Optional fields** — additional context where
  available.
- **Subject identifier** — what the event is
  about.

You may use the OpenTelemetry GenAI semantic
conventions as a base; document your extensions.

### Section 3 — Field-level standard (≤ ¼ page)

For each event, the common envelope:

- Event ID format.
- Timestamp format (system clock + optional TSA).
- Signing key reference format.
- Prior event hash format.
- Reference format for large external artifacts.

### Section 4 — Emission specification (≤ ¼ page)

Per emission source:

- Who emits each event type (orchestrator, trust
  gate, tool service, etc.).
- The latency budget (events must be emitted
  within X of the operation they describe).
- The failure mode (what happens if event emission
  fails — fail-closed, fail-open).
- The batching behaviour (immediate emission vs
  batched).

### Section 5 — Vocabulary registry treatment (≤ ¼ page)

- Where the vocabulary registry lives.
- How additions and modifications are governed.
- How versioning works (when an event type's
  semantics change).
- The relationship to OpenTelemetry GenAI
  semantic conventions over time.

### Section 6 — One worked example (≤ ½ page)

A complete event for one specific operation —
e.g., the agent invoking the funds-transfer tool
on behalf of a customer. Show every field
populated with realistic values. Annotate
non-obvious choices.

## Constraints

- The vocabulary must cover **at least four**
  event categories from §3.2 substantively.
- The number of event types is **bounded** —
  8–15. More than 15 is over-granular per §3.1;
  fewer than 8 is under-coverage.
- Each event type must have **specific emission
  triggers** — "when something happens" is not
  acceptable.
- The worked example must include a **prior event
  hash** field with a realistic placeholder.
- The emission specification must address **fail
  modes** — failure to emit is a real concern in
  high-throughput agent systems.

## Rubric

| Criterion | Weight |
|---|---|
| Granularity principle — clearly stated and applied | 15% |
| Event types — 8–15, well-categorised | 25% |
| Per-type detail — name, trigger, fields, subject | 20% |
| Field-level standard — comprehensive | 10% |
| Emission specification — addresses fail modes | 10% |
| Vocabulary registry treatment | 10% |
| Worked example — annotated, realistic | 10% |

## Where to submit

`solutions/modules/mod-108-audit-ledgers-and-evidence/exercise-01-design-event-vocabulary/SOLUTION.md`

Reference solution uses 12 event types, baselines
on OpenTelemetry GenAI semantic conventions, and
documents Tessera-specific extensions.

## Reading before you start

- Lecture notes §3 (event vocabulary) — all of it.
- mod-106 §5 (trust gates) — authorisation events
  come from gate decisions.
- OpenTelemetry GenAI semantic conventions —
  skim before starting.
