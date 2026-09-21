# Exercise 04 — Build a Contestability Process

**Estimated time**: 3 hours
**Deliverable**: A contestability process design + a
worked example (≤ 3 pages combined)

---

## The scenario

You are the CAIRO at **Northfield Mutual** (continuity from
mod-101 / mod-103). The AI-assisted claims-triage system
— a vision model that classifies vehicle damage from
photos submitted by insureds — has been in production
for two years. The system produces a recommended
claims-handling pathway (express settlement, standard
review, fraud review, total-loss assessment). A claims
adjuster reviews each recommendation and makes the final
decision. The system handles ~40,000 claims per month.

You have noticed in monitoring data that **approximately
1.2% of claim photos are flagged for fraud review based
primarily on the AI's classification** — and that the
acceptance rate of the fraud-review flag is significantly
lower than the bank's other fraud-detection channels.
Meaning: many claims flagged by the AI for fraud review
turn out to be legitimate.

Affected insureds whose claims are flagged for fraud
review experience material consequences: delayed
settlement (average 23 days vs. 4 days for express),
documentation requests, and in some cases on-site
inspection. There is currently no contestability process
specific to AI-driven fraud-review flags.

The AI Risk Council has asked you to **design a
contestability process** for affected insureds whose
claims are flagged for fraud review based on AI
classification.

## Your assignment

Produce two artifacts.

### Artifact 1 — Process design (≤ 2 pages)

Address the six elements from §5.1 of the lecture notes:

1. **The named decision** — what specifically is being
   contested. Be precise (it is not "the claim
   denial"; it may be "the fraud-review flag").
2. **The named decider** — who specifically reviewed
   the decision, and whom the affected party can
   address.
3. **The path** — how the contestation is raised. What
   form, what channel, what required information.
4. **The timeline** — within what window the
   contestation must be acknowledged, reviewed, and
   resolved.
5. **The resource** — what the affected party can use
   (free? mediated? paid? does the insured need their
   own counsel?).
6. **The outcome** — what changes are possible. Can the
   fraud-review flag be removed? Can the claim be
   re-routed? What evidence the affected party
   provides changes the outcome?

For each element, name the **owner role** at Northfield
that operationalizes it.

Also include:

- **Recourse alternatives** (§5.2) — what affected
  parties can do *outside* contestation. Honest naming
  of what these are at Northfield.
- **Contestability anti-patterns avoided** — which §5.4
  anti-patterns the process explicitly avoids and how.

### Artifact 2 — Worked example (≤ 1 page)

A worked example walks through one specific case:

> A small-business owner submits a claim with photos
> taken in poor lighting after an evening
> accident. The AI classifies the damage pattern as
> "unusual" and flags for fraud review. The insured
> objects.

Walk through the process you designed, naming each step,
the actors involved, the artifacts produced, and the
timeline. Include a representative outcome.

## Constraints

- The named decider in §1.2 above must be a **human
  named role**, not "the system" and not "an algorithm".
- The path must be **multi-channel** — at least one
  written channel and one verbal channel. A digital-
  only process is not accessible to all affected
  parties.
- The timeline must be **shorter than the harm
  window**. Average claim-settlement delay for the
  insured is 23 days; contestation resolution must be
  bounded materially shorter.
- The process must avoid all anti-patterns from §5.4 —
  no routing back to the same model, no contestation
  requiring AI expertise from the affected party.
- The worked example must include a **specific,
  defensible outcome** — not "outcome to be
  determined".

## Rubric

| Criterion | Weight |
|---|---|
| Six elements — all named, all specific, all owned | 25% |
| Recourse alternatives — honest, specific | 10% |
| Anti-patterns avoided — at least four named with explicit avoidance | 15% |
| Worked example — specific actors, specific artifacts, specific timeline | 20% |
| Timeline shorter than harm window | 10% |
| Multi-channel path | 10% |
| Defensible outcome in worked example | 10% |

## Where to submit

`solutions/modules/mod-105-responsible-ai-and-ethics/exercise-04-build-contestability-process/SOLUTION.md`

Reference solution names a "Claims Review Specialist"
role staffed within the Claims Operations function (not
within the AI program) as the named decider. Process
allows for written or verbal contestation; resolution
target is 5 business days. Worked example walks through
the small-business case with a re-routed-to-standard-
review outcome.

## Reading before you start

- Lecture notes §5 (contestability and recourse) — all
  of it.
- mod-103 §6 (GOVERN — for the relationship between
  contestation outcomes and the program's loop).
- Sector guidance: state-level insurance contestation
  expectations vary; the reference assumes Northfield
  operates in NY + a few other states.
