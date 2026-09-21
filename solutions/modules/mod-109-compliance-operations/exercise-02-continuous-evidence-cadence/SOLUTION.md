# Exercise 02 — Continuous Evidence Cadence — Reference Solution

## 1. Solution overview

A 3-cadence design for Northfield's bias-monitoring
control on the claims-triage v2 system. Operating
cadence: weekly review by the Clinical Validation
Lead. Steward cadence: monthly review by the AI
Risk Lead. Audit cadence: annual by Internal
Audit. Uses telemetry-derived evidence (primary),
attestation (steward + monthly), and
document-as-evidence (incident responses). The
between-quarterly concern is addressed by surfacing
weekly threshold-crossing data at the operating
cadence.

---

## 2. Control restatement

**Control NM-CTL-BIAS-019** — Demographic-stratified
bias monitoring for claims-triage v2 system.

**Activity:** Monthly demographic-stratified
performance evaluation against the equalized-odds
thresholds (sensitivity gap ≤ 3pp, specificity gap
≤ 5pp); weekly continuous monitoring of leading
indicators; per-event response on threshold crossings.

**Evidence:** Weekly monitoring data; monthly
evaluation runs; AI Review Board response records.

**Owner:** Algorithm Quality Office Clinical
Validation Lead (operating); AI Risk Lead (steward);
Chief Medical Officer (clinical authority).

---

## 3. The three cadences

### Operating cadence — weekly

- **Reviewer:** Algorithm Quality Office Clinical
  Validation Lead.
- **What they review:** Weekly aggregate of the
  bias-monitoring leading indicators — running
  sensitivity-gap and specificity-gap by site,
  current vs. trailing-4-weeks trend, any
  threshold-approaching values.
- **Trigger:** Calendar (every Monday); plus
  immediate trigger on any threshold-crossing event.
- **Artifact produced:** Signed weekly review
  attestation in the audit ledger
  (`bias_monitoring.weekly_review.attested` event
  type per the mod-108 Ex-01 vocabulary). The
  attestation includes the reviewer's signature, a
  reference to the data reviewed, and a one-line
  finding statement.
- **Escalation:** Trending-toward-threshold issues
  (sensitivity gap > 2.5pp at any site or
  specificity gap > 4pp) escalate to the AI Risk
  Lead within 5 business days. Actual threshold
  crossings escalate immediately to the AI Review
  Board.
- **Ledger interface:** Review attestation event;
  the data reviewed is referenced by hash to the
  underlying monitoring data already in the
  ledger.

### Steward cadence — monthly

- **Reviewer:** AI Risk Lead (CAIRO function).
- **What they review:** Monthly compilation of all
  weekly reviews for this control + any incidents
  + the monthly formal evaluation run; portfolio-
  level pattern across sites.
- **Trigger:** Calendar (first Tuesday of each
  month).
- **Artifact produced:** Monthly steward attestation
  in the audit ledger; if material patterns emerge
  (consistent trends across sites, repeated
  near-threshold events), the AI Risk Lead
  produces a finding document referenced from the
  attestation.
- **Escalation:** Material patterns escalate to
  the AI Risk Council at the next regular
  meeting (or convene the Council on the §6.5
  auto-escalation thresholds from mod-107 Ex-04).
- **Ledger interface:** Monthly attestation event;
  finding documents added to the ledger as
  document-evidence events.

### Audit cadence — annual

- **Reviewer:** Internal Audit (third line of
  defence, separate from the AI program).
- **What they review:** Full year of operating
  attestations + steward attestations + incident
  responses + threshold-crossings register; the
  measurement plan version history; the policy
  version history.
- **Trigger:** Annual audit calendar.
- **Artifact produced:** Internal Audit's annual
  report on the AI program, with this control's
  operation as one of the audited items.
- **Escalation:** Audit findings escalate to the
  Audit Committee + CRO + CAIRO; remediation actions
  tracked.
- **Ledger interface:** Annual audit findings
  document added to the ledger; specific findings
  may reference specific operating attestations
  via inclusion proofs.

---

## 4. Evidence collection patterns

The control uses **all three** patterns:

**Telemetry-derived (primary).** The leading
indicators (running sensitivity gap, specificity
gap by site, weekly aggregates) are computed from
the production telemetry of the claims-triage
system. The Algorithm Quality Office's monitoring
service aggregates the per-classification
demographic-stratified outcomes into the leading
indicators. No additional human action produces
this evidence; it is a side effect of the system
operating.

**Attested (secondary).** The weekly, monthly, and
annual reviews are themselves evidence that the
reviews occurred. The attestation event includes
the reviewer's signature, the data reference, and
the review's finding. Auditors look for both the
data (telemetry-derived) and the human review of
the data (attested).

**Document-as-evidence (third).** When a
threshold-crossing event occurs, the response
document (the incident classification per mod-107
Ex-04, the AI Review Board response, any
remediation plan) is itself evidence. The
documents are signed and added to the ledger as
document-evidence events.

---

## 5. Addressing what goes wrong

**Telemetry-that-doesn't-aggregate:** The Algorithm
Quality Office's monitoring service is responsible
for the aggregation pipeline. The pipeline's
outputs are reviewed weekly; if the aggregation
produces unclear or missing data, the weekly
review surfaces it within 5 business days rather
than at audit time.

**Attestation fatigue:** Three attestations per
year (weekly compresses to 52 quick attestations,
monthly to 12 longer ones, annual to 1 deep one)
across this single control feels heavy but is
calibrated: each weekly attestation takes 10
minutes (~ 9 hours/year per reviewer);
attestations are *not* duplicated across the three
cadences; the formats are different (weekly is a
checkbox-and-comment template; monthly is a
finding-or-no-finding analysis; annual is the audit
process). Fatigue is real but bounded.

**Documents not reviewed:** Threshold-crossing
response documents are referenced at the next
monthly steward review *and* at the AI Review
Board's monthly meeting. Documents that don't get
referenced are flagged by the AI Risk Lead within
30 days.

---

## 6. Addressing the regulator's between-quarterly concern

The regulator's specific concern was that quarterly
reviews may miss developing issues for up to 90
days. This design addresses it directly:

- **Weekly operating cadence** at the Clinical
  Validation Lead level surfaces issues within
  5–7 days of materialization.
- **Threshold-approaching escalation** (the > 2.5pp
  / > 4pp trigger that's tighter than the actual
  thresholds) catches developing problems before
  they cross the formal threshold.
- **The audit ledger preserves** the weekly review
  evidence so the regulator can verify that
  Northfield was operating the weekly cadence
  during any period of interest.

The regulator's between-quarterly concern is
substantively addressed; the program's cadence
operates an order of magnitude faster than the
regulator's expectation.

---

## 7. Reasoning notes

- **Why weekly and not daily for the operating
  cadence.** Daily review of bias-monitoring is
  too frequent for meaningful human attention;
  the day-to-day variation in the leading
  indicators is mostly noise. Weekly is the
  granularity at which trends are interpretable
  and at which the reviewer can give substantive
  attention.
- **Why the Clinical Validation Lead and not a
  generic AI Risk role.** Clinical context
  matters for interpreting bias-monitoring
  outcomes on a healthcare system. A pure-AI-risk
  reviewer would miss clinically-informative
  context.
- **Why the threshold-approaching escalation is
  asymmetric.** The 2.5pp sensitivity threshold
  for escalation is tighter than the 4pp
  specificity threshold because sensitivity
  matters more clinically (under-detection of
  sepsis or under-triage of acute cases is more
  harmful than over-triage). The asymmetry reflects
  the clinical-safety priority from mod-105
  Exercise 02.
- **What this design deliberately under-
  specifies.** The exact format of the weekly
  attestation template (checkbox vs. structured
  comment); the specific aggregation pipeline
  architecture (engineering decision); the
  retention of intermediate aggregation states
  (per the mod-108 Exercise 04 policy).

---

Maintained by [Girish Nair](https://github.com/garynair)
