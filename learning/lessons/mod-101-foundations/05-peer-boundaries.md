# Chapter 5 — CAIRO Peer Boundaries

## Why this chapter exists

The CAIRO does not exist in isolation. Nine peer roles have
overlapping equities in AI: Chief Risk Officer, Chief
Compliance Officer, Chief Privacy Officer, Chief Audit
Executive, General Counsel, Chief Information Security
Officer, Chief Information Officer, Chief Technology
Officer, Chief Data Officer. Every one of those boundaries
gets fought about in the first six months of a CAIRO's
tenure — usually about a specific incident, always about
who owns the follow-up.

The cheapest way to avoid the fight is to write the
boundary down *before* there is a specific case, get it
signed by both executives, and cite the written boundary
when the case arrives. This chapter builds the reference
grid you will use to do that.

## How to read this grid

Each peer entry lists three things:

1. **They own.** The core scope of the peer role that
   would exist whether or not AI were on the map.
2. **The CAIRO owns.** The AI-specific intersection where
   the CAIRO holds the decision.
3. **Shared, coordinated.** The zone where neither owns
   alone and a joint operating model is required.

Two roles will never fully agree on where their boundary
sits. The written agreement is what matters — not the
theoretical elegance of the split.

## The nine boundaries

### CAIRO × CRO (Chief Risk Officer)

- **They own.** Enterprise Risk Management taxonomy;
  risk appetite framework; risk register aggregation;
  operational-risk, market-risk, credit-risk, and
  strategic-risk categories.
- **The CAIRO owns.** How AI risks map into the ERM
  taxonomy; AI-specific risk appetite; the AI risk
  register (which rolls up into ERM); definitions of
  AI-specific risk categories (model risk beyond
  traditional MRM, foundation-model dependency risk,
  emergent capability risk).
- **Shared.** Materiality thresholds for AI risks;
  quarterly board risk reporting; risk-adjusted return
  discussions on AI investments.

If the CAIRO reports to the CRO (a common pattern; see
Chapter 4), this boundary is a *scope* question, not a
reporting question. The CAIRO must still be able to name
AI risks the ERM taxonomy has not yet absorbed.

### CAIRO × CCO (Chief Compliance Officer)

- **They own.** Regulatory compliance program across
  all obligations (not just AI); compliance testing;
  regulatory change management; compliance training;
  regulator relationships at the compliance layer.
- **The CAIRO owns.** AI-specific regulatory strategy
  (EU AI Act interpretation, NIST AI RMF adoption,
  sector AI rules); AI policy hierarchy; substantive
  interpretation of what "responsible AI" means for
  this organization beyond bare compliance.
- **Shared.** Control mapping from AI regulation to
  testable controls; evidence collection for AI
  regulator inquiries; joint quarterly compliance-and-
  AI-risk review.

The most useful test: if a new AI regulation is
published tomorrow, who reads it first, who interprets
it for the organization, and who signs the response?
Compliance owns the *reading, testing, and evidence*
discipline. The CAIRO owns the *substantive
interpretation and strategic response*. Both signatures
appear on regulator submissions.

### CAIRO × CPO (Chief Privacy Officer)

- **They own.** Personal-data lifecycle; DPIA process
  (GDPR Art. 35); consent management; data-subject
  rights; DPO responsibilities where applicable;
  cross-border data transfer governance.
- **The CAIRO owns.** AI-specific privacy considerations
  that extend beyond classical DPIA — inference of
  personal data from non-personal inputs, model
  memorization risk, training-data provenance
  restrictions, automated-decision-making governance
  (GDPR Art. 22 substantive design, not just legal
  basis).
- **Shared.** AI + DPIA joint assessments for
  high-risk AI systems processing personal data; model
  cards' privacy sections; incident response when a
  breach is simultaneously a privacy breach and an AI
  incident.

The GDPR Art. 22 boundary is the sharpest in practice.
The CPO/DPO owns the legal-basis and rights layer; the
CAIRO owns whether the decision-making system is
*actually* fit to be making the decision at all.

### CAIRO × CAE (Chief Audit Executive)

- **They own.** Independent assurance across the whole
  organization; audit-committee reporting; audit plan
  and universe; internal-audit methodology; issue
  tracking and remediation verification.
- **The CAIRO owns.** Nothing in the CAE's scope. The
  CAE audits *the CAIRO's function* like any other
  second-line function.
- **Shared.** Only the AI-audit methodology *inputs* —
  the CAIRO's control catalog is one input to the CAE's
  planning of AI-related audits. The CAE decides scope
  and methodology; the CAIRO does not review audit plans.

**This is the boundary the CAIRO should never fudge.**
The CAE is third line (Chapter 3). Any attempt by the
CAIRO to shape audit findings, delay audit reports, or
"pre-review" audit conclusions collapses 3LOD by
capturing the third line. The healthy relationship is
that the CAIRO welcomes audit and *never* attempts to
soften findings before they reach the audit committee.

### CAIRO × General Counsel

- **They own.** Legal advice; privilege; regulatory
  interpretation as a legal question; contract review;
  litigation; disclosure counsel; corporate governance
  filings.
- **The CAIRO owns.** Operational running of the AI
  governance program; substantive AI-risk positions
  that the GC will opine on legally; regulator-facing
  substance (what we are doing and why) where the GC
  handles the framing (how we will say it and under
  what privilege).
- **Shared.** Regulator-facing submissions
  (co-authored); AI-related contract terms with
  vendors and customers; disclosure decisions on
  material AI risks; incident response — the GC
  provides privilege guidance and disclosure counsel,
  the CAIRO owns the operational response.

The CAIRO cannot outsource "what to say to the regulator"
to the GC and remain a real function. The GC cannot
outsource "what is legally defensible" to the CAIRO. Joint
authorship of anything sent to a regulator is the
working default.

### CAIRO × CISO

- **They own.** Information security across all
  systems; security architecture; security operations
  (SOC); security incident response; security policy;
  vulnerability management; identity and access.
- **The CAIRO owns.** AI-specific threat models
  (prompt injection, model extraction, training-data
  poisoning, membership inference, adversarial
  examples); AI-incident classification distinct from
  security-incident classification; RAI/AI-safety
  content-filtering policy (as distinct from
  malicious-input security).
- **Shared.** AI red-teaming (methodology shared;
  scope decisions and disclosure joint); AI-system
  security architecture reviews; joint incident
  response for AI incidents that are also security
  incidents (data leak from an LLM, model exfil,
  poisoned model in production).

The CAIRO and CISO peer boundary is the one most likely
to be a false conflict. Frameworks like NIST AI 100-2
E2023, MITRE ATLAS, and OWASP LLM Top 10 are shared
tooling. The right posture is "CISO owns the security
program; CAIRO adds the AI-specific overlay; joint
runbooks for AI-system incidents." mod-107 covers this
boundary in operational depth.

### CAIRO × CIO

- **They own.** Enterprise IT strategy; core
  infrastructure; enterprise applications and their
  vendor management; help-desk and end-user computing;
  IT service management; IT change management.
- **The CAIRO owns.** AI-specific procurement rules and
  vendor risk criteria; AI-specific change-management
  overlays (impact assessment before deployment);
  AI-inventory scope and definitions.
- **Shared.** AI-related IT procurement (CIO runs
  procurement, CAIRO co-signs on AI vendors above a
  risk threshold); IT change-management integration
  with AI review board; enterprise use of general-
  purpose AI tools by employees.

CIO is a peer, not a parent (Chapter 4). The most
common failure at this boundary is the CIO absorbing AI
governance into IT governance and rendering it invisible
in board-level risk conversations.

### CAIRO × CTO

- **They own.** Technology strategy; engineering
  execution; product engineering leadership; technical
  architecture; build-vs-buy decisions at the
  technology layer; developer productivity.
- **The CAIRO owns.** AI-architecture decisions with
  material *risk* impact (foundation-model choice,
  agentic pattern selection, human-in-the-loop
  requirements); trust-architecture requirements
  (mod-106); model-deployment gating for high-impact
  systems.
- **Shared.** AI reference architecture (jointly
  authored; CTO owns feasibility, CAIRO owns risk
  constraints); trust-gate requirements (mod-106);
  AI evaluation methodology (CTO owns tooling, CAIRO
  owns methodology standards).

CTO is the peer relationship the CAIRO must most
actively invest in. A CAIRO seen as blocking engineering
loses influence; a CAIRO who ships engineering-friendly
governance (SDK-integrated trust checks, self-service
impact assessments, automated evidence collection)
gains it. The health of this relationship is a leading
indicator of program success.

### CAIRO × CDO (Chief Data Officer)

- **They own.** Data strategy; data quality; data
  lineage; data catalog; master data management; data
  governance (as distinct from AI governance).
- **The CAIRO owns.** Training-data provenance
  requirements; downstream-use restrictions on data
  used to train models; data-specific AI-risk
  categories (label bias, sample bias, distribution
  shift).
- **Shared.** Data-catalog integration with AI
  inventory (any dataset used to train an inventoried
  model must be discoverable in the catalog);
  data-quality metrics that feed AI evaluation;
  training-data governance (CDO owns catalog and
  lineage; CAIRO owns fitness-for-training judgments).

The CDO handles "is this data managed"; the CAIRO
handles "is this data fit for training this specific
model for this specific decision." The two questions
converge frequently but are not the same.

## The full boundary table

| Peer | They own | CAIRO owns the AI-specific intersection |
|---|---|---|
| CRO | ERM taxonomy, appetite, register aggregation | AI risk mapping, appetite, register (rolls up), AI risk categories |
| CCO | Enterprise compliance program | AI regulatory strategy, policy hierarchy, substantive RAI position |
| CPO / DPO | Personal-data lifecycle, DPIA, Art. 22 legal basis | AI-specific privacy design, model memorization, ADM system fitness |
| CAE | Independent audit — owns *everything* in scope | Nothing; CAE audits the CAIRO like any other function |
| GC | Legal advice, privilege, disclosure counsel | Operational RAI running, substance behind regulator responses |
| CISO | Enterprise information security | AI-specific threat models, RAI content policy, AI incident classification |
| CIO | Enterprise IT strategy and operations | AI procurement overlay, AI change-management overlay, AI inventory |
| CTO | Engineering execution, tech strategy | Risk-material architecture decisions, trust-arch requirements |
| CDO | Data strategy, quality, lineage | Training-data provenance, fitness-for-training, ADM data risks |

## The "signed boundary" pattern

The mechanism that actually prevents these boundaries
from being re-litigated every quarter:

1. **Draft a one-page boundary memo** with each peer in
   the CAIRO's first ninety days. Structure: they own /
   CAIRO owns / shared / escalation path when disputed.
2. **Both executives sign.** Signature matters — it is
   the artifact you cite when a specific case arrives.
3. **File the memos** in a location both organizations
   reference (typically the enterprise governance
   document repository, not a personal folder).
4. **Revisit annually.** Boundaries drift as AI
   footprint changes. An annual review with each peer
   catches the drift before an incident does.

The CAE is the exception: no boundary memo, because the
CAIRO does not negotiate scope with third-line audit. The
appropriate posture is a written "audit is welcome, at
any scope" standing statement.

## The escalation path when a boundary is disputed

Even with signed boundary memos, cases will arise where
two executives disagree in real time. The escalation
path should be defined *before* the case:

- **Level 1.** The two peers attempt resolution
  directly, with a defined SLA (typically five business
  days).
- **Level 2.** If unresolved, the case escalates to
  the common superior — usually the CEO, sometimes
  the COO. Both peers submit one-page positions.
- **Level 3.** The common superior decides. The
  decision is written and filed alongside the
  boundary memo as precedent.

Programs that skip level 1 (escalating immediately)
train their executives that boundary conflicts are the
CEO's problem. Programs that skip level 3 (letting
disputes fester) train their executives that boundaries
don't matter. Both fail.

## Summary

- Nine peer roles have AI equities: CRO, CCO, CPO, CAE,
  GC, CISO, CIO, CTO, CDO. Every boundary must be
  written down before a specific case arrives.
- The CAE boundary is the one the CAIRO must never fudge —
  the CAE audits the CAIRO, not the other way around.
- Default posture on regulator submissions and incident
  response is joint authorship with GC and CISO.
- CTO is the peer relationship whose health is a leading
  indicator of program success.
- The mechanism is signed boundary memos, revisited
  annually, with a defined three-level escalation path
  for real-time disputes.
