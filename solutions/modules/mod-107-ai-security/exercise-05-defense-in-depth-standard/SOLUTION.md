# Exercise 05 — Defense-in-Depth Program Standard — Reference Solution

## 1. Solution overview

The Halverston AI Defense-in-Depth Program Standard
covers all nine layers tier-differentiated: Tier 1
requires all nine layers; Tier 2 requires seven (no
tool-layer for non-agentic; relaxed response-layer);
Tier 3 requires five. The standard specifies *what*
not *how*, and explicitly addresses Halverston's
multi-LOB challenges (public-markets latency, vendor
LLM swaps, cross-LOB shared infrastructure). Review
cadence: annual + trigger-based.

---

## 2. The standard

> **Halverston Capital — AI Defense-in-Depth Program
> Standard v1.0**
> *Owned by:* CAIRO function (program requirements).
> *Companion document:* CISO's "AI Security
> Engineering Implementation Guide" (mod-107 Ex-03
> resolution pattern).
> *Approval:* AI Risk Council + CRO.
> *Review:* Annual + trigger-based.

### Section 1 — Scope

**In scope:** All AI/ML systems Halverston operates,
across its three lines of business (public markets,
private credit, wealth advisory).

**Out of scope:** Pure analytical dashboards that
do not influence decisions. Internal-use models
that do not affect customers, employees, or
binding decisions. Note: out-of-scope determinations
are made by the AI Review Board and revisited
annually.

**Tiered application:** Per mod-104 §2. Tier 1
Critical systems require defense at all nine
layers. Tier 2 Important systems require seven
layers (specified below). Tier 3 Standard systems
require five layers (specified below).

### Section 2 — The nine-layer model

#### Layer 1 — Principal

*What must be defended:* Authentication and
authorisation of the principal on whose behalf the
AI system operates, per mod-106 trust architecture.

*Required controls:*

- Authenticated principal identity per the bank's
  identity service.
- Multi-factor authentication for principals where
  the operation's blast radius warrants.
- Session management with appropriate timeouts.
- Principal-action audit logging.

*Acceptance criteria:* Production AI systems show
documented principal identification for every
operation. Audit logs allow operation reconstruction
for principal review.

*Tiered application:*
- Tier 1: All controls required.
- Tier 2: MFA required for high-value or
  customer-facing operations.
- Tier 3: Basic authenticated identity required.

#### Layer 2 — Input

*What must be defended:* AI system inputs from
content-based attacks, adversarial inputs, and
unauthorised data injection.

*Required controls:*

- Input validation against accepted format / schema.
- Adversarial-input detection where applicable
  (classification systems).
- Prompt injection defence where applicable
  (LLM systems).
- Input source attribution where the input has
  multi-source provenance (vendor data, customer
  input, internal data).

*Acceptance criteria:* Quarterly evaluation against
known-adversarial-input corpus shows acceptable
detection rates (≥ 95% for documented attacks of
the corpus's vintage).

*Tiered application:*
- Tier 1: All controls required.
- Tier 2: All except input source attribution
  required.
- Tier 3: Basic input validation required.

#### Layer 3 — Model

*What must be defended:* The model itself —
training-data integrity, model-version control,
provenance of the underlying model artifact.

*Required controls:*

- Training-data provenance documented per mod-104
  Ex-03 LLM Supplement pattern (or its classical-ML
  equivalent).
- Model-version pinning where Halverston controls
  it; explicit acceptance of vendor swap policy
  where Halverston does not.
- Model identity verification at runtime (e.g.,
  mod-106 manifest pattern for LLM systems).
- Model integrity attestation at deployment.

*Acceptance criteria:* Model inventory entry (per
mod-104 Ex-03) includes complete provenance and
identity verification. Runtime monitoring detects
unauthorised model changes within 5 minutes.

*Tiered application:*
- Tier 1: All controls required.
- Tier 2: All except runtime model-identity
  verification at sub-5-minute latency (acceptable
  at hourly).
- Tier 3: Provenance + identity documented at
  deployment; runtime verification not required.

#### Layer 4 — Output

*What must be defended:* AI system outputs from
exfiltration, harmful-content, PII leakage, and
format-based evasion.

*Required controls:*

- PII detection and redaction in outputs.
- Harmful-content filtering per the bank's
  acceptable-use policy.
- Output-format constraint enforcement (no
  arbitrary code; no executable content unless
  explicitly scoped).
- Output audit logging.

*Acceptance criteria:* Output filtering catches a
documented corpus of evasion techniques at ≥ 90%.
Audit logs allow output reconstruction for
post-incident review.

*Tiered application:*
- Tier 1: All controls required.
- Tier 2: PII detection and audit logging
  required; harmful-content filtering required
  for customer-facing outputs; format constraints
  required.
- Tier 3: Audit logging required; PII detection
  required for customer-facing outputs.

#### Layer 5 — Tool

*What must be defended (agentic systems only):* The
tools the AI agent can invoke, their authorisation
scope, and their interaction with the agent's
reasoning.

*Required controls:*

- Capability scoping per mod-106 manifest pattern.
- Per-tool authorisation evaluation by the trust
  gate.
- Tool-output sanitisation before return to the
  agent.
- Tool invocation audit logging.

*Acceptance criteria:* No agent operation succeeds
without a verified capability scope match. Tool
audit logs allow reconstruction of every tool
invocation by every agent.

*Tiered application:*
- Tier 1 (agentic systems): All controls required.
- Tier 2 (agentic systems): Capability scoping
  required; tool-output sanitisation may be
  relaxed where the tool's output is in a
  bounded format.
- Tier 3 (agentic systems): Capability scoping
  required; per-tool authorisation can be
  resource-side rather than gateway-mediated.
- Non-agentic systems: This layer is N/A.

#### Layer 6 — Data

*What must be defended:* Data the AI system can
read or write — access control, encryption,
boundary enforcement.

*Required controls:*

- Encryption at rest and in transit.
- Data access control aligned with principal
  authorisation.
- Boundary enforcement between data classes
  (customer data, employee data, system data).
- Data access audit logging.

*Acceptance criteria:* Documented data access
patterns per AI system. Encryption keys managed
per Halverston's existing KMS policy.

*Tiered application:* All tiers require these
controls; specific implementations vary by data
class sensitivity.

#### Layer 7 — Infrastructure

*What must be defended:* The runtime environment —
containers, networks, secrets management.

*Required controls:*

- Hardened container images.
- Network segmentation per the bank's existing
  network architecture.
- Secrets management via Halverston's KMS.
- Vulnerability management on container images
  and dependencies.

*Acceptance criteria:* CISO confirms infrastructure
controls meet the bank's general security baseline,
adapted for AI workload-specific concerns.

*Tiered application:* All tiers require these
controls per CISO baseline; the CISO's
Implementation Guide specifies the technical
details.

#### Layer 8 — Observability

*What must be defended:* Visibility into AI system
behaviour, both for security monitoring and AI-
program monitoring.

*Required controls:*

- Operation logging (who, what, when, why).
- Behaviour anomaly detection (per the
  measurement plan, mod-103 Ex-03 pattern).
- Security event correlation (per CISO's existing
  SIEM).
- Drift monitoring (per mod-103 §4).

*Acceptance criteria:* Production AI systems
produce continuous monitoring signal feed into
both security operations (CISO SOC) and AI Risk
Lead's monitoring dashboards.

*Tiered application:*
- Tier 1: Full observability required.
- Tier 2: Full observability required.
- Tier 3: Operation logging + drift monitoring
  required.

#### Layer 9 — Response

*What must be defended:* Capability to respond when
the prior layers detect a threat or fail.

*Required controls:*

- Documented incident response playbook (per
  Exercise 04 of this module pattern).
- Kill-switch capability (programmatically disable
  the AI system).
- Rollback capability (revert to known-good
  state).
- Post-incident review process.

*Acceptance criteria:* Kill switches are tested
quarterly. Rollback capability is documented and
tested annually. Incident playbooks are current
to the program's classification taxonomy.

*Tiered application:*
- Tier 1: All controls required + quarterly
  kill-switch test + tabletop exercise quarterly.
- Tier 2: All controls required + semi-annual
  kill-switch test.
- Tier 3: Kill switch + rollback documented; tabletop
  exercise annual.

### Section 3 — Layer dependency analysis

**Correlated layer-failure modes (layers that may
fail together):**

1. **Principal + Trust architecture.** If the bank's
   identity service fails, multiple layers
   (Principal, Tool authorisation via trust gates)
   are affected simultaneously. Mitigation: the
   bank's identity service has its own redundancy;
   the AI program's defence-in-depth assumes
   identity-service availability and does not
   add separate principal-layer redundancy.
2. **Model + Vendor.** If the LLM vendor is
   unavailable or the foundation-model identity is
   compromised, the Model layer's controls fail
   simultaneously. Mitigation: Halverston's
   multi-vendor strategy (mod-106 Ex-05 partner
   recommendation) provides a fallback to a
   secondary vendor for critical operations;
   single-vendor outage is treated as a Category
   3 incident (mod-107 Ex-04).
3. **Observability + Response.** If observability
   fails to detect, response cannot trigger.
   Mitigation: independent dead-man-switch
   monitoring that itself alerts on observability
   silence.

**Independent layer redundancy (layers that should
fail independently):**

- Input filtering and output filtering use
  different techniques (input: content
  validation; output: PII detection / harmful-
  content detection). Their failure modes are
  not correlated.
- Multiple trust-gate placements (mod-106 Ex-04)
  fail independently because they have different
  availability and operational dependencies.

**Bypass test application:**

- Tool-layer can be bypassed by agents that
  invoke tools not in the program's tool
  inventory. Mitigation: tool allowlist enforced
  by the orchestrator; quarterly inventory
  reconciliation.
- Output-layer can be bypassed if the agent
  communicates with the principal through a
  channel not subject to output filtering.
  Mitigation: all customer-facing channels are
  routed through filtered output paths;
  exceptions require AI Review Board approval.

### Section 4 — Halverston-specific concerns

**Public-markets latency.**

Public-markets agents operate at microsecond-
to-low-millisecond latencies. Some layers add
significant latency (Trust gates, model-identity
verification at the manifest level). The
standard's tiered application addresses this:
public-markets systems are typically Tier 1 by
risk but operate with **Tier 1 controls executed
in a low-latency path**. The CISO Implementation
Guide specifies the low-latency techniques (in-
process trust verification, pre-validated
capabilities, async-logged audit) used for
public-markets agents.

**Vendor LLM model swaps.**

Per mod-104 Ex-04, vendor model swaps invalidate
the Model-layer's identity acceptance. The
standard's Model-layer controls require:
(a) contract terms that bind the vendor to
advance notification, (b) runtime model-identity
verification, (c) automated alert on model-
identity change, (d) joint incident response
between CAIRO and CISO (mod-107 Ex-03 boundary
pattern). The standard explicitly accepts that
no defence is fully effective against a vendor
that violates contractual notification — the
detection-and-response defence is the appropriate
posture.

**Cross-LOB shared infrastructure.**

The Audit Ledger and Identity Service (per
mod-106 partner recommendation) are shared across
LOBs. Failures in shared infrastructure produce
cross-LOB impact. The standard requires:
(a) the shared infrastructure has its own
defence-in-depth (independent of the AI program
standard, owned by CISO), (b) the AI program
treats shared-infrastructure failure as a
Category 3 incident with cross-LOB escalation,
(c) annual disaster-recovery exercises include
the shared-infrastructure failure scenario.

### Section 5 — Review and update cadence

**Annual review** — full standard review by the AI
Risk Council. Includes:

- Effectiveness against the trailing year's
  incidents (per Exercise 04 taxonomy).
- Coverage gaps surfaced by red-teaming (per
  Exercise 02).
- Industry threat-landscape changes (per §1 of
  the lecture notes).
- Regulatory updates (per the obligations
  register from mod-102 §6.1).

**Trigger-based update** — out-of-cycle revision
when:

- New attack category emerges with documented
  production incidents at peer institutions.
- Regulatory framework changes (e.g., EU AI
  Act implementing act adoption).
- Material vendor change (e.g., primary vendor
  acquisition, foundation-model swap policy
  change).
- Internal incident produces a finding that
  requires standard change.

**Approval authority:**

- Material changes: AI Risk Council + CRO + CISO
  joint approval.
- Editorial changes: CAIRO function with CISO
  concurrence.
- Annual review: AI Risk Council approval.

**Standards interface:**

- The standard's requirements feed the CISO's
  Implementation Guide. Joint review of both
  documents at the annual review.
- The standard's findings (gaps, coverage issues)
  feed the AI risk register (mod-103 §6.2) and
  the obligations register (mod-102 §6.1).

---

## 3. Reasoning notes

- **Why nine layers and not seven or twelve.**
  §3.1 of the lecture notes settled on nine
  based on the working defence categories. Fewer
  layers (e.g., omitting tool layer) under-
  serve agentic systems; more layers (e.g.,
  separating training-data layer from model layer)
  produce a standards document that is too
  granular to operate against. Nine is the working
  number.
- **Why I tier-differentiated and didn't make
  every control universal.** Different systems
  have different risk profiles. Requiring Tier 1
  controls on Tier 3 systems is wasteful;
  requiring Tier 3 controls on Tier 1 systems is
  inadequate. The tiered application addresses
  this. The risk: Tier 2 systems may be under-
  defended if their Tier-2 controls assume their
  risk profile is lower than reality. Annual
  review catches this.
- **Why the standard explicitly references the
  CISO Implementation Guide.** Per the Exercise
  03 boundary resolution, the CAIRO standard is
  intentionally separate from the CISO
  implementation document. The standard's
  references make the relationship explicit.
- **Why I included the Halverston-specific
  concerns section.** Per the exercise constraint:
  the standard must address Halverston's
  multi-LOB structure. Public-markets latency is
  unique to Halverston (or to similar systematic-
  strategy firms); vendor model swap is universal
  but particularly material at Halverston's scale;
  shared infrastructure dependency is also
  universal but more complex at Halverston's
  scale. Addressing them in-standard makes the
  standard operational for Halverston specifically.
- **What this standard deliberately does not
  include.** Specific products (per §6.4 vendor
  capture); specific technical implementations
  (per Exercise 03 boundary); specific tier
  threshold values (per mod-104 §2 tiering
  scheme owned separately). The standard
  specifies *what*; the CISO's Implementation
  Guide specifies *how*; the tiering scheme
  specifies *for which systems*.
- **What I would change in v2.** Add a
  *gap-acceptance procedure* — when a system
  cannot meet all required-tier controls (e.g.,
  a Tier 1 system in public markets cannot
  meet all sub-5-minute model-identity
  verification due to latency), how does the
  AI Risk Council formally accept the residual
  risk per mod-103 §5.3? The current standard
  treats compliance as binary; a v2 would
  introduce the formal exception-acceptance
  pattern.

---

Maintained by [Girish Nair](https://github.com/garynair)
