# Exercise 01 — Frameworks Crosswalk — Reference Solution

## 1. Solution overview

This reference crosswalks **NIST AI RMF 1.0**, **ISO/IEC
42001:2023**, and the **EU AI Act (Reg. (EU) 2024/1689)** at
the sub-function / clause / article level. The mapping is
*defensible*, not unique — see §3 for honest places it could
have gone differently.

## 2. The crosswalk

| Concept | NIST AI RMF | ISO/IEC 42001 | EU AI Act |
|---|---|---|---|
| Role of leadership / governance | `GOVERN-1.1` — "Legal and regulatory requirements involving AI are understood, managed, and documented." | §5.1 — "Top management shall demonstrate leadership and commitment..." | Art. 17(1) — quality management system; Art. 26 — obligations of deployers |
| AI system inventory / scope | `MAP-1.1` — "Intended purposes, potentially beneficial uses, context-specific laws... and assumptions are understood and documented." | §4.3 — "Determining the scope of the AI management system" | Art. 6 — high-risk classification; Annex III — high-risk uses list |
| Risk identification | `MAP-5.1` — "Likelihood and magnitude of each identified risk based on expected use and past uses..." | §6.1 + ISO 23894 — "Actions to address risks and opportunities" | Art. 9(2)(a) — "identification and analysis of the known and the reasonably foreseeable risks" |
| Risk treatment | `MANAGE-1.3` — "Responses to the AI risks deemed high priority... are developed, planned, and documented." | §8.2 — "AI system risk treatment" | Art. 9(2)(d) — "the adoption of appropriate and targeted risk management measures" |
| Continuous monitoring | `MEASURE-2.3` — "AI system performance or assurance criteria are measured qualitatively or quantitatively and demonstrated." | §9.1 — "Monitoring, measurement, analysis and evaluation" | Art. 72 — post-market monitoring system |
| Documentation requirements | `GOVERN-1.6` + `MAP-4.1` — distributed across functions | §7.5 — "Documented information" | Art. 11 + Annex IV — technical documentation |
| Incident reporting | `MANAGE-4.3` — "Mechanisms are in place... to capture and share information about negative impacts." | §10.2 — "Nonconformity and corrective action" | Art. 73 — "Reporting of serious incidents" |
| External assurance / audit | `GOVERN-4.3` — "Organizational practices are in place to enable AI testing, identification of incidents, and information sharing." | §9.2 — "Internal audit"; §9.3 — "Management review" | Art. 43 — conformity assessment (third-party for some high-risk systems) |

Cells marked **partial** with `~`:

| Concept | Where the partial match lives |
|---|---|
| Continuous monitoring | NIST `MEASURE-2.3` is broader than EU AI Act Art. 72; Art. 72 specifically requires a *post-market monitoring system* as a separable artifact, which NIST does not require by name. |
| Documentation requirements | NIST distributes the requirement across `GOVERN` + `MAP`; ISO 42001 §7.5 is more centralized; EU AI Act Art. 11 + Annex IV is more *prescriptive* about content. |

No row is fully empty across all three frameworks for the
concepts chosen — that is itself informative.

## 3. Reflection

### 3.1 Most concrete vs. most flexible

The **EU AI Act** gives the most concrete obligations — by a
wide margin. Art. 11 + Annex IV specifies what must be in
the technical documentation; Art. 73 specifies the
serious-incident notification timeline (15 days for serious
incidents, immediately for widespread infringements). You
either produce these artifacts or you do not.

**NIST AI RMF** gives the most flexibility. It tells you
what functions need to be present and offers sub-categories
to consider; it does not tell you what good looks like in
each. This is a feature for orgs that want to design their
own program and a bug for orgs that want a checklist.

**ISO 42001** sits between — clauses are auditable in the
ISO sense (you can be certified against them), but the
implementation latitude is meaningful, especially in Annex A.

### 3.2 Asymmetric concept: post-market monitoring

The EU AI Act's **post-market monitoring system** (Art. 72)
is treated as a *separable, named artifact*. NIST AI RMF
treats monitoring as a continuous activity within MEASURE;
ISO 42001 treats it as part of §9 *Performance Evaluation*.
The asymmetry exists because the EU AI Act was drafted in
the lineage of medical-device and machinery regulation,
both of which have post-market surveillance as a named
regulatory artifact. NIST and ISO inherited a more
program-centric vocabulary from cybersecurity and
management-system standards respectively. The EU framing is
useful when you need to *show* a regulator the artifact;
the NIST framing is useful when you need to *operate* the
system.

### 3.3 Anchor framework for a global SaaS

For a global SaaS company, **anchor on NIST AI RMF, certify
against ISO 42001, comply with EU AI Act where in scope.**
The framework anchor is NIST because it survives
multi-jurisdictional operation: it is non-binding everywhere,
which means it does not force a US-centric or EU-centric
posture. ISO 42001 is the *external assurance* artifact
(certifiable, recognized internationally). EU AI Act is
*obligation overlay* for in-scope products.

The pattern is: NIST as the operating system, ISO as the
audit-shaped surface, EU AI Act as a compliance overlay.
The two largest mistakes are anchoring on EU AI Act (it does
not cover US sector regulation gracefully) or anchoring on
ISO 42001 first (it under-specifies operational design).

## 4. Reasoning notes

- **Why I avoided the popular "EU AI Act maps to NIST 1:1"
  framing.** It overstates the mapping. The frameworks share
  vocabulary because OECD principles are upstream of both,
  but their *unit of analysis* differs: NIST is functions,
  EU AI Act is articles attached to a use-case
  classification. Pretending the mapping is 1:1 produces
  brittle compliance programs.
- **Where this crosswalk is weakest.** The "Documentation
  requirements" row is the most condensed. A program-grade
  crosswalk would expand it into 5–10 rows, one per artifact
  family (model card, data card, risk register, impact
  assessment, technical file, …). I kept it compact for the
  exercise.
- **A row I almost added.** "Definition of 'AI system'" —
  the three frameworks define the term *meaningfully*
  differently (EU AI Act adopts an OECD-derived definition
  in Art. 3(1); NIST uses an operational one; ISO 42001
  references ISO 22989 for terminology). I omitted it
  because it is more useful as the topic of an Exercise 02
  scope-section than as a crosswalk row.

---

Maintained by [Girish Nair](https://github.com/garynair)
