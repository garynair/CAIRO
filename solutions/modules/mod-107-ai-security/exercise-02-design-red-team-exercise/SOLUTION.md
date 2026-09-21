# Exercise 02 — Design a Red-Team Exercise — Reference Solution

## 1. Solution overview

A 5-day red-team exercise design for **Tessera's
agentic customer-service agent**. Five threat
scenarios: prompt injection chain to funds-transfer,
indirect prompt injection via dispute history,
trust-gate revocation bypass attempt, output-filter
PII evasion, vendor model identity attack. Mixed
team: 2 external + 3 internal red-teamers. Rules
of engagement protect real customers; scoring rubric
combines severity, exploitability, reproducibility,
and detection.

---

## 2. The exercise design

> **Tessera Bank — Red-Team Exercise Design**
> *System:* Customer-service agentic AI (Tier 1)
> *Exercise window:* 5 business days
> *Team:* 2 external researchers + 3 internal CISO
> security engineers (none worked on agent
> development)
> *Authoring:* CAIRO function; *Executing:* CISO
> organisation
> *Approving:* AI Risk Council

### Section 1 — Scope and goals

**Scope (in):**

- The customer-service agent and its supporting
  infrastructure (orchestrator, vendor LLM
  interface, tool layer, trust gates).
- The W3C VC manifest layer.
- The 3-gate trust pipeline (mod-106 Ex-04).
- Output filtering and audit logging.

**Scope (out):**

- Tessera's classical security perimeter (network,
  endpoints, identity infrastructure outside the
  agent context).
- Vendor X's internal model weights and training
  pipeline.
- Customer device compromise scenarios.
- Tessera employee social engineering.

**Goals:**

1. Determine whether the **3-gate trust pipeline
   fails closed** under coordinated bypass
   attempts.
2. Determine whether the **capability scoping**
   prevents tool-call exploitation when an attacker
   successfully manipulates the agent's reasoning.
3. Determine whether **output filtering** prevents
   PII leakage under adversarial output crafting.

### Section 2 — Threat scenarios

**Scenario 1 — Prompt injection chain to funds-transfer**

- *Aligned ATLAS:* AML.T0051 (LLM Prompt Injection)
  + AML.T0053 (LLM Plugin/Tool Compromise).
- *Actions:* Red team operates as authenticated
  customers. They craft input sequences attempting
  to induce the agent to invoke the funds-transfer
  capability outside the customer's intent —
  including attempts to bypass the customer step-up
  via prompt-engineering.
- *Defence layer tested:* Input + Model + Tool +
  Trust gates (Gates 2 and 3).
- *Red team success:* Any successful unintended
  funds-transfer authorisation; documented evidence.
- *Defender success:* All attempts blocked at one of
  the gates; logged with the agent's reasoning
  available for analysis.

**Scenario 2 — Indirect prompt injection via dispute
history**

- *Aligned ATLAS:* AML.T0051.001 (LLM Prompt
  Injection — indirect).
- *Actions:* Red team initiates disputes containing
  crafted text designed to be retrieved into the
  agent's context for a *different* customer
  interaction. Tests cross-context contamination.
- *Defence layer tested:* Input + Data + Output.
- *Red team success:* Cross-session influence
  demonstrated.
- *Defender success:* Context isolation holds; no
  cross-session contamination.

**Scenario 3 — Trust-gate revocation bypass attempt**

- *Aligned ATLAS:* Adapted from AML.T0034 (Disable
  AI/ML/System Logging) — repurposed for trust-
  bypass.
- *Actions:* Red team attempts to bypass Gate 2's
  fresh revocation check on catastrophic
  operations, including (a) cached-credential
  replay, (b) revocation-list manipulation, (c)
  JWKS-rotation timing window exploitation.
- *Defence layer tested:* Principal + Trust gate
  architecture (mod-106 Ex-04 Gate 2).
- *Red team success:* Any catastrophic operation
  authorised via a revoked credential.
- *Defender success:* All bypass attempts fail
  closed; alerts trigger.

**Scenario 4 — Output filter PII evasion**

- *Aligned ATLAS:* AML.T0042 (Output Manipulation)
  + AML.T0024 (Exfiltration via ML Inference API).
- *Actions:* Red team uses techniques known to
  evade output PII filters (encoded data,
  semantic transformations, format-based evasion,
  cross-language exfiltration).
- *Defence layer tested:* Output layer.
- *Red team success:* PII passes through to the
  external interface.
- *Defender success:* Output filtering catches
  evasion attempts; detection alerts trigger
  monitoring.

**Scenario 5 — Vendor model identity attack**

- *Aligned ATLAS:* AML.T0010 (ML Supply-Chain
  Compromise) — adapted.
- *Actions:* Red team simulates a vendor model-
  version change without notification. The
  exercise environment will operate with two
  vendor model versions selectable by configuration;
  the red team will switch between them at random
  intervals to test whether Tessera's model-
  identity verification catches the change.
- *Defence layer tested:* Model layer + Trust gate
  identity verification.
- *Red team success:* Agent operations continue
  successfully under the "swapped" model without
  Tessera-side detection.
- *Defender success:* Model-identity verification
  triggers an alert within 5 minutes of swap.

### Section 3 — Rules of engagement

1. **Authentication:** Red team operates with
   test accounts pre-created in Tessera's testing
   environment. The accounts have realistic but
   not-actually-customer data. Red team does **not**
   attempt to authenticate as real customers.
2. **Data handling:** If any vulnerability would
   produce real PII, the team documents the
   exploit and the affected data class without
   retaining the data itself. All test data is
   destroyed at exercise end.
3. **Coordination:** Daily check-in with the AI
   Risk Lead and CISO on-call. Immediate
   notification of any unintended impact on
   non-testing environments.
4. **Out-of-scope actions:** No DDoS attempts. No
   social engineering. No physical-access attempts.
   No attempts on infrastructure outside the agent
   pathway. No vendor-side direct attempts (Vendor
   X is not the subject of this exercise).
5. **Time-box:** 5 business days. 9am–6pm
   continuous; outside-hours operation only with
   explicit coordination (some scenarios may benefit
   from off-hours exposure of monitoring response).
6. **Termination conditions:** Exercise terminates
   immediately if (a) any unintended customer-
   impact occurs, (b) the security engineering team
   judges the exercise is producing genuine
   production risk, (c) the AI Risk Lead requests
   termination.

### Section 4 — Scoring rubric

| Dimension | Scale | Description |
|---|---|---|
| **Severity** | Critical / High / Medium / Low | If exploited in production, the impact on customers, Tessera, regulators |
| **Exploitability** | Trivial / Moderate / Hard / Very Hard | Skill and resources required for an attacker to execute |
| **Reproducibility** | Always / Often / Sometimes / Rarely | Whether the exploit reproduces reliably |
| **Detection** | Detected / Partial / Missed | Whether Tessera's monitoring caught the attack during the exercise |

Overall priority for remediation:

| If Severity is | And Exploitability is | Priority is |
|---|---|---|
| Critical | Anything except Very Hard | P0 (immediate remediation) |
| High | Trivial / Moderate | P1 (remediate before deployment) |
| High | Hard / Very Hard | P2 (remediate within 30 days) |
| Medium | Trivial / Moderate | P2 |
| Medium | Hard / Very Hard | P3 (remediate within 90 days or accept residual) |
| Low | Any | P3 |

Detection dimension feeds the scoring with a **detection
penalty** — a finding that was *missed* by monitoring
(rather than detected or partially detected) is one
priority level higher than its severity/exploitability
alone would warrant.

### Section 5 — Reporting and disposition

**During exercise:**

- Daily 15-minute status standup with AI Risk Lead,
  CISO on-call, and red-team leads.
- Slack channel for exercise-related communication.

**Immediate briefing (within 24 hours of exercise
end):**

- 30-minute briefing to CISO, CAIRO, CTO summarising:
  scenarios completed, findings, immediate
  red-flag items requiring action.

**Full report (within 10 business days):**

- Per-scenario detailed findings.
- Per-finding: description, ATLAS technique,
  scoring (4 dimensions), affected defence layers,
  reproducibility evidence, suggested remediation
  category (not specific products — that's the
  engineering team's choice).
- Cross-cutting observations.
- Recommendations for the next exercise cycle.

**Disposition:**

- Each finding routed into Tessera's existing
  vulnerability-management process at the
  appropriate priority.
- P0 and P1 findings reviewed by the AI Risk
  Council within 5 business days of full report.
- Re-test policy: P0 and P1 findings re-tested
  after remediation by the original or equivalent
  red-team configuration.

**Audit and regulator evidence:**

- Full report retained for 7 years.
- Exercise-design document retained in the program's
  policy library.
- Findings register integrated with the AI risk
  register (mod-103 §6.2).

---

## 3. Reasoning notes

- **Why a mixed external + internal team.** External
  red-teamers bring novel patterns; internal
  red-teamers bring Tessera-specific context. Pure
  external misses Tessera-specific defence layers;
  pure internal misses techniques the external
  community has discovered. The mix is the working
  pattern.
- **Why a 5-day window.** Long enough for chain
  analysis (a coordinated attack across multiple
  scenarios); short enough to maintain focus and
  to be a recurring exercise rather than a
  long-term project.
- **Why I included the vendor model identity attack
  scenario.** This is the mod-104 Ex-04 concern
  surfaced as a test. Programs that don't
  red-team the vendor-model-swap path are
  vulnerable to the silent-swap pattern. The
  exercise environment specifically supports the
  simulation.
- **Why the scoring rubric weights detection
  separately.** §3.2 of the lecture notes: detection
  is part of defence-in-depth. A vulnerability
  that is exploitable but immediately detected has
  bounded impact; one that is exploitable and
  silent has uncapped impact. The detection
  dimension makes this trade-off explicit.
- **Why I prohibited social engineering and
  customer-device compromise.** Both are real
  attack vectors but they are not specific to AI
  systems. They belong to Tessera's general
  security posture; including them in this
  exercise would dilute focus from the AI-specific
  attack surface.
- **What this design deliberately under-specifies.**
  The specific technical-tooling the red team uses
  (which prompt-injection corpora, which test
  harnesses, which monitoring of the agent's
  behaviour during attacks). The red team's
  expertise determines tooling; the CAIRO's design
  specifies *what's being tested*, not *how the
  testing is implemented*.
- **What I would change in v2.** Add an
  *external dependency analysis* — find what
  happens when Vendor X's API is slow or
  unavailable during a red-team scenario. The
  reference omits for length.

---

Maintained by [Girish Nair](https://github.com/garynair)
