# Chapter 3 — Three Lines of Defense, Applied to AI

## Why this chapter exists

The Three Lines of Defense (3LOD) model comes from the
Institute of Internal Auditors (IIA), updated most recently
as the *IIA Three Lines Model* (2020). It predates AI
governance by decades. Financial services regulators
built entire supervisory programs on it. It is the most
useful single map for deciding *who does what* in an AI
organization.

If you take one structural idea from this module, take
this one. Every peer-boundary argument in Chapter 5, every
reporting-line debate in Chapter 4, and every operating-
model choice in Chapter 6 traces back to whether the lines
are honest.

## The three lines

1. **First line — own the risk.** The teams *building and
   running* AI systems. They own the day-to-day risk:
   model selection, training data, evaluation, monitoring,
   incident response on their systems. In AI: ML
   engineering, data engineering, product teams using AI
   features, MLOps.
2. **Second line — oversee the risk.** Independent
   functions that *set the rules and check that the first
   line is following them*. In AI: a dedicated AI risk
   function, model risk management (in regulated
   industries), the privacy office, the ethics committee,
   and the CAIRO function itself.
3. **Third line — provide assurance.** Internal audit.
   Tests independently that the first two lines are doing
   what they claim to be doing. Reports to the audit
   committee, not to the executive team.

External audit and regulators sit *outside* the three lines
but rely on them; a supervisor's exam will typically walk
the lines in order.

## The independence test

A 3LOD model works only if the lines are *independent
enough* to challenge each other. Two patterns to watch for:

- **Compressed lines.** A small org may not have three
  separate functions. That is acceptable *if* the
  accountabilities are still distinct. It is dangerous if
  the same person makes the build decision, sets the
  rules, and audits themselves.
- **Cosmetic independence.** Second-line functions that
  ultimately report to the engineering executive whose
  work they oversee. They will lose every difficult call.

The IIA 2020 model deliberately renamed 3LOD from the
older "Three Lines of Defense" to the "Three Lines Model"
to acknowledge that the lines are collaborators, not
adversaries. The rename is important but the independence
test is unchanged: if the second line cannot say "no" to
the first line without changing jobs, the model is
theater.

## Where the CAIRO sits

The CAIRO is a **second-line role** in the Three Lines
Model. Specifically:

- Owns the rules (policies, standards, control catalog).
- Owns the oversight machinery (review boards, escalation
  paths, exception process).
- Owns the AI risk register.
- **Does not own** model selection, training data, or
  deployment decisions. Those are first-line.
- **Does not own** assurance. That is third-line (Chief
  Audit Executive / internal audit).

When CAIROs are placed in the first line (e.g., reporting to
a CTO who is also accountable for shipping AI features),
the role becomes structurally unable to disagree with the
function it oversees. This is one of the most common
failure modes; Chapter 4 covers reporting-line viability
in detail.

## The 3LOD map for a typical AI system

Consider an AI-assisted loan-decisioning system. The
3LOD map:

| Activity | Line | Typical owner |
|---|---|---|
| Choose modeling approach, train, deploy | 1st | ML engineering team |
| Monitor in production, respond to model incidents | 1st | ML engineering + product ops |
| Set evaluation standards, approve deployment against them | 2nd | CAIRO function + Model Risk Management |
| Fair-lending policy, disparate-impact testing methodology | 2nd | CAIRO + Chief Compliance Officer + General Counsel |
| Independent validation of the model before deployment | 2nd | MRM (independent of model builders) |
| Periodic audit of whether the above is actually happening | 3rd | Internal audit, reporting to audit committee |

Note that MEASURE (from Chapter 2) appears in both first
line (model owner monitoring) and second line (independent
validation). This is intentional. Measurement without
independence produces theater; measurement without
first-line ownership produces disengagement. Both are
needed.

## Independence traps specific to AI

Three ways 3LOD independence degrades in AI programs
faster than in traditional risk domains:

1. **Talent scarcity captures the second line.** ML
   expertise is scarce, and the second-line AI risk
   function often has to borrow engineers from the first
   line to review technical detail. If the borrowing is
   frequent and the reviewers know they will go back to
   the team they are reviewing, the independence erodes.
   Mitigation: rotate reviewers, keep review responses
   in writing, and treat second-line technical hires as
   a separate recruiting priority.
2. **Vendor collapse.** If the first line, the second
   line, and the third line all rely on the same vendor's
   AI-governance product for evidence, the vendor becomes
   a fourth (invisible) line. If the vendor is wrong,
   all three lines are wrong in the same direction.
   Mitigation: at minimum, third-line evidence must be
   producible without the vendor's tooling.
3. **Speed pressure compresses lines.** Product teams
   under launch pressure will describe governance review
   as "already done" because the first-line self-review
   happened. The second-line review has to be visibly
   distinct — a different signature, a different runbook,
   a different escalation. Otherwise it becomes a
   rubber stamp on first-line work.

## The "one person, three hats" small-org exception

Some organizations are too small to staff three separate
functions. That is fine — but the *decisions* still have
to be distinct. In a 50-person AI startup, the CTO may
functionally be all three lines. What survives is:

- The **build** decision is signed off with an explicit
  build-line hat.
- The **oversight** decision is a separate document,
  written from a different perspective (what could go
  wrong, what would the auditor ask), signed with an
  oversight-line hat.
- The **assurance** decision is delegated externally at
  least annually — an outside auditor, a fractional risk
  officer, a board committee — because "auditing
  yourself" produces the failure mode by construction.

The moment the org is big enough to hire dedicated
oversight and internal-audit functions, it should. The
one-person-three-hats structure is a bridge, not a
destination.

## Summary

- 3LOD (IIA Three Lines Model, 2020 update) is the map
  for who does what in an AI organization.
- First line owns and runs the risk; second line sets and
  oversees the rules; third line provides independent
  assurance.
- The CAIRO is a second-line role. Placing the CAIRO under
  the executive who ships AI (CTO / CIO) collapses the
  second line and is the most common structural
  anti-pattern.
- Independence has to survive talent scarcity, vendor
  concentration, and speed pressure — three trap patterns
  specific to AI programs.
- Small orgs can compress the lines *if* they keep the
  decisions distinct and delegate assurance externally.
