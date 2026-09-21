# Deliverable 01 — Program Charter — Reference Solution

## 1. Solution overview

A 3-page Northrise AI Program Charter. Operating
model: **centralised with hub-and-spoke
elements** for the three product lines.
Standards anchor: NIST AI RMF (operating) + ISO
42001 (certification target). Two governance
bodies: AI Risk Council (CEO-chaired) + AI Review
Board (CAIRO-chaired). Risk-appetite-pending
posture: operate against existing enterprise
risk appetite (which exists in Northrise's
Series C investor materials) plus this charter's
specific commitments until the formal appetite
statement is adopted.

---

## 2. The charter

> **NORTHRISE AI — AI PROGRAM CHARTER v1.0**
> *Adopted by the CEO. Pending Board
> acknowledgment.*

### Mission

This program exists to ensure that Northrise's
AI products, the agents customers build on
Northrise infrastructure, and Northrise's
internal AI usage all behave in ways Northrise
can defend — to customers, to regulators, and
to ourselves. Success is the absence of
material surprises and the presence of a risk
posture Northrise can articulate clearly to
enterprise customers, regulators, and Series D
investors.

### Scope

In scope: (a) all AI/ML capabilities Northrise
operates internally; (b) AI/ML capabilities in
Northrise's three products (Agent Platform,
Analytics, Studio); (c) the *control surface*
of customer-deployed agents — specifically the
controls Northrise provides to customers
operating agents on Northrise infrastructure;
(d) Northrise's AI vendor relationships
(foundation-model providers, etc.).

Out of scope: (a) customer-side configuration
choices on customer-deployed agents — these are
customer's responsibility (Northrise provides
the controls; customers configure them); (b)
deterministic non-ML rule engines used in
Northrise products; (c) generic SaaS infrastructure
governance (covered by the existing security
program).

### Authority

The Chief AI Risk Officer has:

- **Decision authority** to approve or block
  release of any in-scope AI capability where
  the AI Review Board has flagged material
  concerns.
- **Standard-setting authority** for all
  AI-specific policies, controls, and review
  processes.
- **Recommendation authority** on product
  roadmap, vendor selection, and engineering
  architecture; the relevant function holds the
  decision.

Disagreements between the CAIRO and a product/
engineering leader unresolved at the AI Review
Board escalate to the AI Risk Council. Disagreements
at the Council escalate to the CEO. Material
risk matters route to the Board through the
Audit Committee per Northrise's existing Board
process.

### Structure

The CAIRO reports to the **CEO**. Dotted lines to
General Counsel (for regulatory engagement) and
CFO (for budget).

Peer-role boundaries:

- **CTO** owns product engineering; CAIRO sets
  the AI-specific governance requirements
  engineering operates against.
- **Head of Security** owns infrastructure
  security including AI-system security; CAIRO
  owns AI-specific governance (per mod-107 §5
  pattern, scaled for Northrise).
- **General Counsel** owns legal posture; CAIRO
  owns AI-program substantive content for
  regulator engagement (per mod-109 Ex-05
  pattern, scaled for Northrise).

Governance bodies:

- **AI Risk Council.** Chaired by the CEO;
  members are CAIRO, CTO, Head of Security, GC,
  CFO. Quarterly. Reviews AI risk register,
  ratifies AI Review Board tier classifications,
  hears escalations.
- **AI Review Board.** Chaired by the CAIRO;
  members are the product heads of Agent
  Platform, Analytics, Studio, plus the AI Risk
  Lead and a senior engineering representative.
  Bi-weekly. Reviews material AI-related
  releases, classifies by tier, requires named
  controls, approves or blocks.

Operating model: **centralised** for the CAIRO
function and the standards work; **hub-and-spoke**
for execution — the CAIRO function operates as
hub; product-line representatives in the AI
Review Board operate as spokes.

### Standards alignment

The program operates against **NIST AI RMF 1.0**
as the operating framework — its function
structure (GOVERN, MAP, MEASURE, MANAGE) maps
cleanly onto Northrise's existing engineering
discipline. The program **pursues ISO 42001
certification** as the external assurance
target with the intent to achieve initial
certification by year-2.

For specific use cases falling under sector
regulation (financial-services customers
deploying agents that affect credit decisions;
healthcare customers using Analytics on PHI),
the program operates the additional sector-
specific overlay through customer-deployment
guidance and customer-contractual obligations.

### Risk-appetite posture pending formal adoption

Until the AI Risk Appetite Statement is adopted
by the Board (Deliverable 04 in the 90-day plan),
the program operates under the following
posture:

- No AI product capability deploys that takes
  on customer-affecting risk Northrise's
  existing security and reliability posture
  does not already absorb.
- The CAIRO drafts the formal appetite statement
  within 45 days for Board consideration.
- Anything materially novel (e.g., new
  autonomous-agent capabilities; new
  customer-data-processing patterns) is held
  pending the formal statement.

### First-90-day deliverables

The seven deliverables of this 90-day arc:

1. This charter (Deliverable 01) — by day 10.
2. AI risk taxonomy (Deliverable 02) — by day
   18.
3. Year-1 operating plan (Deliverable 03) — by
   day 25.
4. AI risk appetite statement (Deliverable 04) —
   by day 45.
5. Trust architecture build/buy decision
   (Deliverable 05) — by day 60.
6. Compliance operations baseline (Deliverable
   06) — by day 75.
7. First quarterly board report (Deliverable
   07) — by day 90.

The CAIRO commits to these dates. The Board Risk
Committee review on day 90 will receive
Deliverable 07 as the substantive update.

— end charter —

---

## 3. Reasoning notes

- **Why centralised with hub-and-spoke
  elements.** Northrise's three product lines
  have different governance needs, but the
  CAIRO function is too small in year 1 to be
  truly federated. Pure centralised would
  ignore product-line specifics; pure
  hub-and-spoke requires year-2 maturity. The
  hybrid is the realistic year-1 posture.
- **Why CEO-chaired AI Risk Council and not
  CAIRO-chaired.** Northrise's CEO appointed
  the CAIRO substantively; positioning the Risk
  Council as CEO's body reinforces the
  authority. As Northrise grows and a CRO is
  hired, the chair will likely transition.
- **Why two governance bodies and not more.**
  Same restraint discipline as mod-101 Ex-02
  reference. Two bodies — one strategic
  (Council), one operational (Review Board) —
  is the minimum for enterprise oversight
  + per-deployment control at Northrise's
  current scale.
- **What this charter deliberately doesn't
  do.** Establish authority over customer-
  side agent configuration. Northrise provides
  controls; customer configures. Trying to
  govern customer-side configuration would be
  beyond Northrise's contractual reach.
- **What I would do differently.** I might
  have named the dotted-line relationship
  with the Head of Security more strongly —
  Northrise's security organisation is
  unusually capable for its size, and a
  stronger dotted line might pay off in
  year 2.

---

Maintained by [Girish Nair](https://github.com/garynair)
