# Deliverable 07 — Article 73 Serious Incident Reporting — Reference Solution

## 1. Solution overview

The Art. 73 incident reporting procedure for
KH-AI-027 operationalizes mod-110's blame-free
investigation discipline plus mod-107 Ex-04's
classification taxonomy adapted to medical-AI.
The 15-day deadline (10 days for life-
threatening cases) drives a fast classification
gate; incident classification distinguishes
Serious Incident (reportable) from operational
quality issue (handled internally) using
explicit criteria. Reporting integrates with
EU MDR vigilance (parallel reporting to the
same competent authority); FDA MDR (Medical
Device Report) covers US parallel path.

---

## 2. The procedure

### Scope and definitions

Per Art. 73(1): a "serious incident" is any
incident or malfunctioning of the AI system
that directly or indirectly leads to (a)
death or serious harm to health; (b) serious
and irreversible disruption of critical
infrastructure; (c) infringement of
fundamental rights protected by Union law;
(d) serious harm to property or environment.

For KH-AI-027, criterion (a) is the operative
category. The procedure focuses there.

### What counts as a serious incident for KH-AI-027

Explicit triggers:

1. **Missed referable case → adverse outcome.**
   AI classified non-referable; clinician
   accepted; case was actually referable; the
   patient subsequently experiences serious
   harm (vision loss, etc.).
2. **Over-referral → adverse downstream
   intervention.** AI classified referable;
   clinician referred; downstream intervention
   caused serious harm. Less likely for
   diabetic retinopathy where referral leads
   primarily to ophthalmologist evaluation,
   but possible (e.g., adverse reactions to
   diagnostic procedures).
3. **Systemic underperformance signal.**
   Subgroup performance degradation detected
   in PMM (Deliverable 06) that, on review,
   reveals the system was operating below
   validated performance for an extended
   period and harm occurred.
4. **Workflow capture incident.** Documented
   instance of automation bias resulting in
   missed referral with subsequent harm.

### Detection sources

- Customer-side reports via the deployer
  incident hotline.
- PMM signal investigation (Deliverable 06
  Tier-1 escalations that uncover patient
  harm).
- Clinical-quality-lead notifications from
  deployer sites.
- Direct patient reports via the customer-
  service channel.

### Classification gate

Within 24 hours of detection, the Algorithm
Quality Office Clinical Validation Lead, the
CMO designee, and a regulatory-affairs
specialist meet to classify:

- **Serious Incident under Art. 73** —
  reportable. Clock starts.
- **Quality issue** — handled internally
  per PMM Tier-1 procedure.
- **Insufficient information to classify** —
  treat as Serious Incident provisionally
  while investigation continues. Down-classify
  only if subsequent information justifies.

The conservative default avoids the failure
mode where ambiguity leads to delayed
reporting.

### Reporting timeline

Per Art. 73(2):

- **15 days from awareness** for standard
  Serious Incidents.
- **10 days** for incidents involving death
  or serious irreversible harm.
- **2 days** for incidents involving
  widespread infringement (not operative for
  KH-AI-027).

### Reporting recipient

Per Art. 73(1): the market surveillance
authority of the Member State where the
incident occurred. For UK-based Kerridge
operating across EU Member States, the
specific recipient depends on incident
location.

EU MDR vigilance reporting goes to the same
authority via the MDR-defined pathway. Where
possible, integrated reporting (single
submission covering both AI Act and MDR
obligations) is used.

### Investigation methodology

Per mod-110 blame-free discipline:

1. **Establish facts.** What happened. When.
   To whom. Patient outcome.
2. **Trace causal chain.** From AI output
   through clinician decision through
   patient outcome. Multiple causes are
   typical.
3. **Identify systemic causes.** Per
   mod-110 §3.4. The question is not "who
   made the error" but "what allowed the
   error to propagate". Workflow design, UI
   design, training, monitoring, residual
   risk acceptance are all candidate
   systemic causes.
4. **Recommend corrective and preventive
   actions.** Per ISO 13485 CAPA discipline.

Investigation outputs feed: (a) the Art. 73
report; (b) the RMS update per Deliverable
02; (c) potential model retraining or
workflow changes; (d) potential operating-
instructions update.

### Integration with other reporting regimes

Three parallel paths:

- **EU AI Act Art. 73** — to relevant Member
  State authority.
- **EU MDR vigilance** — to relevant Member
  State authority (same recipient in most
  cases).
- **FDA MDR (Medical Device Report)** —
  for US-deployed instances of KH-AI-027.
- **Customer notification** — to affected
  deployer hospitals (incident summary,
  recommended actions).

The procedure maintains a single internal
incident record; outputs are formatted
appropriately for each regime.

### Customer communication

For serious incidents:

- Affected customers (the specific deployer
  site involved) notified within 48 hours.
- All KH-AI-027 deployer customers notified
  of significant incidents within 5 business
  days, including any recommended workflow
  changes or operational considerations.
- Public communication coordinated with
  Marketing and Comms per Kerridge's
  established crisis-communications protocol.

### Procedure ownership

- **Detection-to-classification.** Algorithm
  Quality Office Clinical Validation Lead.
- **Classification gate.** AQO + CMO designee
  + Regulatory Affairs.
- **Investigation.** AQO leads; CMO oversight
  for clinical aspects; CAIRO oversight for
  AI-system aspects.
- **Reporting submission.** Regulatory
  Affairs.
- **Customer communication.** Marketing and
  Comms (technical content from AQO).
- **CAPA tracking.** Quality Management
  System.

---

## 3. Reasoning notes

- **Why the conservative default (insufficient
  information → treat as Serious Incident).**
  The failure mode of delayed reporting is
  worse than over-reporting. Down-
  classification on better information is
  always available; missed deadlines aren't
  recoverable.
- **Why I named four specific incident
  categories.** Generic "any harm caused by
  the system" leaves the classification gate
  with too much discretion. Named categories
  with explicit examples discipline the
  gate.
- **Why blame-free investigation rather than
  fault-finding.** mod-110 systemic-cause
  discipline. Fault-finding identifies the
  individual; blame-free finds the
  conditions that allowed the error. Both
  patient safety and AI-system quality
  improve faster with blame-free.
- **Why integrated reporting across AI Act,
  MDR, FDA MDR.** mod-102 §2.6 separable-
  artifact principle. Reduces total reporting
  burden, ensures consistent message across
  authorities, simpler to maintain.
- **What this procedure deliberately under-
  specifies.** Detailed CAPA workflow
  (lives in the QMS); specific reporting-
  form templates (regulatory affairs
  manages); legal-privilege handling for
  investigation outputs (legal counsel
  judgment per case).

---

Maintained by [Girish Nair](https://github.com/garynair)
