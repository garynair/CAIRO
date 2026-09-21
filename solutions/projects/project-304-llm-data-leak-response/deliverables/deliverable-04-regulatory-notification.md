# Deliverable 04 — Regulatory Notification — Reference Solution

## 1. Solution overview

Six regulatory regimes mapped. Northrise's
notification posture is **processor-side**:
Northrise's customers are data controllers
and primary obligated parties; Northrise's
direct notification obligation is to its
customers (the controllers). Direct
authority notification by Northrise is
required only for SEC-related materiality
in pre-IPO context. Trigger awareness:
Day 0 declaration. Notification timing
calibrated per regime; specific dates with
defensible justification.

---

## 2. Regulatory regime mapping

### GDPR (Art. 33 and Art. 34)

**Applies to:** EU-resident data subjects'
data exposed via the incident. The
affected customers operate in the EU
and have EU data subjects; Northrise is
their processor.

**Northrise's obligation (Art. 28(3)
processor-to-controller):** Notify
customer (the controller) without undue
delay after becoming aware. Awareness:
Day 0 (some confirmed cohorts identified
Day 4-5).

**Customer's obligation (Art. 33
controller-to-authority):** 72 hours
from controller's awareness.
Northrise's notification timing
triggers the customer's 72-hour clock.

**Customer's obligation (Art. 34
controller-to-data-subject):** When
high risk. Customer-side determination.

**Northrise's direct obligation to
authorities:** None directly under
Art. 33 (Northrise is processor not
controller). However, Northrise's
processor notification quality affects
customer's ability to comply; high
quality is required.

### HIPAA (Business Associate Breach
Notification)

**Applies to:** PHI-affected
healthcare-customer incidents. Two
Cohort-A cases involved PHI fragments.

**Northrise's obligation (45 CFR
164.410, Business Associate to
Covered Entity):** Notify covered
entity without unreasonable delay,
no later than 60 days. Per the
underlying BAAs, notification is
typically required sooner.

**Covered entity's obligation:**
- Notify individuals within 60 days.
- Notify HHS Office for Civil
  Rights.
- If 500+ individuals: notify
  prominent media outlets.

**Northrise's BAA-driven obligation:**
Northrise's BAAs typically require
notification within 5-10 business
days. Northrise must meet the
tightest applicable contract term.

### GLBA / State Breach Notification

**Applies to:** Financial-services-
related customer data exposure. Cohort
A includes financial-services
customers; Cohort B sources include
financial-services customers.

**Northrise's obligation:** Service-
provider notification to financial-
institution customers per contract.

**Customer's obligation:** State-by-
state breach notification (50 different
regimes with different triggers and
timelines). Some require AG
notification; some require state
banking regulator notification; some
require CFPB notification.

### NYDFS Part 500

**Applies to:** New York-licensed
financial institutions in the affected
customer set.

**Northrise's obligation:** Third-
party service provider provisions
(Section 500.11) — notify customer of
incidents affecting the customer's
information systems.

**Customer's obligation:** 72-hour
notification to NYDFS.

### EU AI Act

**Applies to:** GuardianGPT's status
under the EU AI Act.

**Analysis:** GuardianGPT is a general-
purpose AI system (per Art. 3
definitions). The incident is not a
"serious incident" under Art. 73 for
high-risk AI systems, because
GuardianGPT is not a high-risk system.

**Northrise's obligation under
Art. 51-52 (general-purpose AI):**
General-purpose AI providers have
documentation and risk-mitigation
obligations. The incident may be
relevant to those documentation
obligations and to EU AI Office
engagement. Compliance review
ongoing.

**Customers' obligation:** Customer
deployments may use GuardianGPT
within their own high-risk AI
systems (e.g., financial-services
credit-decision adjacent uses). The
incident may trigger their own
Art. 73 obligations.

### SEC and Investor Reporting

**Applies to:** Northrise itself,
pre-IPO.

**Analysis:** Materiality assessment.
Northrise's existing investors include
several institutional VCs and a
strategic corporate investor.

**Northrise's obligations:**
- Investor communication per
  investor agreements (typically
  prompt notification of material
  events).
- S-1 disclosure consideration if
  Northrise is in registration
  preparation.
- For pre-IPO Northrise: not subject
  to public-company periodic
  reporting; but material event
  disclosure to existing investors
  is contractual.

**Materiality assessment:** Northrise's
incident is **material** under
reasonable-investor standards: the
incident affects ~26% of customers
(Cohorts A-D); the high-exposure
cohort includes Fortune 500
customers; the incident affects
Northrise's core product positioning
("tenant isolation"); customer
notifications will result in some
press attention; financial exposure
is not yet quantified but is
material.

## 3. Per-regime frameworks

### GDPR notification

**Trigger:** Northrise awareness Day 0.

**Recipient:** Affected customers
(controllers). Customer then notifies
their own authority(ies).

**Content per Art. 33(3) (as
processor-to-controller notification):**
- Nature of the breach.
- Categories and approximate number
  of data subjects.
- Categories and approximate number
  of data records.
- Likely consequences.
- Measures taken or proposed.

**Timing:** Within 72 hours of
awareness. Northrise notifies all
EU customers in affected cohorts
within 72 hours of cohort
identification. For Cohort A
customers: Day 4. For Cohort C and
later: Day 7-10.

### HIPAA BAA notification

**Trigger:** Day 0 awareness.

**Recipient:** Healthcare-customer
covered entities (Cohort A includes
2 covered entities).

**Content per BAA terms (specific
to each customer's BAA):**
Typically includes nature of
incident; categories of PHI
affected; remediation; covered
entity's actions required.

**Timing:** Within 5 business days
per typical BAA. Cohort A
healthcare customer notification
Day 4.

### State financial-services
notification

**Trigger:** Day 0 awareness.

**Recipient:** Financial-institution
customers (Cohorts A and B
include financial-services
customers).

**Content per service-provider
contracts:** As required by
contract terms.

**Timing:** Within contract terms;
typically 5-10 business days.
Cohort A financial-services
customer notification Day 4.

### NYDFS Part 500 (third-party
service provider notification)

**Trigger:** Day 0 awareness.

**Recipient:** NY-licensed
financial-institution customers
(1 customer in Cohort A; 1 in
Cohort B).

**Content:** Per Section 500.11
requirements and customer
contract.

**Timing:** Day 4 alongside
Cohort A notification.

### EU AI Act

**Documentation obligation:**
Incident documented per Art.
51-52 GP-AI obligations within
the documentation framework
Northrise maintains.

**No direct Art. 73 trigger.**

### SEC / Investor notification

**Trigger:** Day 0 awareness;
material event determined Day 2.

**Recipient:** Existing
investors per investor
agreements. Board notified
Day 3.

**Content:** Material event
summary; affected customer
scope; remediation plan; press-
posture briefing.

**Timing:** Investor
notification Day 5-7 after
internal Day-3 Board approval
of the messaging.

## 4. Coordination across regimes

The notification timing is
coordinated:

- **Day 4:** Cohort A customer
  notification. This triggers
  customer-side GDPR 72-hour
  clocks, BAA notification
  clocks, NYDFS clocks. Customer
  Success and Compliance teams
  positioned to support
  customers' downstream
  obligations.
- **Day 5-7:** Cohort B
  notification. Investor
  notification.
- **Day 7-10:** Cohort C and D
  written notification. Cohort
  E proactive notification
  Day 8-12.
- **Day 15:** First regulatory
  inquiry expected (customer
  notifications produce
  authority engagement);
  Compliance and GC support.

## 5. Investor and SEC framing

### Materiality determination

Material. Documented Day 2 per
material-event determination
process.

### Investor communication
strategy

- Existing investors notified
  through Board chair Day 3-5.
- Written investor update Day 7.
- Investor Q&A call Day 10.

### S-1 implications

If Northrise is in active S-1
preparation:
- Incident must be disclosed in
  the registration statement
  under "Risk Factors" and
  potentially in "Business" if
  remediation work shapes the
  business going forward.
- Underwriter and counsel are
  positioned to advise on
  specific disclosure language
  during the registration
  process.
- Timing implications: a
  registration statement that
  disclosed the incident
  proximately may face longer
  SEC review.

### Investor messaging tone

Direct, accountable, forward-
looking. Same as customer
messaging. Investors will press
on financial exposure and
remediation cost; the right
posture is "we are quantifying;
the controls hardening work is
substantively underway; we
believe the incident is
recoverable" — not premature
specific numbers.

---

## 6. Reasoning notes

- **Why the processor-vs-controller
  framing matters.** Northrise's
  obligations flow primarily
  through its customers, not
  directly to authorities (except
  SEC/investor). Pretending
  Northrise has direct authority
  notification obligations under
  GDPR/HIPAA/state regimes
  misframes the work.
- **Why I named the SEC
  materiality determination
  explicitly.** Pre-IPO companies
  often try to avoid materiality
  designations in incident
  response. The honest answer
  here is material; the
  determination affects investor
  communication, S-1 preparation,
  and Board cadence. Pretending
  otherwise creates worse
  problems later.
- **Why the EU AI Act analysis
  was extensive despite no Art.
  73 trigger.** The EU AI Office
  may engage post-publicity even
  without a formal trigger.
  Documenting the analysis is
  defensive.
- **Why timing is coordinated
  across regimes rather than
  optimized per regime.**
  Sequential notification per
  regime would produce a 2-3
  week notification spread that
  creates inconsistent investor
  /press posture and gives some
  customers time to leak before
  others learn. Coordinated
  timing is harder operationally
  but produces a cleaner
  external posture.
- **What I would do differently.**
  I might have separated the
  state-by-state financial-
  services analysis into a
  state matrix appendix. The
  unified treatment understates
  the operational complexity of
  the 50-state regime. The
  matrix would be valuable but
  was deferred for the 30-day
  arc.

---

Maintained by [Girish Nair](https://github.com/garynair)
