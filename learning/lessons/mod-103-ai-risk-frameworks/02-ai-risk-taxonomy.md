# Chapter 2 — AI Risk Taxonomy as the Unifying Spine

## Why this chapter exists

A taxonomy is the vocabulary your program agrees to use for
*risks themselves*, independent of which function is
handling them at a given moment. It is the spine that
connects MAP (what risk is this), MEASURE (how do we know
it is present), MANAGE (how do we treat it), and GOVERN
(what does the board see rolled up).

Chapter 1 argued the taxonomy is the index for everything
else. This chapter builds it. Exercise 01 makes you
customise it for a real company.

## Two anchors: NIST 100-1 characteristics and ISO 23894

Two authoritative documents inform any modern AI risk
taxonomy, and both should be visible in your design.

- **NIST AI 100-1 §3** enumerates seven *characteristics of
  trustworthy AI systems*: valid and reliable; safe;
  secure and resilient; accountable and transparent;
  explainable and interpretable; privacy-enhanced; and
  fair with harmful bias managed. These are *desiderata*,
  not risk categories. A taxonomy that inverts them into
  *the risk of each characteristic failing* is a
  defensible starting point.
- **ISO/IEC 23894:2023** provides the risk-management
  vocabulary layered on ISO 31000. It does not prescribe
  categories but does prescribe the discipline: risks are
  identified, analysed, evaluated, treated, and reviewed
  — all against a stated context. A taxonomy must sit
  inside that discipline.

A working taxonomy is *your* taxonomy. But it should be
readable from either anchor by someone who does not know
your program yet.

## What makes a good taxonomy

Four properties. If your taxonomy fails on any of them, it
will not survive review by Risk on one side and Engineering
on the other.

- **Exhaustive for your domain.** Every risk the program
  encounters fits somewhere. A risk that fits nowhere
  forces the taxonomy to grow, not the risk to be ignored.
  Programs whose taxonomy has no category for the last
  three incidents are in denial.
- **Mutually exclusive at the top level.** A risk belongs
  to one top-level category, even if it manifests across
  multiple sub-categories. Without this, the same risk gets
  handled twice, or worse, gets treated by two owners with
  contradictory controls.
- **Reconciles to the enterprise risk taxonomy.** The AI
  risk taxonomy is a *layer* on top of the ERM taxonomy the
  CRO already maintains. If it cannot roll up, the AI
  program will not appear in the board risk pack. The CAIRO
  × CRO boundary from mod-101 Chapter 5 makes the
  reconciliation a shared artifact.
- **Small enough to remember.** Taxonomies with more than
  10–12 top-level categories are not used; they are
  consulted. The discipline is consolidation. If a category
  exists to cover exactly one system, it is a
  sub-category.

## A starting taxonomy

The following nine top-level categories are a working
starting point for most enterprises. They are not
prescriptive; they are the shape most programs converge on
after one adaptation cycle.

| # | Top-level category | What it covers |
|---|---|---|
| 1 | **Performance risk** | Model produces inaccurate, unreliable, or drift-prone outputs that affect downstream decisions |
| 2 | **Bias and fairness risk** | Model produces systematically different outcomes for protected classes or affected populations |
| 3 | **Transparency and explainability risk** | Model outputs cannot be understood, audited, or contested by affected parties or regulators |
| 4 | **Privacy and data risk** | Model exposes, leaks, or improperly uses personal or confidential information |
| 5 | **Security risk** | Model can be attacked, manipulated, or exfiltrated by adversaries |
| 6 | **Operational risk** | Model failure produces operational disruption, including third-party dependency risk |
| 7 | **Compliance and legal risk** | Model causes the organization to violate law, regulation, or contract |
| 8 | **Reputational risk** | Model behaviour, if disclosed, would materially damage trust with customers, employees, or markets |
| 9 | **Strategic risk** | Model decisions misalign with the organization's strategic direction or commitments |

Each category is a *kind* of harm, not a specific incident.
Specific risks live as sub-categories inside a top-level
category. A specific bias failure mode on the resume
screener is a sub-category of Bias and Fairness Risk, not a
new top-level category.

The correspondence to NIST AI 100-1 §3 is intentional:

| NIST characteristic | Category above |
|---|---|
| Valid and reliable | 1 Performance |
| Fair, with harmful bias managed | 2 Bias and fairness |
| Explainable and interpretable, accountable and transparent | 3 Transparency and explainability |
| Privacy-enhanced | 4 Privacy and data |
| Secure and resilient | 5 Security |
| Safe | Spans 1, 5, 6 depending on context |

Categories 7, 8, and 9 do not have direct NIST
characteristic analogues because NIST is scoped to the
system's trustworthy properties. They come from the ERM
side. This is the reconciliation seam and is normal.

## How the taxonomy plugs into the loop

Once fixed, the taxonomy is referenced by every function:

- **MAP** classifies each system against the taxonomy.
  Each system gets a list of *applicable* categories. Not
  every system carries every category.
- **MEASURE** designs metrics per applicable category. A
  Performance metric for a credit model is not the same
  metric as a Performance metric for a chatbot.
- **MANAGE** treats risks by category. The treatment
  *pattern* (e.g., "for bias risk, X kind of control") is
  category-stable; the specific treatment is system-
  specific.
- **GOVERN** reports up by category. The board sees the
  risk profile organised by category, not by system. A
  board that reads a per-system list will not detect a
  pattern; a board that reads a per-category summary will.

The same taxonomy is used in Chapter 8's risk appetite
statement — appetite is set per category, at CEO/board
scope, then propagated back into MEASURE thresholds.

## Adapting the taxonomy

The starting taxonomy is a template, not a fixed list.
Adaptation is a one-time exercise; the discipline once
adapted is consistency (every system gets classified
against the same taxonomy).

Common adaptations:

- **A bank** may split *Performance risk* into *Model
  performance* (accuracy) and *Process performance*
  (latency, availability) because their SR 11-7-anchored
  MRM function already distinguishes them. mod-102
  Chapter 4 gives the SR 11-7 context.
- **A healthcare system** may add *Clinical safety risk*
  as a distinct top-level category alongside or replacing
  Operational risk, because the clinical-safety regulatory
  regime is operationally separate.
- **A frontier-AI org** may add *Catastrophic risk*
  (low-probability, high-severity scenarios) as a distinct
  category because their Responsible Scaling Policy
  requires it. Anthropic's public RSP is one worked
  example.
- **A federal agency** governed by OMB M-25-21 may add
  *Rights-impacting* and *Safety-impacting* as top-level
  designations because the M-25-21 minimum practices are
  tied to those labels. mod-102 Chapter 9 has the shape.

Adaptation must be defensible in the reasoning note — you
should be able to say *why* your organisation needs a
category the starting taxonomy does not have. Categories
added because they *sound comprehensive* are the ones
programs later abandon.

## Common taxonomy mistakes

These are the four most common errors in taxonomies that
have to be rebuilt within twelve months.

- **Borrowing an enumeration as the top level.** OWASP LLM
  Top 10, MITRE ATLAS, and the NIST GenAI Profile are
  useful catalogues but not taxonomies. Putting *prompt
  injection* at the top level distorts the program toward
  security at the expense of other categories. These
  belong as sub-categories inside Security or Performance,
  respectively.
- **Borrowing the NIST sub-functions as risk categories.**
  MAP-1.1, MEASURE-2.3, and their peers are *activities*,
  not risks. They belong in the program design, not the
  taxonomy. A risk is *what could go wrong*; a
  sub-function is *what work you do to know*.
- **Tracking risks at three levels of depth.** Top-level
  categories plus one level of sub-category is plenty.
  Three-level taxonomies are aspirational documents —
  they get printed on posters and never referenced in
  practice.
- **Allowing a risk to belong to multiple top-level
  categories.** This is the most common error. A bias
  risk and a privacy risk that both stem from the same
  training-data issue are *two related risks*, owned in
  different categories, not one risk in two categories.
  Cross-linking is a sub-category concern; mutual
  exclusion is a top-level requirement.

## Concrete example — one system, taxonomy applied

An AI-assisted small-business loan-decisioning system used
in Exercise 03 later in the module. Which top-level
categories apply?

- **Performance risk** — yes; loan recommendations degrade
  as the small-business economy shifts.
- **Bias and fairness risk** — yes; disparate-impact
  concerns across protected classes are the core
  fair-lending exposure.
- **Transparency risk** — yes; adverse-action notices
  under ECOA / Reg B must be individually meaningful.
- **Privacy and data risk** — yes; cash-flow aggregator
  data must not be used beyond the disclosed purpose.
- **Security risk** — partial; standard controls apply,
  but no unique AI-specific attack surface here beyond
  data poisoning of retrain sets.
- **Operational risk** — yes; the aggregator third party
  is a dependency.
- **Compliance risk** — yes; fair-lending and adverse-action
  are enforceable.
- **Reputational risk** — yes; a public fair-lending
  finding would be material.
- **Strategic risk** — no; a single decisioning system
  does not carry strategic risk unless declared so.

Eight categories apply, one does not. The impact
assessment (Chapter 4) then works only on the eight.

## Summary

- A taxonomy is the vocabulary the program agrees to use
  for *risks*, independent of function. It is the index
  for MAP, MEASURE, MANAGE, GOVERN, and the risk
  appetite statement.
- Good taxonomies are exhaustive, mutually exclusive at
  the top level, reconciled to the enterprise risk
  taxonomy, and small enough to remember.
- A defensible starting shape has around 8–9 top-level
  categories anchored to NIST AI 100-1 §3 characteristics
  extended by ERM categories the NIST list does not
  cover.
- Adaptation is one-time and reasoned; the discipline is
  consistency once fixed.
- The most common mistakes are borrowing an enumeration
  as the top level, using NIST sub-functions as risks,
  going three deep, and allowing a risk to belong to
  multiple top-level categories.
- Exercise 01 builds the taxonomy for a specific company
  and defends the mapping to that company's ERM
  taxonomy.
