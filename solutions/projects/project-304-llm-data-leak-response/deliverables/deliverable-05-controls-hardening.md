# Deliverable 05 — Controls Hardening — Reference Solution

## 1. Solution overview

Defense-in-depth across four layers
(query, retrieval, synthesis,
output) with independent
tenant-scoping enforcement at
each. Development-process changes
target the five systemic causes
from Deliverable 02. Detection-
side improvements address the
6-week detection gap. Independent
third-party assurance through a
specialized AI-security firm
verifies. Roadmap impact: ~25%
of Q1 engineering capacity
diverted; product roadmap slips
~5 weeks; CFO impact ~$8M-12M
direct + indirect over 6 months.

---

## 2. The plan

### Architecture changes — defense-in-depth

Four layers; tenant-scoping
enforcement at each:

**Layer 1 — Query layer.** Tenant
ID derived from authenticated
session; validated against
expected schema; logged.
Default-deny on any missing or
malformed tenant context.

**Layer 2 — Retrieval layer.**
Vector index queries scoped at
the index-segment level by
tenant ID. Independent of any
orchestrator code. Default-
deny on missing tenant filter.
The original-bug-class is
prevented at this layer; the
orchestrator can no longer
default-permissive because the
index layer enforces.

**Layer 3 — Synthesis layer.**
Every chunk arriving at the
synthesis step is re-validated
against the query's tenant ID.
Chunks with mismatched tenant
metadata are rejected; the
synthesis step refuses to
generate a response from
mismatched chunks.

**Layer 4 — Output layer.**
Real-time monitoring on the
response stream for content
patterns characteristic of
cross-tenant disclosure
(e.g., named entities not
present in the tenant's
document corpus). Anomalous
responses are flagged for
review.

Each layer is independently
verifiable. Any single layer's
failure does not enable cross-
tenant disclosure.

### Development-process changes

Targets systemic causes 1, 2, 4:

- **Default-deny norm formalized.**
  Engineering Style Guide updated
  to require default-deny on
  security-relevant decisions.
  Code review checklist includes
  explicit security-default
  verification. Static analysis
  tooling flags default-permissive
  patterns on tenant-scoping code
  paths.
- **Tenant-isolation tests as a
  class.** New test category in
  the test suite specifically for
  tenant isolation. Tests cover
  every pathway through the
  orchestrator + every retrieval
  pattern + edge cases (empty
  context, malformed context,
  missing tenant ID). Tests run
  in CI; CI blocks merge on
  failure.
- **Refactor classification
  scheme.** Refactors that touch
  security-relevant code paths
  classified as "security-
  relevant" and routed for CISO-
  side review. Classification
  criteria explicit; default is
  conservative (security-relevant
  unless demonstrably not).

### Deployment-process changes

- **Staging coverage extended.**
  Staging environment runs query
  patterns representative of
  production agentic workflows,
  including the compare-across-
  sources pattern that triggered
  the bug. Staging dataset
  includes multi-tenant content
  for cross-tenant testing.
- **Canary discipline.** Canary
  rollouts of changes to
  security-relevant code paths
  extended to 7 days minimum
  (was 48 hours). Canary
  monitoring includes tenant-
  isolation invariant checks.
- **Rollback gates.** Automated
  rollback if tenant-isolation
  invariants observed broken in
  canary.

### Operational changes

- **Active tenant-isolation
  monitoring.** Real-time
  monitoring on the synthesis
  layer (Layer 3) tenant-ID
  rejection rate. Spike in
  rejections is a critical
  signal. Quiet rejection
  pattern indicates a quiet bug.
- **Query-pattern anomaly
  detection.** Production
  queries analysed for patterns
  distinct from the training
  distribution; anomalous
  patterns logged for review.
- **Customer-facing self-service
  investigation tools.**
  Customers can investigate
  their own tenant: query
  history, retrieved chunk
  history (subject to privacy
  constraints), audit log
  access. Per the systemic
  cause 5 customer-side
  observability gap.

### Detection-side improvements

Targets systemic cause 3:

- **L2 support playbook
  updated.** Cross-tenant
  content pattern is a new
  triage classification.
  Triage criteria: customer
  describes unexpected content,
  content includes names or
  identifiers not from their
  organization, content
  appears to originate from a
  different domain. Triage
  escalation to engineering
  on-call within 1 hour.
- **L2 training.** All L2
  support staff trained on the
  new triage classification
  and the underlying
  vulnerability class.
- **Pattern monitoring.**
  Anomalous-content-report
  rate monitored as a leading
  indicator of tenant-isolation
  issues.
- **Red-teaming cadence
  established.** Northrise
  internal red team conducts
  tenant-isolation testing
  monthly; external red team
  engagement quarterly.

### Vendor-model interaction

- **The foundation-model layer
  did not cause the bug.** The
  bug is in the Northrise
  retrieval orchestrator, not
  the foundation model. The
  foundation-model vendor's
  involvement is operational
  not causal.
- **Foundation-model vendor
  commitments going forward.**
  Northrise has reviewed the
  vendor's tenant-isolation
  posture; vendor confirms
  their model does not retain
  cross-tenant information.
  Documented for the post-
  mortem.
- **Foundation-model
  switching consideration.**
  Some affected customers have
  asked about foundation-model
  alternatives. Northrise's
  position: the model layer
  is not the issue; the
  retrieval architecture is.
  Switching foundation models
  does not address this incident
  class. Communicated to
  customers.

### Verification

- **Independent third-party
  penetration test.**
  Specialized AI-security firm
  engaged to test the
  defense-in-depth
  architecture and the
  tenant-isolation invariants.
  Days 30-45.
- **SOC 2 control update.**
  Tenant-isolation controls
  added to the SOC 2 control
  set. Next SOC 2 audit
  covers.
- **Customer review.** Selected
  customers (Cohort A) offered
  the opportunity to review
  the architecture remediation
  and verification report.

### Sequencing and timeline

| Control | Status |
|---|---|
| Layer-2 retrieval scoping | Containment Stage 1; Day 0 |
| Layer-3 synthesis tenant check | Containment Stage 2; Day 2 |
| Layer-1 query enforcement | Day 7 |
| Layer-4 output monitoring | Day 14 |
| L2 playbook update + training | Days 5-15 |
| Engineering Style Guide + static analysis | Days 7-30 |
| Tenant-isolation test class | Days 7-45 |
| Refactor classification scheme | Days 14-30 |
| Staging coverage extension | Days 15-45 |
| Canary discipline updates | Days 15-30 |
| Customer self-service tools | Days 30-120 |
| Red-team cadence | Days 30+ ongoing |
| Independent pen test | Days 30-45 |
| SOC 2 control update | Days 30-90 |

### Resourcing implications

- **Engineering capacity:** ~25% of
  Q1 engineering capacity diverted
  to remediation work; ~5 weeks
  of product roadmap slip on
  three planned features.
- **Security capacity:** CISO
  team adds 2 contractor
  positions for Q1; ~$400K cost.
- **Third-party assurance:**
  ~$300K-500K for the
  specialized pen test; ~$100K
  incremental SOC 2.
- **Customer credits / make-
  goods:** Q2 budget; specific
  amount TBD per customer
  conversations; CEO decision.
  Order of magnitude $3M-5M
  estimate.
- **Total direct + indirect
  cost over 6 months:** $8M-12M
  expected. Investor
  communication addresses.

### Honest about customer
cooperation

Two controls require customer
cooperation:
- Customer-facing self-service
  investigation tools require
  customer-side integration to
  be useful at scale.
- Cohort A customer reviews of
  the verification report
  depend on customer
  engagement.

Customers who engage with these
strengthen the controls; those
who don't get a less effective
result.

---

## 3. Reasoning notes

- **Why four layers rather than
  two or three.** Each layer
  catches a distinct class of
  bug. Layer 2 + Layer 3 alone
  miss the case where both
  layers share an upstream
  tenant-ID corruption. Layer
  1 enforces canonical
  identity; Layer 4 catches
  semantic anomalies that the
  upstream layers miss.
  Belt-suspenders-second-pair-
  of-suspenders-belt.
- **Why I named the foundation-
  model framing explicitly.**
  Customers will ask about
  foundation-model switching;
  the answer is "doesn't help
  here." Pre-empting the
  question reads as discipline.
- **Why I named the customer-
  cooperation dependency.**
  Some controls are not under
  Northrise's unilateral
  control. Pretending they are
  invites later disappointment
  ("you said you had self-
  service investigation but we
  can't actually use it").
- **Why the resourcing impact
  is named with dollar
  ranges.** CFO and investor
  conversations need
  quantification; vague
  "significant impact" framing
  fails financial
  conversations.
- **Why customer-credit /
  make-good is at $3M-5M
  range.** Order-of-magnitude
  estimate from similar
  incidents in the industry;
  specific allocation per
  customer is CEO-decision.
  Naming the range supports
  the CFO conversation.
- **What I would do
  differently.** I might have
  separated Layer-1 and
  Layer-4 (the bookends) from
  the core defenses (Layers 2
  and 3). Layer 1 is identity
  hygiene; Layer 4 is anomaly
  detection. Bundling them
  with the core scoping
  defenses understates that
  Layers 1 and 4 catch
  different classes of issue.

---

Maintained by [Girish Nair](https://github.com/garynair)
