# Module 109 — Lecture Notes

About 95 minutes of reading. §2 (control mapping) and
§3 (continuous evidence collection) carry the
operational weight; §5 (ISO 42001 Annex A) is the
reference-heavy section worth coming back to.

---

## §1. What compliance operations is and isn't

Compliance operations is *the day-to-day work of
operating against your compliance obligations*. It is
distinct from each of its neighbors:

| Discipline | Question it answers |
|---|---|
| Compliance | Are we in compliance? |
| Compliance operations | How do we *operate* to stay in compliance? |
| Audit | How do we *verify* we are in compliance? |
| Policy | What do our standards *say* we will do? |
| Governance | How do we *decide* what compliance means for us? |

The five neighbors are related but separable. A
program can have strong policy and weak operations —
the standards exist but nobody follows them. A program
can have strong audit and weak operations — annual
audits find quarterly gaps. Operations is the
*continuous practice* that connects the others.

### 1.1 The quarter-end-scramble failure mode

The single most common compliance-operations failure
mode in CAIRO programs: most of the year, compliance is
quiet; the week before the regulator deadline or the
auditor visit, everyone scrambles. Symptoms:

- Evidence packages are built from scratch each
  cycle.
- People who don't normally work on compliance get
  pulled in.
- The same questions get asked repeatedly because
  prior cycles' answers aren't easily findable.
- Some controls turn out to have not been
  operating for months; the team produces
  retroactive evidence to fill gaps.

The week-before-deadline pattern is itself a tell.
A program in good shape is *steady* — the quarter
end produces an evidence package built on
infrastructure that was already in place. Operations
is what makes the difference.

### 1.2 What working operations looks like

Three properties:

1. **Continuous.** Evidence is produced as a side
   effect of normal operations, not as a quarter-end
   task.
2. **Inspectable.** At any moment, the program can
   answer "what is our current state on obligation
   X" without preparing for the question.
3. **Tested.** The operations themselves are
   periodically tested — evidence pipelines
   exercised, control reviews held, gap analyses run.

A program with all three properties survives both
expected and unexpected regulator inquiry. A program
missing any of them does not.

### 1.3 What this module owns and doesn't

This module owns the *operational machinery* of
compliance:

- Control mapping discipline.
- Evidence cadence design.
- Coverage gap analysis.
- Automation decisions.
- Working application of ISO 42001 Annex A.

This module does *not* own:

- The compliance obligations themselves (mod-102).
- The evidence infrastructure (mod-108).
- The specific regulatory frameworks (mod-102, mod-104,
  mod-105).
- The internal-audit function (third line, separate
  from second-line compliance operations).

Where the boundary with the existing Compliance
function is unclear at your organisation, mod-101 §3
(three lines of defense) is the structural reference;
§6 of this module operationalizes it.

---

## §2. Control mapping

The most fundamental discipline in compliance
operations is **mapping a regulatory obligation to a
specific control**. Done well, the map is the source
of truth for what the program does. Done badly, the
map is wallpaper.

### 2.1 What a control map is

A control map is a structured statement of:

- The **obligation** (specific regulatory text or
  framework requirement).
- The **control** (the operating activity that
  satisfies the obligation).
- The **evidence** (the artifacts produced when the
  control operates).
- The **owner** (the role accountable for the
  control).
- The **cadence** (how often the control operates).
- The **test** (how the program verifies the control
  operates).

A control without all six elements is incomplete.
Programs with partial control specifications produce
evidence that auditors cannot connect to obligations.

### 2.2 The granularity problem

The same failure mode as event-vocabulary granularity
(mod-108 §3.1):

- **Under-granular.** One control covers many
  obligations; specific challenges to compliance
  cannot be answered from the map.
- **Over-granular.** Hundreds of controls, each
  covering a sliver; no human can hold the map in
  their head; auditors get lost.

The right granularity: **one control per
operationally-distinguishable obligation**. If two
obligations are satisfied by the same operating
activity (with the same evidence, same owner, same
cadence), they are one control covering two
obligations. If two obligations require materially
different activities, they are separate controls.

### 2.3 The crosswalk pattern

Many regulations have overlapping requirements (EU AI
Act Art. 9 risk management overlaps with NIST AI RMF
MANAGE function which overlaps with ISO 42001 §8).
The discipline: **build one control that satisfies
all overlapping obligations**, and cross-reference
the obligations in the control's documentation.

The crosswalk pattern keeps the control catalog
small. Programs that build one control per regulation
end up with three controls doing the same thing,
producing three sets of similar evidence, owned by
three roles, on three cadences.

### 2.4 Control specifications

A working control specification has the structure:

```
Control ID: HVN-CTL-007
Name: AI-system inventory currency
Owns: CAIRO function (AI Risk Lead)

Obligations satisfied:
  - EU AI Act Art. 6 (high-risk classification scope) — requires identification of systems in scope
  - ISO 42001 §6.1 + Annex A.6.1 — AI system inventory
  - NIST AI RMF GOVERN-1.6 — AI system inventory
  - SR 11-7 §III — model inventory
  - NYDFS Part 500 §500.13 — asset inventory (overlay)

Activity:
  - Maintain master AI inventory in <inventory system>
  - Quarterly business-unit attestation that inventory is current
  - Monthly automated reconciliation against deployed-system telemetry
  - On-change update on material system event

Evidence produced:
  - Quarterly signed attestation per business unit
  - Monthly reconciliation report
  - On-change inventory event in audit ledger

Cadence:
  - Monthly automated reconciliation
  - Quarterly business-unit attestation
  - On-change inventory event

Test:
  - Internal audit quarterly samples inventory entries against deployed systems
  - Annual external sampling during ISO 42001 audit
```

This control covers five separate obligations with
one operating activity. Programs with this discipline
produce small, defensible control catalogs.

### 2.5 What is *not* a control

Honest distinctions:

- **A policy is not a control.** "AI policy
  requires X" is the source of authority for a
  control, not the control itself. The control is
  the operating activity that satisfies the policy.
- **An aspiration is not a control.** "We will
  improve our bias monitoring" is not a control;
  the actual bias monitoring activity is. Programs
  with aspirations-as-controls fail audits where
  evidence is requested.
- **An organisational structure is not a control.**
  "We have an AI Risk Council" is not a control;
  the Council's decisions and review activities
  are. The Council itself is the *organisational
  container* in which controls operate.

Programs that confuse these end up with control
catalogs that are eloquent but not auditable.

---

## §3. Continuous evidence collection

Once controls exist, the program must collect
evidence that they operate. The §1.1 quarter-end
scramble is the default failure; *continuous*
collection is the discipline that prevents it.

### 3.1 What continuous means

Continuous evidence collection means:

- **Evidence is produced** as a side effect of the
  control's normal operation, not by a separate
  evidence-production task.
- **Evidence is captured** in the audit ledger
  (per mod-108) immediately.
- **Evidence is reviewable** by the control owner
  on a defined cadence shorter than the audit
  cadence.

A control whose evidence is only checked at audit
time is being audited, not operated.

### 3.2 The three review cadences

A working compliance operation has three review
cadences per control:

| Cadence | Reviewer | Question |
|---|---|---|
| Operating cadence | Control owner | Is the control operating today? |
| Steward cadence | CAIRO function / compliance ops team | Have all owners attested for the period? |
| Audit cadence | Internal audit | Are the controls operating as documented across the year? |

Operating cadence is the most frequent (daily,
weekly, or monthly depending on control). Steward
cadence is intermediate (monthly across the
portfolio). Audit cadence is annual or at the audit
firm's choice.

Programs with only audit cadence — the control owner
does not check their own control until the auditor
asks — discover failures too late to do anything
about them.

### 3.3 Evidence collection patterns

Three patterns recur in working compliance
operations:

**Pattern 1 — Telemetry-derived evidence.** Evidence
is computed from production telemetry. Example: the
proportion of agent operations subject to the trust
gate is computed from the trust gate's emission of
`trust-gate.decision` events (mod-108 Ex-01). The
control owner reviews the aggregate weekly; the
auditor samples specific weeks.

**Pattern 2 — Attested evidence.** A named role
attests that an activity occurred. Example: a
business-unit head attests quarterly that the AI
inventory for their unit is current. The attestation
itself is an event in the audit ledger.

**Pattern 3 — Document-as-evidence.** A document
(policy, minutes, plan) is itself the evidence.
Example: AI Risk Council meeting minutes are
evidence that the Council met and addressed agenda
items. The document is signed and added to the
ledger.

Most programs use all three patterns. The
discipline is choosing the right pattern per
control — and not over-using attestation (which is
cheap to produce but weak as evidence) at the
expense of telemetry (which is harder but stronger).

### 3.4 What goes wrong

Common evidence-collection failure modes:

- **Telemetry that doesn't aggregate to control
  evidence.** The data exists but isn't transformed
  into a form the control owner can review or the
  auditor can read. The fix is the *aggregation
  pipeline*, not more telemetry.
- **Attestation fatigue.** Owners are asked to
  attest to too many things; attestations become
  rubber-stamp. The fix is consolidation —
  fewer, larger attestations.
- **Documents not reviewed.** Meeting minutes are
  produced but never reviewed by anyone other than
  the secretary. The fix is making review part of
  the next meeting's agenda.

### 3.5 The cadence calibration question

How often should a control owner review their
control's operating evidence? A rough rule:

- **High-stakes, high-frequency controls**
  (trust-gate decisions, fairness monitoring for a
  customer-facing system): weekly review.
- **Standing controls** (inventory accuracy,
  policy currency): monthly.
- **Periodic controls** (annual risk register
  refresh, biennial training): quarterly.
- **One-time controls** (initial deployment review,
  major release approval): on event.

The wrong calibration in either direction is a
problem. Too-frequent review produces
review-fatigue and reduces signal. Too-infrequent
review allows control failures to persist.

---

## §4. Compliance automation

The compliance-tech industry markets automation
heavily. The marketing is partly right and partly
misleading. The discipline of *what to automate* is
itself a CAIRO question.

### 4.1 What's worth automating

Three categories where automation reliably adds value:

1. **Evidence aggregation.** Computing the
   week's-evidence summary from a million-event
   telemetry stream is computationally trivial and
   beneficial when done at machine speed.
2. **Crosswalk maintenance.** When ISO 42001 §A.X
   maps to NIST GOVERN-Y maps to EU AI Act Art.
   Z, machine-readable crosswalks let regulator
   changes propagate to the control map without
   manual reconciliation.
3. **Standard report generation.** Recurring
   reports (monthly business-unit attestation
   reminders, quarterly board pack data
   collection) automate well.

### 4.2 What's not worth automating

Three categories where automation tends to backfire:

1. **Judgment-laden decisions.** Whether a
   specific incident counts as an EU AI Act
   Art. 73 serious incident is a *judgment*. The
   automation can pre-classify; the decision is
   human.
2. **Novel obligations.** A regulation in its
   first year often has unclear application.
   Automating the unclear produces wrong results
   that look authoritative.
3. **Control-failure detection.** Detecting that a
   control isn't operating requires understanding
   what its operation looks like. This is often
   easier with human review until the program has
   sufficient history.

### 4.3 The automation trap

The most common compliance-automation failure:
buying a comprehensive compliance platform (OneTrust,
Vanta, IBM watsonx, AuditBoard, etc.) and then
configuring it to mirror the program's existing
practice. The platform produces an *appearance* of
operational sophistication without changing
underlying behaviour. Auditors see the dashboards
and assume the program is mature; the underlying
controls operate (or don't) the same as before.

The fix: only adopt automation after the underlying
control discipline is in place. Automation amplifies
existing practice — good or bad. Programs that
automate weak practice end up with sophisticated-
looking weak practice.

### 4.4 The vendor landscape

Practitioner patterns in compliance automation
tooling:

- **General compliance platforms** — OneTrust,
  Vanta, Drata, AuditBoard, Hyperproof. Strong on
  evidence collection workflow; weaker on AI-
  specific controls.
- **AI governance platforms with compliance
  features** — IBM watsonx.governance, Credo AI,
  Holistic AI. Strong on AI-specific controls;
  variable depth on classical compliance.
- **Hyperscaler-embedded compliance** — AWS Audit
  Manager, Azure Compliance Manager. Strong on
  infrastructure compliance; weaker on
  program-level AI controls.
- **Roll-your-own** with the audit ledger from
  mod-108 + custom aggregation. Full control;
  ongoing maintenance.

The CAIRO's contribution to the platform selection
follows the §6 build-buy framework from mod-106 and
mod-108. The reference position: most enterprise
programs do better with a *small, focused* platform
than with a large platform configured around their
specific shape.

---

## §5. ISO 42001 Annex A as control catalog

ISO/IEC 42001:2023 — the AI Management System standard
— includes Annex A: a list of controls (organised as
control objectives) that organisations should consider
in their AIMS. Annex A is one of the more useful
control catalogs available to CAIRO programs in 2026
because it is **authoritative** (a published standard)
and **operationally-shaped** (controls are written as
auditable activities, not principles).

### 5.1 Annex A structure

Annex A is organised into 10 control objectives,
each with multiple controls. The objectives:

1. Policies related to AI
2. Internal organisation
3. Resources for AI systems
4. Assessing impacts of AI systems
5. AI system life cycle
6. Data for AI systems
7. Information for interested parties of AI
   systems
8. Use of AI systems
9. Third-party and customer relationships
10. (Some implementations include) Performance
    evaluation overlay

For each objective, there are between 3 and 8
specific controls. Total: roughly 38 controls in
the published Annex A.

### 5.2 How to use Annex A

The practical use pattern:

1. **Start with the control objectives** as the
   organising spine of the program's control
   catalog.
2. **Map each Annex A control to a program control**.
   Some Annex A controls map 1:1; others map to a
   broader program control that satisfies multiple
   Annex A controls.
3. **Identify gaps** where the program does not have
   a corresponding control. These gaps are the
   remediation roadmap.
4. **Cross-reference with other obligations** — NIST
   AI RMF sub-functions, EU AI Act articles, sector
   regulations.
5. **Test against the program** annually as
   pre-audit preparation.

### 5.3 What Annex A does well

- **Comprehensive** — covers AI lifecycle from
  policy through retirement.
- **Auditable** — controls are written in
  operationally-testable form.
- **Standards-grade** — defensible to regulators
  who recognise ISO.
- **Crosswalkable** — published mappings to NIST AI
  RMF and EU AI Act exist.

### 5.4 What Annex A doesn't do well

- **Limited sector specificity.** Annex A is
  cross-sector; specific financial-services,
  healthcare, public-sector requirements need
  sector-overlay.
- **Doesn't address EU AI Act post-market
  monitoring as a separable artifact.** mod-102
  §2.6 named this; Annex A doesn't carry the same
  emphasis.
- **Trust-architecture and trust-gating not
  directly addressed.** Annex A pre-dates the
  agentic-AI patterns mod-106 introduces.

A working program uses Annex A as the spine and
overlays sector-specific and AI-evolution-specific
controls on top. Programs that adopt Annex A
verbatim and stop there have a defensible baseline
but miss material AI-program territory.

---

## §6. The CAIRO × Compliance Officer boundary

The Chief Compliance Officer (or Chief Compliance &
Ethics Officer; titles vary) is Sentinel's,
Halverston's, or Northfield's existing accountable
function for compliance. The boundary between the
CAIRO function and the Compliance Officer is the
third recurring CAIRO boundary problem (after MRM,
§5 of mod-104; CISO, §5 of mod-107).

### 6.1 What Compliance owns

- The enterprise compliance program — all
  regulatory obligations the organisation faces.
- The compliance risk register at the enterprise
  level.
- Regulator engagement strategy (some firms
  centralise this; others spread it).
- Investigation and discipline for compliance
  failures.
- Compliance training and culture.

### 6.2 What the CAIRO function owns

- AI-specific compliance obligations within the
  enterprise compliance program.
- The AI control catalog (the operational form of
  AI obligations).
- The AI continuous-evidence cadence.
- AI-specific regulator engagement (EU AI Act
  authorities, AI-specific state regulators).
- The CAIRO program's standards (mod-105, mod-107,
  etc.).

### 6.3 The intersection

| Topic | CAIRO and Compliance both have legitimate ownership |
|---|---|
| Obligations register | Compliance maintains the enterprise register; CAIRO contributes AI-specific entries |
| Control catalog | Compliance maintains enterprise controls; CAIRO maintains AI-specific controls; some controls live in both |
| Evidence collection | Compliance has organisation-wide infrastructure; CAIRO uses it with AI-specific overlays |
| Training | Compliance owns enterprise compliance training; CAIRO contributes AI-specific content |
| Investigation | Compliance leads investigations; CAIRO contributes AI expertise |
| Regulator engagement | Joint per topic; CAIRO leads AI-specific |

### 6.4 The operating pattern

The pattern that works:

- The CAIRO's controls **extend** the Compliance
  Officer's enterprise control catalog rather than
  duplicating it. AI-specific controls are
  *additional* to enterprise controls; where they
  overlap, one control covers both (per §2.3
  crosswalk pattern).
- The CAIRO's evidence flows into the **same
  evidence infrastructure** as Compliance's
  enterprise evidence. The audit ledger (mod-108)
  is shared.
- The CAIRO and Compliance Officer **review the
  obligations register jointly** at least
  quarterly.
- The CAIRO **contributes AI expertise to
  investigations** led by Compliance; the CAIRO does
  not run parallel investigations.

The patterns that fail:

- **Separate AI compliance function** running in
  parallel to enterprise Compliance.
- **CAIRO building separate enterprise-wide
  compliance machinery** that duplicates what
  Compliance already operates.
- **Compliance building AI-specific controls
  unilaterally** without CAIRO input on AI-program
  alignment.

### 6.5 The reporting line

Most firms have the Chief Compliance Officer
report to General Counsel or to the CEO directly.
The CAIRO function (per mod-101 §4) typically reports
to the CRO. This is a different reporting line —
the CAIRO and Compliance Officer are peer second-line
functions.

The cooperation pattern works when both report into
the same governance structure (the AI Risk Council,
the enterprise risk committee, the Board Risk
Committee). When they do not — when the Compliance
Officer reports through GC and the CAIRO through CRO
and never share a forum — the cooperation degrades
into ceremony.

Exercise 05 puts this boundary under specific
pressure.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **ISO/IEC 42001:2023 Annex A** — the control
   catalog §5 builds on.
2. **NIST AI RMF Playbook** — the cross-walk
   reference for §2.3.
3. **EU AI Act Art. 17** (quality management
   system) — the operational obligation §1's
   continuous practice satisfies.
