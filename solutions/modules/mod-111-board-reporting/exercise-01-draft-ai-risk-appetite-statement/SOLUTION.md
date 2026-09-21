# Exercise 01 — AI Risk Appetite Statement — Reference Solution

## 1. Solution overview

A 3-page risk appetite statement for **Halverston
Capital** covering all 8 categories from the
mod-103 Ex-01 taxonomy. Each category combines
risk-class framing + boundary OR threshold
language. The bias-and-fairness section adopts
**equalized odds** as the primary fairness
conception, with explicit acknowledgment that
other conceptions (predictive parity) are not
enforced — the §2.5 impossibility-result
discipline.

---

## 2. The statement

> **HALVERSTON CAPITAL — AI RISK APPETITE
> STATEMENT v1.0**
> *Authored by Chief AI Risk Officer. Reviewed by AI
> Risk Council, CRO, CCO, GC. Pre-circulated to
> Audit Committee chair and Board Risk Committee
> chair. For Board adoption.*

### Preamble

AI risk at Halverston refers to the potential
for adverse consequences from decisions made by
or supported by artificial intelligence and
machine-learning systems operated by the
organisation. This statement establishes how
much AI risk Halverston is willing to take,
expressed in board-readable language.

This statement is **adopted by the Board** and
operated against by management. It is reviewed
annually, with material amendments requiring
Board ratification.

This statement is **subordinate to** Halverston's
enterprise risk appetite statement. Where the two
conflict, the enterprise appetite governs; this
statement adds specific AI dimensions the
enterprise appetite does not directly address.

### Risk categories

This statement addresses the 8 categories from
Halverston's AI risk taxonomy: Model Performance,
Bias and Fairness, Transparency and
Explainability, Privacy and Data, Security,
Vendor and Third-Party AI, Market and Conduct,
Strategic and Reputational.

### Appetite per category

**Model Performance.**

We accept material model-performance risk where
the business case justifies it and validation
demonstrates fitness for purpose. We do not
accept performance risk that materially affects
customers without explicit customer-experience
review.

*Threshold:* Model performance degradation
exceeding 10% from validated baseline triggers
mandatory AI Risk Council review for Tier 1
systems.

**Bias and Fairness.**

We adopt **equalized odds** (equal
true-positive AND false-positive rates across
protected populations) as Halverston's primary
fairness conception for binding-decision
systems. We explicitly *do not* enforce
predictive parity simultaneously; the
impossibility result establishes that these
cannot be simultaneously satisfied where base
rates differ, and equalized odds better serves
our affected populations' interests.

*Boundary:* Halverston will not deploy AI
systems producing binding adverse decisions
where sustained equalized-odds gaps exceed 5
percentage points across documented protected
populations.

*Threshold:* Single-period equalized-odds gap >
3 percentage points triggers AI Review Board
investigation; sustained gap > 5pp triggers
AI Risk Council mandatory remediation.

**Transparency and Explainability.**

We require that AI-driven decisions affecting
customers be explainable to the affected
customer in actionable terms (per the mod-105
Ex-03 standard pattern). We do not accept
deployment of customer-affecting AI without
affected-party transparency meeting Reg B /
GDPR Art. 22 standards.

*Boundary:* AI systems producing binding
adverse decisions for which we cannot provide
affected-party explanations meeting the
adopted standard are outside appetite.

**Privacy and Data.**

We require that personal data used by AI
systems be handled per the same standards as
non-AI personal data processing. AI-specific
personal-data risks (training-data leakage,
output exfiltration) are bounded by the trust
architecture and output filtering
infrastructure.

*Threshold:* Any AI-driven personal-data
disclosure beyond the documented use scope
triggers mandatory incident response per
mod-110 and Board notification per the
materiality framework.

**Security.**

AI-system security risks are bounded by the
defense-in-depth program (per mod-107 Ex-05).
We accept residual security risks within the
program's tiered application of the nine-layer
model.

*Threshold:* Multiple-layer security control
failure or trust-architecture compromise is
outside appetite without immediate AI Risk
Council convene.

**Vendor and Third-Party AI.**

We accept vendor AI risks proportionate to the
vendor's strategic importance and our migration
optionality. We do not accept critical-
infrastructure dependency on single vendors for
trust architecture, audit ledger, or other AI-
program-critical infrastructure (per the
mod-106 Ex-05 and mod-108 Ex-05 partner
pattern).

*Boundary:* Single-vendor concentration of more
than two critical AI-program functions is
outside appetite.

**Market and Conduct.**

For public-markets and private-credit AI
systems, we do not accept AI-driven systematic
strategies that produce or could produce
correlated market impact across multiple
participants. Market-conduct obligations apply
fully to AI-driven decisions and outputs.

*Boundary:* AI-driven decisions that produce
documented systematic patterns of market
inefficiency are outside appetite and require
immediate program-level review.

**Strategic and Reputational.**

We will pursue AI capabilities where they
materially advance Halverston's stated
strategic direction. We will not pursue AI
capabilities where the strategic benefit is
unclear and the reputational risk is material.

*Framing:* Strategic AI initiatives require
Board pre-approval at thresholds defined by
the materiality framework. Reputational risk
acceptance follows Halverston's enterprise
posture (no specific threshold beyond
enterprise framework).

### Escalation process

Cases approaching or exceeding the boundaries
above enter Halverston's AI incident
classification taxonomy (per mod-107 Ex-04 and
mod-110 Ex-04). Specifically:

- **Threshold approach** (within 80% of the
  named threshold) triggers AI Risk Lead
  notification and weekly review.
- **Threshold crossing** triggers AI Risk
  Council convene and incident response per
  mod-110.
- **Boundary violation** triggers immediate AI
  Risk Council convene, Board Risk Committee
  chair brief, and incident escalation.

### Review cadence

This statement is reviewed by the Board annually.
Material amendments may be proposed by the CAIRO
at any quarterly meeting; ratification follows
the standard Board approval process.

Off-cycle review may be requested by the Board
Risk Committee chair, the CRO, or the CAIRO at any
time.

— end statement —

---

## 3. Reasoning notes

- **Why I adopted equalized odds and named the
  rejection of predictive parity explicitly.**
  §2.5 + mod-105 §3.2 — programs that claim to
  enforce all fairness conceptions are not
  credible. Naming what is and is not enforced
  is the discipline.
- **Why some categories use threshold language
  and some use boundary.** Thresholds work for
  measurable categories (bias gaps, performance
  degradation); boundaries work for categorical
  obligations (must / must not). Both are
  legitimate; choice per category.
- **Why I subordinated this to the enterprise
  appetite statement.** Halverston has an
  existing enterprise statement; this is an AI
  overlay, not a replacement. Establishing
  subordination prevents conflicts later.
- **Why I included specific numbers.** The
  challenge §2.4 names — appetite is inherently
  fuzzy but the board needs to act on it.
  Specific numbers make the appetite
  operationally usable; reviewing them annually
  keeps them calibrated.
- **What this statement deliberately under-
  specifies.** The detailed operational
  metrics that operationalize each threshold;
  those live in standards downstream of this
  statement. The statement names the threshold;
  the standards specify the metric definition.
- **What would change my drafting approach.**
  For an organisation with less AI maturity
  than Halverston, the appetite would
  reasonably be expressed more conservatively
  (lower thresholds; tighter boundaries) with
  explicit recognition that the appetite will
  expand as the program matures.

---

Maintained by [Girish Nair](https://github.com/garynair)
