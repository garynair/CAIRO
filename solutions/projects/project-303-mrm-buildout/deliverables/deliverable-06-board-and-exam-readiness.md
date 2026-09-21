# Deliverable 06 — Q4 Board Package and OCC Exam Readiness — Reference Solution

## 1. Solution overview

Two artifacts. (1) Board package: 12-page
deck for the Risk Committee at day 75
covering the MRM extension, inventory, four
findings, accomplishments, gaps, exam-
readiness. (2) OCC exam memo: 3-page
working document anticipating the four most
likely lines of inquiry, with Tessera's
documented response on each. Both artifacts
honest about gaps; neither performative.

---

## 2. Q4 Board package (summary)

> **TESSERA BANK Q4 RISK COMMITTEE — AI/ML
> MRM EXTENSION**
> *Author: CAIRO; co-presenter: CRO.*

### Section 1 — Executive summary

Over the past 90 days, Tessera has extended
its Model Risk Management function to cover
artificial intelligence and machine learning
models. The work includes: an updated MRM
Policy (v4.3, this Risk Committee approval);
a complete model inventory (42 AI/ML models
in production or in scope); a tiering
framework now applied to all 42; an
AI/ML-specific validation methodology;
an ongoing monitoring framework; and
readiness work for the February OCC
examination.

Four substantive findings surfaced through
the inventory process; all are being
addressed.

### Section 2 — The MRM extension

Policy v4.3 amends MRM Policy to include
AI/ML models. Definition of "model" is
materially-influences-decision-based; vendor
LLMs are in-scope when their output
materially informs decisions; office-
productivity LLM use is governed separately
under Acceptable AI Use Policy.

Tiering: 3-tier framework (~8 Tier-1, ~24
Tier-2, ~10 Tier-3 across 42 models).

Validation methodology: SR 11-7 three-pillar
adapted to AI/ML; preserves validator
independence; documented for OCC examination.

Monitoring: six streams; phased capability
buildout through Q1.

### Section 3 — The four findings

**Finding 1 — Treasury "smart cash position"
forecasting.** Operating ungoverned 8 months.
Material to Tessera. Action: operational
pause (immediate); provisional Tier-1; full
validation Day 60.

**Finding 2 — Wealth-management portfolio
rebalancing retrain.** Performance
degradation post-retrain (~22% sharpe
degradation). Action: rollback (Day 5);
investigation per mod-110; systemic cause
identified (change-management gate not
operating after training data refresh);
correction in flight.

**Finding 3 — HR resume-screening vendor
LLM.** In-scope per Policy v4.3; provisional
Tier-1; vendor-model validation methodology
applies. EEOC outcome examination required.

**Finding 4 — Two customer-facing consumer-
banking models with complaint patterns.**
Provisional Tier-1; validation Day 45.

### Section 4 — Accomplishments vs. plan

Achieved as planned:
- Policy v4.3 (Risk Committee approval at
  this meeting).
- Inventory complete (42/42).
- Tiering framework operational.
- Validation methodology complete and
  exam-ready.
- Monitoring framework operational for
  Streams 1, 2, 5, 6 across all Tier-1
  and Tier-2 models.

Behind plan:
- Validation completion: 6 of 28 new-to-
  MRM models validated by Day 90 vs.
  planned 8. The Treasury and wealth-
  management findings consumed
  validator-bandwidth ahead of plan;
  outcome is honest sequencing not
  capacity gap.
- Monitoring Stream 3 (performance vs.
  ground truth) for non-Tier-1 models
  deferred to Q1 per the phased buildout.

### Section 5 — Outstanding gaps and plan

- 22 of 28 new-to-MRM models await
  validation. Q1 completion expected for
  ~18; remaining ~4 by end of Q2.
- Stream-3 monitoring buildout for non-
  Tier-1 models in Q1.
- MRM validator staffing: +2 senior
  AI/ML-capable validators needed (CFO
  decision; targeting end-of-Q1 hire).
- Internal Audit Q1 audit will examine
  the framework as it stands; some
  findings expected; CAIRO and CRO have
  pre-engaged with Audit.

### Section 6 — Exam-readiness summary

February OCC examination is in scope for
AI/ML governance review. Tessera is
exam-ready in the following sense:
- Documented framework (this Risk Committee
  approval makes the documentation
  authoritative).
- Operational inventory.
- Active validation pipeline (visible
  evidence of work).
- Honest gap documentation.

Tessera is NOT exam-ready in the following
sense:
- Not all 28 new-to-MRM models will be
  fully validated by exam date. The OCC
  will see the validation pipeline in
  progress, not complete.
- The Treasury finding is an embarrassing
  artifact of pre-CAIRO governance gaps;
  the response is in-flight at exam time.

The OCC exam memo (next section) addresses
these explicitly.

### Section 7 — Risk-decision asks

None required from the Risk Committee
beyond approval of MRM Policy v4.3 and
endorsement of the framework. CFO request
(separate) for +2 MRM validator headcount
is in flight.

---

## 3. OCC Exam Readiness Memo

> **For: CRO, CEO.**
> *Working document. Not for external
> distribution.*

### Anticipated lines of OCC inquiry

Four most-likely areas:

**A. Scope of MRM extension.** "How do you
determine which AI/ML systems are in MRM
scope?" Tessera response: Policy v4.3
definition (materially-influences-decision);
worked examples (in-scope vs. out-of-scope);
applied to the 42-model inventory.

**B. The Treasury finding.** "How was a
material model operating without
governance for 8 months?" Tessera
response: governance gap pre-CAIRO arrival;
CAIRO inventory work surfaced it within 60
days of CAIRO start; immediate pause +
validation; systemic corrections in
monitoring framework Stream 6 prevent
recurrence. Honest framing wins this
question.

**C. Vendor-model treatment.** "How are
vendor LLMs validated under information
asymmetry?" Tessera response: Deliverable
04 methodology; HR vendor LLM as worked
example; explicit acknowledgment of
limits; compensating monitoring.

**D. Validator independence.** "How is
validator independence preserved when the
CAIRO has AI-specific technical expertise?"
Tessera response: CAIRO does NOT validate;
CAIRO authors methodology and provides
technical expertise to MRM; MRM remains
independent decision-maker; this design
choice was made explicitly.

### Likely points of pressure

- Validator capacity (MRM short-staffed
  for the AI/ML workload; +2 hire is in
  flight but not landed by exam time).
- Stream-3 monitoring buildout for non-
  Tier-1 (will not be complete by exam).
- Subgroup performance documentation for
  several Tier-2 models (validation work
  not complete by exam).

### Response posture

Honest framing on each. Documentation of
what is in-flight; specific dates and
deliverables. Tessera is not asking the
OCC to ignore the gaps; we are documenting
the path.

### Personnel and document logistics

- Lead exam presenter: CRO. Backup: CAIRO.
- Document custodian: Head of MRM.
- Pre-exam internal walkthrough: Day 130
  (10 days before exam).
- Document binder: assembled by Day 135.

### What to update if exam date moves

If the exam date moves earlier: Tier-1
validation completion may not be achieved;
the response posture shifts to "this is
the validation plan and current state."
If the exam date moves later: more models
will be validated; subgroup performance
work for Tier-2 may be substantially
complete; the posture strengthens.

---

## 4. Reasoning notes

- **Why the four findings get top-of-deck
  placement.** Risk Committee reads
  top-down; burying findings looks
  evasive. Top placement reads as
  discipline.
- **Why both the "exam-ready in this sense"
  AND "NOT exam-ready in this sense"
  sections.** Honesty discipline. A
  Risk Committee that hears only
  "exam-ready" is a Risk Committee that
  is surprised in February.
- **Why the OCC memo is separate from the
  Board package.** Different audience,
  different framing. Risk Committee gets
  the structured framework view; CRO/CEO
  get the working-document view that
  includes Tessera's anticipated
  responses to likely OCC pressure.
- **Why the Treasury finding response is
  framed as "the systemic correction
  prevents recurrence" rather than
  "Treasury was at fault."** mod-110
  systemic-cause discipline. The OCC will
  read fault-finding as defensive;
  systemic-cause framing reads as
  organisational maturity.
- **What I would do differently.** I might
  have included a quantitative scorecard
  in the Board package (numbers of models
  per tier, validation completion %,
  monitoring stream coverage %).
  Quantitative grounding helps Risk
  Committee follow the picture. Trade-off:
  premature precision can look defensive.

---

Maintained by [Girish Nair](https://github.com/garynair)
