# Exercise 01 — Threat Model Using MITRE ATLAS — Reference Solution

## 1. Solution overview

For **Tessera's agentic customer-service agent**, the
reference treats **11 specific ATLAS techniques**
across 5 tactics, supplements with two OWASP LLM
categories, cross-references three threats to NIST
AI 100-2 E2023 framing, and ranks **prompt injection
(LLM/Tool-Calling Chain)**, **data exfiltration via
output**, and **ML supply-chain compromise of the
vendor LLM** as the top 3 program-level priorities.

---

## 2. System summary

Tessera's agentic customer-service agent (from
mod-106): LLM-based agent with 5 capabilities (read
account, send message, initiate dispute, transfer
funds, schedule appointment, update profile).
Vendor-hosted LLM (Vendor X), Tessera-side
orchestration, signed-W3C-VC manifest at each tool
call, 3-gate pipeline (mod-106 Ex-04). Tier 1 per
mod-104 Ex-01. EU AI Act high-risk per Annex
III(5)(b) (essential private services — financial).

---

## 3. ATLAS-aligned threat enumeration

### Tactic — ML Model Access

**AML.T0010 — ML Supply-Chain Compromise.**

- *Manifestation:* Vendor X's foundation model is
  swapped (intentionally or unauthorised) with a
  version exhibiting different behaviour. The agent
  authorises operations on the assumption of the
  prior model behaviour.
- *Likelihood:* Medium (Vendor X swaps occur with
  notice; unauthorised swap is rare but plausible).
- *Blast radius:* High (all agent decisions affected).

**AML.T0044 — Full ML Model Access (vendor side).**

- *Manifestation:* Vendor X retains conversation
  data for training or operational use beyond
  Tessera's contracted scope.
- *Likelihood:* Low (contract prohibits; not
  zero — vendor logs may exist).
- *Blast radius:* High (sensitive customer
  information exposure).

### Tactic — Execution

**AML.T0051 — LLM Prompt Injection (direct).**

- *Manifestation:* Customer input is crafted to
  override the agent's system prompt, causing the
  agent to take actions outside its intended
  behaviour.
- *Likelihood:* **High** (active in 2026; ongoing
  technique).
- *Blast radius:* High when combined with tool
  calling.

**AML.T0051.001 — LLM Prompt Injection
(indirect).**

- *Manifestation:* Account data or message content
  surfaced to the agent contains adversarial
  content that influences the agent's behaviour on
  the next operation.
- *Likelihood:* Medium (requires content path).
- *Blast radius:* High.

**AML.T0053 — LLM Plugin/Tool Compromise.**

- *Manifestation:* The agent invokes a tool whose
  response is crafted to manipulate the agent's
  subsequent reasoning (chain-of-tool exploit).
- *Likelihood:* Medium.
- *Blast radius:* High when subsequent operations
  are catastrophic (funds transfer).

### Tactic — Defense Evasion

**AML.T0034 — Disable AI/ML/System Logging.**

- *Manifestation:* Attacker causes the agent's
  audit logging to fail or be disabled, preventing
  post-incident review.
- *Likelihood:* Low (logging is well-defended).
- *Blast radius:* High (loss of forensic
  evidence).

**AML.T0042 — Output Manipulation.**

- *Manifestation:* The agent's output is crafted to
  evade Tessera's output filters (e.g.,
  encoded PII; format that defeats classification).
- *Likelihood:* Medium.
- *Blast radius:* Medium.

### Tactic — Exfiltration

**AML.T0024 — Exfiltration via ML Inference API.**

- *Manifestation:* Sensitive customer data is
  exfiltrated through the agent's output (PII in
  response text, account-data leakage to other
  customers' sessions, vendor-side conversation
  logging).
- *Likelihood:* **High** (active in 2026; multiple
  reported patterns).
- *Blast radius:* High (potential customer
  privacy / regulatory).

**AML.T0049 — Exfiltration via Cyber Means.**

- *Manifestation:* Classical exfiltration — through
  the network, through compromised orchestrator
  service, etc. — but specifically affecting
  customer data accessible through the agent
  pathway.
- *Likelihood:* Low.
- *Blast radius:* High.

### Tactic — Impact

**AML.T0061 — Cost Harvesting.**

- *Manifestation:* Attacker exhausts Vendor X's
  inference budget through high-volume queries,
  causing service degradation and unexpected
  costs.
- *Likelihood:* Medium.
- *Blast radius:* Medium (cost + availability).

**AML.T0048 — External Harms.**

- *Manifestation:* The agent's reputation-damaging
  behaviour (e.g., systematically unfair responses
  to a customer cohort) becomes public, affecting
  Tessera's reputation beyond the direct customer
  impact.
- *Likelihood:* Medium.
- *Blast radius:* High (reputational +
  regulatory).

---

## 4. OWASP supplements

**LLM06 — Excessive Agency.**

- ATLAS does not explicitly name this as a
  technique. OWASP's framing is relevant: the
  agent's ability to take consequential actions
  (transfer, profile update) without sufficient
  oversight is itself a security concern. The
  trust-architecture from mod-106 addresses this
  via signed-capability scoping; the OWASP framing
  reminds the program that *the granted scope is
  itself a defence parameter*.

**LLM10 — Unbounded Consumption.**

- Maps to ATLAS AML.T0061 but with broader scope:
  attacker-induced resource exhaustion (long
  prompts, recursive tool calls) on Tessera's
  infrastructure. The defence is rate limiting
  + budget enforcement.

---

## 5. NIST AI 100-2 E2023 cross-reference

Top 3 threats, cross-referenced:

| Threat | NIST attack goal | Adversary knowledge | Attack stage |
|---|---|---|---|
| Prompt injection (LLM/Tool-Calling Chain) | Integrity + abuse | Grey-box (knows the system has tools; doesn't know the system prompt) | Deployment-time |
| Data exfiltration via output | Confidentiality | Black-box (only API access) | Deployment-time / post-deployment |
| ML supply-chain compromise of vendor LLM | Integrity + availability | Black-box (no model weights) | Pre-deployment + ongoing |

The NIST framing helps when communicating with
regulators or framework-oriented stakeholders who
expect attack-goal × adversary-knowledge
classification rather than tactical taxonomies.

---

## 6. Priority ranking

Ranked by (likelihood × blast radius):

1. **Prompt injection (AML.T0051) — direct + via
   indirect content paths.**
   - Reasoning: Highest combined likelihood and
     blast radius. The agent has tool-calling
     capabilities including funds-transfer; a
     successful prompt injection that influences
     tool-call selection has direct financial
     impact. Active 2026 incident base in similar
     systems. Defenses depend on (a) trust gates
     from mod-106 (which limit blast radius even
     under prompt injection), and (b) input/output
     filtering. The program must invest most heavily
     here.
2. **Data exfiltration via output (AML.T0024).**
   - Reasoning: Active 2026 incident base. Multiple
     pathways (PII in response text, cross-session
     leakage, vendor-side logging). Output-layer
     defences are necessary. Customer privacy is at
     stake on every interaction; a single material
     incident has reputational and regulatory
     consequences.
3. **ML supply-chain compromise of vendor LLM
   (AML.T0010).**
   - Reasoning: The vendor LLM swap pattern from
     mod-104 Ex-04 is a real Tessera concern. The
     impact of a silent or unauthorised swap is
     systematic — every agent decision is affected.
     Lower likelihood than prompt injection but
     higher worst-case blast radius (no single
     incident; systematic behaviour change).

The other 8 threats are program-relevant but
secondary; the CISO is expected to defend against
them within the program's overall security
posture, but the top 3 receive the bulk of program
attention and budget.

---

## 7. Reasoning notes

- **Why 11 techniques and not 30.** §1.3
  misallocation pattern. A threat model with 30
  techniques produces 30 partial defences. 11
  forces priority and gets meaningfully better
  defence per dollar.
- **Why prompt injection is ranked first.** Multiple
  factors converge: highest current incident base,
  highest blast radius given the tool-calling
  capabilities, active research and tooling among
  attackers, defence-side maturity is uneven. The
  CISO can argue for first-priority on multiple
  threats; this reference takes the position that
  prompt injection is the right top-priority for
  this specific system.
- **Why vendor LLM supply-chain is in the top 3
  despite lower likelihood.** The worst-case blast
  radius is *systematic* — not one incident but
  systematic behaviour change. mod-104 Exercise 04
  was about exactly this case. A program that has
  the trust-architecture from mod-106 still needs
  defence-in-depth around the model-identity
  layer.
- **Why I did not include classical adversarial
  examples (AML.T0020 — Evade ML Model) in the
  top 3.** This system is LLM-driven, not a
  classification model. Adversarial examples in the
  classical sense (image perturbations, etc.) are
  not the primary threat vector. They are relevant
  to Tessera's fraud-detection model (Model D from
  mod-104) — but that's a different system's threat
  model.
- **What the reference deliberately under-
  specifies.** Specific control recommendations.
  This is a program-level threat model; specific
  controls are the CISO's engineering team's
  output, downstream of this artifact.
- **What I would do differently in v2.** Add a
  *chain analysis* — for the top 3 threats,
  trace the specific defence-in-depth layers (per
  mod-107 §3.1) the threat must bypass. This makes
  the threat model directly actionable for the
  CISO's layer-by-layer control design. The
  reference omits for one-iteration length but a
  working program's v2 would include it.

---

Maintained by [Girish Nair](https://github.com/garynair)
