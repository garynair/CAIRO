# Exercise 05 — End-to-End Loop on One System

**Estimated time**: 3 hours
**Deliverable**: A linked set of MAP / MEASURE / MANAGE /
GOVERN artifacts for one named system

---

## The scenario

You are the CAIRO at any of the fictional companies used in
mod-101 to mod-103. Pick the company and the system that
best fits your interests; the reference solution uses
**Kerridge Healthcare** (the medical-imaging arm of
Kerridge Industries from mod-101 Exercise 05) and a
**pre-submission AI/ML SaMD algorithm for retinal
imaging** as the system.

This exercise is the capstone of the module. It puts the
artifacts from Exercises 01–04 together end-to-end for one
real-shaped system and shows the loop closing.

## Your assignment

Produce the following linked artifacts for one named
system:

### Artifact 1 — Inventory row

The system's row in the AI system inventory, populated
with the attributes from Chapter 3 §*The inventory*.

### Artifact 2 — Classification

Regulatory classification (EU AI Act tier + sector
applicability) and AI risk taxonomy classification (which
top-level categories apply).

### Artifact 3 — Impact assessment (compressed)

Using the template from Exercise 02 (or a defensible
equivalent), a compressed impact assessment for the
system. Compressed means: the structure is complete but
each section is one paragraph maximum. The point is to
show *the shape*, not to produce a full assessment.

### Artifact 4 — Measurement plan (compressed)

Using the format from Exercise 03, a compressed
measurement plan: for each of the top three risks from the
impact assessment, one leading + one lagging indicator
with threshold, response, and owner.

### Artifact 5 — Risk-treatment plan (compressed)

Using the format from Exercise 04, a compressed treatment
plan for the **one most material risk** from the impact
assessment. Full treatment, including residual.

### Artifact 6 — GOVERN summary

A short summary (½ page maximum) that addresses:

- Where this system lives in the risk register (Chapter 7
  §*The AI risk register*).
- What roll-up to the board report it would receive in
  the next quarter (Chapter 7 §*The board report*).
- The named GOVERN-level review cadence for this system
  (from the operating-rhythm calendar).
- One concrete way the loop might close: a pattern that,
  if it appeared in this system's MEASURE outputs, would
  trigger a GOVERN-level change (policy, taxonomy,
  cadence, ownership) — see Chapter 7 §*Closing the
  loop*.
- **Appetite alignment.** Name whether the treated
  residual risk sits within, at, or above the appetite
  tolerance for its category (Chapter 8 §*Category-level
  tolerances*). If above, name the escalation path.

## Constraints

- **Linked**: the artifacts must reference each other.
  The classification (Artifact 2) refers to the inventory
  row (Artifact 1) by ID. The impact assessment
  (Artifact 3) covers the risk categories named in the
  classification. The measurement plan (Artifact 4)
  measures the risks named in the assessment. The
  treatment plan (Artifact 5) treats one of those risks.
  The GOVERN summary (Artifact 6) refers to the whole
  set.
- **Compressed**: each artifact except the GOVERN summary
  is one to one-and-a-half pages. Total length cap: 8
  pages.
- **One named system throughout**. Do not jump between
  systems mid-exercise.
- **Honest gaps**: the impact assessment should name at
  least one risk that the measurement plan does not yet
  fully cover. The treatment plan should name residual
  risk. The GOVERN summary should name the cadence at
  which the gaps would be reviewed.

## Rubric

| Criterion | Weight |
|---|---|
| Inventory row — populated with the Chapter 3 attributes | 10% |
| Classification — both regulatory and taxonomy | 10% |
| Impact assessment — uses template, specific failure modes | 15% |
| Measurement plan — leading + lagging per top-3 risk, observable thresholds | 15% |
| Treatment plan — controls linked to indicators, residual named | 15% |
| GOVERN summary — register placement + roll-up + cadence + loop-closing example + appetite alignment | 15% |
| Linkage — artifacts reference each other coherently | 15% |
| Length discipline — ≤ 8 pages total | 5% |

## Where to submit

`solutions/modules/mod-103-ai-risk-frameworks/exercise-05-end-to-end-loop/SOLUTION.md`

Reference solution uses Kerridge Healthcare's pre-
submission retinal-imaging algorithm as the system.

## Reading before you start

- All previous mod-103 exercises (this builds on them).
- Chapter 7 (GOVERN and Closing the Loop), especially
  the end-to-end synthesis diagram and the loop-closing
  patterns.
- Chapter 8 (The Risk Appetite Statement) for the
  appetite-alignment tag on the GOVERN summary.
- mod-101 Exercise 05 reference for the Kerridge context
  (if you use that scenario).
