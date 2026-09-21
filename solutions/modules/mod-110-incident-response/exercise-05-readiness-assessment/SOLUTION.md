# Exercise 05 — Organizational Incident-Readiness Assessment — Reference Solution

## 1. Solution overview

A readiness assessment for **Aldwych Health**.
Eight dimensions rated; overall verdict **Mostly
Ready with three named blockers** (clinical-
authority-boundary integration, patient-
notification communications testing, MHRA-
specific notification channel gaps). The
assessment is honest about gaps — fully-positive
ratings for a newly-implemented program would not
be credible.

---

## 2. Scope and method

**Scope:** Aldwych Health's AI incident response
readiness across people, process, technology.
Covers the new claims-triage v2 system and the
broader AI program governance machinery.

**Method:** Document review (the program's
charters, standards, and playbooks); interviews
with named role-holders; a 4-hour tabletop
exercise conducted three weeks ago; sampling of
recent incident-adjacent events.

**Readiness scale:**

- **Ready (R):** Capability operates reliably
  under load; recent evidence supports.
- **Mostly Ready (MR):** Capability operates but
  with known gaps; gaps don't block operational
  status.
- **Partial (P):** Capability partial; gaps may
  block operational status.
- **Not Ready (NR):** Capability not in place.

---

## 3. The dimensions assessed

### Detection capability — MR

*Current state:* Algorithm Quality Office
monitoring infrastructure operates per mod-105
Ex-02 + mod-109 Ex-02 patterns. Tabletop
exercise demonstrated detection within minutes
of threshold crossings. *Evidence:* Tabletop
results; recent threshold-crossing event
correctly detected at Site H-12 (mod-110 Ex-01
scenario).

*Top gap:* Trend-toward-threshold leading
indicators are not yet operational; detection
relies on actual threshold crossings rather than
trend prediction. This was a finding from the
Site H-12 incident review.

*Recommendation:* Implement trend-toward-
threshold monitoring per the Exercise 04 worked
example.

### Classification capability — MR

*Current state:* Classification taxonomy from
mod-107 Ex-04 is implemented; AI Risk Lead and
CISO on-call training has been completed.
Tabletop showed classification within the first
hour. *Evidence:* Tabletop results; training
records.

*Top gap:* Joint-classification decisions where
both AI-program and security dimensions are
present sometimes default to one or the other
rather than fully exercising the joint pattern.

*Recommendation:* Add a joint-classification
dimension to the next tabletop scenario.

### Containment capability — MR

*Current state:* Site-level and capability-level
containment have been tested via the H-12
incident and the tabletop. Full system pause has
not been tested. *Evidence:* H-12 site-level
pause operated cleanly.

*Top gap:* Full system pause has not been
exercised; the clinical-fallback workflow at
scale (more than one site) is untested.

*Recommendation:* Tabletop a multi-site pause in
the next quarterly exercise.

### Investigation capability — MR

*Current state:* The five-whys discipline is
established; the H-12 incident review produced a
substantive systemic-cause finding. *Evidence:*
H-12 PIR (per Exercise 04 worked example).

*Top gap:* Investigation independence for
incidents involving the CAIRO function itself has
not been worked out — internal audit-led
investigation pattern needs further definition.

*Recommendation:* Author an "independence
protocol" for incidents where the CAIRO function
is materially in the investigation chain.

### Notification capability — P (blocker)

*Current state:* Notification matrix is drafted
for the major notifications. *Evidence:*
Recent notifications for the H-12 incident
operated within windows.

*Top gap:* MHRA-specific notification channel
is not yet operational at the Aldwych side —
the matrix names MHRA but the technical
notification pipeline has not been built.

*Recommendation:* Implement MHRA notification
channel; ICO + CQC channels need similar review.
**This is a blocker for operational status.**

### Communication capability — MR

*Current state:* Internal communication
operates well per the H-12 incident.
External-to-customer communication has not been
formally tested.

*Top gap:* Patient-affected notification process
has not been tested under simulated incident
pressure. The H-12 incident's patient
notification operated because the CMO designee
took ownership; this pre-coordination cannot be
assumed.

*Recommendation:* Tabletop the patient-
notification process specifically with the
patient-relations team. **This is a blocker for
operational status.**

### Documentation capability — R

*Current state:* The audit ledger (per mod-108)
captures decisions contemporaneously. The H-12
incident produced a complete evidence trail.
*Evidence:* H-12 audit ledger records.

*Top gap:* None material.

### Post-incident review capability — MR

*Current state:* The PIR template (per Exercise
04) is operational. One PIR completed.
*Evidence:* The H-12 review.

*Top gap:* The review-by-independent-lead pattern
worked for H-12 because Internal Audit was
available. The dependency on Internal Audit's
calendar is a concern.

*Recommendation:* Establish a roster of
qualified review leads spanning Internal Audit,
external advisors, and rotating senior leaders.

---

## 4. Aldwych-specific concerns

**Clinical-authority boundary.** Per mod-101
Ex-03 and mod-103 Ex-05, the CMO has clinical
authority. The H-12 incident handling was clean
because the CMO designee was effective; this is
not a system property, it is a luck-of-the-draw
property. The CAIRO + CMO + CMO-designee
arrangement needs formalisation. **This is a
blocker for operational status.**

**Patient-affected notifications.** Healthcare
notifications have clinical-communication
implications absent in financial-services
contexts. The H-12 incident's patient letters
went through clinical review; this took time. The
process is not yet documented as a standing
capability.

**Regulator landscape.** Four UK + EU regulators
may apply simultaneously (MHRA + CQC + ICO +
EU AI Act NCA). The MHRA-specific channel gap is
the binding constraint; the other three are
identifiable but operational.

---

## 5. Overall readiness verdict

**Mostly Ready with three named blockers.**

Aldwych Health's AI incident response capability
is materially developed but is not yet
operational at the standard the program's
governance work to date deserves. Three specific
blockers must be resolved:

1. **MHRA notification channel** — currently
   named in the matrix but technical pipeline
   not built.
2. **Patient-notification process** — not yet
   tested under simulated incident pressure.
3. **Clinical-authority boundary
   formalisation** — H-12 success was
   personality-dependent; needs structural
   formalisation.

Each blocker has a recommendation and an owner
named above. Target close for all three: 90
days. Upon closure, the program is recommended
for "Ready" classification.

The remaining identified gaps (trend monitoring,
joint-classification, multi-site pause testing,
investigation independence, review-lead roster)
are *operational improvements* that should be
addressed but do not block operational status.

---

## 6. Reasoning notes

- **Why the assessment is "Mostly Ready" and not
  "Ready".** The program is genuinely capable —
  the H-12 incident response demonstrated
  this — but the three blockers are real. A
  fully-positive readiness assessment for a
  newly-implemented program would not be
  credible to the Audit Committee or to a
  regulator subsequently reviewing.
- **Why I named specific blockers rather than a
  diffuse list.** The Audit Committee needs to
  know what to demand before declaring the
  system operational. Vague concerns produce
  vague follow-up; specific blockers produce
  specific accountability.
- **Why I gave Documentation a clean "Ready"
  rating.** The audit ledger from mod-108
  operationalizes documentation as a side
  effect of activity rather than as a separate
  task. The H-12 incident's evidence trail
  was complete because the infrastructure
  produces it; this is a structural strength.
- **Why I included Aldwych-specific concerns
  rather than treating them as dimensions.** The
  three Aldwych-specific concerns cut across
  multiple dimensions and require named
  attention. Folding them into the per-dimension
  ratings would obscure the cross-cutting
  nature.
- **What this assessment deliberately doesn't
  do.** Compare Aldwych to peer institutions.
  External benchmarking would be a separate
  exercise; this assessment is Aldwych vs. the
  Aldwych standard.
- **What I would change in v2.** Include a
  *trend assessment* — how each dimension has
  moved over the past 6 months. Current
  assessment is point-in-time; trend would
  surface whether the program is improving or
  regressing.

---

Maintained by [Girish Nair](https://github.com/garynair)
