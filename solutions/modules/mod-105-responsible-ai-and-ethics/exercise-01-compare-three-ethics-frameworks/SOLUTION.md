# Exercise 01 — Compare Three Ethics Frameworks — Reference Solution

## 1. Solution overview

The reference compares **OECD AI Principles (2024)**,
**IEEE 7000 series** (7000, 7001, 7003), and **EU HLEG
Ethics Guidelines for Trustworthy AI**. The clearest
operational disagreement is on **bias mitigation
methodology**; the clearest agreement is on **human
oversight as a structural requirement**. The
recommendation is a *combination anchor*: OECD principles
as the framing-language layer, IEEE 7000 series as the
operational standard, EU HLEG for the trustworthy-AI
seven-element framing within high-stakes contexts.

---

## 2. Comparison table

Dimensions: bias and fairness; transparency; human
oversight; accountability; safety / robustness.

| Dimension | OECD AI Principles (2024) | IEEE 7000 series | EU HLEG Trustworthy AI Guidelines |
|---|---|---|---|
| **Bias and fairness** | Principle 1.2: AI should respect non-discrimination. ~ *No operational definition; appeal to existing anti-discrimination law.* | IEEE 7003 §6: measurable bias property with documented metric trade-off; specifically requires multiple metrics + documented choice rationale. **Operational: required documented trade-off analysis.** | Guideline 2 (Diversity, non-discrimination, fairness): qualitative emphasis on equal opportunity + bias detection + stakeholder participation. ~ *Process-emphasizing without metric-specific guidance.* |
| **Transparency** | Principle 1.3: transparency and responsible disclosure for those *adversely affected*. **Operational: audience-defined to adversely-affected parties.** | IEEE 7001 §5–§7: audience-specific transparency model with five named audience types and content requirements per audience. **Operational: audience taxonomy with content depth specified.** | Guideline 4 (Transparency): traceability + explainability + communication; emphasizes both system-level and decision-level transparency. — *Less specific on audience differentiation.* |
| **Human oversight** | Principle 1.1: human-centered values; oversight as general norm. ~ *General principle.* | IEEE 7000 §6.4: requires explicit identification of decisions delegated to AI vs reserved to humans, documented in development process. **Operational: documented decision-delegation map.** | Guideline 1 (Human agency and oversight): human-in-the-loop / human-on-the-loop / human-in-command framework. **Operational: three modes specified for design choice.** |
| **Accountability** | Principle 1.5: organisations are accountable for the AI systems they design, develop, deploy, operate, or use. ~ *Principle-level; no operational mechanism.* | IEEE 7000 §6.2: identifies accountability roles in the development process; *less explicit on ongoing operation accountability.* | Guideline 7 (Accountability): auditability + minimisation and reporting of negative impacts + trade-offs + redress. **Operational: redress mechanism required.** |
| **Safety / robustness** | Principle 1.4: AI systems should be robust, secure, and safe throughout their lifecycle. ~ *Principle-level.* | — *Not directly addressed by 7000-series operational standards; covered in IEEE 2802 (data privacy) and others.* | Guideline 5 (Technical robustness and safety): resilience to attack + fallback plan + accuracy + reliability + reproducibility. **Operational: specific technical sub-requirements.** |

(Locator format: Principle X.Y for OECD; §N for IEEE
standards; Guideline N for EU HLEG.)

## 3. Operational-disagreement memo

> **MEMO**
> **Subject:** Operational disagreements across OECD,
> IEEE 7000, and EU HLEG — framing-principle-set choice.
> **From:** Chief AI Risk Officer
> **Date:** [date]
> **Pages:** 1

### Two clearest operational disagreements

**Disagreement 1 — Bias methodology.** IEEE 7003 treats
bias as a measurable property with explicit metric
trade-offs that must be documented; the operational
output is a documented metric-choice rationale. EU HLEG
treats bias as a property of process and stakeholder
participation; the operational output is a procedural
participation record. OECD provides no operational
definition. *Implication:* a program anchored on IEEE
7003 will produce a different bias-validation document
than one anchored on EU HLEG, even if both claim
compliance with their anchor. The validation tests, the
artifacts produced, and the basis for accepting residual
risk differ.

**Disagreement 2 — Transparency audience model.** IEEE
7001 specifies five named audience types with content
requirements per audience. EU HLEG and OECD do not
distinguish audiences this explicitly. *Implication:* a
program operationalizing IEEE 7001 produces audience-
specific transparency artifacts as a structural
requirement; a program operationalizing OECD or EU HLEG
may produce a single transparency document that
satisfies the principle as written but fails to deliver
to specific audiences.

### Two clearest operational agreements

**Agreement 1 — Human oversight as structural.** All
three frameworks treat human oversight as a structural
requirement (not just an advisory practice). OECD does
this principally; IEEE 7000 requires documented
delegation maps; EU HLEG names the three oversight
modes (in-the-loop / on-the-loop / in-command). A
program can operationalise any of the three.

**Agreement 2 — Accountability as organisational, not
individual.** All three frameworks place accountability
on the *organisation* deploying the AI, not on
individual developers or users. This is operationally
load-bearing for governance design.

### Recommendation: which to adopt

**Combination anchor.** Adopt:

- **OECD AI Principles** as the **framing-language
  layer**. Use OECD vocabulary in board reports,
  external communications, and program charter. OECD's
  international consensus makes it the right
  vocabulary for stakeholder communication.
- **IEEE 7000 series** as the **operational standard**.
  Use IEEE 7000 in the program's internal standards
  (development standard, validation standard,
  transparency standard). IEEE's operational specificity
  makes it the right reference for engineering.
- **EU HLEG** as the **trustworthy-AI seven-element
  framing** for in-scope high-stakes contexts. Use the
  seven elements as a structural checklist when
  reviewing systems against EU AI Act high-risk
  obligations.

This combination is defensible because each layer is
*locatable* (per §2.4) and the divisions of labor are
operational, not rhetorical.

### What I would not adopt

**UNESCO Recommendation as an operational anchor.** It
is foundational and reflects broad international
consensus, but its language is intentionally broad and
its operational implications are not specific enough to
guide a program's standards. UNESCO is valuable for
*global communication*; it is the wrong source for
program *operation*.

**Microsoft Responsible AI Standard as authoritative.**
It is a practitioner reference. Citing it as
authoritative would import a single firm's
operationalization into the program's authoritative
layer. Source policy: practitioner references are
adopted as patterns of practice, never as authoritative
guidance.

---

## 4. Reasoning notes

- **Why combination over pick-one.** Picking one
  framework forces choosing between OECD's communicative
  power, IEEE's operational specificity, and EU HLEG's
  trustworthy-AI structural framing. The combination
  uses each for what it does best. The risk is
  inconsistency across layers; the discipline is
  documenting which layer applies to which artifact.
- **Why I rejected UNESCO and Microsoft RAI rather than
  using them.** Both are useful in their context but
  neither is operationally adoptable as authoritative
  reference. UNESCO is too broad; Microsoft RAI is too
  vendor-specific. The reference is explicit about
  rejecting them — programs that adopt everything from
  every framework produce *collages*, not standards.
- **The hardest call.** Whether to anchor on IEEE 7000
  series alone vs. the combination. IEEE 7000 is the
  most operationally specific and could carry a program
  by itself. The combination won because OECD's
  external-communication value is real and IEEE 7000
  alone leaves the program without a stakeholder-facing
  vocabulary. A larger and more academically-credentialed
  CAIRO function could plausibly anchor on IEEE 7000
  alone and produce OECD-vocabulary translations as
  needed.
- **What this comparison deliberately under-specifies.**
  Privacy as a dimension. All three frameworks
  address privacy but the operational differences map
  cleanly onto existing privacy law (GDPR, state
  privacy acts). For a CAIRO program, privacy
  operationalization comes from privacy law, not from
  AI-specific frameworks; including it in this
  comparison would distort the comparison.

---

Maintained by [Girish Nair](https://github.com/garynair)
