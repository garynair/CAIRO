# Scenario — Northrise AI, GuardianGPT Incident

## Northrise AI (recap from Capstone 301)

Northrise is a 250-person AI SaaS company.
Flagship product GuardianGPT is a
multi-tenant LLM-based assistant deployed
by enterprise customers (mostly financial
services, healthcare, and legal-sector
companies) to handle internal knowledge
queries, customer-service automation, and
agentic workflows on the customer's
documents and data.

GuardianGPT is built on a foundation model
(vendor-supplied) with retrieval-augmented
generation against per-tenant indexed
content. Customers upload documents that
get embedded and stored in per-tenant
vector indexes. At query time, the system
retrieves relevant context from the tenant's
index and synthesizes a response.

## The product context

GuardianGPT has roughly **180 enterprise
customers** in production. Top customers
include several Fortune 500 financial
institutions and healthcare networks. Total
ARR: ~$140M. The product is positioned as
"enterprise-grade tenant isolation" — a
specific contractual and marketing claim.

The data customers entrust to GuardianGPT
includes:
- Customer support transcripts.
- Internal knowledge bases.
- Some customers: PHI (HIPAA-protected).
- Some customers: financial records, trade
  data, customer PII.
- Some customers: legal documents (some
  subject to privilege).

## The trigger

3 days ago (Day -3), a customer's security
team — Sentinel Mutual's CISO office —
filed a support ticket. They had observed
GuardianGPT, in response to crafted prompts
during their red-team exercise, surface
content fragments that *did not appear to
originate from Sentinel's own document
corpus*. Some fragments looked like
employee names, account numbers, and
customer-service-transcript excerpts that
Sentinel could not source to their own
content.

The support ticket was triaged to L2; L2
flagged the engineering on-call. On-call
escalated to the Head of Engineering Day
-2. Head of Engineering escalated to CTO
and you (CAIRO) Day -1. CEO informed Day -1
evening.

Initial investigation overnight on Day -1
suggests:
- Three other customers have raised related
  concerns in tickets over the past two
  weeks (previously triaged as model
  hallucination).
- The pattern is real: certain prompts
  cause the retrieval layer to fetch
  documents from index segments that
  should not be accessible to the
  requesting tenant.
- Initial theory: a code change to the
  retrieval middleware deployed 6 weeks
  ago introduced a tenant-scoping bug. The
  bug affects a subset of query patterns.

## Day 0 — today

The CEO calls a 7am all-hands of senior
leadership. You (CAIRO) are appointed
incident commander.

The first 24 hours are about classification,
containment, and triage. The 30-day arc
plays out from there.

## Constraints

- Customer trust is the asset at risk.
  The mishandling of disclosure is worse
  than the bug itself.
- Several customers have specific
  contractual notification obligations
  (within hours or days of confirmed
  incident).
- HIPAA-covered customers trigger
  Business Associate notification
  obligations. Financial-services
  customers trigger GLBA / state breach
  notification considerations. EU
  customers trigger GDPR Art. 33 (72-hour
  authority notification) and Art. 34
  (data subject notification).
- The press has not picked it up. This
  is unstable; some customer security
  teams may disclose.
- Northrise is at Series D ($380M
  valuation) and is pre-IPO. Material
  incident disclosure obligations may
  apply to investors.
- The foundation-model vendor is not the
  cause but may be relevant to the
  remediation conversation.
- Existing customers are not your only
  audience. Prospective customers in
  pipeline may see press coverage.
- 30-day arc to the close-out memo.
  Investigation will not be fully
  complete in 30 days; the memo addresses
  what is known and what is in flight.

## Who's at the table

- **CEO** — ultimately accountable;
  resource and decision authority.
- **CAIRO (you)** — incident commander.
- **CTO** — technical investigation,
  containment, remediation.
- **CISO** — security investigation;
  threat model assessment.
- **General Counsel** — legal exposure;
  privilege protection; notification
  drafting.
- **Head of Customer Success** — customer
  communication coordination.
- **VP Communications** — external
  comms; press posture.
- **Head of Compliance** — regulatory
  notification.

The Board has been informed informally;
formal Board update at Day 3.

## You have access to

- mod-107 (CAIRO × CISO boundary; relevant
  to the security investigation split)
- mod-110 (incident response and
  systemic-cause discipline)
- mod-108 (privacy, GDPR, HIPAA, breach
  notification)
- mod-109 (AI Acceptable Use, but more
  relevant: compliance pathways)
- mod-111 (Board reporting)
- mod-112 (closing-discipline framing)
- mod-104 (CAIRO × MRM not directly
  applicable but boundary pattern is)

## What the work is

Lead the 30-day response producing six
deliverables plus the synthesis memo. The
deliverables are real artifacts (regulatory
notifications, customer communications,
post-mortem) — not internal-CAIRO-only
planning.

---

Maintained by [Girish Nair](https://github.com/garynair)
