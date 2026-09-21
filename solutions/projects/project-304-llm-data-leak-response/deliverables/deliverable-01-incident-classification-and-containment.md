# Deliverable 01 — Incident Classification and Containment — Reference Solution

## 1. Solution overview

Tier-1 incident declared at Day 0 07:30.
Incident commander: CAIRO. Initial scope:
cross-tenant disclosure via retrieval-layer
bug; ≤180 customers potentially affected;
6-week vulnerability window. Immediate
containment: feature flag disables the
suspect retrieval code path globally; falls
back to a strict tenant-scoped retrieval
path with reduced functionality. The CAIRO ×
CISO boundary follows mod-107: CISO leads
the security investigation, CAIRO leads the
incident response and external posture,
joint authority for containment decisions.

---

## 2. The declaration

> **NORTHRISE AI — INCIDENT DECLARATION
> NR-2026-013**
> *Declared Day 0 07:30 UTC by CAIRO under
> the Incident Response Policy.*

### Tier

**Tier 1 — Severe.** Per the IR policy:
"Confirmed or suspected unauthorized
disclosure of customer data, including
inadvertent cross-tenant exposure, in a
production system."

### Reasoning

- Pattern is confirmed (Sentinel red team
  surfaced specific cross-tenant
  fragments).
- Three additional customers raised
  related concerns previously triaged as
  hallucination — re-triage suggests
  these may be related instances.
- Vulnerability window: code change
  deployed Day -42 (6 weeks ago); current
  best estimate of vulnerability duration
  is the full 6 weeks pending log
  analysis.
- Affected customer set: pending scope
  analysis; upper bound = all 180
  customers; expected substantially less
  based on query-pattern dependence of
  the bug.

### Why not Tier 2

Tier-2 ("limited scope or unconfirmed
disclosure") was considered. Rejected
because: (a) disclosure is confirmed in
at least one case; (b) potential scope
extends across the customer base; (c)
HIPAA-covered and PCI-relevant customer
data classes are within the potential
exposure.

### Why not Tier 0 ("crisis")

Tier-0 reserved for incidents with
existential implications (significant
customer loss confirmed; press at scale;
regulatory action active). None present
yet. Re-evaluate Day 3.

### Incident commander

**CAIRO** — under the IR policy, CAIRO leads
Tier-1 incidents involving AI-product
behavior. This incident's character is
AI-product-behavior under adversarial
prompting; the CAIRO is the right commander.

### Teams and ownership

- **Technical investigation** — CTO leads;
  CISO partners on security-side analysis.
  Per mod-107 boundary, CISO leads
  vulnerability analysis and threat
  modeling; CTO leads code-side
  investigation and remediation.
- **Customer communication** — Customer
  Success leads operationally; CAIRO
  approves messaging; GC reviews; CEO
  approves high-exposure customer
  conversations.
- **Regulatory notification** — Compliance
  leads operationally; GC reviews; CAIRO
  approves strategy.
- **External communication** — VP Comms
  leads; CAIRO approves; CEO approves
  press posture if/when needed.
- **Investigation documentation** — CAIRO
  office maintains the master incident
  log; CTO/CISO write technical
  appendices.

## 3. Initial scope statement

### What is known

- A retrieval-middleware code change
  deployed Day -42 introduced a
  tenant-scoping defect.
- Under specific query patterns
  (currently being characterised), the
  retrieval layer returns documents from
  index segments outside the requesting
  tenant.
- Sentinel red team surfaced one
  confirmed case Day -3.
- Three previous customer tickets in
  the past 14 days may be related; under
  re-triage.

### What is not yet known

- Exact characterisation of the
  triggering query patterns.
- Number of cases in production traffic
  during the vulnerability window where
  the bug actually surfaced cross-tenant
  data (vs. cases where the bug was
  triggered but did not surface
  meaningful data).
- Whether the disclosed data classes
  include PHI, financial PII, or
  privileged legal documents (likely;
  pending confirmation per cohort).
- The full affected-customer set.

### What investigation is in flight

- Forensic log analysis on the retrieval
  middleware (Days 0-7).
- Query-pattern reconstruction for the
  vulnerability window (Days 0-10).
- Re-triage of all customer tickets in
  the past 6 weeks (Days 0-3).

## 4. Containment

Containment is in two stages.

### Stage 1 — Immediate (Day 0, 08:00 UTC)

**Feature flag disables the suspect
retrieval code path globally.** Falls back
to the prior tenant-scoped retrieval
implementation. Verified by engineering
that:

- The fallback path is the known-good
  pre-Day-42 implementation.
- The fallback functions for ~95% of
  query patterns; ~5% of advanced
  features are temporarily unavailable
  (customers receive an informational
  message).
- Tenant-scoping invariants are enforced
  in the fallback at the index layer.

Verification: red-team test (Northrise
internal team) against a staging mirror
of the fallback configuration confirms
no cross-tenant surfacing on the
previously-triggering prompts.

**Status: Confirmed contained at this
level.**

### Stage 2 — Reinforced (Days 1-3)

Within 72 hours:

- A second-layer scope check at the
  synthesis step (defense-in-depth)
  rejects any retrieved chunk whose
  tenant-ID metadata does not match
  the query tenant. Engineering already
  in-flight.
- Real-time tenant-scoping monitoring
  alerts on any synthesis-layer rejection.

### What containment does NOT yet address

- Historical disclosure has occurred and
  cannot be retracted. Scope-analysis and
  customer notification address this.
- Customer trust impact. Communication
  strategy addresses this.

## 5. Initial timeline (Days 0-7)

| Day | Activity |
|---|---|
| 0 | Declaration. Containment Stage 1. Internal comms cascade. Executive briefing 14:00. |
| 1 | Scope analysis methodology defined. Affected-customer cohorting begins. Sentinel CISO call. CTO/CISO investigation kickoff. |
| 2 | Tickets re-triage complete. First scope estimate. Stage-2 containment design. Board notification Day-3 prep. |
| 3 | Board notification. Initial customer notification to confirmed high-exposure cohort. Regulatory analysis (Deliverable 04) begins. Containment Stage 2 deployed. |
| 4-5 | Customer notification rolling per cohort. Forensic analysis continues. GC privilege workstream established. |
| 6-7 | First-week situational report to CEO and Board. Updated scope. Customer-conversation tracking. |

## 6. Internal communications

**Day 0 cascade:**

- 07:00 — CAIRO, CTO, CISO, CEO meeting.
- 07:30 — Incident declaration.
- 08:00 — Containment Stage 1 deployed.
- 09:00 — Executive team meeting (CAIRO,
  CTO, CISO, GC, Head of CS, VP Comms,
  Head of Compliance, CFO).
- 10:00 — Customer Success team
  briefing.
- 11:00 — Engineering org briefing.
- 14:00 — Full-company briefing
  (high-level: "we are responding to a
  serious incident; CTO/CISO/CAIRO are
  leading; do not discuss externally;
  refer all inquiries to Comms").
- 17:00 — Board chair informal
  notification.

**Day 1-3 cadence:**

- Daily 07:30 executive incident
  stand-up.
- Daily 17:00 status note to CEO.
- Day 3 formal Board update.

**Day 4-30 cadence:**

- Daily executive stand-up through Day 10.
- Twice-weekly through Day 20.
- Weekly through Day 30.

## 7. What we will NOT do yet

- **No press communication.** VP Comms is
  preparing standby statement; deploy
  only if/when press picks up the
  story. Pre-emptive press disclosure
  is not the chosen posture at this
  stage.
- **No customer notification beyond
  Sentinel (Day 0).** Notification
  strategy (Deliverable 03) defines
  cohorts and timing.
- **No regulatory notification today.**
  Notification regimes have specific
  timing requirements; premature
  notification can be counterproductive.
  Deliverable 04 defines.
- **No public-facing post-mortem.**
  Deliverable 06 produces the public-
  facing abstracted version on a defined
  timeline.
- **No engineering organizational
  changes.** mod-110 systemic-cause
  discipline: investigate before
  restructuring. Post-mortem will
  inform.

---

## 8. Reasoning notes

- **Why Tier-1 not Tier-0.** Tier-0 is
  reserved for active business-threatening
  crises. We are not there yet. Tier-1
  is the right tier for confirmed
  multi-customer disclosure under
  investigation; the difference is the
  CEO/Board cadence and resource
  authorization.
- **Why CAIRO is incident commander rather
  than CISO.** This is an AI-product-
  behavior incident in characterisation;
  it is also a security incident. The
  product-behavior frame is the larger
  picture. The CAIRO × CISO boundary from
  mod-107 supports this division.
- **Why containment Stage-1 is a feature
  flag rather than a code rollback.**
  Feature flag is reversible and
  verifiable in minutes; rollback is
  a code-deployment operation with its
  own risk. Stage-1 is about speed.
- **Why "what we will NOT do yet" is
  in the deliverable.** Pre-empts
  premature action. Incident-response
  teams under pressure tend to act
  prematurely on customer
  notification, press posture, or
  organisational changes. Naming the
  deferrals is part of incident
  command discipline.
- **What would change the
  classification.** If forensic log
  analysis reveals significantly higher
  blast radius than current estimate
  (e.g., evidence of malicious
  exploitation, not just bug-triggered
  surfacing); or if press picks up
  the story before customer
  notification is complete — escalate
  to Tier-0.

---

Maintained by [Girish Nair](https://github.com/garynair)
