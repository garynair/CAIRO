# Exercise 05 — Operating-Model Recommendation Memo — Reference Solution

## 1. Solution overview

The reference memo recommends **hub-and-spoke** for
**Kerridge Industries**, with the hub in the Chief Risk
Officer's organization (alongside the newly-appointed CAIRO)
and spokes in each business unit's existing risk function.
The recommendation is justified by Kerridge's combination of
business-unit diversity (four very different regulatory
profiles), shared enterprise-risk machinery (the CRO already
consolidates), and the practical impossibility of a
centralized function carrying the regulatory mass of
Aerospace + Healthcare + Financial in one team.

---

## 2. The memo

> **TO:** Board Risk Committee
> **FROM:** Chief AI Risk Officer
> **SUBJECT:** Operating Model for Enterprise AI Governance
> **PAGES:** 3

I recommend a **hub-and-spoke operating model** for
Kerridge's enterprise AI governance program. The hub sits in
the Chief Risk Officer's organization (where I report). The
spokes are AI risk partners embedded in each of Kerridge's
four business units — Aerospace, Healthcare, Materials, and
Financial — reporting solid-line to the business-unit risk
lead and dotted-line to the hub. This memo lays out why,
what was rejected, what the strongest objection is, and the
first-year roadmap.

### Why hub-and-spoke

Kerridge has a regulatory diversity problem that resists
both centralized and federated solutions. Aerospace lives
under FAA/EASA airworthiness; Healthcare lives under FDA and
EU MDR/AI Act; Financial lives under state insurance
regulation and SR-11-7-flavored MRM; Materials has a
forecasting model and no regulator-specific AI exposure.
Trying to operate this from a single central team would
require the team to maintain working depth across four
regulatory regimes simultaneously — a hiring profile that
does not exist in the market. Letting each business unit do
its own governance, fully federated, would produce four
incompatible programs and a Board view that does not roll
up. Hub-and-spoke gives us a consistent enterprise framework
(authored at the hub, anchored on **ISO/IEC 42001:2023
§5 — Leadership** and **NIST AI RMF**), with regulatory
depth in the business units.

### Why centralized was rejected

A central function could be staffed initially but would face
a hard ceiling within 18 months. Centralization works best
where one regulator dominates (insurance-only, banking-only)
or where the AI exposure is narrow. Kerridge's diversity
means the central team would either be permanently
under-staffed against the regulatory mass, or would become
the rate-limiting step for every business unit's deployment
cycle. The Healthcare arm alone — one FDA-cleared algorithm
plus two pre-submissions — justifies a dedicated AI
governance presence in the business unit; centralizing that
into a corporate team would slow Healthcare's submission
cadence and create a single point of failure for FDA
correspondence.

### Why federated was rejected

Fully federated would produce four good programs and zero
enterprise view. The Board has explicitly asked for an
enterprise risk posture; federated cannot deliver one in any
honest form. It would also leave Materials — which does not
have its own risk function — without anywhere for its single
AI system to live, and would force me to either embed in
Materials directly (turning the CAIRO into Materials' AI
governance team) or to leave Materials uncovered.

### The strongest objection — steel-manned

The strongest objection to hub-and-spoke is that it
*requires* clean management of the dotted-line / solid-line
tension at the spokes. A spoke who reports solid to the
business unit's risk lead and dotted to me will, in any
case of disagreement, default to the solid-line. If that
default is allowed to set the tone of the program, the spoke
becomes a business-unit advocate rather than a corporate
risk function, and the central program becomes ceremonial.
This is a real risk and it is the failure mode this
recommendation is most exposed to.

Two structural mitigations: (1) my approval is required for
the *hiring* of every spoke and for their *annual
performance review*; (2) the dotted line includes a formal
escalation path where a spoke can route any case directly
to the hub without business-unit-lead intermediation, with
the hub then carrying the case to the AI Risk Council. If
either mitigation is removed, this recommendation should be
revisited.

### First-year roadmap

**Days 0–90.** Hub staffed (three roles: policy lead, risk
lead, regulatory engagement lead). Single AI policy
hierarchy and a four-standard set (development, third-party,
monitoring, incident response) authored at the hub. AI
system inventory complete across all four business units. AI
Risk Council operational with monthly cadence.

**Days 90–180.** Spokes appointed in Aerospace, Healthcare,
and Financial. Materials covered by the hub directly until
or unless its AI exposure grows. AI Review Board operational
with bi-weekly cadence. First quarterly Board Risk Committee
AI report delivered (in draft form for ratification).

**Days 180–365.** Spoke-hub working rhythm established and
measured. ISO 42001 readiness assessment commissioned (third
party). Healthcare's two pre-submission algorithms processed
through the program as the first regulatory-grade test.
EU AI Act high-risk classification work begun for any
in-scope Healthcare and Aerospace systems.

### Indicators we will report at the 12-month mark

- Number of in-scope AI systems with completed impact
  assessments, by business unit. *(Coverage indicator.)*
- Time-from-intake-to-decision at the AI Review Board, by
  decision type. *(Operational indicator. Watch for
  degradation.)*
- Fraction of AI Review Board decisions that the spoke
  recommended one way and the hub another. *(Independence
  indicator. Either-side-always-wins is a problem.)*
- Number of in-scope deployments that were *blocked* or
  required material modification at the Review Board.
  *(Substance indicator. Always-zero means rubber-stamp;
  always-many means program is mis-calibrated or the model
  pipeline upstream is broken.)*
- Days from incident detection to incident-response launch,
  for any AI-related incident. *(Speed indicator.)*
- Number of unprompted regulator communications received.
  *(External-perception indicator; a noisy regulator
  signals program weakness.)*

The Board should expect the first year to show some
indicators in their wanted range and some not. The honest
metric I will care about most by month 12 is the
*independence indicator* — whether the spokes and the hub
are reaching genuinely different conclusions some of the
time. If they always agree, the structure is not yet doing
what hub-and-spoke is supposed to do.

— end memo —

---

## 3. Reasoning notes

- **Why I anchored to ISO 42001 §5 rather than NIST.**
  ISO 42001 §5 is the cleaner anchor for *Leadership*
  specifically, which is the question the Board is being
  asked to ratify. NIST AI RMF is the operating framework
  for the program; ISO is the leadership-and-structure
  anchor. Both are cited; ISO is named first.
- **Why I named indicators that can fail.** A board memo
  that promises only-good news in the first year is being
  written for the wrong audience. The risk committee will
  trust a memo more if it names what failure looks like.
- **Why hub-and-spoke despite Kerridge's smallish scale.**
  $14B revenue and four very different regulatory regimes
  is the regulatory complexity profile of a larger
  organization. Org-design choice should follow regulatory
  complexity, not headcount.
- **Where this recommendation could be wrong.** If Kerridge
  decides to divest Healthcare in the next 24 months (no
  signal of this; hypothetical), the regulatory complexity
  drops dramatically and centralized becomes defensible.
  The recommendation should be re-evaluated at any major
  portfolio change.
- **A federated counter-argument I respect.** The strongest
  argument for fully federated would be that each business
  unit's risk lead is closer to that BU's regulator and that
  the hub adds latency without value. The counter is the
  enterprise-view obligation: the Board cannot consolidate a
  federated program. If the Board were willing to live
  without an enterprise view, the federated argument would
  be stronger; they are not, so it is not.

## 4. Failure-mode check (from lecture notes §6)

- *Governance theatre?* Indicators include
  Board-actually-blocked counts. Risk is real but bounded.
- *Control sprawl?* Four-standard hierarchy. Risk is low.
- *Compliance-only?* Memo language ("a noisy regulator
  signals program weakness") is risk-framed, not
  compliance-framed.
- *Vendor capture?* No vendor named in the
  recommendation. Indicators are vendor-agnostic.

---

Maintained by [Girish Nair](https://github.com/garynair)
