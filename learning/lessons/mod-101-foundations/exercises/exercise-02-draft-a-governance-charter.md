# Exercise 02 — Draft a Governance Charter

**Estimated time**: 3 hours
**Deliverable**: A 2–3 page AI governance program charter

---

## The scenario

You are the newly-appointed Chief AI Risk Officer at **Northfield
Mutual**, a 4,000-person mid-market US property & casualty
insurer. Northfield uses AI for underwriting (a credit-score-
adjacent risk model), claims triage (a vision model that
classifies vehicle damage), customer service (a third-party
LLM-based chat agent), and fraud detection (an internal anomaly
detector). Three of those four are in production today; the
LLM chat agent is in pilot.

Northfield has:

- A CEO who appointed you after the state insurance regulator
  asked, in writing, what their AI governance posture is.
- A CRO, CDO, CISO, General Counsel, and CTO already in
  place.
- A Model Risk Management function under the CRO (built for
  actuarial models; has not yet absorbed ML).
- No prior AI policy.
- Three weeks until the regulator wants a written response.

Your CEO has given you fourteen days to produce a charter that
will become the foundation of the program.

## Your assignment

Produce a 2–3 page AI governance program charter that
addresses, at minimum:

1. **Scope.** What is "AI" for the purposes of this program?
   What is *not* in scope and why? (Be specific — there is no
   single right answer, but there is a wrong answer for every
   org.)
2. **Mission.** One paragraph. What does this program exist to
   do? What is success?
3. **Authority.** What decisions can this program make? What
   decisions can it block? What can it only recommend?
4. **Structure.** Where does the CAIRO report? What is the
   relationship to existing functions (especially the CRO/MRM,
   CISO, CDO, GC, CTO)? Use the boundary table from
   [Chapter 5](../05-peer-boundaries.md) as a starting point.
5. **Standards alignment.** Which authoritative framework
   anchors this program (NIST AI RMF, ISO 42001, or both)?
   Justify in two sentences.
6. **Governance bodies.** Name at most two governance bodies
   (review board, ethics committee, etc.). For each: purpose,
   members by role, meeting cadence, decision authority,
   escalation path. *Resist the urge to invent more than two.*
   You will be evaluated on restraint.
7. **Risk appetite framing.** One paragraph. The board has not
   yet adopted an AI risk appetite statement. Until they do,
   how does this program operate? (This is the question that
   separates serious programs from box-checking ones.)
8. **First-90-day work.** A bulleted list of the concrete
   artifacts and decisions you will deliver in the first 90
   days.

## Constraints

- The charter must be **internally defensible** — every
  authority claim must trace to either an existing executive
  delegation or a board action you will request.
- The charter must be **regulator-presentable** — written so
  the state insurance regulator could read it without
  translation.
- The charter must **respect 3LOD** ([Chapter 3](../03-three-lines-of-defense.md)).
  If your structure compromises 3LOD independence, explain why
  it is the right trade-off for Northfield.
- Length cap: **3 pages**. Charters over 3 pages get
  significantly less effective in practice; the discipline is
  part of the exercise.

## Rubric

| Criterion | Weight |
|---|---|
| Scope discipline — including the explicit out-of-scope | 15% |
| Authority clarity — distinguishes make / block / recommend | 20% |
| 3LOD posture — independent oversight is preserved or the trade-off is explicit | 20% |
| Framework alignment — anchored to a Tier-1 framework with a defensible justification | 10% |
| Governance bodies — restraint shown; named bodies have real authority and clear membership | 10% |
| Risk-appetite framing — pre-board posture is defensible, not "wait for the board" | 15% |
| First-90-day work — concrete, deliverable artifacts, not aspirational verbs | 10% |

## Where to submit

`solutions/modules/mod-101-foundations/exercise-02-draft-a-governance-charter/SOLUTION.md`

contains a reference charter for Northfield. As with Exercise
01, it is *one* defensible answer, not the only correct one.

## Pitfalls (from [Chapter 8](../08-failure-modes.md))

When you finish, check your draft against the failure modes:

- **Governance theatre.** Are your governance bodies likely
  to approve everything? Is "complete the impact assessment"
  a checkbox or a decision?
- **Control sprawl.** Are you proposing more controls than
  Northfield can actually execute in 90 days?
- **Compliance-only stance.** Does the charter only address
  what the regulator asked about, or does it address what
  could surprise Northfield?

If any of those applies, redraft.
