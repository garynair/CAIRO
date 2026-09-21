# Exercise 01 — Map a Regulation to Controls — Reference Solution

## 1. Solution overview

Five Tessera controls covering all four EU AI Act
Art. 9 sub-paragraphs (with one cross-cutting
control covering the iterative-process requirement).
Each control includes all six required elements and
explicitly cross-references NIST AI RMF and ISO
42001 obligations.

---

## 2. The control mapping

### Control TES-CTL-009-A — AI risk identification

**Obligations satisfied:**

- EU AI Act Art. 9(2)(a) — identification and
  analysis of known and reasonably foreseeable
  risks
- NIST AI RMF MAP-5.1 — likelihood and magnitude
  of each identified risk based on expected use
- ISO 42001 §6.1.1 — actions to address risks +
  Annex A.4.2 (impact assessments)
- SR 11-7 §III(c) — initial model risk
  identification

**Activity:** AI Review Board reviews every Tier
1 deployment's impact assessment (mod-103 Ex-02
pattern). For each system, a documented impact
assessment exists naming the specific risks per the
mod-103 risk taxonomy.

**Evidence:** Signed impact assessment in the audit
ledger; AI Review Board minutes referencing the
review; impact-assessment entry in the system
inventory.

**Owner:** CAIRO function (AI Risk Lead).

**Cadence:** Per system at deployment + annually
per Tier 1 system + on material change.

**Test:** Internal audit samples 10 Tier 1
deployments quarterly; verifies impact assessment
exists and was reviewed within policy windows.

---

### Control TES-CTL-009-B — AI risk estimation and evaluation

**Obligations satisfied:**

- EU AI Act Art. 9(2)(b) — estimation and
  evaluation of risks from intended use and
  reasonably foreseeable misuse
- NIST AI RMF MEASURE-1.x and MEASURE-2.x —
  metrics and evaluations
- ISO 42001 §9.1 + Annex A.6.2 — monitoring,
  measurement, analysis
- SR 11-7 §IV — model validation

**Activity:** Per-system measurement plan (per
mod-103 Ex-03 pattern) with leading + lagging
indicators is in production. Indicator values are
reviewed per the §3.2 cadence.

**Evidence:** Continuous indicator emissions in the
audit ledger; weekly model-owner review
attestations; monthly AI Risk Council aggregate
review.

**Owner:** Model Owner (operating) + AI Risk Lead
(steward).

**Cadence:** Per operation (telemetry) + weekly
(model owner review) + monthly (steward review).

**Test:** Internal audit verifies measurement
plans exist and are operated for each Tier 1
system annually; samples five recent threshold
crossings and verifies response was per policy.

---

### Control TES-CTL-009-C — Data-risk evaluation

**Obligations satisfied:**

- EU AI Act Art. 9(2)(c) + Art. 10 — risks from
  data collection
- NIST AI RMF MAP-4.x (data) + MEASURE-2.5
  (training-data risks)
- ISO 42001 Annex A.6 (data for AI systems)
- SR 11-7 §III(a)(2) — data inputs

**Activity:** Data-governance review for each Tier
1 system at deployment + annual data refresh
review. Includes training-data provenance,
representativeness analysis, and downstream-use
constraints.

**Evidence:** Signed data-governance review
artifact in the audit ledger; data-source
attestation events for ingestion pipelines;
training-data card / datasheet per system.

**Owner:** CDO + Model Owner + CAIRO function
(joint).

**Cadence:** Per system at deployment + annual
refresh review + on material data-source change.

**Test:** Internal audit samples three systems
annually; verifies data-governance reviews are
current and evidence references are valid.

---

### Control TES-CTL-009-D — Risk-management measures with residual risk discipline

**Obligations satisfied:**

- EU AI Act Art. 9(2)(d) — adoption of risk-
  management measures with residual risk
- NIST AI RMF MANAGE-1.x — risk treatments
- ISO 42001 §8.2 + Annex A.5 (lifecycle)
- SR 11-7 §III(d) — model use

**Activity:** Per-risk treatment plans (mod-103
Ex-04 pattern) for each material risk in the
system. Controls applied are documented; residual
risk is explicitly named and accepted by the
appropriate level.

**Evidence:** Signed treatment plans in the audit
ledger; AI Risk Council minutes accepting residual
risk for material cases; quarterly residual-risk
review attestations.

**Owner:** Model Owner (first-line) + AI Risk Lead
(steward) + AI Risk Council (residual acceptance).

**Cadence:** Per material risk at identification +
re-evaluation triggers per the treatment plan +
quarterly portfolio review.

**Test:** Internal audit verifies that every
material risk in the AI risk register has a
treatment plan with named acceptor; samples
acceptance decisions for traceability to AI Risk
Council minutes.

---

### Control TES-CTL-009-X — Cross-cutting iterative-process requirement

**Obligations satisfied:**

- EU AI Act Art. 9 (continuous, iterative
  process)
- NIST AI RMF GOVERN-1.1 — RMS as a continuous
  process
- ISO 42001 §10 — continual improvement

**Activity:** AI Risk Council quarterly reviews
the program's overall RMS operation; identifies
findings requiring program-level change;
authorises updates to the AI risk taxonomy,
impact-assessment template, measurement plan
shape, or treatment-plan template as needed.

**Evidence:** AI Risk Council quarterly minutes
with explicit RMS-review agenda items; signed
charter / standard updates resulting from review;
metrics on the four-control operation.

**Owner:** CRO (Council chair) + CAIRO function
(prepares agenda + tracks actions).

**Cadence:** Quarterly Council review + annual
formal RMS attestation.

**Test:** Internal audit verifies Council
quarterly reviews occurred and resulting actions
were tracked; samples one quarter's actions for
implementation.

---

## 3. Reasoning notes

- **Why five controls and not nine.** Art. 9 has
  four sub-paragraphs but the iterative-process
  requirement applies across all of them. Folding
  the iteration into each of the four would produce
  duplication; carving it out as one cross-cutting
  control preserves clarity.
- **Why each control cross-references multiple
  obligations.** §2.3 crosswalk pattern. Tessera
  has multiple regulatory regimes simultaneously;
  each control should explicitly note which
  obligations it satisfies so the program doesn't
  need to re-derive coverage during each new
  regulator's inquiry.
- **Why I used joint owners on some controls
  (TES-CTL-009-C).** Data governance crosses CDO,
  Model Owner, and CAIRO function legitimately.
  Single-owner attribution would force a
  political fight that doesn't add control
  strength. Naming joint owners with documented
  coordination is the honest representation.
- **What this control map deliberately under-
  specifies.** The specific evidence-format details
  (what fields appear in the impact assessment,
  what schema the measurement-plan indicators
  follow). Those are downstream specification
  documents.

---

Maintained by [Girish Nair](https://github.com/garynair)
