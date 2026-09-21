# Deliverable 02 — Scope and Root-Cause Analysis — Reference Solution

## 1. Solution overview

Scope: 47 customers had at least one
production query during the vulnerability
window that triggered the bug; 9 of those
queries surfaced cross-tenant content
that could meaningfully be interpreted by
a user; 3 of those 9 are high-exposure
(meaningful customer-data fragments
disclosed). Root cause: a refactor of the
retrieval middleware Day -42 introduced
an implicit-tenant assumption that broke
under a non-default query pattern. Five
systemic causes named including the
detection-gap pattern (3 customer
tickets in the prior 6 weeks misclassified
as model hallucination).

---

## 2. Scope analysis

### Methodology

Forensic log analysis on the retrieval
middleware between Day -42 and Day 0.
Three-stage filter:

1. **Stage A — Queries that triggered the
   bug.** Pattern-match on the query
   characteristics known to trigger
   incorrect tenant-scoping. Resulting
   set: 2,847 queries from 47 distinct
   customer tenants.
2. **Stage B — Queries that surfaced
   cross-tenant content.** Of the 2,847,
   determine which actually surfaced
   chunks from outside the requesting
   tenant. Filtering: tenant-ID
   metadata comparison on retrieved
   chunks. Resulting set: 312 queries
   surfaced at least one cross-tenant
   chunk.
3. **Stage C — Queries that surfaced
   meaningful cross-tenant content.**
   Of the 312, determine which surfaced
   content semantically meaningful
   enough that the user could have
   interpreted it as customer data.
   Manual review of the chunk content
   (with privilege protections).
   Resulting set: 9 queries.

### High-exposure cases

Of the 9 meaningful-disclosure cases:
- 3 cases disclosed identifiable PII
  (names + account numbers) from one
  customer to another.
- 2 cases disclosed PHI fragments
  (clinical narrative) between
  healthcare customers.
- 1 case disclosed financial-product
  pricing detail between competing
  financial-services customers.
- 3 cases disclosed less specific
  fragments (snippets without clear
  identifiers).

### Customer cohorts

- **High-exposure (Cohort A):** 7
  customers — recipients of the 9
  meaningful-disclosure cases. Two of
  the cases involve the same recipient
  customer (Sentinel Mutual; that's
  why their red team caught it).
- **Source-exposure (Cohort B):** 8
  customers — sources of the data
  fragments disclosed. Some overlap
  with Cohort A.
- **Triggered-but-not-meaningful
  (Cohort C):** ~30 customers — queries
  triggered the bug but surfaced no
  meaningful cross-tenant content.
- **Triggered-but-no-disclosure (Cohort
  D):** ~10 customers — queries
  triggered the bug but produced no
  cross-tenant content (retrieval
  returned nothing or only same-tenant
  chunks despite the bug).
- **Not affected (Cohort E):** 133
  customers — no queries during the
  vulnerability window triggered the
  bug.

### Time window

- Bug introduced: Day -42 deployment.
- Bug detected: Day -3 by Sentinel
  red team.
- Bug contained: Day 0 08:00 UTC.
- **Total vulnerability window: 42
  days.**

## 3. Root-cause analysis

### Proximate technical cause

A refactor of the retrieval middleware
component `retrieval-orchestrator` was
deployed Day -42 as part of release
v4.18.0. The refactor consolidated three
retrieval pathways (chat, agentic, batch)
into a single orchestrator.

The bug: the orchestrator's tenant-
scoping check operated on a context
object that was correctly populated
during the chat pathway but, under
agentic workflows that included a
specific sub-query type ("compare-across-
sources" sub-queries), the context
object was not propagated to the
orchestrator. The orchestrator's
tenant-scoping check observed a missing
tenant-ID field and (per the new code's
default behavior) defaulted to "no
tenant filter" — returning chunks from
the global vector index space.

The new code had a default-permissive
behavior on missing tenant-ID rather
than default-deny.

### Systemic causes (per mod-110)

**Systemic cause 1 — Default-permissive
on critical security invariants.**
The refactor introduced default behavior
on tenant-scoping that was permissive
rather than restrictive. Engineering
norm has been default-deny on security
controls; this refactor broke the norm
without challenge in code review.

**Systemic cause 2 — Tenant-isolation
testing inadequacy.** The test suite for
the orchestrator tested chat pathway
tenant-scoping (which worked) but did
not test agentic pathway with the
specific sub-query type that triggered
the bug. Test coverage for tenant
isolation was incomplete; this gap was
not previously visible because the
prior architecture had pathway-specific
scoping that did not depend on the
shared orchestrator path.

**Systemic cause 3 — Detection-side
gap.** Three customer tickets in the
6-week window mentioning unexpected
content were triaged as model
hallucination by L2 support. The L2
playbook did not include a check for
cross-tenant content patterns; the
"hallucination" classification was the
default for unexplained content. This
gap meant the issue went undetected by
Northrise for the full vulnerability
window — the issue was first surfaced
externally by a customer red team.

**Systemic cause 4 — Refactor risk
assessment inadequacy.** The v4.18.0
refactor was treated as an internal
restructuring rather than a security-
relevant change. Security review did
not flag it. The CISO has indicated
that the refactor would have warranted
explicit security review under a
different classification scheme.

**Systemic cause 5 — Customer-side
observability gap.** Affected customers
had no real-time signal that their
queries had returned out-of-tenant
content. Without a customer-side
self-service investigation capability,
detection depended entirely on the
recipient noticing the surfaced
content.

### Why testing did not catch it

Three reasons:

- **Test gap (per systemic cause 2).**
  No specific test for agentic +
  compare-across-sources + tenant
  scoping.
- **Staging coverage gap.** Staging
  load patterns did not include the
  specific query pattern. Staging
  tested chat-pathway tenant isolation,
  not agentic-pathway.
- **Production canary coverage gap.**
  The canary rollout for v4.18.0
  ran for 48 hours on 10% of traffic;
  the specific query pattern was rare
  enough that no triggering query
  occurred during the canary.

## 4. What we don't know

- The full historical view of cross-
  tenant content surfaced — log
  retention covers the full
  vulnerability window with high
  confidence; we are confident in the
  9-meaningful-disclosure count but
  cannot fully exclude additional
  cases below the manual-review
  threshold.
- Whether any external party (beyond
  Sentinel's authorized red team) was
  actively exploiting the
  vulnerability. CISO investigation
  ongoing; no evidence of malicious
  exploitation as of Day 15.
- Downstream propagation of disclosed
  content. We know what was surfaced
  in responses; we don't know whether
  recipients further propagated the
  content (forwarded to colleagues,
  saved in external systems).

## 5. Confidence levels

- **Stage A (queries that triggered):**
  High confidence. Log-based
  determination on well-defined
  pattern.
- **Stage B (queries that surfaced
  cross-tenant content):** High
  confidence. Tenant-ID metadata
  comparison is mechanical.
- **Stage C (meaningful disclosure):**
  Medium-high confidence. Manual
  review introduces judgment;
  threshold for "meaningful" is
  documented but the line between
  Cohort A (high-exposure) and Cohort
  C (triggered-but-not-meaningful) has
  borderline cases.
- **Affected-customer cohorting:** High
  confidence at the cohort boundaries;
  lower confidence on counts within
  cohorts (cohort membership can
  change as scope analysis continues).

---

## 6. Reasoning notes

- **Why the three-stage filter
  methodology.** Separating "triggered
  the bug" from "surfaced cross-
  tenant content" from "surfaced
  meaningful content" lets customer
  notification be calibrated. A
  customer who triggered the bug
  but did not receive meaningful
  cross-tenant content needs to know
  that — and the framing matters to
  the relationship.
- **Why the systemic-cause section is
  five items rather than one.**
  mod-110 §3 single-cause analysis
  ("the bug" alone) misses the
  detection gap, the testing gap, the
  refactor-review gap, and the
  customer-observability gap. Single-
  point fixes invite the next variant.
- **Why I named the L2 triage
  failure (systemic cause 3)
  explicitly.** Honesty discipline.
  Three customer tickets misclassified
  as hallucination is a real
  detection failure; pretending it
  was reasonable triage is
  performative. The L2 playbook will
  be updated per Deliverable 05.
- **Why I noted what we don't know
  about external exploitation.**
  Customer notification, regulatory
  notification, and the post-mortem
  all depend on this. The honest
  answer is "no evidence as of Day
  15" — not "no exploitation
  occurred."
- **What I would do differently.** I
  might have run the Stage-C manual
  review with a second independent
  reviewer to reduce judgment risk on
  the cohort boundary. Privilege
  considerations made this awkward;
  the trade-off was made consciously
  but could go the other way.

---

Maintained by [Girish Nair](https://github.com/garynair)
