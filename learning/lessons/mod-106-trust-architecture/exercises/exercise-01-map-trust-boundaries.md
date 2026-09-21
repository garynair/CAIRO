# Exercise 01 — Map Trust Boundaries Using NIST 800-207

**Estimated time**: 3 hours
**Deliverable**: An annotated trust-boundary diagram + a
one-page accompanying memo (≤ 2 pages total)

---

## The scenario

You are the CAIRO at **Tessera Bank** (continuity from
earlier modules). Tessera is rolling out an **agentic
customer-service assistant** — an LLM-driven agent that
goes beyond the existing chat agent (Model B from
mod-104) to actually *perform* actions on the
customer's behalf. The new agent can:

- Read customer account state (existing).
- Compose customer-facing messages (existing).
- **Initiate disputes** (new).
- **Transfer funds between the customer's own accounts**
  (new, up to $5,000 per transfer, ≤ 3 transfers per day).
- **Schedule appointments with a human banker** (new).
- **Update certain customer profile fields** (new — address,
  contact preferences).

The agent runs as a service. It calls Tessera's internal
APIs. The customer interacts via web and mobile chat. The
LLM is vendor-hosted (same Vendor X from earlier
modules). Tessera's CISO + CTO have asked you to **map
the trust boundaries** that govern this agent before
they finalise the security architecture.

## Your assignment

Produce two artifacts.

### Artifact 1 — The trust-boundary diagram

A diagram (Markdown text-art is fine — the structure
matters more than visual polish) showing:

1. **The agent process** and its components (LLM
   inference layer, agent orchestration layer, tool-
   calling layer, observability).
2. **The principal layer** — Tessera customers, the
   bank itself as principal in some cases.
3. **The downstream resources** the agent touches —
   account-read API, disputes API, transfers API,
   appointments API, profile API.
4. **The trust boundaries** — explicitly marked lines
   where trust must be established. Each boundary
   labeled with: the crossing party, the
   authentication / authorisation method, the
   blast radius if the boundary fails.

Use the seven tenets from §2.1 of the lecture notes
to verify that each boundary is addressed.

### Artifact 2 — The accompanying memo (1 page)

Address:

1. **The three composable questions** per boundary —
   identity, capability, context. For at least two
   boundaries, name the specific implementation for
   each question.
2. **The two highest-blast-radius operations** and
   the gate they go through. The transfer operation
   and the disputes operation are obvious candidates;
   make a substantive call on which is higher and why.
3. **The dynamic-identity problem** for this agent —
   what makes the agent's identity composite
   (model + configuration + principal + session)
   and how the boundary design handles each
   component.
4. **One trust-boundary failure scenario** you would
   want the CISO to address in the security
   architecture (e.g., LLM vendor changes
   foundation model mid-deployment — the
   continuity issue from mod-104 Ex-04).

## Constraints

- The boundary diagram must label **at least six
  trust boundaries**.
- For each boundary, name the **failure scenario** —
  what is the cost if this boundary is bypassed?
- The composable-question analysis must be at the
  level of "this attribute, validated this way" —
  not "we use authentication".
- The dynamic-identity discussion must distinguish
  the *model* identity from the *configuration*
  identity. Many programs collapse these and lose
  the distinction.
- The memo must address the *blast radius framing*
  from §2.3 — at least one boundary's design must be
  justified by blast-radius reasoning.

## Rubric

| Criterion | Weight |
|---|---|
| Boundary diagram — six or more boundaries labeled | 25% |
| Per-boundary attributes — crossing party + method + blast radius | 20% |
| Composable questions — applied substantively to ≥ 2 boundaries | 20% |
| Highest-blast-radius identification — defensible | 10% |
| Dynamic-identity discussion — distinguishes components | 15% |
| Failure scenario — concrete, addressable | 10% |

## Where to submit

`solutions/modules/mod-106-trust-architecture/exercise-01-map-trust-boundaries/SOLUTION.md`

Reference solution maps 8 trust boundaries with explicit
blast-radius analysis. The highest-blast-radius operation
identified is the funds-transfer; the reasoning addresses
why disputes are lower despite the customer-visible
consequence.

## Reading before you start

- Lecture notes §1 (what trust means) and §2 (zero-trust
  adapted).
- mod-104 Ex-04 reference (the Vendor X swap scenario)
  for the dynamic-identity context.
- NIST SP 800-207 §3 (architectural approaches).
