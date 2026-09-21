# Deliverable 03 — Customer Notification Strategy — Reference Solution

## 1. Solution overview

Five-cohort notification model aligned to
the scope analysis (Deliverable 02).
Cohorts A (high-exposure), B (source-
exposure), C (triggered-but-not-
meaningful) get distinct treatment;
Cohort D (triggered-no-disclosure) gets
brief notification; Cohort E (not
affected) gets proactive notification
preserving trust. Sequencing: Cohort A
in 48-72 hours of awareness, then B,
then C, D, E rolled together starting
Day 7. Direct CISO-to-CISO conversations
for Cohort A and notable B customers
before written notification. Tone:
direct, accountable, forward-looking.

---

## 2. Strategy memo

### Cohorts and treatment

**Cohort A — High-exposure (7
customers).** Direct CISO-to-CISO call
within 24 hours of cohort
identification (Day 4-6). Same-day
written notification. Executive call
within 72 hours (CEO + CAIRO + Customer
Success exec).

**Cohort B — Source-exposure (8
customers, some overlap with A).**
Direct call to customer security or
privacy lead within 48 hours of cohort
identification (Day 5-7). Written
notification same-day. Executive call
within 5 business days.

**Cohort C — Triggered-but-not-
meaningful (~30 customers).** Written
notification Day 7-10. Direct call
offered (customer may take or decline).
Executive call on request.

**Cohort D — Triggered-no-disclosure
(~10 customers).** Brief written
notification Day 7-10 informing of the
incident and confirming the absence of
disclosure in their tenant.

**Cohort E — Not affected (133
customers).** Proactive notification
Day 8-12. Confirms the incident
existed; confirms their tenant was
analysed and was not affected;
describes the remediation.

### Sequencing rationale

- High-exposure customers first: the
  customer-relationship asset is at
  highest risk and notification timing
  matters most.
- Source-exposure customers second:
  their data was disclosed; they have
  notification obligations downstream
  (their own customers, regulators).
  They need to know to act.
- Lower-exposure cohorts rolled
  together: avoids a tiered "who knew
  what when" pattern that would
  undermine the proactive-notification
  trust argument.

### Press-risk customers

Two customers in Cohort A operate in
the financial-services sector where
mandatory public disclosure rules
apply once they become aware of a
qualifying incident. These customers
will trigger their own disclosure
process at the moment of notification,
which produces a press signal within
days. Sequencing puts them in Day 4
notification window, with Northrise
press posture ready to deploy when
disclosure becomes public.

### Why proactive notification of
non-affected customers

Three reasons:

1. **Trust posture.** Customer trust is
   the asset at risk. Customers not
   affected today need to know their
   provider behaves consistently
   regardless of their exposure.
   Proactive notification differentiates
   Northrise from competitors who
   notify only forced-by-disclosure
   cohorts.
2. **Press anticipation.** Press
   coverage will follow Cohort A
   notifications. Non-affected
   customers who hear about Northrise
   via the press without prior
   notification are negatively
   surprised; with prior notification
   they have a positive
   data-point about Northrise's
   transparency.
3. **Sales-pipeline impact.**
   Prospective customers in pipeline
   will hear about the incident.
   Existing-customer reference calls
   will reflect Northrise's
   communication discipline. Proactive
   notification creates positive
   reference data.

The trade-off: increased customer
support load for the next 2-4 weeks;
brand attention to an incident some
customers might not have noticed
otherwise. Accepted.

## 3. Notification letters

### High-exposure letter (Cohort A)
template

> Dear [CISO / Privacy Lead],
>
> We are writing to inform you of a
> serious security incident affecting
> [Customer Name]'s GuardianGPT
> service.
>
> **What happened.** Between [date]
> and [date], a defect in our
> retrieval middleware permitted
> queries from your tenant, under
> specific query patterns, to receive
> content fragments from other
> customer tenants. The defect was
> contained on [date] within 24
> hours of confirmation.
>
> **What was affected in your
> tenant.** Our forensic analysis
> identified [N] queries from your
> tenant during the affected window
> that surfaced content fragments
> originating from another customer's
> tenant. The disclosed content
> appears to include [data classes].
> A specific log of the queries and
> the content surfaced is enclosed
> under privilege.
>
> **What we are doing.**
> [Containment summary].
> [Investigation summary.]
> [Controls hardening summary per
> Deliverable 05.]
>
> **What you should do.**
> [Suggested customer-side actions:
> review the enclosed log; assess
> whether further internal action is
> warranted; coordinate with your
> compliance team on any reporting
> obligations.]
>
> We deeply regret this incident. We
> are committed to your trust and to
> ensuring this class of failure
> does not recur. We are available
> at any time at [escalation
> details] to discuss specifics, to
> support your internal
> investigations, and to assist with
> any compliance work.
>
> Sincerely,
> [CAIRO] and [CEO]

### Medium-exposure letter (Cohort C)
template

(Less specific; identifies that the
tenant's queries triggered the
defect but surfaced no semantically
meaningful cross-tenant content;
offers detailed inspection on
request.)

### Low-exposure proactive letter
(Cohort E) template

> Dear [Customer Contact],
>
> We are writing to inform you of an
> incident affecting GuardianGPT that
> we determined did NOT affect
> [Customer Name]'s tenant. We are
> writing proactively because we
> believe you should hear about
> incidents affecting our service
> directly from us rather than from
> news coverage.
>
> [Brief incident summary; explicit
> confirmation that the customer's
> tenant was analysed and was not
> affected.]
>
> [Summary of the remediation.]
>
> If you have questions or want to
> discuss the incident in detail, we
> are available at [contact].

## 4. Customer-conversation playbook

### Pre-call preparation

For each customer:
- Customer's current GuardianGPT
  contract terms (notification
  obligations).
- Customer's known regulatory
  context (HIPAA-covered, EU
  presence, financial-services).
- Customer's history with Northrise
  (relationship duration, ARR,
  health score).
- Specific scope facts for the
  customer.

### Talking points

**On what happened:** "A defect in
our retrieval middleware permitted
cross-tenant data surfacing under
specific query patterns. We
contained it within 24 hours of
confirmation. The vulnerability
window was 42 days."

**On what was disclosed:**
- For Cohort A: specific facts per
  the enclosed log.
- For Cohort C: "Our analysis
  identified that queries from your
  tenant triggered the defect but
  did not surface meaningful
  cross-tenant content. We are
  sharing the full forensic basis
  for that determination on
  request."
- For Cohort E: explicit
  confirmation of non-exposure.

**On what we are doing:**
- Defense-in-depth architecture
  (Deliverable 05).
- Tenant-isolation testing as a
  class.
- Detection-side improvements.
- Independent third-party
  assurance.

**On customer obligations:** "We are
making the forensic basis available
to support your assessment. Your
General Counsel and compliance
teams are the right decision-makers
on your downstream obligations; we
are here to support."

### FAQ

**Q: How did this happen?**
A: A refactor of our retrieval
middleware introduced a default-
permissive behavior on tenant-
scoping under a specific code path.
We will share the full technical
root-cause analysis in the
post-mortem.

**Q: Did anyone exploit this?**
A: No evidence of malicious
exploitation as of [date]. Our
investigation continues.

**Q: Will this happen again?**
A: The specific defect is fixed.
The defense-in-depth architecture
work prevents the class of
defect. Independent third-party
assurance verifies our
implementation. We can describe
specifics on request.

**Q: What is Northrise's
financial exposure?**
A: We refer questions of financial
disposition to General Counsel
and CEO conversations
specifically.

**Q: Will you make us whole?**
A: The CEO is the right person
for that conversation; we will
schedule.

### Escalation triggers

- Customer threatens public
  disclosure or media engagement →
  CAIRO + VP Comms within 2 hours.
- Customer threatens contract
  termination → CEO + CAIRO + GC
  within 4 hours.
- Customer raises regulatory
  notification questions → CAIRO +
  GC + Compliance within 4 hours.
- Customer requests deep technical
  briefing → schedule CTO/CISO
  briefing within 5 business days.

### Documentation

Every customer conversation
logged with: date, time,
participants, key points
discussed, follow-up actions, any
commitments made by Northrise.
Documentation reviewed weekly by
CAIRO.

---

## 5. Reasoning notes

- **Why the proactive Cohort-E
  notification despite the legal
  exposure increase.** Trust
  posture argument. The customers
  who hear about an incident from
  their provider rather than from
  the press become advocates for
  the provider. Customers who hear
  from the press first become
  skeptics. The legal exposure
  increase (more disclosed
  surface) is real but smaller
  than the trust win.
- **Why the high-exposure letter
  is co-signed by CAIRO and CEO.**
  Co-signature signals
  organisational accountability.
  CAIRO-alone reads as a CAIRO problem;
  CEO-alone is unusual for an
  incident-response letter; both
  signals the appropriate level.
- **Why the conversation
  playbook includes "we refer
  financial disposition to CEO
  conversation."** Premature
  financial commitment by CS in
  early conversations would
  produce uncoordinated and
  inconsistent positions across
  customers. The CEO-led posture
  ensures consistency.
- **Why I emphasized written +
  verbal for Cohorts A and B.**
  Written notification meets
  contractual and regulatory
  requirements; verbal
  conversation preserves the
  relationship. Either alone is
  insufficient.
- **What I would do differently.**
  I might have separated the
  Cohort-A notification by data
  class — the HIPAA-covered
  customers may benefit from a
  PHI-specific template, the
  financial-services customers
  from a different one. The
  unified template is simpler
  but loses some specificity. The
  trade-off was made for speed;
  could go the other way.

---

Maintained by [Girish Nair](https://github.com/garynair)
