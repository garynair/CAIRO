# Synthesis Memo — 30-day Incident Closeout — Reference Solution

**To:** CEO; Board; executive team.
**From:** [CAIRO name], Incident Commander.
**Date:** Day 30.

---

## 30-day outcome

Northrise has emerged from the GuardianGPT
tenant-isolation incident with the
following posture:

- Vulnerability contained at Day 0; no
  recurrence in 30 days of post-
  containment operation.
- All 180 customers notified per the
  cohort framework. Cohort A (7 high-
  exposure) all engaged in direct
  conversations.
- Regulatory notifications completed for
  all applicable regimes. No formal
  regulatory action against Northrise
  to date.
- Independent third-party verification of
  remediation underway; preliminary
  findings positive.
- Press coverage to date: 2 trade-
  publication stories (Bloomberg,
  TechCrunch) following Sentinel's
  required public disclosure Day 18.
  Coverage was substantive but neutral
  in tone; cited Northrise's
  transparency and rapid response
  positively.

## Customer-relationship state

**Cohort A (high-exposure, 7).** Three
customers have indicated continued
commitment; renewals on schedule. Two
customers are in detailed remediation-
verification discussions; renewal status
uncertain but not exited. Two customers
have given notice of intent to exit at
the end of current term (collectively
~$8M ARR).

**Cohort B (source-exposure, 8, some
overlap with A).** All engaged; no
exits yet; expect 1-2 may exit per
subsequent investigations.

**Cohort C (triggered-but-not-meaningful,
~30).** 28 engaged; 2 unresponsive but
not flagged as risk. No exits.

**Cohort D (triggered-no-disclosure,
~10).** All engaged; no concerns.

**Cohort E (not affected, 133).** All
notified; most appreciative. ~20 have
asked detailed follow-up questions
about Northrise's controls. ~5 have
engaged at executive level. No exits;
several have expressed strengthened
commitment based on the proactive
notification approach.

**Pipeline (not customers; prospects):**
~12 in-flight deals delayed or paused
pending Northrise's verification
work. ~3 expected losses; ~7 expected
to close with delay.

## Response cost

| Category | Cost |
|---|---|
| Response staffing (30 days; CAIRO, CTO, CISO, GC, Customer Success teams) | ~$1.8M |
| Customer credits and make-goods | ~$3.5M (preliminary) |
| Third-party assurance (pen test, SOC 2) | ~$600K |
| Engineering remediation work (Q1) | ~$2.5M (capacity diverted from product roadmap) |
| Legal (external counsel for notification, privilege, regulatory) | ~$1.4M |
| Communications and PR | ~$300K |
| **Direct total over 6 months** | **~$10.1M** |
| **Indirect: ARR exit (Cohort A) + pipeline loss (estimated)** | **~$12M-15M** |
| **Total exposure 6 months** | **~$22M-25M** |

Pre-IPO valuation impact: not yet
quantified by Northrise's investors;
expected modest given the response
discipline.

## What we got wrong over 30 days

Per honesty discipline. Four substantive
items.

**1. We underestimated the L2 triage
failure as a top-level finding.** In the
first week of response, the L2 triage
gap was treated as a process issue
to be addressed in Deliverable 05.
The post-mortem repositioned it as
the largest single failure mode of
the incident. We should have framed
it as a top-level finding from Day 7,
which would have given the
remediation work the right relative
weight earlier.

**2. The Day 0 customer-comms first
draft was too defensive in tone.**
The draft used hedging language
("we are investigating reports of...")
that read as protective rather than
accountable. CAIRO revision before
sending corrected the tone. The
process failure: the draft was not
reviewed by CAIRO before reaching
near-final state. Going forward,
all customer-comms drafts in
incident response require CAIRO
review before any external-facing
draft state.

**3. The Cohort-A high-exposure
notification template was finalized
later than the scope-analysis work
warranted.** The scope analysis was
complete Day 4; the template was
finalized Day 5; the notifications
went out Day 5-6. A 24-48 hour
slip from scope-complete to
notification-out is not catastrophic
but reflects under-resourced
notification drafting.

**4. The investor communications drafting
ran longer than planned.** Day 8
vs. planned Day 5. The 3-day slip
reflects under-prioritisation of
investor comms during the customer-
notification crunch. CFO observed
that earlier investor communication
would have produced better investor
support during the press window.

## What's fragile going forward

Three specific fragilities.

**1. The Cohort-A exits (~$8M ARR).**
The two announced exits are real and
expected. The fragility is that
additional Cohort-A or Cohort-B
customers may exit if subsequent
investigation (theirs or ours)
surfaces additional concerns. The
~$8M is the floor; the upper
bound could be $20M-30M if a
broader exit wave develops.

**2. The independent pen test
results pending Day 45.** If the
specialized AI-security firm's
verification work surfaces
additional vulnerabilities, the
customer-relationship work
restarts. This is the largest
single risk to the customer
posture in the next 45 days.

**3. The S-1 disclosure if Northrise
proceeds with public-company
preparation in 2026.** SEC and
underwriter review of the
incident disclosure will be
substantive. Going public on
schedule may not be feasible
depending on disclosure
requirements and market
conditions.

## What this changes about Northrise

Structurally:

1. **Default-deny as engineering
   norm.** No longer an unwritten
   pattern; encoded in style guide
   and static analysis. Refactoring
   touching security invariants is
   classified differently.
2. **Multi-layer tenant isolation
   in product architecture.** The
   defense-in-depth pattern is now
   the standard for any
   multi-tenant feature.
3. **L2 triage discipline.**
   Cross-tenant content as
   triage category; broader
   willingness to escalate
   patterns rather than treat
   individual reports as
   isolated hallucinations.
4. **Customer-facing observability
   as product feature.** Building
   self-service investigation
   tools as part of the standard
   product surface, not as
   incident-response artifact.
5. **CAIRO posture in incident
   response.** This incident
   established CAIRO as Tier-1
   incident commander for
   AI-product-behavior incidents.
   The boundary with CISO is
   tested and durable.
6. **Investor communication
   discipline.** Earlier and more
   structured investor
   communication; investor
   confidence is a real
   resource that requires
   maintenance.

## Outstanding Board questions

Q1 Board meeting will likely include:
- What is the durable customer-
  relationship state? (Answer
  comes from Q1 renewal
  outcomes.)
- What is the verification result
  from the independent pen test?
  (Available Day 45.)
- What is the SEC / S-1
  disclosure posture if
  Northrise proceeds with public-
  company preparation? (Counsel
  engagement ongoing.)
- What is the cumulative cost
  picture at quarter-end? (CFO
  will quantify.)
- What other systems may have
  similar patterns? (Internal
  audit in flight.)

Q2 Board meeting:
- Customer-relationship state
  at full Q1 renewal cycle.
- Verification work complete.
- Cost picture firmer.

## CAIRO posture going forward

This incident reframes the CAIRO
work for the next 6-12 months
in three ways:

**1. Operational, not strategic,
weighted.** The next 6 months
are about executing the
remediation, supporting
customers through verification,
and supporting the press /
regulatory / investor cycles.
Strategic AI-governance work
defers.

**2. AI Risk Council cadence
elevated.** Monthly is
insufficient during this
window; weekly Council
meetings through Q1.

**3. Sentinel relationship as
strategic asset.** Sentinel's
red team caught the incident;
their handling of the
disclosure was responsible
and constructive. Maintaining
that relationship as a
strategic partner — and
extending the model to other
customers — is durable value
from the incident.

---

## Reasoning notes

- **Why I named the four "what
  we got wrong" items
  substantively.** Synthesis
  memos that go to Board and
  CEO under-attribute or
  over-attribute. Honesty
  discipline names items with
  enough specificity to be
  acted on.
- **Why I quantified cost in
  ranges.** Premature
  precision creates false
  confidence; vague qualitative
  framing fails CFO
  conversations. Ranges with
  reasoning are the right
  posture.
- **Why I named the Cohort A
  exits as exit risk and
  Cohort A renewals as
  positives.** Both are real;
  framing only positives reads
  as defensive. The Board
  needs both.
- **Why I named the S-1
  disclosure question as a
  fragility.** Northrise is
  pre-IPO; the IPO timeline is
  material to existing
  investors and to Northrise
  employees with equity. Not
  raising it in the synthesis
  understates the picture.
- **What I would do
  differently.** The
  synthesis memo could have
  been delivered Day 25
  rather than Day 30 if the
  drafting had run in
  parallel with the post-
  mortem. The 5-day delay
  is not material but does
  reflect under-
  prioritisation of the
  synthesis vs. operational
  work in week 4.

---

Maintained by [Girish Nair](https://github.com/garynair)
