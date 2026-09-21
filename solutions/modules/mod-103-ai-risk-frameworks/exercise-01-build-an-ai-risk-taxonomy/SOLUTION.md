# Exercise 01 — Build an AI Risk Taxonomy — Reference Solution

## 1. Solution overview

For **Halverston Capital** the reference uses an
**8-top-level AI risk taxonomy** that rolls cleanly into
Halverston's existing 6-category enterprise taxonomy. The
hardest call was whether to split *Performance risk* into
model performance and process performance — the reference
keeps them together at the top level and splits in
sub-categories, because the enterprise taxonomy already
distinguishes operational risk. The most consequential
left-out: a separate *Catastrophic risk* category.

## 2. The taxonomy

| # | AI top-level | Definition (1 line) | Sub-categories | Enterprise roll-up | Public mkts | Private credit | Wealth advisory |
|---|---|---|---|---|---|---|---|
| 1 | **Model performance risk** | Model produces inaccurate, unreliable, or drift-prone outputs that affect downstream decisions | Accuracy drift; calibration drift; out-of-distribution failure; data-pipeline disruption | Operational | **Material** | **Material** | Moderate |
| 2 | **Bias and fairness risk** | Model produces systematically different outcomes for protected classes or affected populations | Disparate-impact in adverse decisioning; subgroup performance gap; representation gap in training data | Compliance | Low | **Material** | **Material** |
| 3 | **Transparency and explainability risk** | Model outputs cannot be understood, audited, or contested at the level required by affected parties or regulators | Adverse-action explanation failure; auditor unreadable; regulator unreadable | Compliance | Moderate | **Material** | **Material** |
| 4 | **Privacy and data risk** | Model exposes, leaks, or improperly uses personal or confidential information | Training-data leakage; output disclosure; aggregator data misuse; cross-tenant leakage | Compliance | Moderate | **Material** | **Material** |
| 5 | **Security risk** | Model can be attacked, manipulated, or exfiltrated by adversaries | Prompt injection; model exfiltration; adversarial examples; supply-chain compromise | Operational | Moderate | Moderate | **Material** |
| 6 | **Vendor and third-party AI risk** | Risk arising from third-party model providers, data providers, or AI-system vendors | Provider failure; provider change; provider data handling; embedded sub-vendors | Operational | **Material** | **Material** | **Material** |
| 7 | **Market and conduct risk** | AI-driven strategy or recommendation produces concentrated, correlated, or otherwise systemic market harm or violates market-conduct obligations | Correlated-strategy risk; manipulation-like patterns; herding | Market | **Material** | Low | Low |
| 8 | **Strategic and reputational risk** | AI deployment misaligns with strategic direction or, if disclosed, would materially damage trust | Reputational disclosure risk; strategic-mismatch; unsanctioned-AI risk (shadow AI) | Strategic | **Material** | **Material** | **Material** |

## 3. Reasoning note

### The hardest call

The hardest call was **Performance vs. Operational**. A
defensible alternative would have split *Performance risk*
into model-quality performance (accuracy, calibration)
and operational performance (latency, availability,
dependency). The reference keeps them together because
Halverston's enterprise *Operational* category already
contains availability, capacity, and dependency framings;
splitting Performance at the AI top-level would create a
seam where the same operational concern lives in two
places. The cost of keeping them together is that
"performance" is now slightly broader than the model-
quality framing some people will expect. Sub-categories
clarify.

### The enterprise mapping seam

Two top-levels do not have a *clean* fit:

- **Bias and fairness** maps to *Compliance* in the
  reference. A defensible alternative would map it to
  *Operational* (it shows up as operational measurement)
  or to *Strategic* (long-term reputational damage). The
  reference picks Compliance because (a) the enforceable
  fair-lending and discrimination law lives there, and
  (b) the AI Risk Council and the Compliance Committee
  share a chair at Halverston, simplifying escalation.
- **Vendor and third-party AI** maps to *Operational*.
  This is a stretch — vendor risk has a compliance
  dimension and a strategic dimension. The reference
  picks Operational because Halverston already runs
  vendor risk through an Operations sub-committee, and
  the AI-specific vendor concerns are *new* obligations
  for that committee rather than a new committee.

### What I deliberately left out

- **Catastrophic risk** (low-probability, high-severity
  scenarios). The reference does not add this category
  because Halverston is not a frontier-AI organisation
  and the existing *Strategic* and *Market* categories
  cover its high-severity exposures. A frontier-AI org
  (an AI lab, a self-driving company) would add this.
- **Sustainability risk** (e.g., compute footprint as a
  reputational concern). Not material at Halverston's
  scale; would dilute the taxonomy.
- **Workforce risk** (employees displaced by AI). A real
  concern but Halverston's enterprise taxonomy already
  has *People and Culture* under Operational; AI-
  workforce risk lives there as a sub-issue, not as an
  AI top-level.
- **Concentrated-vendor risk** as a separate top-level.
  The reference puts it in sub-category 6 because
  carving it out would over-emphasize a single sub-issue.

The discipline is that *every* taxonomy has these "could
have added" categories; the goal is the smallest taxonomy
that handles the org's actual risks.

## 4. Reasoning notes

- **Why 8 and not 9.** The starting taxonomy in §2.2 had
  9. The reference dropped *Strategic risk* (kept as
  Strategic-and-reputational combined) and added *Vendor
  and third-party AI risk*. Halverston's vendor exposure
  across all three lines justified the split-out;
  separating strategic from reputational would have
  created a tight seam.
- **Why "where it applies" matters.** The annotation is
  what makes the taxonomy operationally useful. Without
  it, the same controls would be required everywhere.
  Public markets has minimal bias-and-fairness exposure
  (model decisions affect prices, not natural persons),
  so the bias controls do not have to be the same as the
  private-credit ones. The annotation lets the program
  be honest about where controls are *required* vs.
  where they are *prudent*.
- **What the next iteration should add.** A "data
  domain" column distinguishing financial-counterparty
  data from natural-person-customer data — this would
  refine privacy and bias categories per system. The
  reference omits for size discipline.

---

Maintained by [Girish Nair](https://github.com/garynair)
