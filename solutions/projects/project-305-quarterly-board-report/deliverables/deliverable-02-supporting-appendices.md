# Deliverable 02 — Supporting Appendices — Reference Solution

## 1. Solution overview

Nine appendices supporting the Q2 Board
report. Each is self-contained, skim-
friendly, designed for the technically-
engaged director. The appendices are
template artifacts; future quarterly
reports will use the same structure with
updated data.

---

## 2. The appendices

### Appendix A — AI/ML Model Inventory
Snapshot

**Counts (Q2 close):**

| Business line | Models | Q1 → Q2 change |
|---|---|---|
| Institutional asset management | 28 | +2 |
| Private wealth | 22 | +1 |
| Alternatives | 12 | 0 |
| Shared services | 16 | +1 |
| **Total** | **78** | **+4** |

**Tier distribution:**

| Tier | Q1 | Q2 | Change |
|---|---|---|---|
| Tier 1 | 13 | 14 | +1 |
| Tier 2 | 38 | 41 | +3 |
| Tier 3 | 23 | 23 | 0 |

**Technique distribution:**

- Statistical / classical ML: 30
- Deep learning: 25
- LLM-based (vendor + fine-tuned +
  agents): 15
- Hybrid: 8

**Vendor exposure:**

- Vendor models: 22 (28% of inventory)
- Up from 18 (24%) at Q1 close.
- 12 vendors involved; 3 foundation-
  model providers across the vendor
  stack.

**Validation status:**

| Status | Count |
|---|---|
| Validated within tier cadence | 72 |
| In validation backlog | 6 |
| Not yet validated (recently added) | 0 |

### Appendix B — Top Risks Deep-Dive

**Risk: Vendor AI dependency — Rising.**
- Q2 vendor incident in client-portal
  capability illustrated upstream
  exposure visible only through vendor
  disclosure.
- Mitigation: vendor AI risk register
  updated with explicit upstream-
  dependency tracking; vendor contract
  review prioritizing notification-
  timing language.
- Trend analysis: increasing vendor
  count (22 → from 18 last quarter)
  drives the rising trend.
- Residual position: material.

**Risk: Foundation-model concentration —
Stable.**
- Three foundation-model providers
  across the vendor stack; no single-
  provider exposure exceeds 40% of
  vendor LLM usage.
- Mitigation: vendor diversification
  in critical capabilities.
- Trend: stable but watch.

**Risk: LLM hallucination — Stable.**
- One material event in Q2 (the
  research-support memo citation).
  Control discipline (analyst review)
  caught it.
- Mitigation: citation-tagging on
  agent output; verification at user
  side; audit monitoring.
- Trend: stable; risk inherent to
  the technique; control discipline
  is the durable answer.

**Risk: EU AI Act compliance — Rising.**
- Q2 surfacing of two systems
  plausibly high-risk under the AI
  Act.
- Mitigation: conformity preparation
  begins Q3; outside counsel engaged;
  Notified Body identification
  underway.
- Residual position: open; will
  re-evaluate at Q3 close after
  conformity-assessment scope is
  clearer.

**Risk: Alpha-signal calibration drift
— Stable-falling.**
- Q2 event (the February drift) is
  the last material event. Monitoring
  enhancements deployed.
- Mitigation: calibration metrics
  primary; tightened thresholds.
- Trend: falling.

**Risk: Workflow capture in research
— Stable.**
- Override rates for the LLM agent
  research-support tool indicate
  analysts are using their own
  judgment; no concerning patterns
  detected.
- Mitigation: monitoring; analyst-
  written-content quality review;
  analyst-without-AI spot checks
  planned for Q3-Q4.
- Trend: stable; watch.

**Risk: Privacy / PII exposure in AI
processing — Stable.**
- Acceptable Use Policy adherence at
  96%; no incidents in Q2.
- Mitigation: ongoing; training and
  policy enforcement.
- Trend: stable.

**Risk: Fair-lending exposure in
retail wealth — Slight-rising.**
- CFPB inquiry letter received in
  June. Routine character but the
  CFPB's attention to this space
  has increased.
- Mitigation: response in flight
  under counsel; documentation
  hardening.
- Trend: slight-rising.

### Appendix C — Q2 Incident Detail

**C.1 — LLM agent hallucination
(May 14).**

Timeline:
- May 14, 09:15 — Analyst (Senior
  Associate, US Equities) drafts
  investment-committee memo using
  the research-support LLM agent.
- May 14, 14:30 — Pre-publication
  review by Senior Analyst surfaces
  a citation that the Senior Analyst
  does not recognize.
- May 14, 14:45 — Citation
  investigated; determined
  hallucinated (regulatory filing
  does not exist).
- May 14, 16:00 — Memo revised;
  hallucinated citation removed;
  memo published with corrected
  content.
- May 15-30 — Internal review;
  AI Risk Council meeting May 20;
  controls updated.

Outcome: no client materials
contained hallucinated content; no
investment decision was made on
hallucinated basis.

Lessons:
- The pre-publication-review control
  is the durable defense.
- LLM hallucination prevention at
  the model layer is not currently
  achievable for citation-
  generation tasks.
- Citation-tagging on agent output
  is the additional control.

Controls updated:
- Citation-generation output tagged
  distinctly in the agent UI
  (requires user verification
  before insertion into draft).
- Audit monitoring on agent
  outputs for citation patterns.
- Training updates for analysts
  using the agent.

**C.2 — Alpha-signal calibration
drift (Feb 12 detection, May 18
redeploy).**

Timeline:
- February 12 — Production
  monitoring detects calibration
  drift in one alpha-generation
  signal.
- February 13-15 — Investigation
  by Quantitative team and MRM.
- February 15 — Model paused.
- February 15 - April 30 — Model
  redevelopment; updated training
  data; adjusted features.
- April 30 - May 15 — MRM
  validation.
- May 18 — Redeployed under
  enhanced monitoring.

Outcome: investment outcomes
during the drift window were
modestly affected (estimated
~$120K negative tracking-error
impact across affected strategy
positions); no client harm.

Lessons:
- Monitoring caught the drift
  before significant impact.
- Pre-monitoring discipline was
  the question; the drift was
  gradual over several months
  and warranted earlier
  attention.

Controls updated:
- Calibration metrics now
  primary monitoring signal for
  all alpha-generation models
  (previously secondary).
- Calibration-drift thresholds
  tightened.
- Quarterly calibration review
  added to the alpha-signal
  monitoring cadence.

**C.3 — Vendor LLM upstream
incident (May 20 disclosure).**

Timeline:
- May 20 — Vendor (client-
  portal portfolio-explanation
  capability) discloses security
  incident affecting upstream
  foundation-model dependency.
- May 20-22 — Vendor confirms
  Halverston's specific deployment
  was not in incident scope.
- May 23-30 — Halverston
  internal review; vendor risk
  register update.
- June - ongoing — Enhanced
  monitoring of vendor outputs.

Outcome: no Halverston customer
data confirmed affected.

Lessons:
- Upstream foundation-model
  exposure is real and not
  directly under Halverston's
  control.
- Vendor notification timing
  on upstream events is a
  contract dimension that
  warrants explicit attention.

Controls updated:
- Vendor AI risk register
  with explicit upstream-
  dependency tracking.
- Vendor contract review for
  notification-timing language.
- CISO and CAIRO joint review
  of vendor AI posture
  quarterly.

**C.4 — EU AI Act
classification work.**

The Q2 compliance review
identified two high-risk
candidates:

- Credit decision support
  system (private wealth
  lending): Annex III(5)(b)
  consideration.
- Employee performance
  support model
  (institutional asset
  management): Annex
  III(4)(b) employment.

Q3 work:
- Detailed classification
  analysis per system.
- Conformity assessment
  route determination.
- Notified Body engagement
  initiation.
- Outside counsel
  engagement.

**C.5 — CFPB inquiry letter
(June 8 receipt).**

Letter requests:
- Documentation of AI/ML
  model governance for
  alpha-generation models
  interacting with retail
  wealth clients.
- Fair-lending-adjacent
  analysis where applicable.
- Customer-impact analysis.

Response work:
- General Counsel and
  Compliance leading.
- Documentation hardening
  for the relevant model
  class.
- Submission expected Day
  75 from receipt.

**C.6 — MRM validator hiring
(April 5 and April 19 start
dates).**

Two senior validators
joined. Onboarding included
the Halverston AI/ML
validation methodology;
both up to speed by end-
of-April. Validation
backlog reduced 14 → 6
over Q2.

Forward: steady-state
validation cadence expected
by end of Q3.

### Appendix D — Regulatory
Horizon Detail

**D.1 — EU AI Act**

- Two Halverston high-risk
  systems identified.
- Conformity preparation
  begins Q3.
- Expected Notified Body
  engagement Q4.
- Conformity assessment
  decision Q1-Q2 next
  year.

**D.2 — SEC**

- Annual examination cycle:
  expect AI/ML governance
  scrutiny.
- AI rule: final rulemaking
  not expected in next 12
  months but advancing.
- Watch: marketing-rule
  AI claims guidance.

**D.3 — CFPB**

- Active inquiry under
  response.
- Broader CFPB attention to
  AI in retail wealth and
  consumer-facing financial
  services.
- Expect follow-up
  guidance in 6-12 months.

**D.4 — NYDFS**

- Insurance-side guidance
  evolving; not directly
  applicable to Halverston.
- Banking-side guidance
  affects some financial-
  services counterparts;
  may inform broader
  framework.

**D.5 — State-level**

- California: AB-2013
  algorithmic decision-
  making disclosure; some
  Halverston systems
  potentially in scope.
- Colorado: similar
  framework.
- New York City: hiring-
  AI bias audit
  requirement (Halverston
  NYC office hiring
  affected; HR vendor
  LLM in scope).

**D.6 — UK FCA**

- AI-specific principles
  published; Halverston
  UK entity assessed as
  compliant.
- Active engagement
  ongoing.

**D.7 — Singapore MAS**

- FEAT principles in
  place; Halverston
  Singapore entity
  assessed; compliant.
- Watching upcoming
  AI risk management
  guidance.

**D.8 — International
joint frameworks**

- OECD AI Principles:
  alignment maintained.
- ISO/IEC 42001:
  Halverston in early
  adoption assessment.

### Appendix E — MRM Validation
Pipeline Status

(Visualization in main pack.)

| Tier | Models | Validated within cadence | In backlog |
|---|---|---|---|
| Tier 1 | 14 | 14 | 0 |
| Tier 2 | 41 | 37 | 4 |
| Tier 3 | 23 | 21 | 2 |

Capacity: 6 validators (4
senior + 2 onboarded Q2).
Steady-state capacity matches
forward validation load.

Projection: backlog closes
by end of Q3; steady-state
by Q4.

### Appendix F — Ongoing
Monitoring Scorecard

(Stream-by-stream summary;
detailed dashboard
referenced.)

- Stream 1 (input quality):
  No tier-1 critical breach in
  Q2; 4 tier-A warnings
  resolved.
- Stream 2 (output
  distribution): No critical
  breach; 3 warnings.
- Stream 3 (performance):
  One critical breach (the
  February alpha drift);
  resolved per Event 2.
- Stream 4 (subgroup
  performance): No
  critical breach; ongoing
  attention to two consumer-
  facing models.
- Stream 5 (operational):
  Availability 99.97% for
  Tier-1; meets SLA.
- Stream 6 (material change):
  Detected 18 material
  changes in Q2; all
  reviewed per change-
  management gate.

### Appendix G — AAUP
Adherence

- Training completion: 96%
  enterprise-wide.
- Reported violations Q2:
  4 (all minor; addressed
  through training).
- Policy v3.1 reviewed
  end-of-Q1; v3.2 planned
  for end of Q3.

### Appendix H — Vendor AI
Risk Register

| Vendor | Service | Foundation-model layer | Risk rating |
|---|---|---|---|
| Vendor A | Client-portal explanations | Foundation A | Material (May incident; under monitoring) |
| Vendor B | Research support agent | Foundation B | Moderate (fine-tuned; high adoption) |
| Vendor C | KYC/AML document processing | Foundation B | Moderate |
| Vendor D | HR resume screening | Foundation A | Moderate (NYC bias audit obligations) |
| Vendor E | Marketing analytics | Foundation C | Low |
| ... | (remaining 7) | mix | mix |

Concentration:
- Foundation A: 9 of 22
  vendor systems.
- Foundation B: 8 of 22.
- Foundation C: 3 of 22.
- Other: 2 of 22.

### Appendix I — 24-month
Forward Horizon

**Regulatory:**
- EU AI Act high-risk
  conformity assessments
  complete; ongoing
  obligations operational.
- CFPB AI guidance
  released; Halverston
  response work.
- SEC AI rule potentially
  finalized; adaptation.
- State-level regulation
  expanded; compliance
  capability scaled.

**Product:**
- LLM agent capabilities
  expanded across business
  lines.
- Client-facing AI
  capabilities offered
  selectively under
  transparency principles.
- Predictive analytics
  for private wealth
  client engagement.

**Infrastructure:**
- Foundation-model vendor
  diversification.
- In-house capability for
  specific tasks where
  strategic.
- Customer-facing
  observability of
  AI processing.

**Organisational:**
- CAIRO function steady-
  state at current
  staffing.
- MRM AI/ML capability
  at steady state.
- AI literacy across
  business lines:
  established baseline.
- Continued AI Risk
  Council operation.

---

## 3. Reasoning notes (for the
learner)

- **Why nine appendices rather
  than three.** Modular reading.
  The technically-engaged director
  may read Appendix B only; the
  Risk Committee chair may read
  Appendices A, E, F. Fewer
  appendices conflate concerns and
  produce longer scrolling.
- **Why the model inventory in
  Appendix A is summary-counts
  rather than per-model list.**
  Per-model lists do not serve
  the Board; the operational
  inventory is for MRM
  consumption. The Board wants
  the snapshot.
- **Why Appendix H (vendor risk)
  shows the foundation-model
  concentration explicitly.**
  This concentration is the
  forward-looking concern
  named in Section 7 of the
  main report. The appendix
  provides the data behind
  the concern.
- **Why Appendix I (24-month
  horizon) at the end.** Most
  directors will not read this
  appendix; the directors who
  do want the long-view will
  reach for it. Its placement
  at the end reflects its
  audience.
- **What I would do
  differently.** I might have
  added a "what changed since
  last quarterly report"
  appendix that explicitly
  tracks delta. The trade-off:
  cross-cutting with several
  other appendices. Future
  quarterly reports could
  include this as a separate
  summary appendix.

---

Maintained by [Girish Nair](https://github.com/garynair)
