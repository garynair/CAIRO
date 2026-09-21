# Chapter 8 — The Enterprise AI Risk Appetite Statement

## Why this chapter exists

Every artifact in the preceding chapters — the taxonomy,
the impact assessments, the measurement plans, the
treatment plans, the register — presupposes a single
question answered from the top: **how much AI risk, and
of what kinds, will the enterprise accept?**

Until that question is answered *at CEO and board scope*,
the program has no anchor. Residual acceptance is
unanchored (Chapter 6). Board reports have no *outside
appetite* section to fill in (Chapter 7). Measurement
thresholds are set by first-line owners without top-down
tolerance (Chapter 5). The program looks defensible in
each function and produces incidents the board later says
it never chose to accept.

The AI risk appetite statement fixes this. It is signed
by the CEO and ratified by the board. The CAIRO **proposes,
coordinates, and signs off**; the head-of-ai-governance
**operates the register that the appetite is applied to**
month to month. This chapter defines the artifact, the
sign-off process, the coordination pattern, and the
common failure modes.

## What a risk appetite statement is

A risk appetite statement is the **enterprise's declared
tolerance for risk, expressed in advance**, that the
program then operates against. It is not a policy; it is
a *framing* the policies work under.

The AI risk appetite statement is a *layer* on the
enterprise risk appetite statement the CRO already
maintains. It says nothing about the enterprise's overall
risk tolerance for market, credit, or operational risk;
it says what tolerance the enterprise chooses for the AI
risk categories from Chapter 2.

Two components at the appetite level, mirroring the
enterprise-risk conventions in ISO 31000 and the
practitioner writing collected in COSO's ERM guidance.

- **Risk appetite** — the aggregate level of AI risk the
  enterprise is willing to accept in pursuit of its
  objectives. Usually qualitative at the top: *"we accept
  moderate AI risk in service of accelerated
  product-development throughput; we do not accept
  material AI risk to affected populations' fundamental
  rights."*
- **Risk tolerance** — the acceptable variation around
  the appetite for specific risk categories, usually
  quantitative or thresholded. This is where the
  statement becomes actionable: per Chapter 2 category,
  what residual rating is acceptable, and what triggers
  escalation.

## Why the CAIRO signs off, not owns

Ownership of the enterprise risk appetite statement sits
with the CRO or, in some structures, jointly with the CFO
and CRO. It is a *board-level* artifact.

For the AI risk *layer*:

- The **CEO** signs the appetite statement.
- The **board** (typically the Risk Committee) ratifies
  it, per fiduciary duty.
- The **CAIRO** proposes the statement, drafts the
  category-level tolerances, and *signs off* on the
  coherence between the statement and the operational
  program. Signing off is a professional attestation
  that the operational program can and does apply the
  appetite.
- The **head-of-ai-governance** — as the operator of the
  risk register (Chapter 7) — is the day-to-day
  applicator of the appetite. Register rows get an
  appetite-alignment tag (within / at / above) that only
  makes sense if the appetite is signed.
- The **CRO** integrates the AI appetite layer into the
  enterprise-wide statement so board-level roll-ups are
  coherent.

The CAIRO sign-off is what makes the artifact operationally
credible. A board-signed appetite statement that no CAIRO
would attest to is a governance-theatre artifact — signed
at the top, unusable at the bottom.

mod-101 Chapters 5–6 describe the CAIRO × CRO peer
boundary in more depth; this chapter operationalises it
on one specific artifact.

## The head-of-ai-governance coordination pattern

The role name varies (Head of AI Risk, VP of AI
Governance, AI Chief of Staff in some structures), but
the function is stable — a **second-line** role that
runs the AI risk register and the routine cadence day to
day. mod-101 Chapter 3 has the three-lines-of-defense
framing that places this role.

Two coordination artifacts sit between the CAIRO and the
head-of-ai-governance around appetite.

- **The appetite-application memo.** Once the appetite
  is signed, the head-of-ai-governance produces a one-
  page memo describing how the appetite will be applied
  in the register — which residual ratings map to
  within, at, above the appetite per category; what
  cadence the mapping is checked at; what escalation
  paths cross the boundary. The CAIRO reviews and signs.
- **The quarterly appetite-alignment summary.** From the
  register, the head-of-ai-governance produces a
  category-level roll-up: how many material risks are
  within appetite, at, above. This is the input to the
  Chapter 7 board report's *material risks outside
  appetite* section. The CAIRO reviews before the CRO
  countersigns.

The pattern makes the appetite operational. Without it,
the appetite lives as a slide and the register lives in
a spreadsheet, and they never meet.

## The structure of a working statement

A working AI risk appetite statement is 2–3 pages. The
board and CEO have to read and sign it; length destroys
the artifact.

### 1. Preamble

One paragraph. Ties the AI risk appetite to the
enterprise risk appetite. Names the categories the AI
appetite governs (from Chapter 2 taxonomy). Cites the
signing hierarchy (CEO signs, board ratifies).

### 2. Aggregate AI risk appetite

One or two sentences per stated business-value
dimension. Qualitative.

Example patterns (illustrative — every organisation
writes its own):

- *"We accept moderate AI risk to accelerate customer
  experience improvements and productivity gains in
  operations."*
- *"We do not accept material AI risk to affected
  parties' fundamental rights, including the rights of
  applicants, patients, employees, and members."*
- *"We do not accept AI risk that materially exposes
  the enterprise to regulatory action, above the
  materiality thresholds in the enterprise risk
  appetite."*
- *"We accept operational-risk exposure from AI vendor
  dependencies commensurate with the exposure we accept
  from equivalent non-AI vendor dependencies."*

### 3. Category-level tolerances

A table, one row per Chapter 2 category, with a stated
tolerance and one or two illustrative triggers.

| Category | Tolerance | Trigger for escalation |
|---|---|---|
| Performance | Low residual for revenue-material systems; Medium residual acceptable for pilot systems with a written pilot cap. | Any Performance residual rated High for a production system. |
| Bias and fairness | Low residual for systems affecting hiring, lending, or clinical decisions on protected classes. Medium residual acceptable only with a signed treatment-in-flight plan. | Any Bias residual rated High for a rights-impacting system. |
| Transparency & explainability | Adverse decisions to affected parties must be individually explainable. | Any system producing adverse decisions without an individual explanation pathway. |
| Privacy and data | Low residual; no acceptance of data-purpose-limitation violations. | Any use of personal data beyond disclosed purpose. |
| Security | Medium residual acceptable with named vendor controls and verification cadence. | Any residual High without a mitigation-in-flight plan; any confirmed exploitation. |
| Operational | Medium residual acceptable for third-party dependencies with named fallbacks. | Any dependency with no fallback for a rated-material system. |
| Compliance and legal | Low residual for enforceable regimes (EU AI Act, sector laws). Medium residual acceptable for ambiguous obligations with legal opinion on file. | Any obligation with no assigned owner. |
| Reputational | Medium residual acceptable; monitored via public and employee signals. | Sustained pattern of adverse public / employee sentiment tied to an AI system. |
| Strategic | Medium residual acceptable; reviewed annually. | Any AI system whose failure would materially affect stated strategic commitments. |

The tolerances are set by the CAIRO with the CRO,
reviewed by the head-of-ai-governance for
operationalizability, then presented to the CEO and
board.

*Low, Medium, High* here must be the same rating
vocabulary used in the treatment plans (Chapter 6).
Otherwise the register cannot apply the appetite.

### 4. Category-specific out-of-appetite conditions

Named, short list. What conditions trigger a board
notification without waiting for the quarterly report.

Examples:

- Any confirmed material privacy breach involving a
  production AI system.
- Any confirmed material fair-lending or discrimination
  finding involving a production AI system.
- Any regulator letter (mod-102 Chapter 7) alleging a
  material AI-related violation.
- Any incident meeting the EU AI Act Art. 73 serious-
  incident reporting threshold.

### 5. Review cadence

The statement is reviewed **annually**, with an
interim review triggered by any of the material
out-of-appetite events in Section 4.

### 6. Sign-offs

- CEO (signer).
- Board Risk Committee chair (ratifier).
- CRO (integrator into enterprise appetite).
- CAIRO (professional attestation of operational
  applicability).

## Common failure modes

Six patterns that produce an appetite statement that
does not work.

- **Aspirational, not operational.** The statement says
  *"we do not accept bias in our AI"*, which sounds
  strong and cannot be applied by anyone. The
  head-of-ai-governance cannot tell whether any
  specific residual rating is within appetite. Fix by
  writing tolerances in the same vocabulary as the
  treatment plans use (Low / Medium / High residual).
- **Uncoordinated with enterprise appetite.** The AI
  appetite is drafted by the CAIRO alone and never lands
  in the enterprise statement, so the board has two
  disconnected appetite documents. Fix with the CRO
  integration step above.
- **Signed but not applied.** The statement is signed and
  filed; the register never gets appetite-alignment
  tags. Fix with the appetite-application memo and the
  quarterly summary.
- **Tolerances too coarse or too fine.** A single Low /
  Medium / High per category is too coarse to
  discriminate; a five-cell matrix per category with
  qualitative footnotes on each is too fine to read.
  Match the granularity to the register's rating scale.
- **Silent on the categories that matter most.** The
  statement covers Performance and Operational in
  detail but says nothing about Reputational or
  Strategic because those are harder to make
  operational. Regulators and boards read the omission
  as *the program has not thought about them*.
- **Reviewed reactively, not on cadence.** The statement
  is only revisited when an incident forces it. The
  cadence should be annual, and the interim review
  should be triggered by the events in Section 4 — not
  by whatever is on fire.

## Where the appetite sits in the loop

Once signed and applied:

- **MAP** classifies systems against the taxonomy the
  appetite uses; assessments name failure modes in the
  same category vocabulary.
- **MEASURE** sets thresholds coherent with the
  appetite's category tolerances — the leading
  indicator threshold is set to fire *before* the
  category tolerance would be breached.
- **MANAGE** treats risks toward residuals compatible
  with appetite; residuals above appetite either enter
  the exception register (with named senior approval)
  or trigger board notification (per Section 4).
- **GOVERN** reports by category, with appetite
  alignment surfaced explicitly (Chapter 7's board
  report Section 3).

The appetite is the top of the loop. Everything else
implements it. This is why the CAIRO signs off, even
though the CEO signs.

## Concrete example — one line of the tolerance table

For the small-business loan-decisioning system used
throughout the module, the Bias-and-Fairness line of
the tolerance table might read:

- **Tolerance.** Low residual for approval-rate parity
  across protected classes. Medium residual acceptable
  during a signed treatment-in-flight period of no more
  than six months. High residual not accepted for a
  production credit system.
- **Trigger.** Any quarterly demographic-parity gap
  measurement above 5 pp on approvals; any confirmed
  disparate-impact finding at the state or federal
  level; any pattern of adverse-action notices flagged
  as inadequate by internal audit sampling.
- **Escalation on trigger.** Board notification within
  thirty days for any confirmed disparate-impact
  finding; CRO / CAIRO joint action for parity-gap
  breach.

The treatment plan in Chapter 6 was drafted assuming
this line. The residual rating (Medium × High) was
accepted by the AI Risk Council because it fits inside
the *Medium residual acceptable during signed
treatment-in-flight* window. Without this line signed
at the top, the AI Risk Council's acceptance would be
unanchored.

## Summary

- The AI risk appetite statement is the enterprise's
  declared tolerance for AI risk, at CEO / board scope,
  layered on top of the enterprise risk appetite.
- The CAIRO **proposes, coordinates, and signs off**; the
  CEO signs; the board ratifies; the CRO integrates;
  the head-of-ai-governance operates the register
  against the signed statement.
- A working statement is 2–3 pages: preamble, aggregate
  appetite, category-level tolerances mirroring
  Chapter 2, out-of-appetite trigger conditions, review
  cadence, sign-offs.
- Coordination between the CAIRO and head-of-ai-governance
  is anchored in two artifacts: the appetite-application
  memo and the quarterly appetite-alignment summary.
- Common failures: aspirational language, uncoordinated
  with enterprise appetite, signed-but-not-applied,
  granularity mismatch, silent on the harder categories,
  reactive review.
- The appetite is the top of the loop. MAP,
  MEASURE, MANAGE, and GOVERN implement it. If any of
  the four does not know the appetite, the appetite is
  not real.
