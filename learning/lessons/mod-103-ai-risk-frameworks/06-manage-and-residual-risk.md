# Chapter 6 — MANAGE and Residual Risk

## Why this chapter exists

MANAGE is the NIST AI RMF function that says *given what
MEASURE is telling us and MAP surfaced, what do we do
about it*. It is where the program's decisions become
visible: which risks are treated, which are accepted,
which are exceptioned, and — most importantly — what
residual risk is left when treatment is done.

The residual-risk step is the single most common
integrity failure in AI risk programs. Programs claim
full mitigation, close the ticket, and the risk resurfaces
as an incident later with no acknowledgement that it was
known and left in place. This chapter fixes that.

Chapter 6 also introduces the exception register — the
place where the program tells the truth about the systems
that operate outside standard treatment.

## What MANAGE produces

Three artifacts, again small and named.

1. **The control catalog** — the library of treatments
   the program knows how to apply.
2. **A risk-treatment plan** per material risk — which
   controls apply, residual risk after controls, who has
   accepted the residual.
3. **The exception register** — the risks and systems
   that depart from standard treatment, with named
   accountability.

Together these are the substrate for EU AI Act
Article 9(2)(d), OCC/FRB SR 11-7's model-risk-management
mitigation and effectiveness requirements, and ISO 23894
§7 (risk treatment).

## The control catalog

A control catalog is a structured library of *treatments
the program knows how to apply*, organised by the AI risk
taxonomy from Chapter 2.

A working catalog entry looks like:

```
Control ID:            CTRL-BIAS-004
Name:                  Subgroup performance evaluation
Category (Chapter 2):  Bias and fairness risk
Lifecycle stage:       Pre-deployment
Description:           Model accuracy, precision, recall,
                       and calibration reported per
                       protected-class stratum at model
                       validation.
Treats:                Systematic under-performance on a
                       protected subgroup.
Implementation cost:   Medium
Known limitations:     Requires ground-truth labels on
                       the strata; does not detect
                       intersectional failure modes.
Owner (2LOD):          Fair-Lending Analytics
Evidence artifact:     Stratified validation report,
                       versioned with the model release.
```

Structured this way, the catalog is:

- **Searchable** by risk category and lifecycle stage.
- **Reusable** across systems — a treatment plan cites
  catalog entries rather than reinventing them.
- **Auditable** — every treatment plan is traceable to
  named catalog entries, and every catalog entry has
  named limitations.

Organising the catalog by category *and* lifecycle stage
(pre-deployment, deployment, post-deployment) forces the
program to see gaps. If Bias-and-Fairness has ten
pre-deployment controls and no post-deployment controls,
the program is designing for launch and blind to drift.

Google SAIF and the NIST AI RMF Playbook both provide
starting inventories of controls; either is a fine seed.
The catalog becomes real when the program's own systems
start citing entries.

## The treatment plan

A risk-treatment plan for one specific risk in one system
is the working artifact. It is one page.

```
System:             SB-LOAN-01 (from inventory)
Risk:               Bias in credit recommendation for
                    non-English-speaking applicants,
                    mediated by cash-flow OCR quality
                    (from impact assessment §3, failure
                    mode B-2)
Risk category:      Bias and fairness (Chapter 2 #2)

Unmitigated rating: Likelihood High × Severity High
                    (impact assessment §4)

Controls applied:
  - CTRL-BIAS-004  Subgroup performance evaluation
                   at every model release, stratified
                   by receipt-language.
  - CTRL-BIAS-011  Multilingual-OCR quality gate on
                   ingestion; retrain-blocked if error
                   rate exceeds threshold.
  - CTRL-BIAS-022  Adverse-action-notice audit sampling
                   stratified by applicant primary
                   language.

Confirmatory indicators (from measurement plan):
  - Leading:  OCR error rate on non-English receipts,
              weekly (threshold 8% absolute).
  - Lagging:  Demographic-parity gap on approvals,
              quarterly (threshold 5 pp).

Residual rating:    Likelihood Medium × Severity High
                    (parity gap could still emerge
                    from OCR classes we do not yet
                    detect; sub-threshold OCR issues
                    could accumulate).

Residual accepted by: AI Risk Council, 2026-Q3.
Basis for acceptance: v2 OCR pipeline in flight;
                     interim monitoring in place;
                     6-month re-review scheduled.

Re-evaluation trigger:
  - Parity gap approaches 4 pp (75% of threshold).
  - OCR error rate on non-English receipts exceeds
    threshold on any single weekly measurement.
  - New receipt-language cohort exceeds 5% of
    volume.
  - Scheduled 2027-Q1 review, whichever comes first.

Exception status: within standard treatment pattern.
```

Six properties every treatment plan needs.

- **The specific risk** it treats, quoted from the impact
  assessment. Not a category name; a failure mode.
- **The controls applied**, cited from the catalog by ID.
- **The confirmatory indicators** from the measurement
  plan that show the controls are working.
- **A residual rating** strictly lower than the
  unmitigated rating. If it is not lower, the controls
  are not working and the plan should not be approved.
- **A named accepter of the residual** at an appropriate
  level. Chapter 8's risk appetite statement is what
  makes *appropriate level* observable.
- **A re-evaluation trigger** that is itself observable.
  *"If things change"* is not a trigger; *"if
  demographic parity gap exceeds 4pp on any quarterly
  measurement"* is.

## Residual risk discipline

Residual risk is the most important concept in MANAGE.
Every meaningful AI risk has residual risk after controls.
The discipline is:

- **Name** the residual risk explicitly. Not "fully
  mitigated". Not "residual acceptable". *The specific
  residual failure mode that survives the controls.*
- **Rate** it. It must be lower than the unmitigated
  rating. If it is not, the controls are not working —
  either the controls are wrong or the rating is
  self-serving.
- **Assign** it to a named accepter — the role or
  committee that has accepted the residual. Anonymous
  acceptance is unaccountable acceptance.
- **Document** the re-evaluation trigger.

Programs that systematically claim *zero residual risk*
across their portfolio are not credible. A risk-treatment
portfolio with a residual distribution of *all Low,
accepted* is either dealing with trivial systems, or —
more likely — running the "treat everything" trap below.

Programs that name residual risk and assign it survive
regulator reviews. The discipline is in the naming.

## The exception register

Not every risk fits the standard treatment pattern.
Systems are launched under waivers; controls are deferred
because of operational constraints; risks are accepted at
levels above the program's default appetite because a
business case has been made.

The exception register is where these live. Every
exception:

- Has a written **business justification** — what the
  system does that makes the exception worth it.
- Has an **expiration date** or a defined re-evaluation
  trigger. Open-ended exceptions become permanent
  policies by default.
- Has a **named approver** at the appropriate level —
  more senior for more material exceptions. A high-risk
  system running without a control the program normally
  requires is not a business-unit-manager exception; it
  is a CAIRO or CRO exception.
- Is **reviewed** at a defined cadence — quarterly at a
  minimum for material exceptions.

The register is one of the most-asked-for artifacts in
regulator reviews. Programs that produce it on demand
pass through faster than programs that have to assemble
it from tickets and emails.

Two properties of a healthy exception register.

- **It is not empty.** An empty register on a portfolio
  of any size means either the program is trivial or the
  program is hiding exceptions in the treatment plans.
- **It is not the risk register in disguise.** Every
  exception has a defined path back to standard
  treatment. If exceptions accumulate without ever
  resolving, the policy is wrong, not the exception
  process.

## The "treat everything" trap

A program with abundant controls and no residual-risk
discipline will treat every risk to *"Low / accepted"*
and declare itself complete. This is the *governance
theatre* failure mode from mod-101 Chapter 8.

Symptoms:

- Every treatment plan ends with residual Low.
- The residual accepter is always the same role — often
  the first-line owner of the system.
- Re-evaluation triggers are missing or vague.
- The exception register is empty or trivial.

The expected distribution of a real program's residuals
is a mix. Some risks land at Low; some at Medium
accepted with named triggers; some at High with a named
mitigation-in-flight and a review clock. A program that
cannot produce that distribution honestly is producing
decoration.

The corrective is not to inflate risk ratings. It is to
apply the four residual-risk disciplines — name, rate,
assign, trigger — consistently. Ratings settle honestly
under that discipline.

## Third-party and vendor risk

A distinct MANAGE surface, tied to NIST MANAGE-3.x
(third-party AI risks monitored). Two patterns matter.

- **Vendor-model dependency.** If a system depends on a
  vendor's model (a foundation model provider, a
  scoring vendor, a data enricher), the vendor's risk
  posture becomes yours in the impact assessment. The
  vendor's changes are a re-classification trigger
  (Chapter 3).
- **Vendor-control substitution.** When a vendor claims
  to provide a control, the control is only real if the
  program can *verify* it. A vendor-claimed bias eval is
  not a control until the program has read the eval
  results.

Third-party controls in the catalog are marked as such
and have a required *verification* line — how the
program checks the control is running.

## Article 9(2)(d), SR 11-7, and residual language

For high-risk EU AI Act systems, Article 9(2)(d) requires
appropriate and targeted risk-management measures *with
explicit attention to residual risk*. Article 9(5)
requires the residual to be **communicated to deployers**
in the operating instructions (Art. 13). Your treatment
plans are the source of the residual-risk language that
lands in those instructions.

For SR 11-7-regulated banking models, MRM's effectiveness
assessment operates on the same substrate. SR 11-7 asks
whether controls are appropriate given model use and
whether ongoing monitoring is effective — the treatment
plan answers both when it links to leading indicators
from the measurement plan.

Both regimes reward the discipline of *naming what
remains*. Both punish the assertion that nothing does.

## Summary

- MANAGE produces three artifacts: the control catalog,
  the per-risk treatment plan, and the exception
  register.
- The control catalog is organised by taxonomy category
  and lifecycle stage; each entry has named
  limitations, an owner, and an evidence artifact.
- The treatment plan is one page and links the specific
  risk to the controls, the confirmatory indicators, the
  residual rating, and the named accepter.
- Residual risk must be named, rated (strictly lower
  than unmitigated), assigned to a named accepter, and
  paired with an observable re-evaluation trigger. A
  program that cannot do this is not credible.
- The exception register captures departures from
  standard treatment with justification, expiration,
  approver, and cadence. A healthy register is neither
  empty nor accumulating without resolution.
- The *treat everything* trap produces uniformly Low
  residuals and empty exception registers; correct with
  discipline, not with inflated ratings.
- Third-party controls require a verification line, not
  a vendor claim.
- For high-risk EU AI Act systems, treatment plans feed
  Article 9(2)(d) and (5). For SR 11-7 systems, the
  treatment plans support MRM effectiveness.
- Exercise 04 drafts a working treatment plan for one
  named risk, including residual, acceptance, and
  trigger.
