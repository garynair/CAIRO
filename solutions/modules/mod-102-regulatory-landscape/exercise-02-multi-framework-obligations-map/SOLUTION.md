# Exercise 02 — Multi-Framework Obligations Map — Reference Solution

## 1. Solution overview

This reference is for Crestbridge's specialty marine cargo
**AI-assisted underwriting workbench**. Three regimes are
consolidated: **EU AI Act** (EU exposure via Dublin
operations and EU-resident insureds), **NIST AI RMF**
(parent program anchor), and **NYDFS Part 500 + NAIC Model
Law** (US insurance regulation focused on Connecticut + NY +
California exposure). The register has 18 rows. The memo
classifies the workbench as **high-risk under Annex
III(5)(a)** (essential private services — insurance) and is
honest about three significant gaps.

## 2. Classification call

The workbench is **high-risk** under EU AI Act Art. 6(2) via
Annex III(5)(a) — *"AI systems intended to be used for risk
assessment and pricing in relation to natural persons in the
case of life and health insurance"* is the textual hook;
specialty marine cargo is a hard call, since the natural-
person-affected analysis is indirect (the policyholder is
typically a commercial entity, with natural persons as
beneficiaries). The reference takes the conservative position
that *Annex III(5)(a) applies* because the LLM-based
extractor processes broker emails that include natural-
person beneficiary information.

Art. 6(3) exemption analysis: the system surfaces a
*recommended* premium range, not a final premium. The
underwriter retains decision authority. This sounds like the
exemption — but the LLM extractor *populates the
underwriter's workbench fields directly*, which influences
the underwriter's evaluation. Exemption fails.

A defensible alternative classification (which the reference
considered and rejected) would be to call the workbench
limited-risk on the basis that specialty marine cargo
underwriting is principally commercial-line, with natural
persons only indirectly affected. The reference chose
conservatism because the cost of an under-classification
discovered at regulator review is high; the cost of
over-compliance is bounded.

## 3. Merged obligations register

| ID | System | Obligation | Source | Trigger | Owner | Status | Evidence |
|---|---|---|---|---|---|---|---|
| O-001 | Workbench | Risk Management System (continuous, iterative) | EU AI Act Art. 9; NIST GOVERN-1.1 / MAP-5.1 / MEASURE-2.5 / MANAGE-1.3 | High-risk classification | CAIRO + Underwriting Risk | Drafting | RMS document, iterative review log |
| O-002 | Workbench | Data governance and management practices | EU AI Act Art. 10; NIST MAP-2.x; NAIC Model Law §5 | High-risk classification + insurance regulation | CDO + AI Risk | Partial — Crestbridge has general data governance but no AI-specific overlay | Documented data practices, including training-data provenance |
| O-003 | Workbench | Technical documentation per Annex IV | EU AI Act Art. 11 + Annex IV | High-risk classification | Model Owner + Documentation Lead | Not started | Annex IV-conforming technical file |
| O-004 | Workbench | Record-keeping (automated logs) | EU AI Act Art. 12 | High-risk classification | CTO + Model Owner | Partial — operational logs exist, AI-decision audit log does not | Logs that allow ex-post evaluation of system decisions |
| O-005 | Workbench | Transparency and information to deployers | EU AI Act Art. 13 | High-risk classification | CAIRO + Underwriting | Drafting | Operating instructions to deployers (Crestbridge's own underwriting teams) |
| O-006 | Workbench | Human oversight | EU AI Act Art. 14; NIST MANAGE-2.1; NAIC Model Law §6 | High-risk classification + insurance regulation | Underwriting + CAIRO | Designed (underwriter authority preserved); needs documentation | Documented oversight mechanisms |
| O-007 | Workbench | Accuracy, robustness, cybersecurity | EU AI Act Art. 15; NYDFS Part 500 §500.3 + AI amendments | High-risk classification + NYDFS supervision | CISO + Model Owner | Partial — cybersecurity exists, AI-specific robustness testing does not | Robustness test reports, accuracy thresholds |
| O-008 | Workbench | Conformity assessment (Annex VI internal control) | EU AI Act Art. 43 + Annex VI | High-risk classification | CAIRO | Not started | Declaration of conformity |
| O-009 | Workbench | Registration in the EU database for high-risk systems | EU AI Act Art. 49 + Art. 71 | High-risk classification | CAIRO + Regulatory Engagement | Not started | Database entry |
| O-010 | Workbench | Post-market monitoring system | EU AI Act Art. 72 | High-risk classification | CAIRO + Model Owner | Not started | Documented monitoring system + actively-collected data |
| O-011 | Workbench | Serious-incident reporting | EU AI Act Art. 73; NYDFS Part 500 §500.17 | High-risk classification + NYDFS supervision | CAIRO + Incident Response | Drafting | Reporting procedure, timeline-tracked, regulator contact list |
| O-012 | Workbench | Adverse-action notice (where adverse decisions reach US natural persons) | ECOA / Reg B (US); state-level analogues | When the workbench's recommendation drives a denial of coverage | Underwriting + GC | Existing for non-AI; AI-overlay not yet | Adverse-action notice language inclusive of model-driven reasoning |
| O-013 | Workbench | Algorithmic discrimination testing (CO + state analogues) | CO Reg 10-1-1; NAIC Model Law §3 | Insurance regulation in CO + states adopting NAIC Model Law | Underwriting Fairness + AI Risk | Not started | Documented non-discrimination testing program |
| O-014 | Workbench | Third-party / vendor AI governance | NIST MANAGE-3.1; NYDFS Part 500 §500.11; EU AI Act (deployer obligations Art. 26 if GPAI used) | If any third-party model (e.g., LLM extractor) is used | Vendor Risk + CAIRO | Inventory exists; AI overlay incomplete | Vendor contracts with AI-specific provisions; ongoing risk monitoring |
| O-015 | Workbench | AI system inventory (parent program) | NIST GOVERN-1.6; NYDFS Part 500 §500.13 (asset inventory) | Continuous | CAIRO | In place | AI inventory, kept current |
| O-016 | Workbench | Risk-management program governance | NIST GOVERN-1.1 / GOVERN-2.1; NAIC Model Law §4 | Continuous | CAIRO | In place | Governance documentation |
| O-017 | Workbench | Notice to insured persons / brokers re: AI use | EU AI Act Art. 50; NAIC Model Law §7; CA AI Transparency Act | EU + US state regulatory regimes | Compliance + Marketing | Drafting | Customer-facing notice text |
| O-018 | Workbench | Board-level reporting of AI material risk | NIST GOVERN-3.x; NYDFS Part 500 §500.4(b) | Material risk threshold | CAIRO + CRO | Quarterly cadence agreed; first report pending | Board pack with AI risk section |

## 4. Operating-conclusion memo (½ page)

### Classification call

High-risk under EU AI Act Art. 6(2) via Annex III(5)(a).
Conservative call; the indirect natural-person effect of
specialty marine cargo could support a limited-risk
argument, but the LLM extractor processes natural-person
beneficiary data and the cost asymmetry favors
classification as high-risk. The conformity-assessment route
is Annex VI internal control.

### Double-coverage handling

Two obligations are most clearly double-covered:

- **Human oversight** (O-006). EU AI Act Art. 14 and NAIC
  Model Law §6 both require it. One documented oversight
  mechanism satisfies both. The Art. 14 documentation is
  the binding artifact; the NAIC requirements add
  insurance-specific framing but no incremental control
  obligation.
- **Serious-incident reporting** (O-011). EU AI Act Art. 73
  and NYDFS Part 500 §500.17 both require notification.
  Different timelines (Art. 73: 15 days for non-fundamental-
  rights incidents; NYDFS: 72 hours from the relevant
  trigger). One incident-response procedure with both
  timelines tracked; the shorter timeline is the binding
  one in practice.

### Top three gaps

1. **No AI-specific data governance** (O-002). Crestbridge
   has general data governance; the AI overlay (training-
   data provenance, third-party data restrictions, lineage)
   is missing. Without it, Art. 10 cannot be satisfied and
   adverse-action explainability will fail.
2. **No conformity assessment process** (O-008). No one at
   Crestbridge currently knows how to produce a declaration
   of conformity. External counsel engagement likely.
3. **No algorithmic-discrimination testing program** (O-013).
   Crestbridge has historical loss-ratio reviews but no
   protected-class testing. NAIC and Colorado will catch
   this.

### First kept-promise (30 days)

A drafted technical file per Annex IV (O-003) — even in
incomplete form. The technical file forces the program to
inventory what we *know* and what we *do not yet know* about
the workbench. It is the most useful single artifact for
both EU AI Act conformity and for the NYDFS asset-inventory
obligation, and producing it surfaces every other gap.

## 5. Reasoning notes

- **Why I picked NYDFS + NAIC instead of UK FCA.** UK
  regulatory AI posture in 2026 is supervisory-and-
  guidance, not rule-and-obligation. Picking the UK regime
  would have produced a register dominated by "principle:
  follow the FCA's guidance" rows, which is a less useful
  exercise than the US insurance regulation which has
  concrete obligations. If Crestbridge's London HQ exposure
  were the dominant regulatory surface, the UK choice
  would be defensible — but Crestbridge's US footprint and
  CT+NY+CA presence make NYDFS+NAIC the substantive choice.
- **Why I did not split Art. 9 RMS into multiple rows.**
  The RMS is *one obligation* covering the entire risk
  process. Splitting it into MAP/MEASURE/MANAGE rows is the
  NIST-internal structure, not the obligation structure.
  The merged register tracks obligations, not framework
  internals.
- **The conservatism trade-off.** Calling the workbench
  high-risk produces eighteen obligations; calling it
  limited-risk produces three. The cost of being wrong on
  the limited-risk side is potentially seven percent of
  worldwide turnover. The cost of being wrong on the
  high-risk side is the cost of producing the technical
  file and conformity assessment — six-figure, bounded.
  Asymmetry justifies conservatism.
- **What the next iteration should add.** A column for
  *who is the deployer* (Art. 26 obligations sit with the
  deployer; if Crestbridge sells the workbench, the
  deployer chain matters). The reference uses Crestbridge
  as both provider and deployer; an external-deployer
  variant would add 3–4 rows.

---

Maintained by [Girish Nair](https://github.com/garynair)
