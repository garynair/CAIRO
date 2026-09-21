# Exercise 03 — Tabletop Exercise Design — Reference Solution

## 1. Solution overview

A half-day tabletop for **Halverston Capital**
based on a **vendor LLM model swap discovered via
bias monitoring** scenario — chosen because it
tests cross-LOB coordination (all three LOBs use
the affected vendor), exercises the notification
matrix, includes an ambiguous classification
moment, and reflects a real-pattern (mod-104
Ex-04) Halverston near-miss.

---

## 2. Goals

Three specific outcomes:

1. **Readiness indicator:** The first-hour
   decisions (verify, classify, lead, contain,
   convene) are made within the first hour of
   simulated time.
2. **Coordination indicator:** Cross-LOB
   coordination — public markets + private credit
   + wealth advisory — operates with named single
   lead and clear hand-offs.
3. **Learning indicator:** The exercise surfaces
   at least 2 substantive process gaps that
   become program improvement actions.

---

## 3. The scenario

> **Simulated date:** Tuesday, [date]. **Time:**
> 09:30. **Setting:** Halverston Capital.
>
> Halverston's wealth-advisory LLM assistant (the
> Exercise 05 system from mod-105 — deployed in
> production for 4 months) produces a flagged
> output via the AI program's content monitoring:
> the assistant's response to a client portfolio-
> rebalancing query includes an investment
> recommendation that *does not match Halverston's
> documented house view*. The monitoring service
> classifies the output as a "drift from house
> view" alert.
>
> Investigation begins. The Algorithm Quality
> Office data lead identifies an unusual pattern:
> in the trailing 72 hours, multiple wealth-
> advisory client interactions have included
> portfolio recommendations that diverge from
> documented house view by 5–15%. The pattern is
> not specific to one advisor; it spans the
> entire wealth-advisory population.
>
> Initial hypothesis: the vendor LLM provider has
> swapped the underlying foundation model. The
> 30-day contractual advance notice has not been
> received. Initial vendor contact at 10:00
> produces a non-confirmation ("we don't comment
> on internal model operations").
>
> By 11:00, similar drift patterns are surfacing
> at the private-credit underwriting workbench
> (different LLM use case, same vendor) and at
> the public-markets research summarization tool
> (third LLM use case, same vendor). All three
> Halverston LOBs are affected.

---

## 4. Injects

| Sim time | Inject | Decision required |
|---|---|---|
| T+0 (09:30) | Initial detection alert from wealth-advisory monitoring | First-hour decisions: verify, classify, lead, contain |
| T+1.5h (11:00) | Private-credit and public-markets drift patterns surface | Reclassification — single system → multi-LOB |
| T+2h (12:00) | EU AI Act notification window decision point | Notification trigger evaluation; CAIRO + GC + CCO decision |
| T+3h (13:00) | Vendor formally acknowledges model change (after Halverston escalation) | Vendor risk action; contract review |
| T+4h (14:00) | Client complaint surfaces from wealth advisor's high-AUM client questioning a specific recommendation | Customer-notification decision |
| T+5h (15:00) | Public-markets desk requests permission to continue operating with elevated monitoring for end-of-day positioning | Containment-posture decision under business pressure |
| T+6h (16:00) | Regulator inquiry arrives (SEC informal questions about wealth-advisor AI behaviour) | Coordination with CCO; regulator-response posture |
| T+7h (17:00) | End of half-day; transition to ongoing-response posture | Post-exercise hot-wash |

The T+5h inject is the **ambiguous classification
moment** — pure-AI-program if vendor change is
documented; joint if security dimension emerges
(unauthorised model swap = potential contract
violation = potential security event under some
readings).

---

## 5. Roles and observers

**Active participants:**

- AI Risk Lead (single named lead candidate).
- CAIRO.
- CISO + CISO on-call.
- CCO.
- GC.
- MRM Lead.
- Vendor Risk Lead.
- Head of Wealth Advisory.
- Head of Private Credit.
- Head of Public Markets.
- CTO designee for engineering decisions.

**Observers:**

- One Audit Committee member.
- Internal Audit lead (observing for the audit
  perspective).
- External facilitator (drives injects, observes
  coordination, scores).
- Two members of the Board Risk Committee (one
  invited per the §6.5 annual broader-
  participation tabletop pattern).

**Facilitator role:** Drives the injects on
schedule, maintains time, documents decisions
made and the timing, does not participate
substantively in the response. The facilitator
also notes coordination patterns and individual
contributions.

---

## 6. Scoring rubric

Four dimensions, each on a 1–5 scale.

### Decision quality (1–5)

- 5: All major decisions are well-founded;
  alternatives were considered and rejected on
  substantive grounds.
- 4: Major decisions well-founded; minor
  decisions sometimes ad hoc.
- 3: Major decisions made; reasoning sometimes
  shaky.
- 2: Decisions made but reasoning often weak.
- 1: Decisions made by default rather than
  deliberately.

### Decision timing (1–5)

- 5: All decisions made within the windows
  appropriate to their criticality.
- 4: First-hour decisions made within the hour;
  later decisions sometimes lag.
- 3: First-hour decisions made within 90
  minutes.
- 2: First-hour decisions made within 3 hours.
- 1: First-hour decisions delayed.

### Coordination (1–5)

- 5: Cross-functional, cross-LOB coordination
  operates with clear named-lead pattern.
- 4: Coordination operates but occasionally
  requires facilitator intervention.
- 3: Coordination is uneven across functions.
- 2: Coordination breaks down at key moments.
- 1: Functions operate in parallel without
  effective coordination.

### Documentation (1–5)

- 5: All decisions documented contemporaneously;
  the audit trail is complete.
- 4: Major decisions documented; minor decisions
  sometimes missed.
- 3: Documentation partial.
- 2: Documentation occurs but with significant
  gaps.
- 1: Documentation neglected.

**Composite reading:** Sum of the four. 16+ is
strong readiness; 12–15 is acceptable with
specific findings; below 12 indicates significant
readiness gaps requiring remediation before the
program is considered operational.

---

## 7. Post-exercise review

**Hot-wash (immediately after, 30 minutes):**
Each participant briefly identifies one thing
they would do differently. Facilitator captures.

**Written exercise report (within 10 business
days):** Authored by the facilitator with
contributions from participants. Covers:

- The scenario and its goals.
- Per-inject decision summary with timing.
- Scoring per dimension.
- Substantive findings (the §6 issues the
  exercise surfaced).
- Recommendations routed into the program
  improvement backlog.

**Audit committee briefing (within 30 days):**
The CAIRO presents findings and recommendations to
the Audit Committee; Recommendations are tracked
through closure per the standard backlog
discipline.

---

## 8. Reasoning notes

- **Why this scenario.** It exercises the
  cross-LOB pattern Halverston specifically
  needs to test; the vendor-swap pattern is a
  real concern (mod-104 Ex-04); the
  classification ambiguity at T+5h tests the
  reclassification discipline (§6.5 of mod-107
  Ex-04 lecture notes).
- **Why I named the external facilitator
  separately from the observers.** The
  facilitator's role is operationally
  different — driving the exercise — and
  conflating with observers would dilute their
  effectiveness.
- **Why I included Audit Committee + Board
  members as observers.** §6.5 annual broader-
  participation tabletop. Their presence
  signals seriousness and provides an outside
  perspective on coordination.
- **Why the scoring rubric weights documentation
  specifically.** §6.1 — programs that
  document contemporaneously survive audit;
  programs that reconstruct later don't.
  Without the documentation dimension, the
  exercise might be scored highly while the
  underlying readiness is weak.
- **What I would change in v2.** Add an
  *after-action analysis cell* — facilitator
  asks each participant 1-2 reflective
  questions during the hot-wash. The current
  hot-wash is open-ended; structured
  reflection produces better
  recommendations.

---

Maintained by [Girish Nair](https://github.com/garynair)
