# Module 107 — Lecture Notes

About 100 minutes of reading. §2 (attack taxonomies)
is the densest reference section; §5 (the CAIRO × CISO
boundary) carries the operational weight.

---

## §1. The AI threat landscape — real vs hype

The AI security literature in 2024–2026 has produced
more *theoretical* threat categories than any of them
have produced documented incidents. A working CAIRO
distinguishes the threats that have produced
reproducible production harm from the threats that
remain academic curiosities, and weights the program's
attention accordingly.

This is not a claim that theoretical threats are
unimportant. Many will become operational. The
claim is that a program organising its defences
around every theoretical threat will produce defenses
that are *broad and shallow*, while real incidents
keep happening in the same handful of categories.

### 1.1 The categories with documented production incidents

The threat categories where production incidents
recur publicly:

1. **Prompt injection (direct and indirect).** Users
   or upstream content sources cause an LLM-based
   system to produce outputs outside its intended
   behaviour. Public incident base is large and
   growing.
2. **Data exfiltration through model output.**
   Models trained on or with access to sensitive
   data produce that data in outputs.
3. **Adversarial inputs to classification models.**
   Image classifiers, fraud detectors, content
   moderators can be evaded by inputs crafted to
   exploit specific decision boundaries.
4. **Training-data poisoning of curated datasets.**
   Open-source dataset contributors have repeatedly
   introduced data designed to produce specific
   model behaviours.
5. **Supply-chain compromise.** Compromised model
   weights, compromised inference container images,
   compromised vendor-hosted services. The
   classical software supply-chain problem applied
   to model artifacts.
6. **Tool-call exploitation in agentic systems.**
   Agents that call tools can be manipulated to
   invoke tools the principal did not authorise —
   especially when prompt injection meets agentic
   tool calls.
7. **Denial of service through expensive inputs.**
   Long inputs, recursive prompts, or
   computationally-expensive operations cause
   resource exhaustion.

These seven account for the majority of incidents
the CISO community has documented. Defenses against
them are the right priority.

### 1.2 The categories that remain mostly theoretical

The threat categories that appear in literature with
limited or no documented production exploitation:

- **Membership inference attacks** (determining
  whether a specific record was in training data).
  Possible in some settings; weaponisation in
  production is rare.
- **Model stealing via API queries** (extracting a
  model by querying it). Possible against
  unprotected APIs; the economics are usually
  against the attacker.
- **Reward hacking in production.** Discussed in
  alignment literature; production AI systems
  generally do not have the reward-hacking
  topology that makes this exploit interesting.
- **Catastrophic misalignment at deployment scale.**
  An active research area; not a present operational
  threat for non-frontier-AI organisations.

Programs should be *aware* of these — research
moves; what is theoretical in 2026 may be live in
2028. They should not be the priority for the
defences that get built in 2026.

### 1.3 The misallocation pattern

The most common AI security program misallocation:
program effort spent on theoretical threats while
the seven documented categories continue producing
incidents. Symptoms:

- The program's threat model is dominated by
  academic-literature categories.
- Detection coverage is broad but shallow — many
  signals, low fidelity on any single threat.
- Recent incidents at peer organisations are not
  reflected in the program's threat model.

A working CAIRO ensures the program's attention is
weighted toward what is happening, not toward what
could happen.

### 1.4 Why this discipline matters for the CAIRO

The CAIRO does not own AI security. The CISO does.
But the CAIRO sets the program-level threat-model
expectations the CISO operates within — and the
CAIRO's program-level reporting to the Board and
regulators is informed by the threat landscape.

A CAIRO who treats every theoretical threat as a
priority will under-resource the actual defences;
a CAIRO who dismisses theoretical threats will be
caught off-guard when one operationalises. The
discipline is informed prioritisation.

---

## §2. Attack taxonomies

Three taxonomies dominate AI security work in 2026.
They are complementary, not competitive. Working
programs use elements of all three.

### 2.1 MITRE ATLAS

**MITRE ATLAS** (Adversarial Threat Landscape for
Artificial Intelligence Systems) is the
ATT&CK-pattern taxonomy adapted for AI systems.
Tactics + techniques, mapped to AI-specific kill
chains.

ATLAS tactics include reconnaissance, resource
development, initial access, ML model access,
execution, persistence, privilege escalation,
defense evasion, discovery, collection, ML attack
staging, exfiltration, and impact. Each tactic has
specific techniques (e.g., under *ML model access*:
ML supply-chain compromise; query-based model
extraction; physical environment access).

**Strengths for CAIRO use:**

- Structured vocabulary that maps onto existing
  MITRE ATT&CK familiar to security teams.
- Concrete techniques rather than high-level
  principles.
- Connected to a curated case-study base.

**Limitations:**

- The taxonomy is large; using it as a checklist
  produces too many items to act on at program
  level.
- Some techniques are technically interesting but
  rarely material to enterprise deployments.

**How the CAIRO uses it:** as a structured *vocabulary*
for threat-modelling and incident-classification —
not as a checklist.

### 2.2 OWASP LLM Top 10

**OWASP Top 10 for Large Language Model
Applications** (currently the 2025 update) is a
deliberately short list of the most prevalent and
impactful LLM-specific risks.

Current categories include prompt injection,
sensitive information disclosure, supply chain
vulnerabilities, data and model poisoning, improper
output handling, excessive agency, system prompt
leakage, vector / embedding weaknesses, misinformation,
and unbounded consumption.

**Strengths for CAIRO use:**

- Short enough to remember and to communicate to
  non-security executives.
- Maps roughly to §1.1 — the categories with
  documented production incidents.
- OWASP's broader credibility transfers.

**Limitations:**

- LLM-specific; does not directly cover classical-
  ML attack categories (adversarial inputs to
  classifiers, etc.).
- The 10-item ceiling forces aggregation that can
  hide structure.

**How the CAIRO uses it:** as the *priority list* for
LLM-specific defence — and as the right framing
when communicating threat priorities to non-security
executives.

### 2.3 NIST AI 100-2 E2023

**NIST AI 100-2 E2023** — *Adversarial Machine
Learning: A Taxonomy and Terminology of Attacks and
Mitigations* — provides a taxonomy for both
classical-ML and LLM attacks with mitigation
recommendations.

Structured by:

- **Attack stage** — training-time, deployment-
  time, post-deployment.
- **Attack goal** — availability, integrity,
  confidentiality, abuse.
- **Adversary knowledge** — white-box, grey-box,
  black-box.

**Strengths for CAIRO use:**

- Covers both classical ML and LLMs in one
  framework.
- Includes mitigation recommendations, which
  ATLAS and OWASP do not directly.
- Government-authored — useful for regulator-
  facing context.

**Limitations:**

- Comparatively academic in tone.
- Less practitioner traction than ATLAS or OWASP.

**How the CAIRO uses it:** as the *bridging
framework* when the program has both classical ML
and LLM systems (which is the common case in
financial services and healthcare).

### 2.4 Composing the taxonomies

A working program does not pick one. The
composition pattern that works:

- **OWASP LLM Top 10** for LLM-specific priority-
  setting and executive communication.
- **MITRE ATLAS** for threat-modelling vocabulary
  and incident-classification structure.
- **NIST AI 100-2 E2023** for cross-LLM-and-classical
  framing in regulator-facing program
  documentation.

The program's threat-model artifacts cite *all
three* where relevant. Exercise 01 uses ATLAS as the
primary framing; the reference solution shows
where OWASP and NIST 100-2 supplement.

---

## §3. Defense-in-depth for AI systems

Defense-in-depth is the security principle that no
single control should be sufficient to prevent
compromise; multiple layered controls handle the
case where any individual control fails. The
principle is classical (NIST SP 800-39); the
adaptation for AI systems requires understanding
that the *layers* are different.

### 3.1 The layers of an AI system

A working defense-in-depth for AI systems considers
defences at:

1. **The principal layer** — authentication and
   authorisation of the principal (user, service,
   agent's invoking principal) per mod-106.
2. **The input layer** — what the system accepts as
   input; content-based filtering; input validation;
   adversarial-input detection.
3. **The model layer** — the model itself: its
   training-data provenance, its alignment, its
   robustness properties.
4. **The output layer** — what the system emits;
   output filtering; format constraints; PII
   detection; harmful content filtering.
5. **The tool layer** — for agentic systems: which
   tools are reachable, with what authority, with
   what audit.
6. **The data layer** — what data the system can
   read or write; access control; encryption at
   rest and in transit.
7. **The infrastructure layer** — the runtime
   environment: container security, network
   isolation, secrets management.
8. **The observability layer** — what is logged;
   what is monitored; what triggers alerts.
9. **The response layer** — what happens when an
   alert fires: kill switches, rollback,
   notification, post-mortem.

A program with defences at all nine layers is well-
designed; programs missing layers have
characteristic blind spots.

### 3.2 The common blind spots

Programs most often miss:

- **The tool layer.** Agentic systems add the tool
  layer to the threat surface; many programs apply
  classical-API security but do not separately
  control which tools the AI agent can invoke.
- **The output layer.** Input filtering is well-
  understood; output filtering is often an
  afterthought, leaving classical exfiltration
  paths open.
- **The response layer.** Detection without response
  is governance theatre. A program where an alert
  fires and produces no documented response is a
  program in name only.

mod-105 §6 (operationalizing ethics) named the
governance-theatre risk; the AI security version is
*security-theatre*: alerts that nobody acts on,
playbooks nobody runs, kill switches that have
never been tested.

### 3.3 The non-classical layers

Two layers that AI defense-in-depth needs but
classical defense-in-depth doesn't emphasise:

**The model-layer defences.**

- Training-data integrity controls (datasheets +
  provenance + signed manifests).
- Alignment training (RLHF, constitutional methods,
  etc.).
- Model-versioning controls and re-validation on
  swap (continuity with mod-104 Ex-04).
- Vendor model-version pinning where the bank
  controls it.

**The tool-layer defences (for agentic systems).**

- Capability scoping per mod-106 §3.2.
- Tool allowlist enforcement.
- Per-tool authorisation evaluation.
- Tool-output sanitisation before returning to the
  agent.

A program that addresses input + output but not
model and tool layers has *partial* defense-in-
depth, not full.

### 3.4 The cost-benefit reality

Defense-in-depth is not free. Each layer adds
latency, complexity, and operational cost. The
right depth depends on the system's blast radius
(per mod-106 §2.3). Three principles:

1. **High blast radius → more layers.** Catastrophic
   operations get all nine layers; routine
   operations may operate with fewer.
2. **Layer redundancy where layer failure modes
   correlate.** Two input-filter layers using the
   same technique are *one* control with two
   instances; two layers using independent
   techniques are *two* controls.
3. **The bypass test.** A layer that an attacker can
   skip without consequence is a layer providing
   no protection. Defence-in-depth is about layers
   the attacker must bypass *each one*, in series.

---

## §4. Red-teaming as governance practice

Red-teaming — adversarial evaluation of an AI
system by people specifically tasked with breaking
it — has emerged as one of the most-cited AI
governance practices in 2024–2026. The EU AI Act
mandates it for general-purpose AI above certain
thresholds. The CAIRO's job is making sure the
red-teaming the program does is *governance*-grade,
not security-engineering-grade.

### 4.1 What red-teaming is for

Red-teaming for AI systems serves three program-
level functions:

1. **Discover unknown failure modes.** Adversarial
   minds find behaviours that the development team
   did not anticipate.
2. **Stress-test the controls.** Test whether the
   defence-in-depth design actually defends.
3. **Produce evidence.** For regulators, for the
   Board, for internal audit — evidence that the
   program has done adversarial testing.

A red-teaming exercise that serves none of these
functions is performance art.

### 4.2 What red-teaming is not

Honest distinctions:

- Red-teaming is **not penetration testing**. Pen
  testing focuses on infrastructure (network,
  endpoint, identity). Red-teaming for AI focuses
  on the AI system's behaviour and the system's
  defence-in-depth surface as a whole.
- Red-teaming is **not validation**. Validation
  (mod-104 §3) evaluates whether the model is fit
  for purpose. Red-teaming evaluates whether the
  system fails under adversarial pressure.
- Red-teaming is **not a substitute for monitoring**.
  Red-teaming surfaces failure modes; monitoring
  detects production occurrences. Both are needed.

### 4.3 Red-teaming program elements

A working red-teaming program at the CAIRO level
specifies:

| Element | What it requires |
|---|---|
| Scope | Which systems get red-teamed, at what cadence |
| Methodology | The structured approach the red team uses (per ATLAS, per OWASP, etc.) |
| Independence | Red team independence from the system development team |
| Reporting | What findings get reported, to whom, in what format |
| Disposition | How findings get triaged, prioritised, and remediated |
| Re-test | When and how findings are re-tested after remediation |
| Evidence | What artifacts get retained for audit and regulator |

A program missing any element is not red-teaming;
it is ad hoc adversarial testing.

### 4.4 Cadence

The right cadence depends on the system's tier (per
mod-104 §2):

| Tier | Red-teaming cadence |
|---|---|
| Tier 1 Critical | Before deployment + quarterly + on material change |
| Tier 2 Important | Before deployment + annually + on material change |
| Tier 3 Standard | Trigger-based (incident, environment change) |

Frontier-AI capability-tier systems (per Anthropic
RSP and adjacent frameworks) have additional
cadences specific to capability thresholds.

### 4.5 Independence

The §3.3 of mod-104 independence test applies: if
the system fails in production, can the red team be
reasonably accused of bias toward the development
team? If yes, independence is insufficient.

The strongest red-team independence patterns:

- **External red team** — contracted specialists
  outside the organisation. Highest assurance;
  highest cost.
- **Internal red team in a separate organisational
  branch** — reports to CISO or to an independent
  function, not to the AI program. Good assurance;
  moderate cost.
- **Internal red team within the AI program with
  structural safeguards** — separate from the
  development team but in the same organisation.
  Operationally available; weaker independence test.

CAIRO-level positions: Tier 1 systems use external or
the second pattern at minimum; the third pattern is
acceptable for Tier 2 with explicit governance
arrangements.

### 4.6 The exercise design

A red-team exercise is *designed*, not improvised.
Exercise 02 asks you to design one. The elements:

- **Threat model** — what the red team is testing
  against. Drawn from ATLAS / OWASP / NIST 100-2.
- **Rules of engagement** — what the red team can
  and cannot do (e.g., they can attempt prompt
  injection but cannot extract real PII even if
  the system would allow it).
- **Time-box** — how long the exercise runs.
- **Goals** — what specific outcomes the red team
  is trying to demonstrate.
- **Scoring rubric** — how findings are graded
  (severity, exploitability, reproducibility,
  detection).
- **Out of scope** — what is explicitly excluded.
- **Reporting structure** — how findings flow into
  remediation.

---

## §5. The CAIRO × CISO boundary

The CAIRO × CISO boundary is the second of the three
recurring CAIRO boundary problems (mod-104 §5 covered
CAIRO × MRM; mod-111 will cover CAIRO × CFO for board
reporting). The discipline is parallel: respect the
CISO's domain expertise; do not encroach; do
contribute the AI-program perspective the CISO does
not own.

### 5.1 What the CISO owns

Within AI-related security:

- AI-system security in the classical sense:
  infrastructure security, network security,
  identity, endpoint security, secrets management.
- AI-related incident response operations.
- The security-monitoring stack as it applies to
  AI systems.
- The penetration-testing program.
- The vulnerability-management program.
- Vendor security risk assessment for AI vendors
  (in coordination with the CAIRO function).

### 5.2 What the CAIRO function owns

Within AI-related security:

- The AI risk taxonomy's security category (per
  mod-103 §2).
- The AI-program-level threat-model expectations
  the CISO operates within.
- The AI-program-level red-teaming policy.
- AI-specific incident classification (when is an
  incident a security incident vs an AI-program
  incident vs both — covered in §6).
- AI-program reporting on the security posture to
  the Board and regulators.
- The EU AI Act, NYDFS Part 500 AI amendments, and
  similar AI-specific regulator interfaces (in
  coordination with the CISO for any
  cybersecurity-overlap).

### 5.3 The intersection

The overlap is genuine. Specific recurring topics:

| Topic | CAIRO and CISO both have legitimate ownership |
|---|---|
| Prompt-injection defence | CISO does the engineering; CAIRO sets the program expectations |
| LLM output filtering | CISO operates; CAIRO defines what must be filtered (PII, harmful content, secrets) |
| Adversarial-input defence | CISO engineers detection; CAIRO sets the validation expectation (mod-104 Ex-02 pattern) |
| AI vendor security | CISO assesses; CAIRO sets AI-specific assessment criteria |
| Red-teaming program | CISO often executes; CAIRO defines program-level requirements |
| AI incident response | CISO operates IR; CAIRO classifies and reports |
| Regulator-facing security posture | CISO authors security parts; CAIRO authors AI-program parts |

The pattern is mirror-image with the MRM boundary:
the CISO does the technical work; the CAIRO sets the
program-level requirements and addresses what the
CISO does not own (governance, AI-program reporting,
AI-specific regulator interfaces).

### 5.4 Operating the boundary cleanly

The patterns that work:

- **Joint red-teaming expectations.** CAIRO defines
  the program-level expectations; CISO executes
  (or commissions external execution); both review
  findings.
- **Cross-referenced incident classification.** AI
  incidents that are also security incidents have
  one classification reflecting both, not two.
- **Single regulator response on joint topics.** EU
  AI Act Art. 73 incident reporting may have
  both AI-program and security elements; CAIRO leads
  on Art. 73 specifically with CISO's content
  contribution.
- **Shared vendor-risk machinery.** AI vendor
  security assessments use the CISO's existing
  vendor-risk infrastructure with AI-specific
  criteria contributed by CAIRO.

The patterns that fail:

- **CAIRO writing the security engineering standards.**
  Encroachment; produces standards engineers won't
  follow.
- **CISO ignoring AI-program-level threat-model
  expectations.** Decoupling; produces security
  controls that don't align with the AI program.
- **Separate AI security incident channels.**
  Duplication; loses coherent posture.

### 5.5 The reporting line dynamic

A recurring debate: should the AI program's
security-specific work report into the CISO or stay
within the CAIRO function?

The pattern that works: AI-specific security
*engineering* sits in the CISO's organisation; the
CAIRO function's contribution is **program design and
oversight**. This mirrors the MRM pattern: MRM
engineering sits with the CRO, while the CAIRO's
contribution is program-level. The principle: where
established functions exist, embed the AI-specific
work within them; don't create parallel functions.

Exercise 03 puts this boundary under specific
pressure and asks you to resolve.

---

## §6. AI incident classification

AI incidents need classification. The classification
determines (a) who responds, (b) what notification
obligations apply, (c) what regulatory reporting is
required, and (d) how the incident gets reported up.

### 6.1 The three primary classifications

A working classification distinguishes:

1. **Security incident** — the AI system was
   compromised in a security sense (unauthorised
   access, data breach, malicious code execution).
   Routes through CISO's incident response.
2. **AI-program incident** — the AI system behaved
   in a way the program's controls were intended
   to prevent (bias incident, transparency failure,
   contestability failure, capability violation by
   the agent itself). Routes through the CAIRO
   function.
3. **Joint incident** — the incident has both
   security and AI-program dimensions. Routes
   through both, with a single named lead.

The third category is common for AI systems.
Prompt injection that exfiltrates customer data is a
joint incident: security (data exfiltration),
AI-program (agent behaviour failure). A model that
silently swaps and produces different decisions is
also joint: security (supply-chain), AI-program
(unauthorised behaviour change).

### 6.2 Routing rules

A working classification produces *routing rules*
that determine the response path. Example:

```
Incident detected
    │
    ▼
Classify: security / AI-program / joint?
    │
    ├── security: route to CISO IR; notify CAIRO
    │
    ├── AI-program: route to CAIRO function; notify CISO
    │
    └── joint: AI Risk Council assigns single named
                  lead; both functions respond; CAIRO
                  + CISO joint status
```

The single-named-lead pattern is the same as
mod-104 Ex-04 (CAIRO × MRM vendor swap response).
Distributed leads on joint incidents is the failure
mode that produces conflicting responses to the
same incident.

### 6.3 Notification obligations

AI incident regulatory notification obligations are
complex and overlapping in 2026. The CAIRO and CISO
share the responsibility for triggering and
fulfilling them. Notable obligations:

- **EU AI Act Art. 73** — high-risk AI system
  serious incidents. Timelines: immediate for
  critical infrastructure; 2 days for fundamental
  rights; 15 days for other serious incidents.
  CAIRO lead.
- **NYDFS Part 500 §500.17** — cybersecurity
  events affecting NYDFS-supervised entities. 72-
  hour notification. CISO lead with CAIRO content.
- **GDPR Art. 33/34** — personal data breaches.
  72-hour notification to DPA. CISO + privacy +
  CAIRO.
- **Sector-specific** — varies (SR 11-7 model
  events, FDA medical device adverse events,
  state insurance regulations).

Programs that try to compute notification
obligations *during* an incident response have
already lost time. The discipline is pre-computed
notification matrices: for each incident
classification, which notifications are required, on
what timeline, who is responsible.

### 6.4 Incident classification examples

| Incident | Classification | Lead | Why |
|---|---|---|---|
| Prompt injection causes the customer-service agent to disclose another customer's account information | **Joint** | CAIRO + CISO (CAIRO lead) | Security (unauthorised disclosure) and AI-program (agent behaviour failure); CAIRO leads because EU AI Act Art. 73 may apply |
| Vendor LLM provider silently swaps the foundation model | **AI-program** | CAIRO | Not a classical security incident; an AI-program behaviour change. Notify CISO of the vendor governance failure |
| Container image hosting the agent service is found to have a known CVE | **Security** | CISO | Classical security; CAIRO informed because the agent is in scope of the AI program |
| Bias monitoring detects new disparate impact in production | **AI-program** | CAIRO | Not a security incident in the classical sense; AI-program response |
| Customer reports that the agent's responses include text from another customer's session | **Joint** | CAIRO + CISO (CISO lead initially) | Both possible privacy breach and agent behaviour failure; CISO leads on the immediate-containment phase |
| Adversarial input to the fraud-detection model produces a false-negative pattern detectable in production | **Joint** | CAIRO + CISO | Adversarial defence is engineering (CISO); pattern detection feeds AI-program risk register |

The pattern: most non-trivial incidents are joint.
The classification's value is naming the single
lead and the response path; not pretending the
incident is one-sided.

### 6.5 Post-incident discipline

A working program's post-incident discipline:

- Classification is **revisited** during the
  incident as more facts emerge. A classification
  that was right at hour 0 may need revision at
  hour 24.
- Findings feed both the **security threat model**
  and the **AI risk register** (mod-103 §6.2).
- Lessons learned are **shared** across the CAIRO
  and CISO functions.
- The classification *taxonomy itself* is
  reviewed annually based on incidents that
  surfaced. Categories may need to evolve.

Exercise 04 asks you to build the taxonomy and the
routing rules.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **MITRE ATLAS** — the AI-adversarial vocabulary
   §2 builds on.
2. **OWASP LLM Top 10 (2025)** — the LLM-specific
   priority list.
3. **NIST AI 100-2 E2023** — the bridging
   taxonomy across classical ML and LLM attacks.
