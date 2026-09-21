# Deliverable 06 — Compliance Operations Baseline — Reference Solution

## 1. Solution overview

Compliance operations baseline for Northrise.
Obligations register covering ~18 distinct
obligations. Initial control map of 9 controls
covering the major obligation categories with
mod-109 §2.3 crosswalk pattern. Continuous
evidence cadence detailed for the AI inventory
control (the foundation control). Reflects
Northrise's existing SOC 2 maturity by cross-
referencing existing controls; reflects
resource constraints by phasing what year 1
can credibly operate.

---

## 2. Obligations register

| ID | Obligation | Basis | Trigger | In scope per |
|---|---|---|---|---|
| O-01 | High-risk AI system identification | EU AI Act Art. 6 | Northrise-hosted / customer-deployed | EU customers with high-risk use cases |
| O-02 | High-risk system risk management system | EU AI Act Art. 9 | Per O-01 | Same |
| O-03 | Technical documentation | EU AI Act Art. 11 + Annex IV | Per O-01 | Same |
| O-04 | Logging / record-keeping | EU AI Act Art. 12 | Per O-01 | Same |
| O-05 | Transparency to deployers | EU AI Act Art. 13 | Per O-01 | Same |
| O-06 | Human oversight | EU AI Act Art. 14 | Per O-01 | Same |
| O-07 | Post-market monitoring | EU AI Act Art. 72 | Per O-01 | Same |
| O-08 | Serious incident reporting | EU AI Act Art. 73 | All in-scope | All EU-operating products |
| O-09 | NYDFS cybersecurity event notification | NYDFS Part 500 §500.17 | NY-supervised customer affected | Customers in financial services |
| O-10 | GDPR data breach notification | GDPR Art. 33-34 | Personal data breach | EU-resident personal data |
| O-11 | SOC 2 controls (existing program) | Customer contractual | All in-scope | All products |
| O-12 | ISO 42001 (in progress) | Customer contractual + strategic | All in-scope | All products |
| O-13 | CA AI Transparency Act | CA AI Transparency Act + SB 243 | CA-resident customer | Consumer-facing products |
| O-14 | NYC AEDT bias audit | NYC Local Law 144 | Customer using product for hiring decisions | Analytics + Studio if used in HR contexts |
| O-15 | CFPB AI explainability expectations | CFPB Circular 2022-03 + general | Financial services customer using product for credit decisions | Per customer use |
| O-16 | HIPAA (BAA, security, privacy) | Customer contractual + HIPAA | Healthcare customer using product on PHI | Healthcare customers |
| O-17 | Foundation-model vendor SLA | Vendor contractual | All deployments using foundation-model vendors | All products |
| O-18 | Customer contractual AI Bill of Materials | Customer contractual | Top-20 enterprise customers | All products |

18 obligations. Mix of regulatory, contractual,
and strategic.

## 3. Initial control map (9 controls)

| Control ID | Name | Obligations satisfied | Activity | Evidence | Owner | Cadence |
|---|---|---|---|---|---|---|
| NR-CTL-01 | AI System Inventory | O-01, O-04, O-07, O-12, O-15, ISO 42001 §6.1 | Maintain master inventory of in-scope AI systems including customer-deployed agents at platform level | Inventory entries; quarterly attestations; on-change events | CAIRO function (AI Risk Lead) | Continuous (event-driven) + quarterly attestation |
| NR-CTL-02 | Impact Assessment | O-02, O-06, ISO 42001 §6.1.1 | Impact assessment per in-scope AI capability before release | Signed assessment artifact | CAIRO + Product Owner | Per release + annual refresh |
| NR-CTL-03 | Risk Management System | O-02, NIST AI RMF MANAGE | Continuous risk identification + treatment per the taxonomy | Risk register entries; treatment plans | CAIRO function | Continuous |
| NR-CTL-04 | Technical Documentation | O-03 | Annex IV-conforming technical files for high-risk Northrise-hosted systems; equivalent customer-deployment guidance for Agent Platform | Documented technical files | Product Owner + CAIRO function | Per release + on material change |
| NR-CTL-05 | Logging and Audit Trail | O-04, O-11 (existing SOC 2 cross-ref) | Audit ledger evidence flow per Deliverable 05 architecture | Ledger events | CTO (operates); CAIRO (specifies) | Continuous |
| NR-CTL-06 | Human Oversight Documentation | O-06, O-15 | For customer-deployment guidance: how customers configure human-in-loop; for Northrise-hosted: documented oversight | Configuration docs; customer guidance | Product Owner + CAIRO function | Per release |
| NR-CTL-07 | Post-Market Monitoring | O-07, O-12 | Performance + drift + customer-platform monitoring; per-Northrise-hosted-product bias monitoring on Analytics | Monitoring outputs in ledger | Engineering + CAIRO function | Continuous |
| NR-CTL-08 | Incident Response | O-08, O-09, O-10 | Incident classification + notification matrix execution | Incident reports + notifications | CAIRO function (lead); CISO supports | Per incident |
| NR-CTL-09 | Customer Guidance Maintenance | O-13, O-14, O-15, O-16, O-18 | Customer-facing guidance on configuring Northrise products for customer-side compliance obligations | Guidance documents + customer success interactions | CAIRO + Customer Success | Quarterly refresh |

The crosswalk pattern (one control satisfies
multiple obligations) keeps the count manageable.

## 4. Continuous evidence cadence for NR-CTL-01 (AI System Inventory)

**Why this control gets full cadence treatment:**
inventory is the foundation; without it, no
other control operates.

**Operating cadence (weekly):** AI Risk Lead
reviews inventory completeness against
Northrise's product engineering activity in the
trailing week (new capabilities released, new
customer deployments above threshold, vendor
changes).

**Steward cadence (monthly):** CAIRO reviews
aggregate inventory status; identifies gaps;
plans remediation.

**Audit cadence (annual):** Internal audit (not
yet in place at Northrise but pattern
established) samples inventory entries against
deployed AI capabilities.

**Evidence-collection patterns used:**

- Telemetry-derived: Product engineering activity
  feeds inventory automatically through
  release-process hooks (year-1 build).
- Attested: Quarterly business-unit head
  attestation that inventory is current.
- Document-as-evidence: Inventory snapshot
  signed quarterly and added to the audit
  ledger.

**Ledger interface:** Inventory entries are
themselves events in the audit ledger (per
Deliverable 05 architecture).

---

## 5. Reasoning notes

- **Why 18 obligations and not 30.** The
  register names obligations Northrise is
  actually exposed to. Adding speculative
  obligations (e.g., GDPR-style state privacy
  laws in jurisdictions Northrise doesn't yet
  operate) would dilute the focus.
- **Why 9 controls and not 20.** Crosswalk
  pattern (mod-109 §2.3) — each control
  satisfies multiple obligations. 9 is the
  count for foundation; year 2 will add more
  granular controls as the program matures.
- **Why the Customer Guidance control
  (NR-CTL-09) groups multiple state laws.**
  These laws all require customer
  configuration of Northrise products for
  customer-side compliance. The same Northrise
  control activity (customer guidance) satisfies
  them all.
- **What this baseline deliberately doesn't
  do.** Full per-system control specifications;
  comprehensive evidence cadence on all 9
  controls; the third-party AI vendor
  assessment criteria. These are year-2 work.

---

Maintained by [Girish Nair](https://github.com/garynair)
