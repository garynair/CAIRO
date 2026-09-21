# Chapter 2 — The NIST AI RMF as the Operating System

## Why this chapter exists

You will encounter many frameworks in this track. The NIST
AI Risk Management Framework 1.0 (NIST AI 100-1) is the one
to learn first because everything else cross-walks to it. If
your program has a "GOVERN / MAP / MEASURE / MANAGE" spine,
you can absorb ISO/IEC 42001, EU AI Act Article 9, and the
sector-specific overlays as extensions rather than
alternatives.

This chapter walks the four functions, shows where they
land on a real org chart, and calls out the failure mode
new CAIROs hit when they treat the framework as a checklist
instead of an operating system.

## Why NIST AI RMF first

Three practical reasons to anchor here before touching
ISO 42001 or EU AI Act structure:

1. **Framework-agnostic.** It does not require any
   specific technology, methodology, or industry.
2. **Structured around functions, not artifacts.** It
   survives translation to whatever artifacts your
   organization already produces (design docs, risk
   registers, model cards, SOC 2 evidence).
3. **Almost everything cross-walks to it.** ISO/IEC 42001
   publishes an official crosswalk. EU AI Act Article 9
   (risk management system) maps onto it. OECD AI
   Principles sit upstream of it. Sector rules (SR 11-7,
   FDA GMLP) fit inside MEASURE and MANAGE.

## The four functions

NIST AI RMF organizes the work into four functions. Treat
them as the four columns of your governance program;
everything you do should land in one of them.

| Function | What it does | Typical artifacts |
|---|---|---|
| **GOVERN** | Establishes the culture, structures, processes, and accountabilities that enable AI risk management | Policy hierarchy, RACI, escalation paths, roles, risk appetite |
| **MAP** | Builds context-aware understanding of where and how AI is used, and what risks each use creates | AI inventory, use-case classification, impact assessments |
| **MEASURE** | Identifies, analyzes, and tracks risks against the system | Evaluations, metrics, red-team reports, monitoring dashboards, audit findings |
| **MANAGE** | Allocates resources to identified risks; treats them | Risk treatment plans, controls, kill switches, exception logs, incident response |

GOVERN is the only function that operates *continuously
across* the others — it sets the conditions that make the
others work. The first quarter of a new governance program
is almost entirely GOVERN work. People who try to jump
straight to MEASURE (the tempting, demonstrable one)
without the GOVERN foundation typically build dashboards
that no one acts on.

## Placing each function on a real org chart

The functions are abstract; the accountabilities have to
land on named humans. A defensible default placement for a
mid-to-large enterprise:

| Function | Primary accountable role | Where it typically sits |
|---|---|---|
| GOVERN | Chief AI Risk Officer | Second line (see Chapter 3) — sets policy, decision rights, appetite |
| MAP | Business-unit AI/ML leaders, coordinated by the CAIRO function | First line — the teams building and running AI own the map of their own use cases |
| MEASURE | Model owners (first line) *and* independent validation (second line for material systems, third line periodically) | Split intentionally — measurement without independence produces theater |
| MANAGE | Business-unit executives who own the P&L of the impacted product or process | First line — the accountable executive for the *decision the AI supports* owns the treatment plan |

Two important consequences:

- **The CAIRO does not own MAP, MEASURE, or MANAGE
  end-to-end.** The CAIRO owns the *rules* under which they
  are done and the *aggregation* into an enterprise view.
  A CAIRO who tries to personally curate the AI inventory,
  run every evaluation, and approve every treatment plan
  will bottleneck the program by the second quarter.
- **The board's counterparty is GOVERN.** When the board
  asks "how are we managing AI risk," they are asking a
  GOVERN question — about the *system*, not about any
  specific model. Chapter 7 covers what the CAIRO owes the
  board here.

## The "GOVERN-everything" trap

NIST AI RMF deliberately does not tell you *what good looks
like* in each function. The Playbook offers sub-categories
and considerations, not pass/fail criteria. New CAIROs who
treat it as a checklist produce documents that satisfy the
framework's letter without changing the company's behavior.

The framework is an *operating system*, not an
*application*. Your job is to ship the applications that
run on top of it — the specific controls, escalation
triggers, risk thresholds, and decision rights that make it
real. The framework only tells you that all four functions
need to be present.

Concretely: `GOVERN-1.1` says the organization should
establish policies and procedures for AI risk management.
The framework does not tell you which policies, at what
altitude, or how they escalate. Two organizations can both
satisfy `GOVERN-1.1` and have wildly different actual
governance postures. The framework is the outline; you
write the essay.

## Crosswalks (read once, then refer back)

- **ISO/IEC 42001 (2023).** Published crosswalk in
  ISO's own documentation. Roughly: 42001 §5 (Leadership)
  ≈ GOVERN; §6 (Planning) ≈ MAP; §9 (Performance
  Evaluation) ≈ MEASURE; §8 + §10 (Operation +
  Improvement) ≈ MANAGE.
- **EU AI Act Article 9** (risk management system) sits
  on top of all four functions and is, structurally, a
  continuous, documented, high-risk-only application of
  the cycle. Article 72 (post-market monitoring) and
  Article 73 (serious incident reporting) are MEASURE and
  MANAGE obligations respectively.
- **OECD AI Principles (2024 update)** sit *upstream* —
  they define the values (human-centered, transparent,
  accountable, robust, privacy-respecting) that the
  framework operationalizes. Cite them when a policy
  needs a principle to trace to.
- **OMB M-25-21** (US federal CAIO designation) is
  structured around a similar function decomposition; a
  federal-agency CAIRO can lift the NIST spine intact.

You will use these crosswalks in Exercise 01.

## Concrete example: a control that lives in all four functions

Consider a bias-and-fairness control on a hiring model:

- **GOVERN.** The AI policy defines fairness as a
  first-class evaluation dimension for hiring systems and
  names the accountable executive (typically the CAIRO,
  jointly with the head of HR).
- **MAP.** The hiring model appears in the AI inventory
  tagged as high-impact, employment domain, protected-class
  relevant.
- **MEASURE.** Fairness metrics (selection rate ratios,
  equal opportunity difference) are computed at defined
  cadence and cross-checked by independent validation.
- **MANAGE.** If metrics breach threshold, the treatment
  plan — retraining, restriction, retraction — is
  executed by the model owner under a defined runbook and
  logged to the risk register.

A program with dashboards but no policy fails at GOVERN.
A program with policy but no inventory fails at MAP. A
program with metrics but no runbook fails at MANAGE. All
four have to be present for the control to actually work.
This is what "operating system" means in practice.

## Summary

- NIST AI RMF is the operating-system framework. Learn it
  first; other frameworks cross-walk to it.
- Four functions: GOVERN (continuous), MAP (context),
  MEASURE (evidence), MANAGE (treatment).
- GOVERN typically lands with the CAIRO; MAP and MANAGE with
  the business; MEASURE is split between first and second
  line by design.
- The framework tells you what functions must exist, not
  what good looks like inside them. Treating it as a
  checklist produces theater.
- Every real control lives in all four functions. If a
  control is present in only one, the program has a hole.
