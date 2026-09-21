# Deliverable 01 — Q2 Quarterly Board AI Risk Report — Reference Solution

## 1. Solution overview

The Q2 report. ~12 pages. Executive summary
leads. Quarter events honestly framed. Top
risks register named. Regulatory horizon
specific to Halverston. Forward-looking
section explicit about three concerns the
CAIRO is most attentive to. Customer-product
framing addresses lead independent's ask.
Q3 priorities with specific Board ask.
Template choices documented at end for
future quarterly reports.

---

## 2. The Report

> **HALVERSTON CAPITAL — Q2 AI RISK
> REPORT TO THE BOARD**
> *For the quarter ended June 30.
> Author: Chief AI Risk Officer.*

### Section 1 — Executive summary

The AI risk picture at Halverston in Q2
is **stable with three forward-looking
attention points.**

**Stable means:** The model inventory
grew modestly (74 → 78); MRM validator
hiring is complete with the backlog
falling 14 → 6 models; the Q2 incidents
(noted below) were each contained and
produced learning; regulatory engagement
is on plan.

**Three forward-looking attention
points:**

1. **EU AI Act high-risk classification
   work surfaced two Halverston systems
   in scope.** Conformity preparation
   begins in Q3; substantive resource
   commitment over the next 12 months.
2. **Vendor LLM dependency.** The May
   vendor-side incident illustrates
   Halverston's exposure to upstream
   foundation-model providers; vendor
   AI risk warrants continued
   prominent treatment.
3. **The LLM agent for research
   support — high adoption, one
   meaningful hallucination event.**
   Acceptable position today; durable
   discipline requires watching this
   carefully over Q3-Q4.

Q2 had no losses, no customer harm
incidents, no regulatory action against
Halverston. Q3 priorities focus on the
three attention points above and
continued buildout of monitoring and
validation depth.

### Section 2 — State of AI at Halverston

- **78 AI/ML models** in scope (up
  from 74 at Q1 end).
- **Distribution:** ~28 in
  institutional asset management;
  ~22 in private wealth; ~12 in
  alternatives; ~16 in shared
  services.
- **Tier distribution:** 14 Tier-1;
  41 Tier-2; 23 Tier-3.
- **MRM validation status:** 72 of
  78 validated (within tier cadence);
  6 in backlog (down from 14 at
  Q1 end).
- **Technique distribution:** ~30
  statistical / classical ML;
  ~25 deep learning; ~15 LLM-based
  (vendor + fine-tuned + agents);
  ~8 hybrid.
- **Vendor models:** 22 of 78
  (28%). Up from 18 at Q1.

(Detailed quantitative view in
Appendix A.)

### Section 3 — Quarter events of note

Six events warrant Board awareness.

**Event 1 — LLM agent for research
support: launch and hallucination.**

The research-support LLM agent
launched in early April for the
institutional asset management
team. Adoption is strong (~80% of
analysts use weekly; ~40% use
daily).

One material incident in May: the
agent hallucinated a citation in a
draft investment-committee memo.
The hallucinated citation referenced
a regulatory filing that did not
exist. The senior analyst preparing
the memo caught the hallucination
during pre-publication review.

**What it tells us.** The control
that worked was the analyst's
review discipline — the AI Risk
Council's design choice to require
senior-analyst review for any
LLM-augmented memo before
distribution. The control that
did not work was any prevention of
the hallucination at the AI layer
itself; LLM hallucination is
intrinsic to the technology and
requires downstream control.

**What changed.** L1 controls
remain unchanged. L2 controls
updated: the LLM agent's
citation-generation output is
now tagged distinctly and triggers
mandatory verification at the
user-side. L3 monitoring added:
audit of agent outputs for
citation-pattern consistency.

**Event 2 — Alpha-generation signal
pause and redeploy.**

In February, production monitoring
detected calibration drift in one
of Halverston's alpha signals (an
ML model used to score
opportunities for one of our
quantitative strategies). The
model was paused; rebuilt with
updated training data and adjusted
features; revalidated by MRM;
redeployed in May with enhanced
ongoing monitoring.

**What it tells us.** The
monitoring discipline worked —
the drift was detected before
client outcomes were materially
affected. The pre-monitoring
discipline was the question; the
drift had been gradual over
several months and warranted
earlier attention. We've
strengthened the calibration-
specific monitoring across all
alpha-signal models in response.

**What changed.** Calibration
metrics added as primary
monitoring signal for all alpha-
generation models (previously
secondary). Calibration-drift
thresholds tightened.

**Event 3 — Vendor LLM upstream
incident.**

The vendor providing our client-
portal portfolio-explanation
capability disclosed a security
incident affecting an upstream
foundation-model dependency in
May. No Halverston customer data
was confirmed affected; the
vendor confirmed our specific
deployment pattern was not in
the incident's scope.

**What it tells us.** Halverston's
upstream exposure through vendor
LLMs is real and not fully
under our control. The vendor's
disclosure was prompt and
substantive (good), but the
underlying foundation-model
incident took weeks to surface to
us through the vendor chain (less
good).

**What changed.** Vendor AI risk
register updated with explicit
upstream-dependency tracking.
Vendor contract review prioritized
notification-timing language for
upstream incidents. CISO and CAIRO
joint review of vendor AI
posture quarterly going forward.

**Event 4 — EU AI Act
high-risk classification
surfacing.**

The Q2 EU AI Act compliance work
identified two Halverston systems
that are plausibly high-risk
under the AI Act:

- A credit-related decision
  support system used in the
  private wealth lending
  workflow (Annex III financial).
- An employee performance
  support model used in the
  institutional asset management
  team (Annex III employment).

Classification determinations
are pending detailed analysis;
conformity preparation begins
Q3. We expect both to be
confirmed high-risk; Annex VII
third-party conformity
assessment is the likely route.

**What it tells us.** Halverston's
EU AI Act exposure was
understated in our prior
quarterly reports. The systems
have operated for some time;
the classification determination
under the EU AI Act adds a
substantive new compliance
workstream.

**What changed.** Q3 priorities
include the conformity
preparation work; resourcing
implications flagged for the
CFO; outside counsel engaged.

**Event 5 — CFPB inquiry letter.**

In June, Halverston received a
CFPB inquiry letter regarding
the interaction of our alpha-
generation models with retail
wealth clients. The inquiry is
routine in character (the
CFPB is exploring AI use in
retail wealth-management
broadly) and asks for
documentation of model
governance, fair-lending-
adjacent analysis, and customer-
impact analysis.

**What it tells us.** Halverston's
AI governance documentation is
substantial; the response is in
hand and on schedule. The
broader signal: CFPB is actively
exploring this space; future
inquiries are likely; engagement
posture matters.

**What changed.** Response in
flight under counsel; expected
submission Day 75 (within the
inquiry-response window).
Documentation hardening for
the relevant model class
prioritized.

**Event 6 — MRM validator
hiring.**

Two senior AI/ML-capable
validators joined the MRM team
in April. The validation backlog
fell from 14 models to 6 over
Q2. Validation cadence is on
plan; we expect to reach steady-
state validation tempo by end
of Q3.

**What it tells us.** Capacity
investment in MRM is paying
back. The previous report's
flagged risk (validation backlog
becoming a regulatory
vulnerability) has been
addressed.

### Section 4 — AI risk register
update

The current top 8 risks at
Halverston:

| Risk | Q1 Trend | Q2 Trend | Notes |
|---|---|---|---|
| Vendor AI dependency | Rising | Rising | Vendor incident in May; risk register update |
| Foundation-model upstream concentration | Rising | Stable | Three foundation-model providers across vendor stack; no single point of failure now |
| LLM hallucination in client-facing materials | Stable | Stable | Controls operating per design; one event confirmed control discipline |
| EU AI Act compliance | Stable | Rising | Q2 surfacing of two high-risk systems |
| Calibration drift in alpha-signal models | Stable | Stable-falling | Monitoring discipline strengthened post-Event 2 |
| Workflow capture (analysts deferring to AI) | Stable | Stable | Override rates monitored; no concerning patterns |
| Privacy / PII exposure in AI processing | Stable | Stable | Acceptable Use Policy adherence at 96% |
| Fair-lending exposure in retail wealth | Stable | Slight-rising | CFPB inquiry adds attention without changing fundamental position |

### Section 5 — Regulatory horizon

The next 6-12 months in regulatory
context:

**Tier 1 — Definite, near-term.**

- *EU AI Act:* conformity preparation
  for the two Halverston high-risk
  systems; conformity assessment with
  Notified Body in Q4 or Q1.
- *CFPB inquiry response:* on-track
  for Day-75 submission; potential
  follow-up.
- *SEC AI rule:* watching; final
  rulemaking not yet expected in
  this window.

**Tier 2 — Likely, mid-term.**

- *SEC examination cycle:*
  Halverston's annual examination
  may include AI/ML governance
  scrutiny for the first time.
- *NYDFS guidance:* New York-based
  insurance and financial services
  regulators are signaling AI-
  specific guidance.
- *State-level legislation:*
  California, Colorado, and others
  advancing AI-specific
  legislation; Halverston's
  exposure varies by client base.

**Tier 3 — Possible, longer-term.**

- *Federal financial regulator
  joint AI guidance:* OCC, FRB,
  FDIC have signaled coordinated
  guidance; timing uncertain.
- *International regimes:* MAS, FCA
  are evolving their AI
  positions; impacts Halverston's
  Singapore and London entities.

(Detailed view in Appendix D.)

### Section 6 — Customer and product
implications

(Per lead independent director's
request.)

**LLM agent for research support.**
Adoption is strong and analyst
satisfaction is high. The
hallucination event reinforces
the design discipline — AI as
augmentation, not replacement,
for the analyst. The product
implication: Halverston's
research output should be
better supported, not visibly
LLM-generated. Client-facing
materials should not advertise
LLM authorship.

**Vendor LLM client-portal
capability.** The May vendor
incident did not affect
Halverston clients but
illustrated upstream exposure
visible only through vendor
disclosure. Considering: a
periodic client communication
on how Halverston's AI use
is governed (proactive, not
incident-driven).

**EU AI Act exposure.** The two
high-risk systems support
institutional and private
wealth lines. Conformity
preparation may produce
temporary capability
constraints during the
preparation window. Customer
communication on this point
needed.

**Customer trust as durable
asset.** Across the AI
landscape, Halverston's
customer position is "trusted
sophisticated manager that
uses AI thoughtfully." Each
quarterly event either
reinforces or weakens this
position. The Q2 events
reinforced (hallucination
caught at the right control;
vendor incident handled
transparently; CFPB engagement
substantive).

### Section 7 — What we are
worrying about going forward

(Per independent chair's
request.) Three specific
concerns the CAIRO is most
attentive to.

**Concern 1 — Vendor AI
concentration risk in client-
facing capabilities.** Halverston
relies on multiple vendor LLMs
in client-facing capabilities;
each vendor relies on a
foundation-model provider. The
May vendor incident reminds us
of the chain. We have no
single-vendor concentration
risk today; we do have
foundation-model concentration
risk (most vendors use one of
2-3 major foundation models).
Defense: vendor diversification
in critical capabilities;
in-house capability development
where strategic. Q3-Q4 work
on a defense-in-depth strategy
for foundation-model dependency.

**Concern 2 — Workflow capture
in research and analytics.**
The LLM agent for research is
high-adoption (~80% of
analysts). High adoption is
the right outcome; the
concern is the long-tail
risk of subtle analyst
capability erosion — analysts
becoming proficient at
prompting but less proficient
at the underlying analytical
work. Watching for this over
Q3-Q4 through specific metrics
(analyst-written-content quality
review; analyst-without-AI
spot-checks).

**Concern 3 — Regulatory
fragmentation creating governance
strain.** Halverston operates
across US, UK, EU, Singapore.
AI regulation is fragmenting.
Maintaining a unified governance
posture across jurisdictions
becomes more expensive over
time. Concerning trajectory;
mitigation through investment
in regulatory tracking and
through unified internal
posture even when external
requirements diverge.

### Section 8 — Q3 priorities and
Board asks

Q3 priorities:

- EU AI Act conformity preparation
  for the two high-risk systems
  (substantive resource
  commitment).
- CFPB inquiry response submission
  and follow-up.
- Vendor AI concentration analysis
  and mitigation planning.
- Continued model validation per
  cadence (steady-state by end of
  Q3).
- Q3 monitoring scorecard updates
  including calibration-
  monitoring enhancements.

**Board asks:**

1. *Endorsement of EU AI Act
   conformity work as Q3-Q1
   investment priority.* Resource
   commitment ~$1.2M-1.8M direct
   over 9 months; CFO has
   modeled.
2. *Acknowledgment of the
   forward-looking concerns
   (Section 7).* No specific
   Board action required today;
   noting for tracking.
3. *Endorsement of the standing
   quarterly review pattern
   (this report defines).* Future
   quarterly Board reviews will
   follow this template; light
   adjustments expected.

### Section 9 — Appendices index

- A — Model inventory snapshot.
- B — Top risks deep-dive.
- C — Q2 incident detail.
- D — Regulatory horizon detail.
- E — MRM validation pipeline.
- F — Monitoring scorecard.
- G — AAUP adherence.
- H — Vendor AI risk register.
- I — 24-month forward horizon.

---

## 3. Reasoning notes (for the
learner)

- **Why I led with "stable with
  three attention points."** The
  executive-summary opening shapes
  the entire reading experience.
  "Everything is fine" reads
  evasive; "we are facing crisis"
  is wrong. "Stable plus
  attention points" is honest and
  serves the directors' actual
  decision-relevant attention.
- **Why I gave each Q2 event a
  what-it-tells-us framing.**
  Boards under-engage with bare
  incident summaries. The
  what-it-tells-us framing
  provides the synthesis the
  Board would otherwise have
  to produce themselves.
- **Why I named three forward-
  looking concerns specifically.**
  The independent chair's ask is
  for the CAIRO's judgment. Three
  is the right number — fewer
  reads as evasive; more reads
  as scattered.
- **Why I named the LLM hallucination
  event prominently rather than
  burying it.** Hallucination is
  the AI risk Board members
  most ask about. Naming it
  honestly, framing the control
  that worked, and naming what
  changed is the right discipline.
- **Why I named "workflow capture"
  as a concern.** The 80% adoption
  is being celebrated by the
  business line; it is also a
  concern. The CAIRO is the right
  person to surface this nuance
  to the Board; the business
  line would not.
- **Why the Q2 events include the
  MRM hiring success.** Reporting
  only problems reads as
  performative. Reporting wins
  alongside concerns is honest
  and durable.
- **Why I named "no losses, no
  customer harm, no regulatory
  action" in the executive
  summary.** The Risk Committee
  chair specifically asks
  "what bad things happened?";
  the answer for Q2 is "the
  bad-but-not-catastrophic things
  named here, and importantly,
  no losses or customer harm."
  Naming the latter is the
  honest disposition.
- **What I would do differently.**
  I might have included a
  one-page front-of-document
  scorecard with the key
  numbers — model count, tier
  distribution, validation
  status, top-3 risks, Q3
  priorities — to support
  even-faster Board scanning.
  The trade-off: scorecard
  reading short-circuits the
  substantive read. The
  current design prioritises
  substantive reading.

---

Maintained by [Girish Nair](https://github.com/garynair)
