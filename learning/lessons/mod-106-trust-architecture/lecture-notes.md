# Module 106 — Lecture Notes

About 105 minutes of reading. §4 (trust scoring) is the
technically densest section; §5 (trust gates in the
request path) is the most operationally consequential.

---

## §1. What "trust" means for AI systems

"Trust" is a metaphor we borrow from human relationships
and apply, often loosely, to AI systems. For operational
purposes the metaphor is unhelpful: humans extend trust
based on context, history, and intuition; AI systems do
not have any of those, and reasoning *as if they did*
produces designs that do not survive contact with
production.

The discipline of trust architecture begins by replacing
the metaphor with operational definitions.

### 1.1 Two senses of "trust" in AI systems

When practitioners talk about trust in AI systems, they
usually mean one of two things:

**Sense A — Trust as a property of the system.**
*"Can we trust this AI?"* In this sense, the question is
whether the system reliably produces outputs the
organisation can defend. It is the question NIST AI RMF,
ISO 42001, and the EU AI Act all address. **This sense
of trust is the subject of mod-101 through mod-105**;
it is *not* the subject of this module.

**Sense B — Trust as a runtime authorisation question.**
*"Should this agent be allowed to do this thing on
behalf of this principal right now?"* In this sense, the
question is about identity (who is this agent),
capability (what is it permitted to do), and context
(under what conditions). **This sense of trust is the
subject of mod-106.**

The two senses are related — an organisation that
cannot do (B) operationally will have a harder time
demonstrating (A) at the program level — but they are
not the same. Conflating them produces governance
documents that talk about agent identity in the same
breath as fairness, which is not coherent.

### 1.2 Operational trust as three composable questions

For any AI agent operation, trust architecture asks
three composable questions:

1. **Identity.** Is this agent who it claims to be?
2. **Capability.** Is this agent permitted to perform
   this operation? On behalf of which principal? Within
   what scope?
3. **Context.** Do current conditions support performing
   this operation? Has anything in the agent's
   environment changed in ways that should alter the
   decision?

These three are *separable* — a system can be strong on
identity and weak on capability, or strong on both but
unable to evaluate context. A working trust architecture
addresses all three.

### 1.3 What this is not

Honest distinctions:

- **Trust architecture is not safety.** Safety asks
  whether the system's catastrophic failure modes are
  bounded. Trust architecture asks whether routine
  operations are authorised.
- **Trust architecture is not security.** Security (in
  the CISO sense) defends against adversaries. Trust
  architecture authorises non-adversarial agents. The
  two interact heavily — mod-107 treats this — but
  they are distinct disciplines.
- **Trust architecture is not the model.** The model
  is what the agent runs on. The agent is what the
  trust architecture authorises. A program that
  conflates them ends up trying to authorise model
  weights, which is incoherent.
- **Trust architecture is not the ledger.** A tamper-
  evident audit ledger (mod-108) records what
  happened. Trust architecture decides what is
  *allowed to happen*. They are complementary
  artifacts.

### 1.4 Why this matters for the CAIRO

The CAIRO does not typically *build* trust architecture
— that is a CISO + CTO + CIO partnership. The CAIRO's
job is to know what good looks like, to set the
program-level requirements that the architecture must
meet, and to recognise when an architecture is
operationally inadequate.

mod-106's discipline is producing CAIRO-grade fluency on
a topic that is otherwise dominated by engineering and
security vocabulary. A CAIRO who can read an architecture
proposal and identify whether identity, capability, and
context are separable in the design is doing the job.

---

## §2. Zero-trust adapted for AI agents

Zero-trust architecture (NIST SP 800-207) is the most
useful structural inheritance for thinking about AI
trust. It is *not* a perfect fit — 800-207 was written
for human and service identities, not for agents that
generate novel intents at runtime — but the structural
discipline transfers cleanly when adapted.

### 2.1 The 800-207 core tenets

The seven tenets, adapted for the AI-agent case:

| 800-207 tenet | Translation for AI agents |
|---|---|
| All data sources and computing services are considered resources | Every model, every tool, every data store the agent touches is a resource |
| All communication is secured regardless of network location | Agent-to-tool and agent-to-data communication is authenticated regardless of "internal" / "external" |
| Access is granted on a per-session basis | Each agent operation is independently authorised; prior operations do not extend authority |
| Access is determined by dynamic policy | Authorisation considers the requesting agent's identity, capability scope, the resource's classification, and runtime context |
| Asset integrity and security posture is monitored | Both the agent's deployed configuration and the resources it touches have continuous posture monitoring |
| Authentication and authorisation are dynamic and strictly enforced | No standing privilege; capability assertions are short-lived and evaluated per request |
| Information about asset state, network infrastructure, and communications is collected for posture improvement | Agent operation logs feed back into trust scoring and gate-design improvement |

The discipline these tenets encode — *do not extend
trust beyond the scope you can verify, do not assume
that prior verification carries forward without re-
evaluation* — is the right discipline for AI agents.

### 2.2 Where 800-207 needs adaptation

Three places the source framework was not designed for
agentic AI:

1. **Agent identity is not static.** A human or service
   has a stable identity; an AI agent may be one of
   many instances of an underlying model, each
   instantiated for a specific session, possibly with
   different system prompts or memory state. Identity
   in this case is a *combination* of (model version,
   configuration, principal-on-whose-behalf, session
   id). NIST 800-207's identity model does not directly
   address this.

2. **Agent intent is generated at runtime.** A service
   knows in advance what API calls it will make. An AI
   agent decides at runtime, possibly based on a user
   prompt. Authorisation cannot pre-approve all
   possible intents.

3. **Policy enforcement must scale to per-operation
   granularity.** Service-level access control is
   typically per-API-call or per-resource. Agent-level
   trust architecture is per-operation, which can mean
   per-tool-invocation within a single conversation.
   Throughput requirements are different.

The adaptations: **dynamic identity composition**,
**intent-aware authorisation**, **per-operation policy
evaluation**. §§3–5 of these notes treat each in turn.

### 2.3 The blast-radius framing

NIST 800-207 implies but does not name what is, for AI
agents, the operationally most important framing: the
*blast radius* of an unauthorised operation.

Blast radius for AI agents is unusually large because:

- A single agent operation may touch multiple
  downstream services (tool-calling chains).
- An agent's "decision" to do something is often a
  natural-language reasoning step that, if compromised
  (prompt injection, hallucination, jailbreak), can
  cascade.
- Recovery from an unauthorised operation may not be
  possible — an agent that sends a customer email or
  posts to a public channel has produced an action that
  cannot be retracted by removing the agent's access.

The trust-architecture implication: where blast radius
is large, the *prior authorisation* gates matter more
than the *posterior detection* gates. Architecture
should fail closed; bypassing the trust gate should not
be the default fast path; the gate should be in the
critical path for any operation that has externally-
visible effects.

---

## §3. Identity and capability scoping

Identity and capability are the two questions the trust
architecture answers before letting an agent act.

### 3.1 Agent identity — the composite model

For an AI agent, identity is *composite*: it consists
of several attributes that together specify what the
runtime trust gate is being asked to authorise. A
working composite identity includes:

| Attribute | What it specifies | Standard / pattern |
|---|---|---|
| Model identity | Which underlying model is being invoked | Vendor identifier + model version |
| Configuration identity | What system prompt + tools + memory the agent is running with | Configuration hash; prompt-template version |
| Principal | On whose behalf the agent is acting | OAuth identity / OIDC identity / service principal |
| Delegation chain | If the principal authorised an agent, which delegations are in effect | Verifiable credential chain |
| Session | Which interaction this operation is part of | Session identifier; cryptographically bound to principal |
| Origin | Where the operation request came from | Network origin; client attestation |

A working trust architecture binds these together
cryptographically — the agent presents a token (often
a JWT) that names all relevant attributes and is
signed by an authority the gate trusts.

Different practitioner patterns implement this
differently:

- **OAuth 2.1 + JWT** for the principal layer; the
  agent acts as a confidential client with delegated
  authority via a token bound to the principal.
- **W3C Verifiable Credentials** for the delegation
  chain; the principal issues a VC that names the
  agent's permitted capabilities, the agent presents
  the VC at each operation.
- **Agent passports** (term used by several
  practitioners — IBM watsonx trust IDs, and
  others) — a single signed document that
  packages all identity attributes into one verifiable
  artifact.
- **Roll-your-own** with mTLS for transport, signed
  JWTs for identity, and a service-side capability
  registry. Works, requires more maintenance.

There is no single right pattern. Choosing among them
is the subject of Exercise 03 and §6 of these notes.

### 3.2 Capability scoping

Capability is the question *what is this agent
permitted to do*. Capability scoping is the discipline
of expressing capabilities precisely enough that the
trust gate can evaluate them and not so broadly that
the scope is meaningless.

A working capability scope includes:

- **Action type.** What kind of operation is being
  authorised (read, write, invoke, send, etc.).
- **Resource.** Which specific resource is the action
  on.
- **Constraints.** Any conditions on the action
  (amount limits, recipient restrictions, time
  windows).
- **Delegation depth.** Can the agent delegate this
  capability further to sub-agents.
- **Audit obligation.** What must be logged when this
  capability is exercised.

Capability scopes should be:

- **Bounded.** "Can read customer data" is too broad;
  "can read customer records for the authenticated
  principal in the customer-service context" is
  scope-appropriate for a customer-service agent.
- **Verifiable.** The trust gate must be able to
  decide *yes* or *no* deterministically given the
  capability scope and the operation request.
- **Short-lived.** Capability assertions should
  expire. "This agent has capability X" without an
  expiration is a standing-privilege pattern that
  800-207 explicitly disfavours.

### 3.3 Signed capability manifests

The practitioner pattern that works: a **signed
manifest** that declares the agent's identity,
permitted capabilities, and the authorising principal.
The manifest is:

- Issued by a trusted authority (the principal, or a
  delegated administrator).
- Signed cryptographically (ES256 / RS256 / Ed25519).
- Short-lived (minutes to hours, depending on stakes).
- Presented at each operation; verified at the trust
  gate.
- Revocable via a revocation list or token-binding
  scheme.

Several practitioner patterns:

- **Anthropic agent attestation pattern** — signed
  attestations of model identity + configuration; one
  implementation.
- **Cloudflare AI Gateway** — gateway-mediated identity
  + capability, the gateway becomes the trust
  authority. One implementation.
- **Roll-your-own with W3C VC + JWT** — author the
  manifest format using standard credential types; one
  implementation.

Exercise 03 asks you to author the manifest format
for a specific context. None of the practitioner
patterns is the answer; choosing among them is the
exercise's discipline.

### 3.4 The revocation problem

The hardest practical problem in agent identity:
revocation. When something goes wrong (compromise,
policy change, principal revokes authority), the
trust architecture must stop honouring the agent's
existing capability assertions.

Patterns:

- **Short-lived tokens.** Capability assertions
  expire quickly; revocation is implicit (just stop
  renewing). Works for routine cases.
- **Active revocation lists.** The trust gate checks
  a revocation list before authorising; revoked
  tokens fail. Works but adds latency; the list must
  be available and current.
- **Per-operation re-attestation.** Each operation
  re-fetches a fresh attestation; revocation is
  immediate. Highest assurance, highest cost.

A working architecture combines these — short-lived
tokens for routine operations, active revocation list
checks for high-stakes operations, per-operation re-
attestation for catastrophic-action operations.

---

## §4. Trust scoring — deterministic vs heuristic

The most contested topic in AI trust architecture: how
do you express *how trusted* an agent is, and what do
you do with that expression?

Two broad approaches.

### 4.1 The deterministic approach

A trust score is computed from inputs the system can
specifically verify, by a function the operator can
inspect. Inputs are signed events, attestation
artifacts, capability assertions, and posture
indicators. The function is rule-based or weighted-
sum based; given the same inputs, it produces the
same score.

**Properties of deterministic scoring:**

- Reproducible — the same inputs produce the same
  score.
- Auditable — the operator can inspect why a score
  is what it is.
- Defendable — to regulators, to customers, to
  internal review.
- Limited — can only score what is verifiable; cannot
  capture subtleties no signed event reflects.

**Where it fits:** high-stakes authorisation decisions
(payments, customer-facing actions, regulated-domain
operations), regulator-facing trust attestations.

### 4.2 The heuristic approach

A trust score is computed from observable signals,
many of which are proxies for trustworthiness. Inputs
may include historical agent performance, response-
pattern similarity, anomaly detection signals, peer
agent comparisons. The function is often a learned
model.

**Properties of heuristic scoring:**

- Captures patterns deterministic scoring cannot.
- Adapts to new threats or behaviours.
- Performant — usually fast.
- Opaque — the operator may not be able to inspect
  why a score is what it is.
- Brittle — subject to its own bias, drift, and
  adversarial manipulation.

**Where it fits:** detection-style use cases (anomaly
flagging, prioritisation, secondary signal alongside
deterministic gating).

### 4.3 The deterministic-is-better posture

For trust scoring used in **authorisation decisions**,
deterministic is generally the right posture. Reasons:

1. **Defendability.** A regulator, an auditor, or a
   customer challenging an authorisation decision
   needs to know why. A deterministic score can be
   explained; a heuristic score requires explaining a
   model, which is harder and more vulnerable to
   inspection challenges.
2. **Reproducibility.** When an incident occurs and
   the post-mortem asks why the trust gate authorised
   the operation, a deterministic score reproduces
   exactly. A heuristic score may have shifted by the
   time the post-mortem runs.
3. **Adversarial robustness.** A heuristic score is
   itself a model, subject to adversarial manipulation
   (a sophisticated attacker may craft operations that
   game the score). Deterministic scoring computed
   from cryptographic attestations is harder to game.
4. **Maintenance cost.** Heuristic models drift and
   need retraining; deterministic scoring functions
   change only when the operator changes them.

This is the *posture* the reference recommends. It is
not the only defensible posture. Heuristic scoring has
a place — typically as *adjacent* to authorisation
rather than as the authorisation itself. A program
that uses heuristic scoring to flag-for-review
combined with deterministic scoring to authorise has
both advantages.

### 4.4 The trust-score axes

A useful pattern: trust scoring on **multiple
orthogonal axes** rather than a single combined score.
Common axes:

- **Identity.** Strength of identity verification.
  Cryptographic attestation + current revocation
  status + delegation-chain verification.
- **Risk.** Risk profile of the requesting principal,
  the requested operation, and the operation context.
- **Reliability.** Track record of past operations
  by this agent or class of agents.
- **Autonomy.** Level of independent decision-making
  the operation requires.

For each axis, a deterministic computation produces a
score in a bounded range (typically 0–100 or 0.0–1.0).
The trust gate's authorisation logic considers all
axes.

This is the *4-axis pattern* used by several
practitioners — Cloudflare AI Gateway uses this shape
with a different specific set of axes; IBM
watsonx.governance varies the structure further.
None is the canonical answer. The pattern (multiple
orthogonal axes, deterministic per-axis scoring,
policy-level decision logic on top) is reusable
across implementations.

### 4.5 The 22-event vocabulary problem

A working deterministic trust system depends on a
*vocabulary of signed events* — a standardised set of
event types the agent ecosystem emits and the trust
gate consumes. The vocabulary needs to be:

- **Comprehensive** enough that meaningful
  operations are captured.
- **Specific** enough that events are unambiguous.
- **Stable** enough that ecosystem participants can
  emit compatible events.

Practitioner patterns:

- **A closed, numbered event taxonomy** — a fixed
  vocabulary (commonly 15-30 event types) defined by
  a single vendor or program; simple to implement,
  but ecosystem participants must adopt that vendor's
  specific taxonomy.
- **OpenTelemetry's evolving GenAI semantic
  conventions** — community-maintained event
  vocabulary; broader adoption potential, less
  trust-specific.
- **Roll-your-own** with project-specific event types
  — works for closed ecosystems, doesn't compose
  with others.

There is no settled standard as of 2026. CAIRO programs
operating across multiple agent ecosystems should
expect to invest in event-vocabulary discipline.

---

## §5. Trust gates in the request path

A trust gate is the runtime component that *makes the
authorisation decision*. It sits between the AI agent
and the resources it would touch.

### 5.1 Where trust gates sit

Four common placement patterns:

| Placement | What it sees | Strengths | Weaknesses |
|---|---|---|---|
| **Agent-side** (inside the agent's process) | Every operation the agent attempts | Lowest latency; full agent context | Trusts the agent process; agent can bypass |
| **Reverse-proxy** (between agent and downstream) | Every operation the agent makes outbound | Cannot be bypassed by the agent | Cannot see agent reasoning before the call |
| **Resource-side** (inside the resource being accessed) | Every operation against the resource | Sees authentic resource state | Each resource implements its own gate (duplication) |
| **Gateway-mediated** (separate gateway service) | Every operation through the gateway | Single point of policy enforcement; comprehensive audit | Latency, availability, scale considerations |

In practice, programs deploy **multiple** gates with
overlapping responsibilities. Defence-in-depth applies
to trust architecture as much as to security
architecture.

### 5.2 What a trust gate does

A trust gate's responsibilities, in order:

1. **Authenticate.** Verify the agent's identity
   attestation (signature, freshness, revocation
   status).
2. **Verify capability.** Confirm the requested
   operation is within the agent's signed capability
   scope.
3. **Evaluate context.** Apply any runtime policy:
   risk thresholds, recent posture signals, anomaly
   flags.
4. **Decide.** Allow / deny / require additional
   evidence (step-up authentication, human approval).
5. **Log.** Emit a signed event recording the
   decision and the reasoning.

Each step is independently failable. A gate that does
step 2 without step 1 authorises operations from
unauthenticated agents; a gate that does steps 1–4
without step 5 cannot be audited.

### 5.3 The latency trade-off

Trust gates add latency. For interactive agents
(customer-facing chat, real-time decision-support),
the gate's latency is on the user-experience critical
path. For asynchronous agents (overnight
processing, batch operations), latency is less
constrained.

Latency budgets vary; useful targets:

- **Interactive operations:** trust gate < 50ms p99.
- **High-frequency operations** (per-token
  validation in streaming): trust gate < 5ms p99.
- **Batch operations:** trust gate < 200ms p99 OK.
- **Catastrophic operations** (payments, customer-
  facing actions): trust gate latency is irrelevant
  if it preserves correct authorisation.

Programs sometimes try to optimise the gate by
caching authorisation decisions. Caching is dangerous
when capability assertions are short-lived or
revocation matters; the cache must be invalidated on
revocation events.

### 5.4 What trust gates break

Honest accounting. Trust gates impose costs:

- **Latency** (above).
- **Availability dependency.** The gate becomes a
  dependency for any operation that goes through it.
  Gate outage = system outage.
- **Operational complexity.** The gate must be
  deployed, monitored, scaled, updated.
- **Developer friction.** Agent developers must
  understand the gate's policy model; mis-
  understanding produces operations that the gate
  rejects, which manifests as system errors.
- **False positives.** A gate that rejects too
  aggressively breaks legitimate operations; one that
  rejects too leniently fails its purpose.

A working gate balances all five. Exercise 04 asks you
to design one with explicit attention to the trade-
offs.

### 5.5 Step-up authentication patterns

For high-stakes operations, the gate may *require
additional evidence* rather than allow or deny. Patterns:

- **Human-in-the-loop approval.** The operation
  pauses for a human approver.
- **Re-attestation.** The agent must present a fresh
  attestation with extra strength (e.g., from a
  higher-authority issuer).
- **Posture re-check.** The agent's deployed
  configuration is re-verified.
- **Multi-party authorisation.** Multiple principals
  must approve.

Step-up is the right pattern when the operation's
blast radius is high but legitimate use is also
expected. It avoids the binary trap of
allow-or-deny.

---

## §6. Build, buy, or partner

The CAIRO does not typically build trust architecture —
but the CAIRO has decision input on the build-vs-buy-
vs-partner question that determines how the program
operates against the architecture.

### 6.1 The three options

**Build.** The organisation engineers its own trust
architecture using standards (NIST 800-207, W3C VC,
OAuth 2.1, JWT/JOSE) and in-house implementation.

- *Strengths:* maximum control; no vendor dependency;
  architecture matches the organisation's specific
  needs; intellectual property is the firm's.
- *Weaknesses:* substantial engineering investment;
  maintenance burden; the organisation must maintain
  cryptographic expertise.
- *Best for:* organisations with strong engineering
  capacity, novel requirements that don't fit
  commercial offerings, or regulatory contexts where
  vendor dependency is itself a risk.

**Buy.** The organisation licences a commercial trust
architecture product (Cloudflare AI Gateway, IBM
watsonx.governance, or another vendor).

- *Strengths:* fast deployment; vendor support;
  architecture is battle-tested with other customers;
  vendor handles standards evolution.
- *Weaknesses:* vendor lock-in; product roadmap
  divergence from organisation needs; cost scales
  with usage.
- *Best for:* organisations without specialised
  cryptographic engineering capacity, common
  requirements where commercial offerings are well-
  developed, or contexts where speed matters more
  than maximal control.

**Partner.** The organisation engages a commercial
partner for some components and builds others —
typically buy the identity / attestation infrastructure
and build the policy / orchestration layer; or buy the
audit ledger and build the gates.

- *Strengths:* uses vendor expertise where it is
  strongest; preserves control where the
  organisation's specific needs matter.
- *Weaknesses:* integration burden; coordination
  across vendor + internal teams; partial-vendor-
  lock-in.
- *Best for:* most large enterprises; the modal
  pattern by 2026.

### 6.2 The decision framework

A useful framework for the choice, by dimension:

| Dimension | Build | Buy | Partner |
|---|---|---|---|
| Time-to-deploy | Slow | Fast | Medium |
| Engineering investment | High | Low | Medium |
| Maintenance burden | High | Low | Medium |
| Vendor dependency | None | High | Mixed |
| Customisation | Maximum | Limited | Selective |
| Standards evolution | Self-managed | Vendor-managed | Mixed |
| Regulatory defensibility | Self-attested | Vendor-attested + audit | Mixed |
| Cost over 5 years | Variable | Predictable | Mixed |
| Talent recruiting | Hard | Easy | Mixed |

No row determines the choice. The CAIRO's input
focuses on:

- **Regulatory defensibility** — can the program
  explain the architecture to a regulator and defend
  it?
- **Maintenance burden** — does the organisation have
  the capacity to maintain what is built?
- **Vendor dependency** — what happens if the chosen
  vendor changes terms, gets acquired, or fails?
- **Customisation** — does the program have
  requirements that commercial offerings don't meet?

### 6.3 Practitioner patterns — the 2026 landscape

The current commercial and open-source landscape (no
specific endorsement; observe the range):

- **Commercial AI-trust-architecture products:**
  Cloudflare AI Gateway (gateway-mediated trust +
  observability), IBM watsonx.governance (governance
  platform with trust components), Robust
  Intelligence, Credo AI, Holistic AI.
- **Open-source patterns:** SPIRE / SPIFFE for
  workload identity (originally designed for services;
  adaptable to agents); OpenID Connect + W3C VC
  combinations; Sigstore for attestation chains;
  OpenTelemetry GenAI semantic conventions.
- **Hyperscaler offerings:** AWS Bedrock guardrails;
  Azure AI Content Safety; Google Cloud AI safety
  features. These are partial trust architecture —
  they handle some axes (content safety) and not
  others (capability scoping in agent ecosystems).

Each of these is a *practitioner pattern*, not the
answer. The build-vs-buy-vs-partner decision is
itself a build-vs-buy-vs-partner across the matrix of
trust-architecture components.

### 6.4 Vendor capture risk

The most insidious risk in the buy or partner
patterns is **vendor capture**: the program's
architecture becomes structurally dependent on a
specific vendor's product in ways that are not
visible at decision time but become irreversible
later. mod-101 §6 named this as a failure mode of
ethics programs; it applies equally to trust
architecture.

Mitigations:

- **Standards-based interfaces.** Components used
  must speak standard protocols (W3C VC, OAuth,
  OIDC) so substitution is technically possible.
- **Documented assumptions.** The architecture
  documentation states what the vendor handles and
  what would need to be replaced if the vendor
  were unavailable.
- **Periodic vendor risk review.** The CAIRO function
  reviews vendor dependency annually as part of the
  obligations register (mod-102 §6.1).
- **Acceptable concentration.** Some vendor
  dependency is acceptable; concentration of
  multiple critical functions in one vendor is
  not. Spread risk across vendors where feasible.

### 6.5 What the CAIRO contributes to the decision

The CAIRO function's contribution to a trust-
architecture build / buy / partner decision is **not**
the architecture choice itself. The CAIRO contributes:

- The *requirements*: what regulatory defensibility
  the architecture must support, what audit and
  evidence requirements apply, what AI-program
  constraints the architecture must respect.
- The *risk assessment*: vendor capture risk,
  architectural fragility, dependency on novel
  standards.
- The *program-level position*: how the chosen
  architecture is described in the program charter,
  in board reports, and to regulators.
- The *long-term maintenance posture*: the
  architecture has lifecycle implications for the
  program; the CAIRO names them.

The actual architecture choice belongs to the
engineering and security executives — CISO, CTO, CIO.
The CAIRO informs that choice; the CAIRO does not own it.

Exercise 05 asks you to author the CAIRO's contribution
to a build-vs-buy-vs-partner decision for a specific
context.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **NIST SP 800-207** — Zero Trust Architecture. The
   structural inheritance §2 builds on.
2. **W3C Verifiable Credentials Data Model** — the
   identity / capability standard §3 references.
3. **OAuth 2.1 + RFC 9068 (JWT for OAuth)** — the
   token-based identity layer most architectures use.
