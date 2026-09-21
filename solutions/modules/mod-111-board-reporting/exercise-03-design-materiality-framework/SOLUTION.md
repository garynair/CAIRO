# Exercise 03 — Materiality Framework — Reference Solution

## 1. Solution overview

A 3-page materiality framework for **Tessera Bank**
calibrated to its $25B regional-bank scale. Five
dimensions with specific quantitative thresholds.
Five scenarios applied with one explicit boundary-
case escalation (Scenario D — single customer
complaint requires §4.5 escalation given the
classification ambiguity).

---

## 2. The framework

> **TESSERA BANK — AI MATERIALITY FRAMEWORK v1.0**
> *Owned by Chief AI Risk Officer. Approved by AI Risk
> Council and Audit Committee.*

### Definition and approach

Materiality for AI matters at Tessera is the
threshold at which a matter is important enough
to require Board attention. It is a judgment, not
a calculation, but is structured by the
framework below to be consistent and defensible.

This framework **structures judgment**, it does
not replace it. The boundary-case escalation
(§4.5) ensures that judgment-laden cases are
escalated for joint disposition rather than
handled unilaterally.

This framework is **subordinate to** Tessera's
enterprise materiality framework and adds AI-
specific overlays.

### The dimensions

The five §4.2 dimensions:

1. **Financial.**
2. **Regulatory.**
3. **Reputational.**
4. **Operational.**
5. **Strategic.**

### Calibrated thresholds for Tessera ($25B regional bank)

| Dimension | Threshold | Examples |
|---|---|---|
| Financial | > $5M one-time impact OR > 0.2% of annual revenue | $5M+ customer remediation; $X+ AI-related fine; AI-related write-down or charge |
| Regulatory | Any regulator-initiated action; EU AI Act Art. 73 trigger; CFPB inquiry; NYDFS examination question | Formal letter, examination request, settlement opening |
| Reputational | Public exposure of an AI-related issue; potential exposure where > 1,000 customers affected; sustained media attention | Press coverage; social media wave; customer-segment-wide pattern |
| Operational | AI system outage > 4 hours; trust-architecture failure; cross-LOB AI incident | Trust gate outage; LLM vendor outage affecting multiple LOBs; widespread bias monitoring trigger |
| Strategic | Material change in AI program direction; major vendor change; material capability expansion or retirement | Decision to enter/exit a major AI use case; primary LLM vendor replacement; major partnership |

The thresholds are calibrated to Tessera's $25B
scale. They are recalibrated annually as part of
the appetite statement review and on material
scale changes.

### Decision examples

**Scenario A — Site H-12-style bias incident
pattern at Tessera.**

A pattern of bias-monitoring threshold crossings
at one Tessera location, affecting approximately
400-500 customer interactions.

*Material? **Yes — Regulatory + Reputational.***
The pattern triggers EU AI Act Art. 73
notification (if any EU-resident customers
affected) and potentially CFPB inquiry; the
customer-affected count meets the reputational
threshold. *Disposition:* Board pack inclusion;
off-cycle briefing to Board Risk Committee
chair within 5 business days.

**Scenario B — Trust gate outage of 2 hours
affecting one LOB.**

*Material? **No.*** Outage duration under the
4-hour threshold; affects one LOB only. *Disposition:*
Internal incident response per mod-110;
included in next quarterly report's appendix
incident summary; not a board-level matter
unless it recurs or extends.

**Scenario C — Vendor LLM swap discovered with
required notice received.**

*Material? **No.*** The vendor provided
contractual notice; the response is per the
vendor management process. *Disposition:*
Internal AI Risk Council briefing; included in
next quarterly report's material-changes
section.

**Scenario D — One customer complaint about
AI-driven adverse action.**

*Material? **Boundary case — escalate per §4.5.***

The complaint's significance depends on facts
not yet known: is it a pattern (other
complaints?) or isolated? Is the complaint
substantively about the model's behaviour or
about the explanation? Does the complaint
involve a protected class? Has the customer
threatened legal action or regulatory
complaint?

Until these facts are clarified, the matter is
neither clearly material nor clearly non-
material. *Disposition:* Per §4.5 — brief CRO
within 5 business days; brief Board Risk
Committee chair within 10 business days;
disposition decision then made.

**Scenario E — 6pp sensitivity gap in monitoring
for one weekly cycle (single data point, no
trend).**

*Material? **No.*** Single-week data point
without trend; weekly cycle variation is
expected. *Disposition:* Routine monitoring
review per mod-109 Ex-02 pattern. Becomes
material if it sustains for two consecutive
weeks or grows.

### Boundary-case escalation process (specific to Tessera)

Per the §4.5 framework adapted for Tessera:

1. **Within 5 business days** of a matter being
   recognised as boundary, the CAIRO function
   briefs the CRO.
2. **Within 10 business days**, the CAIRO function
   briefs the Board Risk Committee chair.
3. **Disposition by day 15:** include in next
   regular board pack; raise off-cycle if
   warranted; or stand down with documented
   reasoning.
4. All escalation events are recorded in the
   program's evidence ledger.

### Calibration cadence

- **Annual recalibration** as part of the risk
  appetite statement review.
- **Trigger-based recalibration** on material
  scale change (acquisition, divestiture,
  market expansion).
- **Quarterly review** by the AI Risk Council
  to confirm thresholds remain calibrated; no
  formal Board action required unless thresholds
  change materially.

---

## 3. Reasoning notes

- **Why I named Scenario D as boundary.**
  Single complaints can be isolated noise or
  the first signal of a systemic issue. The
  §4.5 escalation gives the CAIRO function 10
  business days to develop facts before
  classifying — preserving optionality without
  committing to either material or non-
  material call prematurely.
- **Why I calibrated to $25B.** Materiality
  thresholds at a $1B firm and a $100B firm
  differ by orders of magnitude. Calibrating to
  Tessera's specific scale gives the framework
  operational meaning.
- **Why I named the appetite statement
  subordination explicitly.** Mirroring the
  appetite statement's enterprise-framework
  subordination keeps the documents aligned
  and prevents conflicts later.
- **What this framework deliberately doesn't
  do.** Define materiality for non-AI matters —
  that's Tessera's enterprise framework. The AI
  framework operates within it.
- **What I would change.** Add a *consequence
  weighting* — some materiality crossings are
  more important than others; a multi-
  dimension crossing (financial + regulatory)
  is more material than a single-dimension
  crossing. The current framework treats all
  crossings as equal-material; a v2 would
  weight.

---

Maintained by [Girish Nair](https://github.com/garynair)
