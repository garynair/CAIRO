# Exercise 04 — Prepare for an Unexpected Board Ask — Reference Solution

## 1. Solution overview

Internal briefing identifies the question behind
the question as "could Sentinel be the
institution in the next news cycle on AI
failures?" The prepared response addresses
specific exposure (adverse-action notice
standardisation gap), specific mitigations (the
defense-in-depth program, the contestability
process, the bias monitoring), and one honest
concession (the CFPB-relevant
adverse-action explainability standard is in
process, not complete). Response is deliverable
in 5 minutes; closing ask is for Board guidance
on a specific edge case.

---

## 2. Artifact 1 — Internal briefing

> **INTERNAL BRIEFING — Pre-Thursday Board Meeting**
> *For: CAIRO and team. Not for distribution.*

### The question behind the question

The board is not asking for an educational
overview of AI risk. The board is asking
whether Sentinel could be the institution in
the next news cycle. The recent industry
incidents the chair referenced (Air Canada
chatbot settlement, the bank-AI bias case
recently in press) have made boards across the
industry ask their CAIROs the same question.

The board wants to know:

- Where Sentinel is exposed.
- What is being done about it.
- How worried the CAIRO is.

### Honest exposure assessment

**Real exposures (substantive):**

1. **Adverse-action notice explainability
   standard.** Sentinel's CFPB-relevant credit
   systems are operating with Tier 1 explainability
   per the existing program (mod-105 Ex-03
   pattern), but the formalised standard is in
   process, not complete. If a customer
   contested an adverse action today and the
   CFPB inquired, we would meet the legal
   threshold but our written standard would not
   yet be the documented-current basis.
2. **Bias monitoring on smaller-volume
   subgroups.** Our monitoring is tight on the
   largest protected populations; statistical
   power on smaller subgroups is limited
   (per mod-105 Ex-02 reference). A pattern
   could develop in a small subgroup before
   our monitoring catches it.
3. **Vendor LLM dependency.** Customer-service
   chat agent uses a vendor LLM that has
   already swapped once during deployment
   (mod-104 Ex-04). Our trust architecture
   addresses identity verification, but a
   sophisticated vendor-side compromise
   wouldn't surface in our monitoring.

**Manageable exposures:**

- Trust architecture is mature; defense-in-
  depth standard is in place; incident
  response readiness is at acceptable level
  (per mod-110 Ex-05 pattern).
- Notification matrix is pre-computed; we
  can respond in regulator timelines.

**Concerning developments:**

- Industry incident frequency is increasing.
  The probability of *any* large bank having
  a significant AI incident in the next 12
  months is high; the probability of *Sentinel*
  specifically is lower but non-zero.

### What I should not say

Things that are true but volunteering them
makes the response harder:

- The specific vendors of our trust
  architecture and audit ledger. Board doesn't
  need; volunteering invites vendor-specific
  questions.
- The total annual AI-program spend. Board
  has this in the budget review; surfacing it
  in this conversation invites budget
  discussion in an inappropriate forum.
- Specific employee names involved in recent
  incidents.

### 24-hour follow-up plan

If asked specific questions I can't answer in
the meeting:

- A 1-page follow-up note within 24 hours of
  the meeting.
- A formal materials response within 5
  business days if the board's question
  warrants.

---

## 3. Artifact 2 — Prepared response

Direct opening: *Sentinel's exposure to an AI-
driven adverse-action incident with regulatory
response is real and manageable. I'd describe it
in four parts — the specific risk, what's in
place, what's still being built, and a question
I'd like the board to engage on.*

**The specific risk.** Two-thirds of Sentinel's
customer-facing AI systems produce binding
adverse decisions — credit, fraud-detection-
driven holds, certain claims-handling decisions.
Adverse-action obligations under Reg B and the
CFPB's interpretation apply. The exposure: a
customer who contests an adverse action, where
our written explanation does not meet what a
CFPB examiner believes the standard to be,
produces either a CFPB inquiry or, in the worst
case, a settlement.

**What's in place.** Our customer-facing AI
systems operate today with adverse-action
explanations that meet the legal threshold. The
specific explanations are produced by our
underlying decision systems and surface to
customers per the regulatory format. Our
trust architecture, defense-in-depth program,
bias monitoring, and incident response are all
mature.

**What's still being built.** Our formalised
adverse-action explainability *standard* —
the documented program-level commitment that
goes beyond meeting the per-decision legal
threshold — is in process, not complete. We're
operating to it but it's not the documented
current basis. We expect formal completion in
Q3. The CFPB is unlikely to find us non-
compliant with current obligations; we may
find ourselves explaining the gap if asked
about our program standard rather than our
operational practice.

**The question for the board.** The CFPB has
been increasingly clear that the
"black-box defense" doesn't work — they expect
banks to be able to explain adverse decisions
in detail. Our current explainability is
specific but not the level of detail some
recent enforcement actions have called for.
Two options for closing the gap: invest now
in a more substantive explainability program
(estimated $X+, 6-9 months), or wait for the
CFPB to specifically signal the new standard
(saving $X but creating risk of being on the
wrong side of the next enforcement action).
I'd appreciate the board's view on which
posture is right for Sentinel.

— end response —

---

## 4. Reasoning notes

- **Why I structured the response around four
  parts.** The format makes it digestible in
  5 minutes and gives the board specific
  anchors. Without structure, the response
  becomes either too detailed (the §5.2
  education-as-answer pattern) or too vague
  (the hedging pattern).
- **Why I included the honest concession.**
  Per §5.2 — overclaiming is the worst
  pattern. The honest concession about the
  adverse-action standard being "in process"
  acknowledges a real gap; the board respects
  the honesty and the rest of the response
  carries more weight as a result.
- **Why I ended with a question for the
  board.** Per §3.2 — the asks discipline.
  This is exactly the kind of board-decision
  question that benefits from board input
  rather than the CAIRO making the decision
  unilaterally.
- **Why I named specific things not to say.**
  Per the mod-102 Ex-04 reverse-regulator-
  letter discipline — managing information
  disclosure is part of board prep, not just
  regulator prep. Things that are true but not
  helpful in this conversation should not be
  volunteered.
- **What this response under-specifies.** The
  specific dollar amount of the explainability
  investment, the specific 6-9 month
  timeline. These would be presented in the
  follow-up materials if the board engages.

---

Maintained by [Girish Nair](https://github.com/garynair)
