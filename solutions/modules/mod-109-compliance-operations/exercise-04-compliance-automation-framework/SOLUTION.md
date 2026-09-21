# Exercise 04 — Compliance Automation Framework — Reference Solution

## 1. Solution overview

A 5-criteria framework applied to 8 Tessera
compliance activities. 4 are "automate," 2 are
"partially automate," 2 are "don't automate." The
recommendation is **partial adoption of OneTrust**
— scoped to the 4 fully-automatable activities,
not the comprehensive deployment the CTO
originally proposed. The reasoning explicitly
addresses the §4.3 trap.

---

## 2. Decision criteria

The framework uses five criteria:

| Criterion | How it weighs in |
|---|---|
| **Volume** | High-frequency activities benefit more from automation; low-frequency activities don't amortise cost |
| **Judgment** | Judgment-laden activities should not be automated (per §4.2); automation can support but not decide |
| **Maturity** | Activities without mature underlying practice should not be automated (per §4.3); automation amplifies, doesn't establish |
| **Standardisation** | Activities that are uniform automate well; activities with high variation produce wrong results when automated uniformly |
| **Vendor independence** | Activities that tie Tessera to a specific vendor's model of practice carry vendor capture risk |

---

## 3. The decisions

### Activity 1 — Evidence aggregation (across the program)

| Criterion | Assessment |
|---|---|
| Volume | High — millions of events daily |
| Judgment | Low — aggregation is mechanical |
| Maturity | High — Tessera's audit ledger (mod-108) is mature |
| Standardisation | High — event vocabulary is standardised (mod-108 Ex-01) |
| Vendor independence | Medium — aggregation logic could become vendor-specific |

**Decision: Automate.** Aggregation is the
clearest automation candidate. Vendor independence
risk addressed via standards-conformant export
(per mod-108 Ex-05).

### Activity 2 — Crosswalk maintenance (regulatory mappings)

| Criterion | Assessment |
|---|---|
| Volume | Medium — crosswalks change with each regulator update |
| Judgment | Low for routine updates; high for novel regulations |
| Maturity | Medium — Tessera's obligations register exists but isn't mature on AI-specific cross-mappings |
| Standardisation | High once established |
| Vendor independence | High — crosswalks should be standards-based |

**Decision: Automate** for routine updates;
**don't automate** for novel-regulation handling.
The first time a new regulation is mapped,
human; subsequent updates can use the established
mapping.

### Activity 3 — Incident classification (per mod-107 Ex-04)

| Criterion | Assessment |
|---|---|
| Volume | Medium — multiple incidents per quarter |
| Judgment | **High** — classification often requires interpretation of facts |
| Maturity | Medium — taxonomy is established but reclassification (§6.5 of mod-107 Ex-04) is judgment-laden |
| Standardisation | Low — incidents vary materially |
| Vendor independence | High — classification is Tessera's |

**Decision: Don't automate.** Per §4.2 judgment-
laden category. Automation can produce a
*provisional* classification at intake; the actual
classification decision is human (the AI Risk Lead
or CAIRO function).

### Activity 4 — Quarterly board pack preparation

| Criterion | Assessment |
|---|---|
| Volume | Low — quarterly |
| Judgment | Mixed — data aggregation is mechanical; narrative is human |
| Maturity | Medium — Tessera's quarterly process exists |
| Standardisation | Medium — narrative varies by quarter |
| Vendor independence | Medium |

**Decision: Partially automate** — data aggregation
into the board pack format, automated; narrative
synthesis, human.

### Activity 5 — Vendor risk assessment for AI vendors

| Criterion | Assessment |
|---|---|
| Volume | Low — vendor selection is infrequent |
| Judgment | **High** — vendor risk requires substantial judgment |
| Maturity | Low — AI-specific vendor assessment is not mature at Tessera |
| Standardisation | Low — vendors are heterogeneous |
| Vendor independence | High |

**Decision: Don't automate.** Per §4.2 (judgment)
and §4.3 (immature practice). Human assessment
process should be operating cleanly before any
automation is considered.

### Activity 6 — Adverse-action notice generation

| Criterion | Assessment |
|---|---|
| Volume | High — thousands of notices daily |
| Judgment | Medium — the underlying decision is judgment-laden but the notice itself follows a template |
| Maturity | High — Tessera's adverse-action process is mature |
| Standardisation | High — notices follow regulatory-required templates |
| Vendor independence | High |

**Decision: Automate** the notice *generation*
(template population from the decision data); the
underlying *decision* remains the model + the
underwriter per existing program. The notice
language and explainability per mod-105 Ex-03
must be honest, not formulaic.

### Activity 7 — Bias-monitoring threshold-crossing detection

| Criterion | Assessment |
|---|---|
| Volume | High — continuous monitoring |
| Judgment | Medium — threshold-crossing detection itself is mechanical; *meaning* of a crossing is judgment |
| Maturity | High — Tessera's bias monitoring is mature |
| Standardisation | High — thresholds are defined |
| Vendor independence | High |

**Decision: Partially automate.** Detection of the
crossing event is automated (the §3.2 leading
indicator system surfaces it within the operating
cadence). The *response* to the crossing is human
— the Algorithm Quality Office Clinical Validation
Lead's weekly review determines whether response
is required.

### Activity 8 — Training completion tracking

| Criterion | Assessment |
|---|---|
| Volume | High — thousands of employees, multiple courses |
| Judgment | Low — completion is binary |
| Maturity | High — Tessera's training infrastructure is mature |
| Standardisation | High |
| Vendor independence | High — most training platforms are interchangeable |

**Decision: Automate.** Cleanest automation
candidate.

---

## 4. Platform recommendation

### Whether to adopt

**Yes, but partial.** The 4 fully-automatable
activities + 2 partially-automatable activities
justify a platform. The 2 don't-automate
activities should not flow through the platform
(integrating them creates risk of accidental
automation later).

### Which platform

**OneTrust** is the recommendation for Tessera,
based on:

- Strong evidence-collection workflow (matches
  Activity 1 — Evidence aggregation).
- Crosswalk maintenance capability (matches
  Activity 2).
- Generic enough that Tessera-specific event
  vocabulary (from mod-108 Ex-01) can be
  accommodated.
- Standards-based exports (mod-108 §6.4 vendor
  capture mitigation).

Vanta and Drata are credible alternatives;
OneTrust is recommended for Tessera's
financial-services scale specifically. IBM
watsonx.governance is rejected for this scope
because it imposes IBM's broader governance model
on the program where Tessera's existing program
is already established.

### What to use the platform for

- Activity 1 (evidence aggregation).
- Activity 2 (crosswalk maintenance, routine
  updates).
- Activity 4 (board pack data aggregation;
  not narrative).
- Activity 6 (adverse-action notice template
  generation).
- Activity 7 (threshold-crossing detection
  alerting; not response).
- Activity 8 (training tracking).

### What to keep outside

- Activity 3 (incident classification) — judgment.
- Activity 5 (AI vendor assessment) — judgment +
  immature.
- Activity 4 narrative work — judgment.
- Activity 6 underlying decision — judgment.
- Activity 7 response — judgment.

### Cost-benefit at $0.8M/year

The 4 fully-automatable activities save
approximately 3 FTE of compliance operations
work — $1.2M+ annually at Tessera's compensation
rates. The 2 partially-automatable activities
save another 1 FTE. The platform pays for itself
within year 1.

The §4.3 trap is addressed: Tessera adopts the
platform only for activities where the underlying
practice is already mature. Activities where
practice is immature (vendor risk, incident
classification) are explicitly kept outside the
platform.

---

## 5. Reasoning notes

- **Why I split the 8 activities into automate /
  partial / don't automate.** The framework
  forces a discipline of *naming what is human*
  in each activity. "Automate" without specifying
  what stays human produces the §4.3 trap; the
  trichotomy makes the human role explicit.
- **Why I rejected the comprehensive deployment.**
  The CTO's proposal was for a fully-automated
  compliance posture. That's the §4.3 trap by
  another name — and at Tessera's scale, the
  failure would not be cheap.
- **Why OneTrust over the alternatives.** OneTrust
  has the broadest evidence-collection workflow
  in the price tier; Vanta is stronger on
  smaller-scale programs; Drata is in between.
  Tessera's scale (millions of events daily)
  fits OneTrust's enterprise tier; the smaller
  vendors would require scaling effort. IBM
  watsonx.governance is structurally a different
  product — better for organisations building
  their governance from scratch.
- **The hardest decision.** Activity 7 (bias-
  monitoring threshold-crossing detection). The
  argument for full automation: detection is
  mechanical. The argument for partial: response
  is judgment. The reference takes the partial
  position because automated *response* to bias
  crossings would create false confidence in
  remediation; programs that automate response
  here have had high-profile failures.
- **What this framework deliberately doesn't
  address.** The specific integration architecture
  with Tessera's audit ledger; the data model
  for OneTrust; the migration timeline.
  Engineering decisions downstream of the CAIRO's
  contribution.

---

Maintained by [Girish Nair](https://github.com/garynair)
