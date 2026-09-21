# Deliverable 06 — Blame-Free Post-Mortem — Reference Solution

## 1. Solution overview

Two-version post-mortem. Public version
~6 pages, abstracted, focused on what
customers need to understand. Internal
version ~14 pages, full causal chain,
honest about all failure modes including
the L2 triage failure and the
CTO-knew-Day-minus-2-CEO-Day-minus-1
timing question. Blame-free framing
throughout per mod-110. Names the pattern
(default-permissive on security
invariants in refactors) not just the
specific bug.

---

## 2. Public-facing abstracted version

> **GUARDIANGPT — TENANT ISOLATION
> INCIDENT POST-MORTEM**
> *Published [date]. Authoring: CAIRO and
> CTO. For Northrise customers and
> stakeholders.*

### What happened

On [date], a member of a customer's
internal security team discovered that
their GuardianGPT instance, under
specific test prompts, returned content
fragments that did not originate from
their own document corpus.

We confirmed the report within hours.
Investigation revealed that a software
defect in our retrieval middleware,
introduced 42 days earlier in a
refactoring release, caused certain
queries — under a narrow combination
of agentic workflow patterns — to
receive content fragments from outside
the requesting customer's tenant.

We contained the defect within 24 hours
of confirmation. We then completed a
substantive scope analysis, customer
notification process, and remediation
program over the following 30 days.

### What was affected

Of our 180 production customers:
- 7 customers were affected with
  identifiable cross-tenant content
  surfaced in at least one query
  response during the affected period.
- 8 customers (some overlapping with
  the 7) were the source of content
  fragments that appeared in other
  customers' responses.
- Approximately 30 additional
  customers triggered the defect with
  at least one query during the
  affected period, but the responses
  did not surface semantically
  meaningful cross-tenant content.
- The remaining ~135 customers' tenants
  were not affected.

We notified all affected customers and,
proactively, all customers in our
service.

### What caused it

A refactor of our retrieval middleware
consolidated three separate retrieval
pathways into a unified orchestrator.
The unified orchestrator's tenant-
scoping check operated on context
information that was correctly
propagated for two of the three
pathway types but not, under specific
query patterns, for the third
(agentic workflows with compare-
across-sources sub-queries).

When the tenant context was not
present, the orchestrator's design
defaulted to "no tenant filter" —
returning chunks from across the
global index — rather than failing
closed (returning no results, or
raising an error).

Our test coverage for tenant isolation
did not include the specific pathway
+ sub-query combination that
triggered the bug. The bug deployed
to production undetected; our
staging environment did not surface
the bug because the triggering query
patterns were not represented in
staging traffic.

Three previous customer-support
tickets had reported responses
containing content their staff did
not recognize. These tickets were
triaged as model hallucination, the
common pattern for such reports.
This triage classification meant our
detection process did not flag the
underlying pattern, and the issue
went unrecognized internally until
the external red-team report.

### What we changed

We have implemented four independent
layers of tenant-scoping enforcement
across our retrieval architecture.
Any single layer's failure no longer
enables cross-tenant disclosure.

We have updated our engineering
standards to enforce default-deny
behavior on security-relevant code
paths and added static analysis
tooling that catches default-
permissive defaults.

We have created a new test category
for tenant-isolation testing,
covering every pathway through the
orchestrator and edge cases.

We have updated our support triage
to include cross-tenant content as
an explicit classification with
escalation to engineering.

We have engaged a specialized
AI-security firm to independently
verify our remediation.

### What we learned

The largest lesson is structural: a
refactor that consolidates code
paths is a security-relevant
change, even when its stated
purpose is internal restructuring.
We did not classify the original
refactor as security-relevant; we
will going forward.

The detection gap was as serious
as the bug itself. A multi-week
window between bug introduction
and detection is unacceptable for
a system whose product positioning
includes tenant isolation. The
detection-side improvements we
made are at least as important as
the architectural defense-in-
depth work.

### Available for questions

Customers with questions are
encouraged to contact [escalation
contact]. We will continue to
update affected customers
substantively as the verification
work progresses.

— Signed: [CAIRO] and [CTO]

---

## 3. Internal full version

> **NORTHRISE INTERNAL POST-MORTEM
> NR-2026-013**
> *Privilege-protected. For
> Northrise employees, Board, and
> authorized counsel. Not for
> external distribution.*

### Timeline

| Day | Time | Event |
|---|---|---|
| -42 | — | Release v4.18.0. Retrieval middleware refactor. |
| -38 | — | First production query triggers the bug; surfaced content judged unremarkable. |
| -28 | — | Customer ticket #45112 (financial-services customer): "we got an answer about a person we don't know." Triaged as hallucination by L2. |
| -17 | — | Customer ticket #45891 (healthcare): "GuardianGPT mentioned procedures we don't have." Triaged as hallucination. |
| -9 | — | Customer ticket #46342 (healthcare): "Response included an MRN format that's not ours." Triaged as hallucination. |
| -3 | — | Sentinel security team red-team exercise surfaces multiple cross-tenant fragments. Sentinel files support ticket #46901. |
| -3 | 17:30 | L2 triages #46901 as hallucination initially; analyst flagged for L3 review due to Sentinel's pattern of careful filing. |
| -2 | 09:00 | L3 review concludes content is not consistent with hallucination. Escalates to engineering on-call. |
| -2 | 14:00 | Engineering on-call replicates the pattern. Escalates to Head of Engineering. |
| -2 | 18:00 | Head of Engineering informs CTO. |
| -1 | 08:00 | CTO informs CAIRO. |
| -1 | 14:00 | CAIRO informs CEO. |
| -1 | 17:00 | Joint CAIRO/CTO/CISO investigation begins. |
| -1 | 22:00 | Initial bug-class identification: tenant-scoping defect in orchestrator. |
| 0 | 07:00 | Executive meeting. Tier-1 declaration. |
| 0 | 07:30 | Incident declaration. |
| 0 | 08:00 | Containment Stage 1 deployed (feature flag). |
| 0 | 14:00 | Executive team briefing. |
| 0 | 17:00 | Board chair informal notification. |

(... continues through Day 30.)

### Causal chain — multiple layers

**Proximate technical cause.** The
default-permissive tenant-scoping
behavior in the unified orchestrator
under missing tenant context.

**Architectural cause.** The
consolidation of three retrieval
pathways into one orchestrator
created a shared point of failure
that did not exist in the prior
architecture. The prior pathway-
specific tenant scoping had
independent failure modes; the
unified architecture concentrated
the risk.

**Development-process cause.** The
refactor was reviewed for
correctness and performance but
not specifically for security
behavior under edge cases. The
default behavior on missing
tenant context was not explicitly
considered.

**Testing cause.** Tenant-isolation
testing was implicit in the
existing test structure (pathway-
specific). The unified architecture
created a new failure mode that
required explicit tenant-isolation
tests, which did not exist.

**Deployment-process cause.** Staging
traffic did not represent agentic
workflow patterns. Canary rollout
in production did not surface the
issue because the triggering query
patterns were rare enough that no
triggering query occurred during
canary.

**Detection-process cause.** Three
customer tickets reporting symptoms
consistent with the bug were
triaged as hallucination. The L2
playbook did not include cross-
tenant content as a triage
category.

**Organisational pattern cause.**
Northrise's engineering culture
treats refactoring as "internal,
no security implications." The
refactor was classified accordingly.
This cultural pattern is the
systemic root.

### What went well

- Sentinel's CISO conversation
  Day 1 set the tone for all
  subsequent customer
  conversations. Honest, direct,
  forward-looking.
- The CAIRO/CTO/CISO collaboration
  worked: no boundary disputes;
  clear technical leadership on
  containment; clear external-
  posture leadership.
- General Counsel's privilege
  workstream was set up in the
  first 48 hours; investigation
  documentation has been
  protected throughout.
- Proactive Cohort-E notification
  produced positive customer
  reference data within the
  first week.
- Foundation-model vendor
  engagement was constructive
  and rapid.

### What didn't go well

- The three previous customer
  tickets misclassified as
  hallucination represent a
  6-week detection failure. This
  is the most serious finding.
- The CTO knew Day -2 14:00;
  the CEO was not informed
  until Day -1 14:00. This 24-
  hour gap is meaningful and
  is examined further below.
- The Day 0 customer-comms
  initial draft was too
  defensive in tone; revised
  before sending after CAIRO
  review.
- The Cohort-A high-exposure
  notification template was
  finalized later than ideal
  (Day 3 vs. Day 2); the
  template-finalization process
  was slower than the
  scope-analysis work.
- Investor communications
  drafting took longer than
  expected; investor letter
  finalized Day 8 vs. planned
  Day 5.

### The CTO-CEO timing question

The CTO knew the issue Day -2;
the CEO knew Day -1. The 24-
hour gap is examined here because
it would be normal in many
incident responses but matters
for our discipline going
forward.

CTO's reasoning Day -2: "I have
an early signal but not
confirmation; I am working with
the engineering team to
characterise the issue. I will
escalate when I have enough
to brief the CEO meaningfully."

CAIRO's view: this reasoning is
defensible but reflects a
specific organisational pattern
("don't escalate until you
understand"). The alternative
pattern — "escalate signals,
not confirmations" — would
have given the CEO and the
executive team more time to
prepare for Day 0.

We are not concluding that the
CTO was wrong. We are
concluding that we should
adopt the "escalate signals,
not confirmations" pattern
explicitly for incidents of
this class going forward.

### The pattern that recurs

The pattern: **default-
permissive defaults on
security invariants under
refactoring**.

This pattern recurs across many
software systems. The original
pathways had independent tenant
scoping; the refactor
consolidated them; the
consolidation created a single
point where a default-permissive
decision had broad security
impact.

Future refactoring that touches
identity, scoping, or
authorization should be
classified as security-relevant
by default. The static analysis
tooling enforces; the
engineering norm reinforces.

The post-mortem names the
pattern, not just the instance,
because the next variant of
this pattern is the next
incident we want to prevent.

### What we still don't know

- Whether any external party
  beyond the Sentinel red team
  was actively probing or
  exploiting the vulnerability.
  Investigation continues.
- The full downstream propagation
  of disclosed content (whether
  recipients further forwarded
  fragments).
- Whether other Northrise systems
  have similar default-permissive
  patterns. Audit in flight.

### What we anticipate may surface
later

- Additional customer reports as
  customers complete their own
  investigations.
- Regulatory inquiries triggered
  by customer-side
  notifications.
- Press coverage when one of
  the financial-services
  customers makes its required
  public disclosure.
- Possible subsequent finding
  of similar patterns elsewhere
  in the codebase.

---

## 4. Reasoning notes

- **Why two versions.** The
  public version serves customer
  trust and external posture; the
  internal version serves
  learning and Board governance.
  Conflating them produces
  either an unhelpful public
  document (too vague) or a
  damaging external one (too
  specific). The split is
  standard for mature incident
  post-mortems.
- **Why I named the CTO-CEO
  timing question explicitly.**
  mod-110 §3 blame-free framing
  does not mean ignoring
  organisational patterns.
  Naming the pattern without
  blaming the CTO is the
  discipline. The CEO needs to
  know; the engineering org
  needs to know; the pattern
  recurs across companies.
- **Why I named the L2 triage
  failure prominently.** The
  three-ticket detection gap is
  the largest single failure
  mode of the incident. Burying
  it in a footnote would
  misframe the learning.
- **Why the pattern (not just
  the instance) is in the public
  version.** Customers want to
  know what is being learned at
  a level that informs their
  trust assessment. "We fixed
  the bug" is insufficient;
  "we identified the underlying
  pattern that produced this
  bug class and are addressing
  it" is the right depth.
- **What I would do
  differently.** I might have
  separated the L2 triage
  failure into its own
  detection-side post-mortem
  document. It deserves
  individual treatment; folding
  it into the main post-mortem
  buries it relative to its
  importance.

---

Maintained by [Girish Nair](https://github.com/garynair)
