# Synthesis Memo — Conformity Submission Preparation — Reference Solution

**To:** Kerridge Healthcare CEO; Kerridge
Industries Board; Notified Body engagement
file.
**From:** [CAIRO name], Chief AI Risk Officer,
Kerridge Healthcare.
**Date:** Day 60 of conformity preparation arc.

---

## What was produced

Over the 60-day arc, Kerridge produced the
EU AI Act conformity package for KH-AI-027:

1. Classification analysis — high-risk under
   Art. 6(1) and Art. 6(2) Annex III(5)(a),
   Art. 6(3) exemption rejected, Annex VII
   third-party conformity route.
2. Article 9 Risk Management System — 11
   risks; 4 acknowledged material residuals.
3. Article 10 Data and governance
   documentation — three honest data gaps
   named.
4. Article 11 + Annex IV Technical
   documentation summary — ~6-page navigable
   summary over the ~85-page technical file.
5. Article 14 Human oversight design —
   asymmetric escalation with three
   automation-bias controls.
6. Article 72 Post-market monitoring plan —
   six monitoring streams; explicit pause/
   withdraw criteria.
7. Article 73 Serious incident reporting
   procedure — conservative-default
   classification gate.

The package supports the Annex VII third-
party conformity assessment with the
engaged Notified Body, which begins formal
review next week.

## What the Notified Body is about to see

I expect the Notified Body to focus on:

- **The Art. 6(3) exemption analysis.** They
  will probe whether KH-AI-027 might fit the
  "deviation detection" exemption (#3) under
  a different workflow framing. We have
  documented our rejection of this with
  explicit reasoning.
- **The data governance bias examination.**
  The three honest data gaps will be the
  first detailed conversation. They will
  press on the South-Asian under-
  representation specifically.
- **The Article 14 oversight design,
  particularly the asymmetric escalation
  framing.** They have seen symmetric
  designs before; the asymmetric framing
  requires explanation.
- **The PMM plan's pause/withdraw thresholds.**
  Quantitative thresholds invite specific
  challenge.

## What we got wrong over the 60 days

Per honesty discipline. Three substantive
items:

**1. The classification analysis took longer
than planned.** The Art. 6(3) exemption
analysis — particularly walking through all
four exemptions explicitly — was the right
call but consumed 8 working days vs. the
planned 3. We compressed Articles 11 and 14
work to compensate, which left the technical
documentation summary in less-than-ideal
shape (see "Fragility" below).

**2. We initially designed the PMM thresholds
too aggressively.** The first draft had
1.5pp subgroup performance threshold; the
Clinical Advisory Board flagged that this
would generate false alarms at validation-
set sample sizes. We revised to 3pp + two-
month confirmation. The revision is right,
but the initial mistake reflects a tendency
in the team toward defensive-too-tight
thresholds.

**3. We under-invested in customer (deployer
hospital) communication preparation during
the 60-day window.** Operating-instructions
documentation is complete; deployer-side
training materials are not. We have a 30-
day post-conformity-decision window to
catch up; this is feasible but tight.

## What's fragile in the conformity package

Per honesty discipline. Three specific
fragilities:

**1. South-Asian subgroup performance
documentation.** The validation-set sample
size for the South-Asian subgroup is
~6% of training data. While performance is
within threshold (98.0% sensitivity),
statistical power is limited. If the
Notified Body presses hard on whether the
documented performance is reliable, our
answer (additional data acquisition
underway; ongoing monitoring will detect any
deterioration) is honest but does not
fully resolve the concern. Risk: Notified
Body may request additional validation
before approval, adding 3-6 months to
timeline.

**2. The asymmetric escalation oversight
design depends on clinician training and
discipline.** The override-rate monitoring
threshold (10%) catches gross automation
bias but does not protect against subtle
patterns. If a deployer-site clinician
accepts the AI's "non-referable"
classification in a case that warranted
clinician judgment, the system does not
detect this. The monitoring stream is the
backstop, not a real-time control.

**3. The technical documentation summary
under-explains the cybersecurity
treatment.** Cybersecurity is one section
in the summary; the underlying analysis is
solid (in TF/Section-07) but the summary
under-represents the depth. If the Notified
Body's cybersecurity reviewer is the first
contact, this could create a worse-than-
warranted impression.

## Launch implication

**Assuming Notified Body engagement proceeds
per plan:** Expect approval decision in
4-6 months from formal submission start.
EU launch in 7-8 months. The first six
months of EU operation will be cautiously
phased, starting with 3-5 anchor customer
sites under enhanced monitoring before
broader rollout.

**Assuming Notified Body requests additional
validation work:** The South-Asian
subgroup data is the most likely trigger.
Additional 6-9 months for data acquisition,
re-validation, re-submission. Total path
to EU launch: 14-18 months from today.

**Assuming the conformity assessment fails
outright:** Unlikely but not impossible.
Most likely cause: a clinical-safety
finding from independent Notified Body
validation. Recovery: re-design (~12
months) plus re-submission. This would be
a material business event for the
Healthcare division; the Industries board
should be aware of the tail.

## Handoff condition

If I were unavailable for the Notified Body
engagement:

- The Algorithm Quality Office Clinical
  Validation Lead can present Deliverables
  02, 03, 04, 06 directly. She has been
  the substantive author on these and can
  defend the choices.
- The CMO can present Deliverable 05 (human
  oversight) — she signed off on the
  asymmetric escalation design.
- The Head of Regulatory Affairs can
  present Deliverables 01, 07 — these are
  in her substantive domain.
- The Industries board should designate a
  backstop CAIRO-equivalent for the synthesis-
  level questions; the Algorithm Quality
  Office Lead is the natural candidate but
  has not had board exposure.

---

## Reasoning notes

- **Why the package summary leads.** Board
  audience first wants to know what
  exists, not what's wrong.
- **Why the Notified Body reading guide is
  detailed.** The board needs to know what
  to expect; the engagement file needs the
  cross-reference to where we anticipated
  questions.
- **Why three substantive "what we got
  wrong" items.** mod-112 §6.3 honesty
  discipline. Two would have read as
  perfunctory; four would have read as
  performative.
- **Why the South-Asian subgroup fragility
  is named explicitly with timeline
  implications.** The board needs to plan
  for the tail scenario. Burying it would
  fail the discipline.
- **Why the handoff section names specific
  individuals.** Generic "the team can
  cover" handoffs don't work in regulated
  engagements where the Notified Body
  expects accountable individuals at the
  table.

---

Maintained by [Girish Nair](https://github.com/garynair)
