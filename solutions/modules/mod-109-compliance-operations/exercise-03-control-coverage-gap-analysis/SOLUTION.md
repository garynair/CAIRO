# Exercise 03 — Control-Coverage Gap Analysis — Reference Solution

## 1. Solution overview

Halverston's coverage of ISO 42001 Annex A is
**partial** across the 10 control objectives —
strong on objectives 2–5 (policies, organisation,
resources, impact assessment), moderate on 6–7
(data, information), weak on 8–9 (use,
third-party). The top 5 gaps span post-market
monitoring formalisation, AI-specific
third-party governance, customer disclosure for
wealth advisory, AI-specific data governance, and
impact-assessment template formalisation. The
remediation roadmap closes 4 of 5 gaps pre-audit
and accepts the fifth (third-party governance
overlay) as a 6-month-post-audit residual with
specific monitoring.

---

## 2. Approach

**Scope.** ISO 42001 Annex A — all 10 control
objectives and approximately 38 controls within.

**Method.** Map each Annex A control to Halverston's
existing program controls (per mod-105, mod-106,
mod-107, mod-108 standards + the Exercise 01
mapping pattern). Identify gaps where no
Halverston control maps.

**Maturity scale:**

- **Not Present (NP)** — no Halverston control
  maps to this Annex A control.
- **Partial (P)** — a Halverston control maps but
  significant elements are missing or under-
  developed.
- **In Place (IP)** — a Halverston control fully
  maps; evidence is collected; audit cadence is
  established.
- **Mature (M)** — In Place + multi-year history
  of operation + lessons-learned integration.

---

## 3. The mapping

| Annex A control objective | Halverston coverage | Maturity | Gap notes |
|---|---|---|---|
| A.2 Policies related to AI | AI policy hierarchy from mod-101 §5; standards from mod-105–mod-107 | IP | None material |
| A.3 Internal organisation | CAIRO function + AI Risk Council + AI Review Board per mod-101 | IP / M | None material |
| A.4 Resources for AI systems | AI program budget + roles; engineering capacity per Halverston CTO | IP | None material |
| A.5 Assessing impacts of AI systems | Impact assessment template from mod-103 Ex-02 | P | Template formalisation: template exists but isn't yet authoritative; usage is inconsistent across LOBs |
| A.6 AI system life cycle | Lifecycle stops per mod-104 §4 | IP | Stop 9 (retirement) is not yet operationally tested |
| A.7 Data for AI systems | General data governance (CDO) + AI-specific overlay needed | P | AI-specific data governance is under-developed; data provenance not consistently documented |
| A.8 Information for interested parties | Affected-party explainability standard (Tessera Ex-03 pattern); customer disclosure for wealth advisory pending | P | Wealth advisory customer disclosure not yet formalised post the mod-105 Ex-05 decision |
| A.9 Use of AI systems | Operating-instructions to deployers per mod-105 Ex-03; specific control over uses pending | P | Use-of-AI policy is implicit, not explicit; post-market monitoring (Annex A.8.x) not formalised as separable artifact |
| A.10 Third-party + customer relationships | General vendor program; AI-specific overlay incomplete | NP / P | AI-specific third-party governance is the gap |

---

## 4. The top 5 gaps

### Gap 1 — Post-market monitoring not formalised as separable artifact

**Annex A reference:** A.8 — explicit post-market
monitoring of in-use AI systems.

**Halverston-specific implication:** Halverston
has continuous monitoring (per mod-108 Ex-02
pattern) but the *post-market monitoring system*
as a separable artifact (as the EU AI Act Art. 72
expects, per mod-102 §2.6) is not formalised.
This affects wealth-advisory and private-credit
systems with EU exposure most directly.

**Remediation activity:** Author a *Post-Market
Monitoring Standard* that explicitly designates the
existing monitoring infrastructure as the
post-market monitoring system; document the
artifact, the cadence, the responsible role, and
the reporting structure.

**Owner:** CAIRO function (AI Risk Lead).

**Target close:** 90 days (pre-audit).

### Gap 2 — AI-specific third-party governance

**Annex A reference:** A.10 — third-party AI
governance.

**Halverston-specific implication:** Halverston's
general third-party program assesses vendors for
classical risks (security, financial stability,
service quality). AI-specific concerns (vendor
model swaps per mod-104 Ex-04; foundation-model
behaviour drift; AI-specific data handling) are
not addressed in the assessment framework.
Particularly relevant for the vendor LLM used in
wealth advisory.

**Remediation activity:** Build an AI-vendor
assessment overlay to the general third-party
program. Specific criteria: AI-specific data
handling, model versioning policy, model identity
attestation, AI-specific incident notification.

**Owner:** CAIRO function + Vendor Risk Office +
Compliance.

**Target close:** 12 months (6 months post-audit).
*Accepted as residual gap during certification
window with the residual position documented in
the audit committee minutes.*

### Gap 3 — Wealth advisory customer disclosure

**Annex A reference:** A.7 — information for
interested parties.

**Halverston-specific implication:** The mod-105
Ex-05 decision was to disclose AI assistance to
wealth advisory clients. The disclosure language
has been drafted but is not yet operationally
deployed; clients have not yet been receiving
the disclosure.

**Remediation activity:** Finalise the disclosure
language; integrate with the wealth advisor's
communication system; train advisors on the
disclosure protocol; track adoption.

**Owner:** Head of Wealth Advisory + CAIRO function.

**Target close:** 60 days.

### Gap 4 — AI-specific data governance overlay

**Annex A reference:** A.6 — data for AI systems.

**Halverston-specific implication:** General data
governance under the CDO is mature but doesn't
cover AI-specific concerns: training-data
provenance, downstream-use restrictions,
data-poisoning detection (per mod-107 Ex-04
incident 3 pattern). The gap surfaced during the
mod-103 Ex-02 impact assessment template work.

**Remediation activity:** Author an AI Data
Governance Standard as overlay to the existing CDO
standards; populate per Tier 1 system with
specific data-source attribution, retention, and
use-restriction documentation.

**Owner:** CDO + CAIRO function (joint).

**Target close:** 120 days.

### Gap 5 — Impact-assessment template formalisation

**Annex A reference:** A.5 — assessing impacts of
AI systems.

**Halverston-specific implication:** The mod-103
Ex-02 impact-assessment template exists but is
not authoritative across LOBs. Different teams
use different versions; some use no template.
This affects the program's ability to
consistently assess impacts across the portfolio.

**Remediation activity:** Designate the mod-103
Ex-02 template as authoritative; update via the AI
policy hierarchy; require usage on all new
deployments and on annual refresh of Tier 1
systems.

**Owner:** CAIRO function.

**Target close:** 30 days (policy update); 6
months (full portfolio adoption).

---

## 5. Remediation roadmap

**Pre-audit (next 6 months):**

- Gap 1 (Post-Market Monitoring Standard) — 90
  days.
- Gap 3 (Wealth Advisory Customer Disclosure) —
  60 days.
- Gap 4 (AI Data Governance Standard) — 120
  days.
- Gap 5 (Impact Assessment Template
  Formalisation) — 30 days for policy; 6 months
  for portfolio adoption.

**Post-certification (months 6–12 after audit):**

- Gap 2 (AI-Specific Third-Party Governance) —
  full implementation by month 12 post-audit.
  *Accepted as residual gap during the
  certification window* — Halverston obtains
  certification with the gap acknowledged in the
  management review.

**Acceptance posture for un-closed gaps:**

Gap 2 is accepted as a 12-month residual because
the implementation requires coordination with the
Vendor Risk Office and Compliance that cannot be
compressed into the pre-audit window without
forcing change-control issues in the broader
third-party program. The acceptance is recorded
in the audit committee minutes with specific
monitoring: monthly progress reports to the AI
Risk Council; if the gap is not on track to close
by month 12, the residual is re-evaluated.

---

## 6. Reasoning notes

- **Why I tier-differentiated rather than rating
  each Annex A control individually.** Annex A has
  ~38 controls; rating each one would produce a
  longer document than the §5.2 use pattern
  intends. Tier-by-objective gives the audit
  committee the right granularity; auditor will
  verify per-control during the audit itself.
- **Why Gap 2 is the residual accepted gap.**
  AI-specific third-party governance requires
  building an overlay on a working third-party
  program. The overlay's specifics depend on
  decisions Halverston is making about the AI
  vendor landscape (per mod-106 Ex-05). Forcing
  closure pre-audit would risk authoring an
  overlay that conflicts with downstream
  decisions.
- **Why Gap 5 has a split target date.** Policy
  update is fast (publish the standard); portfolio
  adoption is slow (changing operating practice
  across three LOBs takes months). Acknowledging
  both is honest.
- **What this gap analysis deliberately doesn't
  do.** Rate Halverston's controls against
  external benchmarks. The reference is the
  internal-vs-Annex-A gap. External benchmarking
  is a separate exercise.

---

Maintained by [Girish Nair](https://github.com/garynair)
