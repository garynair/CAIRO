# Exercise 02 — Design a Continuous-Evidence Cadence

**Estimated time**: 3 hours
**Deliverable**: Cadence specification (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Northfield Mutual**. The
state insurance regulator's recent inquiry (mod-108
Ex-02) included a question about how Northfield
demonstrates compliance with its bias-monitoring
obligations *between* quarterly reviews. The
regulator's specific concern: programs that only
review evidence quarterly may miss developing
issues for up to 90 days.

The CRO has asked you to design a **continuous-
evidence cadence** for the bias-monitoring control
that addresses the regulator's concern.

## Your assignment

For Northfield's bias-monitoring control (per
mod-105 Ex-02 + mod-108 Ex-02 references):

### Section 1 — Control restatement (≤ ½ page)

State the control whose evidence cadence you are
designing — including its operating activity,
evidence produced, and owner.

### Section 2 — The three cadences (≤ 1½ pages)

Per §3.2, specify the **operating cadence**,
**steward cadence**, and **audit cadence** for this
control:

For each:

- Who reviews.
- What they review.
- The trigger that produces the review (calendar
  date, threshold crossing, etc.).
- The artifact produced by the review.
- The escalation path if review surfaces an
  issue.
- The interface with the audit ledger (mod-108).

### Section 3 — Evidence collection patterns (≤ ¾ page)

Per §3.3, specify which evidence-collection pattern
applies to which evidence type for this control:

- Telemetry-derived (compute from production
  signals).
- Attested (named role attests).
- Document-as-evidence (signed document is the
  evidence).

For each pattern used, describe the specific
implementation.

### Section 4 — What goes wrong, addressed (≤ ¼ page)

Address the three failure modes from §3.4:

- Telemetry that doesn't aggregate to control
  evidence — how the design prevents this.
- Attestation fatigue — how the cadence calibrates
  to avoid it.
- Documents not reviewed — how the design ensures
  review.

## Constraints

- The operating cadence must address the
  regulator's "between-quarterly" concern
  substantively.
- The cadence must use **at least two** of the
  three patterns from §3.3.
- Each review must produce an **artifact** that
  becomes evidence — reviews that produce no
  artifact are ceremonial.
- The cadence calibration (per §3.5) must be
  defended for each level.

## Rubric

| Criterion | Weight |
|---|---|
| Three cadences specified with reviewer + trigger + artifact | 35% |
| Evidence patterns — at least two used | 15% |
| Failure-mode mitigations addressed | 15% |
| Operating cadence addresses regulator concern | 15% |
| Audit ledger interface specified | 10% |
| Length discipline — ≤ 3 pages | 10% |

## Where to submit

`solutions/modules/mod-109-compliance-operations/exercise-02-continuous-evidence-cadence/SOLUTION.md`

Reference solution uses weekly operating-cadence
review of demographic monitoring telemetry by the
Algorithm Quality Office Clinical Validation Lead;
monthly steward review by the AI Risk Lead;
annual audit cadence by Internal Audit.

## Reading before you start

- Lecture notes §3 (continuous evidence collection).
- mod-105 Ex-02 reference (the bias metric
  specification).
- mod-108 Ex-02 reference (the evidence package
  showing this control in operation).
