# Deliverable 02 — AI Risk Taxonomy — Reference Solution

## 1. Solution overview

A 7-top-level taxonomy adapted for Northrise's
AI SaaS context. The Northrise-specific
addition: **Customer-Deployed Risk** as a
top-level category, distinct from the other
categories because the control surface lives
outside Northrise's direct enforcement reach.
Left out: separate Strategic and Reputational
top-levels (combined; Northrise's smaller scale
doesn't yet justify separation).

---

## 2. The taxonomy

| # | Top-level | One-line definition | Sub-categories | Maps to Northrise enterprise risk | Agent Platform | Analytics | Studio |
|---|---|---|---|---|---|---|---|
| 1 | **Model Performance Risk** | Model produces inaccurate, unreliable, or drift-prone outputs | Accuracy drift; calibration drift; data-pipeline failure | Operational | **Material** | **Material** | Moderate |
| 2 | **Bias and Fairness Risk** | Model produces systematically different outcomes for protected populations | Demographic bias; subgroup performance gap; representation gap | Compliance | Moderate (varies by customer use) | **Material** | Low |
| 3 | **Transparency and Explainability Risk** | Model outputs cannot be understood or audited at the level required | Explanation failure; auditor unreadable; regulator unreadable | Compliance | **Material** (customer-side audit) | **Material** | Moderate |
| 4 | **Privacy and Data Risk** | Model exposes, leaks, or improperly uses personal/confidential data | Training-data leakage; output disclosure; cross-customer leakage; PII exposure | Compliance | **Material** | **Material** | Moderate |
| 5 | **Security Risk** | Model can be attacked, manipulated, or exfiltrated | Prompt injection; model exfiltration; adversarial inputs; supply-chain compromise | Operational | **Material** | **Material** | **Material** |
| 6 | **Vendor and Foundation Model Risk** | Risk arising from foundation-model providers and AI infrastructure vendors | Provider failure; provider change; provider data handling; foundation model behavioral drift | Operational | **Material** | **Material** | **Material** |
| 7 | **Customer-Deployed Risk** | Risk arising from customer-side configuration and operation of products on customer infrastructure (Northrise-specific) | Customer mis-configuration; customer over-extension of agent capability; customer abuse of product capability beyond intended use | Operational + Reputational | **Material** | Low (Analytics is Northrise-hosted) | N/A (Studio is dev-tool only) |
| 8 | **Strategic and Reputational Risk** | AI-program failure that affects business strategy or public trust | Reputational disclosure; strategic mismatch; competitive positioning | Strategic | **Material** | **Material** | Moderate |

8 top-level categories. The Northrise-specific
addition (#7) reflects that the Agent Platform's
control surface lives partly at customer edge.

## 3. Reasoning notes

### Hardest call

The hardest call was whether to make
**Customer-Deployed Risk** a top-level category
or a sub-category of Operational Risk. Arguments
for sub-category: it's a kind of operational
exposure. Arguments for top-level: the control
surface is fundamentally different (Northrise
provides controls, customer configures) and the
risk-treatment patterns require different
discipline. The reference makes it a top-level
because the operational control model is
different in kind, not just in degree.

### What I deliberately left out

- **Catastrophic risk** (low-probability, high-
  severity). Northrise's Agent Platform has
  some catastrophic-adjacent failure modes
  (e.g., an agent autonomously taking
  high-blast-radius action at customer edge),
  but these are sub-cases under existing
  categories (Security #5 or Customer-Deployed
  #7). A separate Catastrophic top-level would
  be premature for a year-1 program.
- **Workforce risk.** Real concern at Northrise's
  growth rate (people displaced by AI; AI
  workforce competition), but enterprise risk
  language covers it; not AI-specific.
- **Concentrated foundation-model vendor risk**
  as a separate top-level. Sub-category of #6
  in this iteration; year-2 might warrant
  separation if Series D investors press on
  it.

### Enterprise risk mapping

Northrise doesn't yet have a formal enterprise
risk taxonomy; the closest equivalent is the
Series C investor materials' risk-factor
language (Operational, Compliance, Strategic,
Reputational, Financial). The mapping in the
table uses this vocabulary. Year-2 work will
likely formalise the enterprise taxonomy
itself, and this AI taxonomy will be
re-validated against it.

### Per-product applicability

The "where it applies" annotation distinguishes
material from technical. Bias risk applies
technically to all three products; it is most
material for Analytics (which often processes
customer-employee data for HR analytics
use cases) and customer-side material for
Agent Platform (depending on what customers
deploy). The annotation lets the program
prioritise controls without applying everything
everywhere.

### What would change the taxonomy

- If Northrise launches a fourth product line
  with novel risk characteristics, a category
  may need adding.
- If foundation-model vendor concentration
  becomes the binding risk (rather than the
  general vendor exposure), #6 splits.
- If a CRO joins in year 2 with a formal
  enterprise taxonomy, the mapping column
  needs reconciliation.

---

Maintained by [Girish Nair](https://github.com/garynair)
