# Exercise 04 — AI Incident Classification Taxonomy — Reference Solution

## 1. Solution overview

A 3-top-level taxonomy with 4 sub-categories each for
**Northfield Mutual**. Routing rules name specific
Northfield roles. External notification obligations
cite EU AI Act Art. 73, NYDFS Part 500 §500.17, and
GDPR Art. 33 where applicable. The bias incident
(claims-triage) starts as AI-program and escalates
to joint at hour 24 when investigation finds an
external data-source manipulation.

---

## 2. Artifact 1 — The taxonomy

> **Northfield Mutual — AI Incident Classification
> Taxonomy v1.0**
> *Owned by Chief AI Risk Officer with CISO concurrence.
> Reviewed annually + after each incident.*

### Category 1 — Security Incident

**Definition.** An incident where an AI system was
compromised in a classical security sense:
unauthorised access to the system or its data,
malicious code execution, infrastructure compromise,
or compromise of a credential or key affecting an
AI system.

**Northfield-specific examples:**

- The agent's orchestrator container is found to
  be running a known-CVE'd library version.
- An attacker gains access to the JWKS signing key
  used by the trust architecture (mod-106 Ex-03).
- An LLM vendor API key is exposed via a
  configuration error.

**Sub-categories:**

| Sub | Description |
|---|---|
| 1.a Infrastructure compromise | Container, network, or platform compromise |
| 1.b Credential / key compromise | Stolen / leaked credentials affecting AI |
| 1.c Supply-chain compromise | Compromised model artifact, container image, vendor API |
| 1.d Insider abuse | Internal user abusing legitimate AI access |

**Default lead:** CISO IR.
**Default escalation:** Sentinel's existing IR
playbook; CAIRO informed within 1 hour; AI Risk
Council briefed at next regular cadence (or
immediately for material).

### Category 2 — AI-Program Incident

**Definition.** An incident where the AI system
behaved in a way the program's controls were
intended to prevent: bias materialization,
transparency failure, capability scope violation,
behaviour change from a model update, or other
deviation from program-policy-defined acceptable
behaviour.

**Northfield-specific examples:**

- Demographic bias monitoring detects new disparate
  impact in claims-triage outputs.
- Customer-service agent produces a response that
  fails the program's transparency standard.
- Vendor LLM provider silently swaps the foundation
  model without notice.

**Sub-categories:**

| Sub | Description |
|---|---|
| 2.a Bias / fairness incident | Disparate impact materializes |
| 2.b Transparency / explainability failure | Required explanation cannot be produced |
| 2.c Capability scope violation | Agent acts outside its signed capability scope |
| 2.d Model behaviour change | Model version or behaviour changes outside expected envelope |

**Default lead:** CAIRO function (AI Risk Lead in the
specific case).
**Default escalation:** AI Review Board; AI Risk
Council if material; Board Quality Committee /
Board Risk Committee for systemic.

### Category 3 — Joint Incident

**Definition.** An incident with both security and
AI-program dimensions. The most common category for
non-trivial incidents.

**Northfield-specific examples:**

- Prompt injection causes the agent to disclose
  another customer's account information (security:
  unauthorised disclosure; AI-program: agent
  capability violation).
- Customer-service agent's responses contain text
  from another customer's session (cross-session
  leakage).
- Fraud-detection model trained partly on a
  corrupted dataset has been producing
  inappropriate false-positive patterns.

**Sub-categories:**

| Sub | Description |
|---|---|
| 3.a Adversarial exploitation of agent | Prompt injection, tool abuse, output exfiltration |
| 3.b Cross-context / cross-session leak | Information flow across boundaries |
| 3.c Training-data integrity event | Poisoning, corruption, or improper inclusion |
| 3.d Identity / capability spoofing | Trust architecture bypass or spoofing |

**Default lead:** Determined by initial-impact
framing — security-dominant initial impact → CISO
leads with CAIRO content; AI-program-dominant initial
impact → CAIRO leads with CISO content. **Single
named lead always.** AI Risk Council assigns if
unclear.
**Default escalation:** Both AI Risk Council and
Sentinel's security executive forum.

---

## 3. Artifact 2 — Routing rules

### Detection sources and initial classification

| Detection source | Initial classification by | Notification within |
|---|---|---|
| Security monitoring / SOC alert | SOC analyst → CISO on-call | 15 min — CAIRO function (AI Risk Lead) |
| AI program monitoring | AI Risk Lead | 15 min — CISO on-call |
| Customer complaint flagged as AI-related | Customer Experience → AI Risk Lead | 1 hour — CISO if security dimension |
| Vendor notification | Vendor Risk → CAIRO function | 1 hour — CISO |
| Internal whistleblower / staff report | Human Resources → CAIRO function (initial routing) | Per incident |
| Regulator inquiry | GC → CAIRO function + CISO | Immediate |

### Classification can be revised

Initial classification is *provisional* and
revisited at the 24-hour mark and as new facts
emerge. Material reclassification (e.g.,
single-category → joint) requires sign-off from
both the CAIRO function and the CISO; the AI Risk
Council can require reclassification.

### Specific named Northfield roles

- **CISO on-call.** Always reachable; first
  responder for Category 1 and Category 3-security.
- **AI Risk Lead.** Always reachable; first
  responder for Category 2 and Category 3-program.
- **Chief AI Risk Officer.** Reachable within 30
  minutes for Tier 1-system incidents and
  high-severity Category 2 / 3 incidents.
- **Chief Information Security Officer.**
  Reachable within 30 minutes for Tier 1-system
  incidents and high-severity Category 1 / 3
  incidents.
- **AI Risk Council Chair (CRO).** Convene within
  4 hours for material Category 3 incidents or
  Council-required reclassification.
- **Board Risk Committee Chair.** Notify within 24
  hours for material incidents; Board meeting
  brief at next scheduled meeting.

### AI Risk Council auto-escalation thresholds

The AI Risk Council is automatically convened (not
just informed) when:

- Any incident involves a Tier 1 system AND
  produces customer impact.
- Any incident triggers EU AI Act Art. 73
  notification.
- Any incident triggers NYDFS Part 500 §500.17
  notification.
- Two or more incidents in the trailing 90 days
  involve the same system.
- Reclassification from a non-joint to a joint
  category occurs.

### External notification obligations checklist

For each incident at classification time:

| Trigger | Notification | Timeline | Lead |
|---|---|---|---|
| Personal data breach affecting EU residents | GDPR Art. 33 DPA notice | 72 hours | CISO + Privacy + CAIRO |
| Personal data breach with high risk to individuals | GDPR Art. 34 data-subject notice | "without undue delay" | CISO + Privacy |
| High-risk AI system serious incident (EU) — fundamental rights | EU AI Act Art. 73 | 2 days | CAIRO |
| High-risk AI system serious incident (EU) — other serious | EU AI Act Art. 73 | 15 days | CAIRO |
| Cybersecurity event (NYDFS-supervised) | NYDFS Part 500 §500.17 | 72 hours | CISO + CAIRO content |
| State insurance regulator (per Northfield's footprint) | State-specific | Varies (typically 72 hours) | Insurance Compliance + CAIRO |

---

## 4. Artifact 3 — Worked examples

### Incident 1 — Claims-triage bias (elderly insureds flagged elevated for fraud)

**Hour 0:**

- *Detected by:* AI program monitoring (demographic
  parity gap > 5pp on elderly-vs-others
  triggered).
- *Initial classification:* Category 2 (AI-Program
  Incident, sub-category 2.a Bias / fairness).
- *Lead:* AI Risk Lead.
- *Notification within 1 hour:* CISO on-call
  informed (no immediate security indicator).
- *External notification:* None yet; bias
  materialisation is monitored, not yet a
  reportable event.

**Hour 24:**

- *New facts:* IR investigation discovers that
  an external data-source the AI program uses
  (third-party fraud-pattern feed) had been
  manipulated by an attacker to produce a
  systematic bias toward elderly applicants. The
  manipulation is detected through an unrelated
  CISO-side investigation of the data-feed
  vendor.
- *Reclassification:* Joint (3.c Training-data
  integrity event). The bias was the surface
  symptom; the underlying cause is a
  security incident at the data-feed vendor
  affecting Northfield's AI program.
- *Lead:* CAIRO (initially) → joint with CISO; CAIRO
  retains program-level lead given regulatory
  framing.
- *External notification:* EU AI Act Art. 73
  evaluation triggered if any EU-resident
  insureds affected — fundamental-rights
  considerations (discriminatory treatment) →
  2-day timeline. Also NYDFS §500.17 evaluation
  for cybersecurity-event aspect. State insurance
  regulator notification per Northfield's
  footprint (NY + others).

**Final classification:** Joint (3.c).

**Path:** AI Risk Council convenes within 4 hours
of reclassification. Both CAIRO function and CISO
respond. CAIRO leads regulatory engagement; CISO
leads data-feed-vendor remediation.

### Incident 2 — Customer-service chat agent cross-session leakage

**Hour 0:**

- *Detected by:* Customer complaint via support
  channel.
- *Initial classification:* Category 3 (Joint,
  sub-category 3.b Cross-context leak). Both
  security (unauthorised disclosure) and
  AI-program (agent behaviour failure)
  dimensions.
- *Lead:* CISO initially (immediate-containment
  phase requires security ops); CAIRO joint.
- *Notification within 15 min:* AI Risk Lead
  notified; CISO on-call notified.
- *External notification (provisional):* GDPR
  Art. 33 evaluation triggered if any
  EU-resident customer affected (72-hour
  timeline). NYDFS §500.17 evaluation. EU AI
  Act Art. 73 evaluation (high-risk system
  with affected-rights implication).

**Hour 24:**

- *New facts:* Investigation identifies the bug
  as a Northfield-side orchestrator context-
  handling error, not a vendor or external
  attacker. The leak affected 14 customers (3
  EU residents).
- *Reclassification:* Remains Joint (3.b), but
  the security-incident aspect narrows
  (Northfield-internal bug, not external
  compromise). CAIRO becomes the appropriate lead
  for the post-containment phase.
- *External notification (confirmed):* GDPR Art.
  33 within 72 hours (3 EU-resident customers);
  data-subject notification per Art. 34
  (affected customers contacted directly within
  120 hours); EU AI Act Art. 73 within 15
  days (other serious incident — not
  fundamental-rights specifically because no
  discriminatory pattern but a privacy-rights
  violation).

**Final classification:** Joint (3.b), CAIRO-led
post-containment.

### Incident 3 — Fraud-detection model trained on corrupted dataset

**Hour 0:**

- *Detected by:* MRM-led model performance review
  (precision degradation noticed in routine
  monthly evaluation).
- *Initial classification:* Category 2 (2.d
  Model behaviour change) — provisional. MRM
  initially treats as a routine model-performance
  finding.
- *Lead:* AI Risk Lead + MRM Lead.

**Hour 24:**

- *New facts:* Investigation traces the
  performance degradation to corrupted training
  data ingested 8 weeks prior. Root-cause
  analysis is ambiguous: was the corruption
  malicious or accidental? IR investigation
  begins.
- *Reclassification:* Joint (3.c Training-data
  integrity event), pending root-cause
  determination.
- *Lead:* CAIRO (program impact); CISO joint on
  investigation.

**Hour 72:**

- *Root cause confirmed:* Accidental data
  corruption (not malicious); a Northfield-
  internal data-engineering error. Not a
  security incident in the classical sense.
- *Final reclassification:* Category 2 (2.d
  Model behaviour change). CISO informed but
  not lead.
- *External notification:* SR 11-7 model-event
  documentation required (Northfield's MRM
  practice); state insurance regulator
  notification per the discriminatory-pattern
  evaluation (false positives may have
  systematically affected certain customer
  cohorts).

**Final classification:** Category 2 (2.d), CAIRO-led
with MRM support.

---

## 5. Reasoning notes

- **Why three top-levels and not more.** §6.1 and
  §6.4 — most non-trivial incidents are joint;
  the value of the taxonomy is in distinguishing
  the four categories the routing actually needs:
  security-only, AI-program-only, joint-CISO-lead,
  joint-CAIRO-lead. Adding more top-levels would
  require routing-rule expansion that doesn't
  match the operational reality.
- **Why four sub-categories per top-level.**
  Operational sweet spot: enough to distinguish
  meaningfully-different patterns; few enough to
  be remembered. mod-103 §2.1 taxonomy
  discipline.
- **Why the bias-triage worked example escalates.**
  Most bias incidents start as AI-program
  incidents but a meaningful fraction have
  underlying security causes. The §6.5 post-
  incident discipline of revisiting classification
  as facts emerge is exactly this pattern.
- **Why I split the joint category by initial-
  impact dominant function rather than by sub-
  category.** §6 — the single-named-lead pattern
  requires a single function to be in charge; the
  natural split is by *who responds first* to the
  immediate impact, which then transitions as
  facts emerge. The CAIRO Risk Council can override
  if needed.
- **Why I included a 72-hour reclassification in
  the data-corruption example.** Many incidents
  start as joint and converge to single-category
  as root cause becomes clearer. Programs that
  *only* allow upward reclassification (single →
  joint) get over-burdened with joint incidents
  that didn't need to be; the discipline of
  *bidirectional* reclassification keeps the
  routing accurate.
- **What this taxonomy under-specifies.** The
  *severity* dimension within each category. The
  routing rules above don't directly differentiate
  P0 / P1 / P2 / P3 by category. A working taxonomy
  may include severity dimensions; the reference
  treats severity as an orthogonal property to be
  determined per incident.
- **What I would change in v2.** Add an
  *escalation criteria for sub-categories* —
  some sub-categories (e.g., 2.a bias materialisation)
  may have systemic implications that warrant
  Board-level briefing at lower thresholds than
  the current rules support. The reference treats
  sub-categories as routing-equivalent within a
  top-level; v2 would differentiate.

---

Maintained by [Girish Nair](https://github.com/garynair)
