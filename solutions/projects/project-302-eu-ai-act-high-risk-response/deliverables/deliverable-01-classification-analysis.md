# Deliverable 01 — Classification Analysis — Reference Solution

## 1. Solution overview

KH-AI-027 is **high-risk under both Art. 6(1)
and Art. 6(2)**. The Art. 6(3) exemption was
considered and rejected — the workflow gives
the AI's classification material influence over
the referral decision rather than merely
preparing for an independent clinician
assessment. Conformity assessment route: **Annex
VII third-party** — Kerridge's first high-risk
AI system warrants third-party rigor; the
incremental cost over Annex VI is modest given
the Notified Body is already engaged for EU
MDR.

---

## 2. The classification analysis

### System description

KH-AI-027 is an adult diabetic-retinopathy
screening SaMD. Intended for use in primary-
care diabetes screening by non-ophthalmologist
clinicians. Outputs a referable / non-referable
classification and a heatmap. Workflow:
clinician operates the screening; AI generates
classification; clinician reviews; referable
cases route to ophthalmologist for confirmation.
Patients are EU adults receiving routine
diabetes care.

### Art. 6(1) analysis

KH-AI-027 functions as a *safety component* of
the underlying medical device. The medical
device (the integrated imaging and analysis
system) is regulated under EU MDR Class IIa.
Class IIa medical devices require **third-party
conformity assessment** under MDR. Per Art. 6(1)
of the AI Act, when (a) an AI system is intended
to be used as a safety component of a product
covered by EU sectoral law, AND (b) the product
requires third-party conformity assessment under
that sectoral law, the AI system is
automatically high-risk.

Both conditions are satisfied. **KH-AI-027 is
high-risk under Art. 6(1).**

### Art. 6(2) + Annex III analysis

As a secondary basis, Annex III(5)(a) covers AI
systems used in "essential private services...
healthcare". KH-AI-027 supports access to
healthcare services via screening. **Annex
III(5)(a) applies as a secondary high-risk
basis.**

Either Art. 6(1) or Art. 6(2) alone would
establish high-risk status. Both apply.

### Art. 6(3) exemption analysis

Article 6(3) provides four exemption conditions.
A system that would otherwise be high-risk
under Annex III is NOT high-risk if it falls
within one of these:

1. **Narrow procedural task.** Does KH-AI-027
   perform a narrow procedural task? No — the
   system makes a clinically meaningful
   classification (referable vs. non-referable)
   that materially influences a clinical
   decision.
2. **Improve a previously completed human
   activity.** Does the system improve a prior
   independent clinician judgment? No — the
   AI's classification is the *first* signal
   the screening clinician receives about
   referability; it is not improving a prior
   assessment.
3. **Detect decision-making patterns or
   deviations from prior decision-making
   patterns and not meant to replace or
   influence the previously completed human
   assessment.** No — the AI's output is meant
   to influence the screening clinician's
   referral decision. This is the closest
   exemption to consider; we reject it because
   the workflow design makes the AI's output
   material to the clinician's decision.
4. **Preparatory task.** Does the system
   perform a preparatory task to an
   assessment relevant for the purposes of
   the use cases listed in Annex III? No —
   image classification *is* the assessment
   in this workflow, not preparation for it.

**None of the four exemption conditions apply.**
KH-AI-027 is high-risk; Art. 6(3) does not
apply.

This is a deliberate clinical-workflow design
choice. A version of KH-AI-027 that operated
*after* the screening clinician had formed an
independent assessment might qualify for the
third exemption (deviation detection). The
current workflow makes that exemption
unavailable. This choice was made
deliberately — the clinical-safety value of
having the AI surface before the clinician's
assessment outweighs the regulatory simplicity
of qualifying for the exemption.

### Conformity assessment route

Two routes are available under Art. 43:

- **Annex VI internal control.** Provider
  self-assesses against the requirements.
  Faster; lower cost.
- **Annex VII third-party.** Notified Body
  assesses. Slower; more rigorous; required
  for certain biometric subsets and
  recommended for first-deployment high-risk
  systems.

**Recommendation: Annex VII third-party
assessment.**

Reasoning:

- The Notified Body is already engaged for EU
  MDR Class IIa (which requires third-party).
  The incremental cost of also addressing EU
  AI Act conformity through the same body is
  modest.
- KH-AI-027 is Kerridge's first high-risk AI
  system. Third-party rigor establishes the
  pattern.
- Notified Body sign-off carries weight with
  customers (national healthcare systems,
  ophthalmology networks) and provides
  defensible posture if challenged by a
  competent authority.

### Art. 49 database registration plan

Per Art. 49, high-risk systems must be
registered in the EU database before being
placed on the market. Kerridge will register
KH-AI-027 through the standard EU AI Office
process at the point of EU declaration of
conformity. Registration data includes the
declaration of conformity, the intended
purpose, the Member States where the system
will be placed on the market, the harmonised
standards applied. The registration is the
final step before market placement.

---

## 3. Reasoning notes

- **Why I named both Art. 6(1) and Art. 6(2)
  bases.** Belt and suspenders. The Notified
  Body will appreciate the explicit
  acknowledgment; defensive posture if either
  basis were somehow contested.
- **Why I explicitly walked through all four
  Art. 6(3) exemption conditions.** This is
  the place Notified Bodies most often
  probe — providers sometimes try to fit
  systems into the exemption to avoid the
  high-risk obligations. Explicit rejection
  with reasoning is the defensible posture.
- **Why I noted the workflow-design choice
  honestly.** Art. 6(3) #3 could have been
  available with a different workflow design.
  Naming this honestly demonstrates Kerridge
  considered the trade-off rather than
  ignoring the exemption.
- **Why Annex VII over Annex VI.** Cost is
  marginal because the Notified Body is
  already engaged; rigor is meaningful;
  posture is durable.
- **What would change the analysis.** If the
  underlying medical device were Class I (no
  third-party conformity required), Art. 6(1)
  wouldn't apply and Art. 6(2) via Annex III
  would be the sole basis. The Art. 6(3)
  exemption analysis would be the same; the
  conformity route could be Annex VI more
  defensibly.

---

Maintained by [Girish Nair](https://github.com/garynair)
