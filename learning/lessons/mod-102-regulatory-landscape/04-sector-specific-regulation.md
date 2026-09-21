# Chapter 4 — Sector-Specific Regulation

## Why this chapter exists

The two AI-specific frameworks (EU AI Act, NIST AI RMF) sit
on top of substantial **sector-specific** regulatory
regimes that already cover AI implicitly. Banking, health,
insurance, employment, and aviation each had a supervisory
frame long before "AI regulation" was a phrase. Those
frames still apply, and where they conflict with an
AI-specific rule the sector rule usually wins in near-term
enforcement — because the sector regulator is the one who
holds your license.

A CAIRO who builds a program that satisfies the EU AI Act
but ignores SR 11-7 will pass the first EU audit and fail
the next OCC exam. A CAIRO who satisfies FDA SaMD but has
not read the EU AI Act × MDR intersection will get through
the FDA clearance and be blocked at the EU border.

This chapter walks the sector regimes a CAIRO is most likely
to touch. The list is not exhaustive; it is the working
subset you need to be able to name and reason about
without looking up.

## Financial services

Banks and other financial institutions carry the deepest
supervisory tradition of any AI-relevant sector. The AI
that supervisors expect banks to govern goes well beyond
AI-specific statutes.

### OCC / FRB SR 11-7 — Supervisory Guidance on Model Risk Management (2011)

The foundational document. Every banking model, including
ML and AI, is a *"model"* for SR 11-7 purposes: any
quantitative method that applies statistical, economic,
financial, or mathematical theories, techniques, or
assumptions to process input data into quantitative
estimates. The guidance establishes:

- A **model inventory** as a supervisory expectation.
- **Model development, implementation, and use** standards
  — including proper documentation, data quality, and
  testing.
- **Model validation** as an independent function —
  effective challenge from someone who did not build the
  model.
- **Governance, policies, and controls** — the model risk
  framework, roles, and reporting.
- **Ongoing monitoring** — outcomes analysis and periodic
  revalidation.

SR 11-7 recurs across the track. mod-104 is largely built
on it. If you have not read it, read it now.

### FRB SR 22-6 — Interagency Guidance on Third-Party Risk Management (2023)

Third-party AI is a first-class supervisory concern. When
you use a vendor model, the bank owns the outcome; the
vendor does not. SR 22-6 sets expectations for third-party
oversight throughout the relationship — planning, due
diligence, contract, ongoing monitoring, termination — and
supervisors read it alongside SR 11-7 for models.

### CFPB enforcement under ECOA / Regulation B / UDAAP

CFPB has no AI-specific regulation, but has active
enforcement authority. Two positions worth internalising:

- **CFPB Circular 2022-03** — the "no black box defense"
  position. A lender cannot avoid ECOA's adverse-action
  notice obligation by pointing to a model whose decisions
  are not human-interpretable. If the model is complex,
  the lender still owes the applicant the specific
  principal reasons for the adverse action.
- **UDAAP** framing on AI marketing claims — "our AI is
  unbiased" is a claim subject to substantiation like any
  other.

The CFPB position is the clearest example in US regulation
of a non-AI-specific statute *eating an AI-specific
implementation choice*. If your program has decided to
adopt an opaque model because it is more accurate, ECOA
still requires the adverse-action notice.

### NYDFS 23 NYCRR Part 500 (with AI amendments)

The New York Department of Financial Services cybersecurity
regulation applies to NYDFS-supervised entities (many banks,
insurers, and money-services businesses). The regulation
carries governance, third-party risk management, and
incident-reporting obligations. AI amendments and NYDFS
industry guidance now treat AI as a first-class asset
category under the regulation. mod-107 revisits Part 500 in
depth.

## Healthcare

### FDA Software as a Medical Device (SaMD)

Software that qualifies as a medical device is regulated by
FDA. AI/ML SaMD has its own guidance lineage, including the
**Good Machine Learning Practice (GMLP) guiding
principles** (a joint FDA / Health Canada / MHRA
publication). The most operationally distinctive FDA move
is the **Predetermined Change Control Plan (PCCP)**
framework, which allows for defined ongoing model updates
within a pre-cleared envelope. PCCP is one of the few
regulatory instruments in any jurisdiction that explicitly
accommodates continuous-learning ML models.

### EU MDR × EU AI Act intersection

An AI medical device sold into the EU may be subject to
*both* the Medical Device Regulation (MDR, Reg. (EU)
2017/745) and the EU AI Act high-risk provisions
(Art. 6(1) via Annex I). The two regimes have explicit
coordination provisions, but the practical work is
harmonising two technical files, two conformity assessment
processes, and often two Notified Bodies. Plan the
technical documentation to serve both.

### HIPAA and state breach laws

Non-AI-specific but triggered by any AI system that
processes PHI. Data-use, security-rule, and breach-notice
obligations apply regardless of whether the system is AI.
The HIPAA privacy rule's minimum-necessary standard and
patient right-of-access provisions both interact with
AI-driven summaries and clinical decision support.

## Insurance

### NAIC Model Bulletin on the Use of AI Systems by Insurers

The National Association of Insurance Commissioners
published a model bulletin on the use of AI in insurance.
The bulletin is not itself law — the NAIC is a coordinating
body, not a regulator — but it has been adopted by many
state insurance departments as their supervisory
expectation. It covers:

- Governance, risk management, and internal controls for
  AI systems used in the insurance business.
- Third-party AI systems and vendor management.
- Testing for outcome quality and disparate outcomes on
  protected classes.
- Adverse-event reporting.

State adoption drives what actually applies to you. Track
adoption in the states you operate in.

### Colorado Division of Insurance Reg 3 CCR 702-10 (AI governance in life insurance)

Colorado has adopted a set of insurance regulations that
apply specifically to insurers' use of external consumer
data and AI/predictive models in underwriting. The
regulation includes testing requirements for unfairly
discriminatory outcomes and documentation of the governance
framework. States are watching Colorado's implementation
closely.

### State unfair-trade-practice statutes

Every state has an unfair-trade-practices statute. When AI
systems produce systematically different outcomes for
protected classes, those statutes provide an enforcement
hook independent of any AI-specific rule.

## HR and employment

### NYC Local Law 144 (Automated Employment Decision Tools)

New York City requires employers using an automated
employment decision tool for hiring or promotion to:

- Have a **bias audit** conducted by an independent
  auditor within one year of the tool's use.
- **Publish** a summary of the audit results.
- Give **notice** to candidates that an AEDT is being used.

The law is narrow — it applies to NYC-based positions and
candidates — but has been influential in shaping other
state proposals and vendor practices.

### EU AI Act Annex III(4)

Employment-related AI (recruitment, task allocation,
performance monitoring, promotion, termination) is high-risk
in the EU by default under Annex III(4). The Art. 6(3)
carve-out is generally not available because these systems
profile natural persons.

### Illinois AI Video Interview Act

Employers using AI to analyse video interviews of Illinois
applicants must give notice, obtain consent, and limit
distribution of the recorded interviews. Narrow scope,
illustrative of the state-patchwork pattern developed in
Chapter 5.

## Aviation

FAA and EASA airworthiness frameworks apply to AI in
safety-critical aviation systems. The AI becomes a
component of the airworthiness case. The regulatory regime
is heavily structured, change cycles are slow, and the
overlap with the EU AI Act high-risk provisions (via
Annex I, Art. 6(1)) is nearly complete for
safety-classified components.

## The sector-specific pattern

Across sectors the same shape recurs:

1. The sector has a **baseline regulation** that predates
   AI regulation, often by decades.
2. The sector regulator **interprets** the baseline
   regulation as applying to AI, publishes guidance, and
   examines under that interpretation.
3. **AI-specific regulation** (EU AI Act, NIST AI RMF,
   state AI laws) layers on top.
4. The CAIRO operates **both regimes simultaneously**, with
   the sector regulator usually the more aggressive
   near-term enforcer because they hold the license.

The failure mode is easy to spot. A CAIRO who builds a
program addressing the AI-specific regulation but not the
sector regulation ships a program that will fail the first
sector exam. Sector rules on model validation,
adverse-action notices, breach notification, and
third-party oversight predate every AI framework in this
track. Ignoring them is not a strategy.

## Where sector and AI-specific rules disagree

Occasionally the two regimes will pull in different
directions. Two common patterns:

- **AI-specific rule wants an explanation the sector rule
  does not require.** Do both. The AI-specific
  explanation is cheap to produce; the sector rule is what
  you will be examined on; producing the explanation
  costs nothing you were not already going to do.
- **Sector rule requires an independent validator the
  AI-specific rule does not name.** Follow the sector
  rule. Independent validation is a well-defined
  supervisory expectation; skipping it because the EU AI
  Act does not name it will lose you the sector exam.

When in doubt, do the union. The cost of over-satisfying
one regime is almost always less than the cost of failing
another.

## Summary

- Sector-specific regulation predates AI regulation and
  keeps its enforcement power. Programs that address
  AI-specific rules but not sector rules fail sector
  exams.
- Financial services: SR 11-7 baseline + SR 22-6
  third-party + CFPB "no black box defense" + NYDFS
  Part 500. All apply regardless of AI-specific
  frameworks.
- Healthcare: FDA SaMD + PCCP + EU MDR × AI Act
  intersection. The two-regime technical file is the
  operational challenge.
- Insurance: NAIC Model Bulletin, state-by-state
  adoption; Colorado's implementation is a leading
  indicator.
- HR: NYC LL 144 bias audit; EU AI Act Annex III(4)
  keeps most HR AI high-risk.
- The failure mode is building for one regime and being
  surprised by the other. Do the union where they
  disagree.
