# Deliverable 04 — AI Risk Appetite Statement — Reference Solution

## 1. Solution overview

3-page risk appetite statement for Northrise.
8 categories from Deliverable 02. Each combines
risk-class framing + threshold language. The
Customer-Deployed Risk category gets explicit
appetite treatment — Northrise accepts that
customer misconfiguration is partly outside
direct control but provides specific controls
and visibility. Bias category adopts equalized
opportunity as the primary fairness conception
for Analytics-driven hiring use cases (the
material bias surface).

---

## 2. The statement

> **NORTHRISE AI — AI RISK APPETITE STATEMENT v1.0**
> *Authored by Chief AI Risk Officer. Reviewed by CEO,
> CTO, GC, CFO. For Board adoption.*

### Preamble

AI risk at Northrise is the potential for
adverse consequences from Northrise's AI
products, internal AI usage, or customer
deployments built on Northrise infrastructure
producing outputs Northrise cannot defend. This
statement is adopted by the Board and operated
against by management.

This statement is subordinate to Northrise's
overall enterprise risk posture (currently
codified in Series C investor materials and
the Board-approved risk register). Where they
conflict, enterprise risk posture governs; this
statement adds AI-specific dimensions.

### Risk categories

Per Deliverable 02 taxonomy: 8 categories.

### Appetite per category

**Model Performance Risk.**
We accept material model-performance risk where
product value justifies it and customer-facing
communications honestly characterise the
product's limitations. Performance degradation
> 15% from validated baseline triggers
mandatory AI Review Board review for any
production capability.

**Bias and Fairness Risk.**
For Analytics use cases that produce or
materially inform binding decisions about
natural persons (e.g., hiring use cases), we
adopt **equalized opportunity** as the primary
fairness conception. We do not enforce
predictive parity simultaneously (mod-105 §3.2
impossibility result). Single-period gap > 5
percentage points in true-positive rate across
documented protected populations triggers AI
Review Board review.

For Agent Platform customer deployments,
appetite is more nuanced — customers configure
their agents. Northrise provides bias
monitoring tooling and customer guidance;
explicit appetite for what *Northrise* does
with the visibility this generates is bounded
by the customer-deployed appetite below.

**Transparency and Explainability Risk.**
For Northrise-hosted products affecting customer
decisions, customers receive explanations
meeting the documented Customer Explainability
Standard. Customer-deployed agents must
support customer's own affected-party
explanation requirements via documented
APIs. Outside appetite: any deployment where
Northrise cannot demonstrate to a regulator,
on request, what controls govern the
explainability of in-scope decisions.

**Privacy and Data Risk.**
Personal data is processed per documented
controls in line with applicable regulation
(GDPR, state privacy laws, healthcare-specific
where customers' use of products invokes
sector-specific obligations). Cross-customer
data leakage is outside appetite. Threshold:
any single cross-customer leakage event
triggers mandatory incident response and
immediate AI Risk Council convene.

**Security Risk.**
Bounded by Northrise's overall security
program (SOC 2, ISO 27001 in pursuit). AI-
specific overlays apply per mod-107 §3 nine-
layer model adapted for Northrise.
Multi-layer security control failure or trust-
architecture compromise is outside appetite.

**Vendor and Foundation Model Risk.**
Single-foundation-model-vendor dependency on
critical capabilities is outside appetite.
Northrise pursues multi-vendor strategy for
foundation-model providers; primary-vendor
outage tolerance is bounded by SLA terms in
customer contracts.

**Customer-Deployed Risk (Northrise-specific).**
This category requires explicit treatment.
Northrise's posture:

- **We provide controls.** Customers operate
  agents on Northrise infrastructure with
  Northrise-provided trust gates, monitoring
  tooling, and audit capabilities.
- **Customers configure controls.** Customer-
  side configuration choices are customers'
  responsibility per contract.
- **Northrise visibility.** Northrise has
  visibility into agent operation patterns at
  the platform level; this visibility informs
  Northrise's customer-deployment guidance
  and triggers Northrise-side actions on
  Northrise-controlled surfaces.
- **Outside appetite:** Customer deployments
  that operate outside the documented
  product capability boundary. Northrise
  identifies such deployments through
  platform-level monitoring and works with
  customers to bring them into the documented
  boundary or off the platform.

Specific threshold: > 1% of active customer
deployments operating outside the documented
capability boundary triggers AI Risk Council
review.

**Strategic and Reputational Risk.**
We accept reputational risk proportionate to
strategic ambition; we do not accept
reputational risk where the strategic benefit
is unclear or where mitigation requires
unprincipled customer-facing communication.

### Escalation process

Cases approaching or exceeding boundaries enter
incident classification per the in-progress
incident response policy. Pending formal
incident policy, the AI Risk Lead is the named
first responder for any threshold approach;
material crossings escalate to the AI Risk
Council; boundary violations trigger
AI Risk Council emergency convene + Audit
Committee chair notification within 24 hours.

### Review cadence

This statement is reviewed annually by the
Board. Material amendments may be proposed by
the CAIRO at any AI Risk Council meeting and
ratified by the Board through the standard
Northrise board process.

— end statement —

---

## 3. Reasoning notes

- **Why the Customer-Deployed Risk section is
  longer than others.** It's the Northrise-
  specific dimension and the most ambiguous;
  it deserves explicit treatment rather than
  inheriting language from financial-services
  reference patterns.
- **Why equalized opportunity (not equalized
  odds) for Analytics.** Equalized opportunity
  focuses on true-positive rate across
  qualified populations — the right
  conception for hiring use cases. Equalized
  odds would also be defensible but the
  reference picks the conception most directly
  applicable to the most material bias surface
  for Northrise.
- **Why some categories have specific
  quantitative thresholds and some don't.**
  Same calibration as mod-111 Ex-01 — where
  measurable, threshold; where qualitative,
  boundary or framing.
- **What would change.** As Series D investor
  diligence sharpens specific questions, some
  thresholds may need re-stating in
  investor-facing language. The substance
  shouldn't change.

---

Maintained by [Girish Nair](https://github.com/garynair)
