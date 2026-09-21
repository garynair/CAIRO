# Exercise 01 — Walk an Incident Through Response

**Estimated time**: 3 hours
**Deliverable**: Phase-by-phase response narrative (≤ 4 pages)

---

## The scenario

You are the CAIRO at **Northfield Mutual**. On Tuesday
at 09:30 local time, the demographic-stratified
bias monitoring on the claims-triage v2 system
emits a threshold-crossing alert: a 6.5pp
sensitivity gap on the age-80+ subgroup at one
specific site (Site H-12), the second consecutive
month showing the gap.

Per the §6.5 escalation thresholds (mod-107 Ex-04
taxonomy), this triggers automatic AI Risk Council
convene.

## Your assignment

Walk this incident through all five NIST IR phases
+ the response-team mechanics. For each phase,
describe:

- The decisions made and who made them.
- The actions taken.
- The artifacts produced (added to the audit
  ledger per mod-108).
- The notifications considered (consulting the
  matrix per §4).
- The time elapsed.

Carry the incident from detection at 09:30 through
notification, containment, investigation, and
post-incident review.

### Hour 0 (09:30) — Detection (≤ ½ page)

- What detection event fired.
- Who received it.
- The first response.

### Hour 0–1 — First Hour (≤ 1 page)

The four §2.2 decisions in detail. Specifically:

- Verification (is this real?).
- Provisional classification (per mod-107 Ex-04
  taxonomy).
- Single named lead assignment.
- Containment-posture decision.

### Hours 1–24 — Containment + Initial Investigation (≤ 1 page)

- The containment posture chosen and the
  reasoning.
- The investigation team and scope.
- The initial findings.
- The notification matrix consultation (per §4).
- Any notifications triggered or pending.

### Hours 24–168 (one week) — Deep Investigation (≤ ¾ page)

- The deepening investigation.
- Root cause emergence (per §5.2 five-whys).
- Proximate vs. systemic causes.
- Resolution of the incident.

### Days 8–30 — Post-Incident Review (≤ ¾ page)

- Review process per §6.
- Findings: what worked + what didn't.
- Recommendations.
- Loop closure (per mod-103 §6.5).

## Constraints

- The narrative must be specific — not "the team
  decided" but "AI Risk Lead X decided, at
  10:18, to pause Site H-12 specifically".
- The provisional classification must be made
  within the first hour.
- At least one notification obligation must be
  triggered (EU AI Act Art. 73 if any
  EU-resident insureds affected; state insurance
  regulator at minimum).
- The investigation must surface a *systemic*
  cause, not just proximate.
- The post-incident review must produce at least
  3 specific recommendations.

## Rubric

| Criterion | Weight |
|---|---|
| Phase coverage — all five phases | 20% |
| First-hour decisions per §2.2 | 20% |
| Containment posture defensible | 15% |
| Notification matrix consulted | 15% |
| Systemic cause surfaced | 15% |
| Post-incident review produces specific recommendations | 15% |

## Where to submit

`solutions/modules/mod-110-incident-response/exercise-01-walk-incident-through-response/SOLUTION.md`

Reference solution surfaces a systemic cause at the
training-data refresh process (which removed
age-80+ examples that the model had been calibrated
on). Recommendations cover monitoring sensitivity,
training-data refresh review, and a Site H-12-
specific re-validation gate.

## Reading before you start

- Lecture notes §1 (what AI IR is) + §2–§6.
- mod-107 §6 + Ex-04 (classification taxonomy).
- mod-105 Ex-02 (bias metric specification).
- mod-103 Ex-04 (treatment plan format for the
  systemic-cause response).
