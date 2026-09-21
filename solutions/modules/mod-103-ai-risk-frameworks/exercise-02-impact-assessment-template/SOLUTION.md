# Exercise 02 — Impact-Assessment Template — Reference Solution

## 1. Solution overview

Two artifacts. The template is structured around the seven
sections from §3.3 of the lecture notes, with named fields
and prompts. The worked example applies the template to
Northfield Mutual's LLM-based customer-service chat agent
and surfaces three real gaps.

---

## 2. Artifact 1 — The template

> **Northfield Mutual — AI Impact Assessment Template
> (Development Standard §3)**
> *Version 1.0. Owned by the CAIRO. Reviewed annually.*

### Section 1 — System summary
*Purpose: orient the reader. Should be readable by an
auditor with no prior context.*

Fields:

- **System ID** *(stable identifier from the inventory)*
- **System name and one-line purpose**
- **First-line owner** *(role)*
- **Business unit** *(for roll-up)*
- **Users / affected parties** *(employees, customers,
  third parties — be specific about who is downstream)*
- **Decisions affected** *(name the decision the system
  influences; describe materiality)*
- **Status** *(pilot / production / deprecated)*

Constraint: this section is **one paragraph**, not multiple
pages. The detail goes in sections 3 and 5.

Example fill: *"NM-AI-014. Customer-service chat agent.
LLM-based assistant that answers customer inquiries on
account balances, transaction details, and dispute
initiation. First-line owner: Head of Customer Experience.
Business unit: Retail. Users: ~120k unique customers per
month. Decisions affected: dispute initiation (substantive)
and self-service self-routing (administrative). Status:
pilot."*

### Section 2 — Risk categories applicable
*Purpose: declare scope of the assessment. Honest
under-scoping is worse than over-scoping.*

Fields:

- For each top-level category in the AI risk taxonomy:
  **applicable (Y / N) + one-line justification**.

Constraint: every category must be addressed (Y or N).
"N/A" is not acceptable; if the category truly does not
apply, write the one-line reason.

Example fill: *"Bias and fairness: Y. The agent can
influence which customers initiate disputes; non-uniform
willingness to dispute across populations is a real
concern."*

### Section 3 — Failure modes per applicable category
*Purpose: name the specific things that could go wrong.
This is the heart of the assessment.*

Fields (per applicable risk category):

- **At least 2 specific failure modes**, in the form *"X
  could happen because Y, affecting Z"*.
- Each failure mode rated **likelihood × severity** on a
  3×3 grid (Low / Medium / High on each axis).

Constraints:

- "The model could be biased" is **not** a failure mode.
  Specificity is the entire point.
- **No control proposals here.** The control belongs in
  the treatment plan, not in MAP. Sentences like "we
  could prevent this by..." are explicitly out of scope.
- Likelihood × severity must be rated. *"It depends"* is
  not a rating.

Example fill (Bias and fairness):

> *Failure mode 1: The agent could disclaim its ability
> to help with disputes more readily for customers whose
> initial message uses informal English (e.g., AAVE,
> ESL patterns), affecting dispute initiation rates for
> those customer populations. Likelihood: Medium.
> Severity: High.*
>
> *Failure mode 2: The agent could escalate to a human
> agent at different rates by inferred customer
> characteristic, producing a quieter version of the
> same disparate-treatment pattern. Likelihood: Medium.
> Severity: Medium.*

### Section 4 — Existing controls (honest inventory)
*Purpose: state, for the record, what is in place today.
Honest under-claiming is encouraged.*

Fields:

- Bullet list of current controls.
- For each control: **what risk category it addresses**,
  **lifecycle position** (pre-deployment / deployment /
  post-deployment).

Constraint: only list controls that are *operating today*.
Aspirational controls go in Section 7 (Recommendations),
not here.

### Section 5 — Gaps
*Purpose: state, for the record, what is missing. The
hardest section to fill out honestly; the most useful.*

Fields:

- Bullet list of named gaps.
- For each gap: **risk category**, **why it is a gap**
  (not just "we don't have it"), **first-line
  acknowledgment** that the gap is real.

Constraint: every assessment must surface **at least one
gap**. Assessments that surface none are not credible.
Reviewer will challenge.

### Section 6 — Reasonably foreseeable misuse
*Purpose: name how the system could be used in ways the
designers did not intend.*

Fields:

- At least 2 misuse scenarios, in the form *"Someone
  could use this system to X by doing Y"*.
- For each, an indication of whether the current
  controls would detect or prevent the misuse.

Constraint: misuse is **not** unauthorized access. It is
authorized use in unintended ways.

### Section 7 — Recommendations to MEASURE and MANAGE
*Purpose: hand off to the next functions. Recommendations
are framed as questions, not answers.*

Fields:

- For MEASURE: bullet list of *what to measure* per risk
  category. Format: "measure X, because Y."
- For MANAGE: bullet list of *what to consider*. Format:
  "consider whether X is needed; basis: Y."

Constraint: recommendations are **inputs to MEASURE /
MANAGE**, not decisions made by MAP. The MEASURE design
and the MANAGE treatment plans are separate artifacts.

### Sign-off

Fields:

- **MAP author** + date.
- **First-line owner concurrence** + date.
- **CAIRO review** + date.

The CAIRO review is **required** before this assessment
feeds into the AI Review Board agenda.

---

## 3. Artifact 2 — Worked example

> **Impact Assessment: NM-AI-014 — Customer-service chat agent**
> *Northfield Mutual — Customer Experience*
> *MAP author: Lead AI Risk Analyst. Date: [date].*

### 1 — System summary

NM-AI-014. LLM-based customer-service chat agent. Helps
customers with balance inquiries, transaction
explanations, and dispute initiation. First-line owner:
Head of Customer Experience. Business unit: Retail.
Affected parties: roughly 120k unique customers per
month. Decisions affected: dispute initiation (the agent
can guide a customer into starting a dispute, which has
operational and financial consequences) and self-service
routing (administrative). Status: pilot, four months in.

### 2 — Risk categories applicable

| Category | Applicable? | One-line justification |
|---|---|---|
| Performance | Y | LLM outputs vary; accuracy materially affects customer experience |
| Bias and fairness | Y | The agent influences whether disputes are initiated; differential treatment is a real concern |
| Transparency | Y | Customers need to understand the agent's role |
| Privacy and data | Y | Customer financial information flows through the system |
| Security | Y | Prompt injection and exfiltration are documented LLM risks |
| Operational | Y | Third-party LLM provider; provider downtime affects service |
| Compliance | Y | UDAAP, Reg E disclosure, state-level AI transparency |
| Reputational | Y | Public-facing system; high reputational stakes |
| Strategic | N | The pilot is bounded; no material strategic exposure |

### 3 — Failure modes per category

**Performance.**

- *F1: The agent could mis-state account balance or
  transaction details when the underlying data has
  unusual structure (joint accounts, recent transfers
  not yet posted), causing customer to act on incorrect
  information.* Likelihood: Medium. Severity: Medium.
- *F2: The agent could refuse to help with a topic it
  is capable of helping with, falling back to a "please
  call us" response unnecessarily, degrading
  self-service value.* Likelihood: High. Severity: Low.

**Bias and fairness.**

- *F1: The agent could disclaim more readily for
  customers whose initial message uses informal
  English, AAVE patterns, or ESL phrasing, producing
  differential dispute-initiation rates.* Likelihood:
  Medium. Severity: High.
- *F2: The agent could escalate to a human at
  different rates by inferred customer characteristic,
  producing a quieter disparate-treatment pattern.*
  Likelihood: Medium. Severity: Medium.

**Transparency.**

- *F1: A customer interacts with the agent without
  realising it is AI, and forms a belief about the
  bank's commitments based on the conversation.*
  Likelihood: Low. Severity: Medium.
- *F2: The agent's reasoning for refusing to help is
  not explainable in a regulatory adverse-action
  context.* Likelihood: Medium. Severity: Medium.

**Privacy and data.**

- *F1: The LLM provider could retain conversation
  content past the contract's retention window.*
  Likelihood: Low. Severity: High.
- *F2: Cross-session leakage — context from a previous
  customer surfaces in a current customer's session.*
  Likelihood: Low. Severity: High.

**Security.**

- *F1: A malicious customer could craft a prompt that
  extracts the system prompt or backend configuration.*
  Likelihood: Medium. Severity: Medium.
- *F2: An automated attacker could probe for
  information disclosure across many sessions.*
  Likelihood: Medium. Severity: Medium.

**Operational.**

- *F1: The third-party LLM provider experiences an
  outage; the agent is unavailable; call-center volume
  surges.* Likelihood: Medium. Severity: Medium.
- *F2: The provider changes the underlying foundation
  model mid-pilot, materially changing behaviour without
  Northfield's controlled re-evaluation.* Likelihood:
  High. Severity: Medium.

**Compliance.**

- *F1: The agent's dispute-initiation flow fails to
  surface a required Reg E disclosure under specific
  flows.* Likelihood: Medium. Severity: High.
- *F2: A state-level AI transparency obligation
  (CA AI Transparency Act applicable to CA-resident
  customers) is not met in the agent's introduction.*
  Likelihood: Low. Severity: Medium.

**Reputational.**

- *F1: Conversation transcripts showing the agent
  misadvising are published on social media.*
  Likelihood: Medium. Severity: High.

### 4 — Existing controls

- LLM provider contractual data-handling restrictions
  (Privacy + Operational).
- Agent introduction message that discloses AI status
  (Transparency).
- Session-level conversation logging with 30-day
  retention (Performance + Security; partial Compliance).
- Manual review of 1% of sessions weekly (Performance +
  Bias).
- Escalation-to-human button always present
  (Operational).

### 5 — Gaps (named honestly)

- **No bias-stratified evaluation.** The 1% manual review
  does not stratify by customer demographic or language
  pattern. Failure mode F1 in Bias would not be detected
  by current controls.
- **No model-change detection.** If the third-party LLM
  provider swaps the foundation model (Operational F2),
  Northfield would not know unless the provider
  proactively notified. This has already happened once
  during the pilot.
- **No automated probing detection.** Security F2 (automated
  probing across sessions) would not be flagged by current
  controls.

### 6 — Reasonably foreseeable misuse

- *Misuse 1:* An employee uses the agent to look up
  another customer's information by impersonating that
  customer via session context. Current controls
  (session-isolated context) would prevent the lookup
  but not the attempt; the attempt itself would not be
  logged for review.
- *Misuse 2:* A third-party fraudster uses the agent's
  dispute-initiation flow to gather information about
  what disputes get accepted, refining a fraud pattern.
  Current controls would not detect.

### 7 — Recommendations to MEASURE and MANAGE

**For MEASURE:**

- Measure dispute-initiation rate stratified by inferred
  language pattern (Bias F1). Because: current 1% review
  does not catch this.
- Measure escalation-to-human rate by customer cohort
  (Bias F2). Because: same.
- Measure model-version probe — automated daily check
  against a fixed prompt suite to detect provider model
  changes (Operational F2). Because: provider does not
  reliably notify.
- Measure prompt-injection attempt rate (Security F1).
  Because: not currently tracked.

**For MANAGE:**

- Consider whether to require the LLM provider to
  attest in writing to model-version stability between
  contracted change-windows (Operational F2). Basis:
  the unreviewed swap during pilot.
- Consider whether to add a Reg-E-disclosure check to
  the dispute-initiation flow as a deterministic guard
  (Compliance F1). Basis: regulatory severity outweighs
  the friction.
- Consider whether to invest in a bias-stratified eval
  set as a near-term priority (Bias F1, F2). Basis:
  Bias F1 is currently unmonitored *and* high severity.

### Sign-off

- MAP author: [name], Lead AI Risk Analyst. Date:
  [date].
- First-line owner concurrence: [name], Head of
  Customer Experience. Date: [date].
- CAIRO review: [name]. Date: [date].

---

## 4. Reasoning notes

- **Why the template caps at 4 pages.** A longer template
  will not get filled out faithfully. Length discipline
  *is* the design.
- **Why Section 5 (Gaps) is the most important.** Section
  5 is the section auditors and regulators read first.
  An impact assessment with no named gaps is implausible
  for a non-trivial system. The template forces honesty
  here.
- **Why Section 7 frames as "consider whether".** The
  recommendation is an *input* to MANAGE. MANAGE owns the
  decision. Phrasing recommendations as questions
  preserves the function boundary.
- **The worked example deliberately includes the mid-pilot
  model-version swap** as a real event. This is the same
  event referenced in mod-102 Exercise 04 (Trillium
  scenario). The continuity across exercises is
  intentional — readers build a richer mental model of
  each fictional company.
- **The Operational F2 failure mode is the most likely to
  catch a real reader off guard.** Most CAIROs new to LLM-
  based systems do not know that provider model swaps
  are not reliably disclosed. The worked example surfaces
  this so it is on the program's radar.
- **What would change if this were a real assessment.**
  Section 3 would expand — each failure mode would
  reference a specific likelihood-estimation basis (peer
  incidents, internal red-team results, etc.). The
  reference compressed for module length.

---

Maintained by [Girish Nair](https://github.com/garynair)
