# Chapter 7 — GOVERN and Closing the Loop

## Why this chapter exists

GOVERN is the NIST AI RMF function that says *given
everything above, is the program working, and if not,
what do we change*. Unlike the other three, GOVERN is
continuous and cross-cutting — it does not run once per
system per year; it runs against the *pattern* the other
three functions produce.

A program can perform MAP, MEASURE, and MANAGE with
discipline and still fail if the outputs of those
functions never trigger a change to policy, taxonomy,
cadence, or ownership. That is what the loop closing
means. This chapter names the observable behaviour of
the loop closing, defines the GOVERN artifacts that make
it visible, and finishes the end-to-end synthesis that
Exercise 05 asks you to run.

## What GOVERN produces

Fewer named artifacts than the other functions, but
higher leverage.

1. **The AI risk register** — the consolidated, current
   view of every material risk across the portfolio.
2. **The quarterly board report** — the rolled-up view
   of the program's posture, including material change
   since last quarter.
3. **The operating-rhythm calendar** — the cadence of
   every GOVERN review, RACI for every artifact, and
   the escalation paths.
4. **The policy hierarchy** — the controlled set of
   policies and standards the program operates under.

The four together are the working definition of the
program at the GOVERN level. Regulators reading a
program's GOVERN maturity read these four.

Note: **the risk register is operated by the
head-of-ai-governance, not the CAIRO.** The CAIRO reviews,
signs off, escalates. The head-of-ai-governance keeps the
register current, chases owners, closes items. mod-101
Chapters 5–7 have the peer-boundary language for this
split; Chapter 8 in this module has the risk-appetite
handoff. If the CAIRO is personally editing the register,
the operating model is under-staffed.

## The AI risk register

The register is **the single source of truth** for
material risks. Not every risk lives there. Operational
nuisances do not. Material risks do.

A risk is *material* when it:

- Has been surfaced by MAP or escalated from MEASURE.
- Is rated above the program's materiality threshold, set
  by policy in advance (not case-by-case).
- Has a named owner (first-line role).
- Has a current treatment status (from the treatment
  plan; Chapter 6).

The register is not the treatment plan; it is a summary
row that points to the plan. The row includes:

| Column | What it says |
|---|---|
| Risk ID | Stable identifier |
| Risk (one line) | The specific failure mode |
| System(s) affected | Inventory ID(s) |
| Category (Chapter 2) | Top-level taxonomy category |
| Current rating | Residual, from treatment plan |
| Appetite alignment | Within / at / above (Chapter 8) |
| Treatment status | Planned / in-flight / effective / accepted |
| Owner | First line role |
| Second-line reviewer | Named 2LOD role |
| Last review | Date |
| Next scheduled review | Date |

Discipline:

- **Revisited monthly** by the AI Risk Council (or
  equivalent, depending on operating model — see
  mod-101 Chapter 6).
- **Summarised quarterly** for the Board Risk Committee.
- Risks at the same status for **more than two quarters**
  are reviewed for whether they should be re-rated,
  accepted formally, or exceptioned. Static risks are a
  program smell.

## The board report

The quarterly board report is the highest-stakes artifact
the CAIRO produces. A working board report is short — 3–5
pages — and structured to address what the board can act
on.

Sections that work:

1. **Current risk posture, rolled up by taxonomy
   category.** The board sees Bias-and-Fairness posture,
   not a per-system list. The board is not staffed to
   diff a per-system list quarter over quarter.
2. **Material changes since last quarter.** New material
   risks, retired ones, ratings that moved, exceptions
   granted or expired.
3. **Material risks outside appetite.** Per Chapter 8's
   appetite statement — the risks the program is
   currently carrying that are above the signed
   tolerance. Named, not paraphrased.
4. **Programmatic indicators.** A small handful, not a
   dashboard. Coverage (systems in scope vs. total),
   assessment currency (systems whose assessment is
   older than twelve months), residual acceptance
   distribution.
5. **Asks of the board.** Resources, ratifications,
   decisions to be made.

The report should land **one clear request per quarter**.
Reports with no asks are decoration. Reports with five
asks dilute the board's attention.

The report is signed by the CAIRO and countersigned by the
CRO (in the common operating-model configuration where
the AI Risk Council is CRO-owned; see mod-101
Chapter 6).

## The operating-rhythm calendar

A program's operating rhythm is the cadence at which each
function runs. When published, it makes the program
observable — anyone can tell whether the cadence is being
kept.

A working rhythm:

| Activity | Cadence | Owner |
|---|---|---|
| Inventory attestation | Monthly | Business unit leads |
| Impact-assessment review | On material change + annually | Model owner + AI Review Board |
| Measurement review | Weekly per system, monthly across program | Model owners + AI Risk Lead |
| Risk register update | Monthly | Head-of-AI-Governance |
| AI Review Board | Bi-weekly or monthly | CAIRO chairs |
| AI Risk Council | Monthly | CRO chairs (or per operating model) |
| Board Risk Committee report | Quarterly | CAIRO + CRO |
| Risk appetite review | Annual | CEO + Board, CAIRO proposes |
| Annual program review | Annually | CAIRO + Internal Audit |

Two disciplines:

- **The rhythm is published.** Roles know when their
  artifacts are due. The rhythm sits inside the policy
  hierarchy, not on a wiki page that changes silently.
- **The CAIRO's calendar reflects the rhythm.** If the CAIRO
  is spending most weeks on unscheduled escalations, the
  rhythm is not working — either it is missing an
  activity or the operating model is wrong. Both are
  diagnostic.

## The policy hierarchy

Two-tier or three-tier, per the operating-model choice in
mod-101 Chapter 6. What matters at the GOVERN level:

- The **AI policy** — board-approved, changes rarely,
  states principles and scope.
- The **standards** underneath — CAIRO-approved, change
  quarterly at most, state required practices (a
  development standard, a monitoring standard, an
  incident standard, an evaluation standard).
- The **procedures** underneath those — owned by roles
  in first and second line, change as often as needed.

The GOVERN artifact here is the *policy hierarchy
document itself* — one page showing which policy /
standard / procedure exists, who owns it, when it was
last updated, when it is next due for review. Programs
that cannot produce this on demand are running policies
they cannot audit.

## Closing the loop — what it looks like

The loop closes when an item from MEASURE or MANAGE that
indicates the program is *not working* triggers a change
to GOVERN — policy, taxonomy, cadence, or ownership.
Programs that never change GOVERN in response to
MEASURE / MANAGE findings are not closing the loop; they
are running through the motions.

Concrete patterns.

- **A consistent MEASURE pattern** — a category's
  leading indicators cross thresholds across multiple
  systems — triggers a **policy update** on that
  category's required controls. Example: bias leading
  indicators drift across three systems in a quarter →
  the Development Standard adds a mandatory
  subgroup-performance review at model release.
- **A recurring MAP gap** — impact assessments across
  multiple systems miss the same failure mode class —
  triggers a **template update**. Example: three
  incidents in six months involve integrations with
  vendors that were not modelled → the impact
  assessment template gains a Section 3 prompt on
  third-party surfaces.
- **A treatment-plan pattern** — residual risk repeatedly
  accepted above the appetite for one category —
  triggers a **risk appetite review** (Chapter 8).
  Example: five treatment plans accept High residual in
  Reputational risk → the CEO and Board are asked
  whether the appetite is right or the treatment
  practice is under-invested.
- **An operating-rhythm mismatch** — the AI Risk Council
  is escalating the same items to the CAIRO between
  meetings — triggers a **cadence update**. Example:
  bi-weekly review is insufficient for the current
  portfolio → the CAIRO adjusts the rhythm and the policy
  hierarchy reflects it.

If twelve months pass with no GOVERN-level change
triggered by the lower functions, the loop is not
closing. The CAIRO's job is to detect this and respond.
This is the diagnostic Exercise 05 makes you exercise
end-to-end.

## The end-to-end synthesis

The six artifacts, once produced, form a chain:

```
Inventory  ─┐
            ├─→ Impact assessment
Classify.  ─┘         │
                      ├─→ Measurement plan
                      │         │
                      │         ├─→ Treatment plan
                      │         │         │
                      │         │         └──┐
                      └─────────┴────────────┼─→ Risk register
                                             ├─→ Board report
                                             └─→ Loop closure into
                                                 policy / taxonomy /
                                                 cadence / ownership
```

Every arrow is a traceable dependency. When a regulator
asks *"how did this control get here"*, the chain
supports the answer *"from the treatment plan on Risk
X in System Y, which cited the failure mode from the
impact assessment on 2026-Q2, which cited the taxonomy
category from our v3 policy"*. Programs that can walk
the chain pass reviews. Programs that cannot are
producing paperwork.

Exercise 05 walks the chain for one system end to end.
Chapter 8 attaches the risk-appetite statement above
the chain — the signed statement of what residual the
enterprise will accept.

## What GOVERN is *not*

Two clarifications.

- **GOVERN is not the AI Review Board.** The Review
  Board is one *forum* the GOVERN function operates
  through. Confusing forum and function is a common
  new-CAIRO mistake — one produces meetings, the other
  produces policy changes.
- **GOVERN is not compliance.** Compliance is a
  neighboring discipline (mod-101 Chapter 1) that
  checks whether required external rules are met.
  GOVERN checks whether the internal system is
  producing outcomes the board can defend. A program
  can pass compliance and fail governance if the
  compliance frame does not cover the operational
  behaviour that produces the incidents.

## Summary

- GOVERN produces four artifacts: the risk register,
  the quarterly board report, the operating-rhythm
  calendar, and the policy hierarchy.
- The risk register is operated by the
  head-of-ai-governance, reviewed and signed by the CAIRO;
  it is a summary of material risks pointing to
  treatment plans, not the treatment plans themselves.
- The board report is 3–5 pages, rolled up by taxonomy
  category, with one clear ask per quarter.
- The operating rhythm is published and observable; the
  CAIRO's calendar reflects it.
- The loop closes when a MEASURE or MANAGE pattern
  triggers a change to policy, taxonomy, cadence, or
  ownership. No GOVERN-level change in twelve months is
  a diagnostic that the loop is not closing.
- The six artifacts (inventory → classification →
  impact assessment → measurement plan → treatment
  plan → GOVERN summary) form a chain a regulator can
  walk from control back to policy. Exercise 05 walks
  it.
- GOVERN is not the AI Review Board (that is a forum)
  and not compliance (that is a different discipline).
