# Exercise 05 — Annual Program Self-Assessment — Reference Solution

## 1. Solution overview

End-of-year-1 self-assessment for **Halverston
Capital**. NIST AI RMF maturity at *Developing*
(Level 2) on GOVERN/MAP/MEASURE, *Initial* (Level
1) on MANAGE due to the third-party governance
gap from mod-109 Ex-03. Honest about
under-investment in vendor risk capability and
over-investment in tabletop exercises. Year 2
focuses on closing the third-party gap and
deepening cross-LOB integration.

---

## 2. The self-assessment

> **HALVERSTON CAPITAL — AI PROGRAM ANNUAL
> SELF-ASSESSMENT (YEAR 1)**
> *Author: Chief AI Risk Officer. For: AI Risk
> Council, Audit Committee. Date: [date].*

### Section 1 — Program maturity

Rated against NIST AI RMF maturity model
(Levels 1-5: Initial, Developing, Defined,
Managed, Optimizing):

**GOVERN — Level 2 (Developing).**

- *Evidence:* AI Risk Council operates monthly
  with documented decisions; AI Review Board
  bi-weekly; policy hierarchy in place; year 1
  of operation gives 12 months of operating
  history.
- *Gap to Level 3 (Defined):* Repeatable
  processes are in place but not yet
  formalized across all LOBs identically;
  cross-LOB integration of GOVERN is partial.

**MAP — Level 2 (Developing).**

- *Evidence:* AI system inventory complete;
  impact assessments performed on all Tier 1
  systems; risk taxonomy in operation.
- *Gap to Level 3:* Impact assessment template
  formalisation pending (per mod-109 Ex-03 gap
  analysis); subgroup-discovery practice not
  yet repeatable across systems.

**MEASURE — Level 2 (Developing).**

- *Evidence:* Bias monitoring operational on
  Tier 1 systems; trust-architecture metrics
  flowing; evidence cadence per mod-109 Ex-02
  pattern operating.
- *Gap to Level 3:* Cross-system measurement
  not yet standardised; some Tier 2 systems
  operate with manual monitoring.

**MANAGE — Level 1 (Initial).**

- *Evidence:* Treatment plans documented for
  Tier 1 risks; residual risk acceptance
  pattern (per mod-103 Ex-04) in use; vendor
  AI risk treatment partial.
- *Gap to Level 2:* The third-party AI
  governance gap (from mod-109 Ex-03) limits
  MANAGE maturity. AI vendor assessment
  overlay is not yet operational.

**Overall:** Mid-developing range, with vendor
governance the binding constraint.

### Section 2 — Operating effectiveness

**Are the controls operating?** Mostly yes, with
specific gaps.

*Evidence:*

- **The first cross-LOB tabletop** (per
  mod-110 Ex-03 pattern) demonstrated that
  the team can coordinate effectively across
  LOBs. Scored 14/20 on the scoring rubric
  — acceptable but with specific findings.
- **The trust architecture** (per mod-106 Ex-05
  partner pattern) is operational. The
  audit-ledger evidence flow is mature.
- **The near-miss incident** (a bias-pattern
  trend detected at the operating cadence
  before threshold crossing) demonstrated that
  the program is catching issues earlier than
  the lagging indicators would have.

*What worked:*

- Single-named-lead pattern in incident
  response operated cleanly.
- The trust architecture's defense-in-depth
  posture held under the tabletop's
  adversarial pressure.
- The CCO + CAIRO split-authorship pattern (per
  mod-109 Ex-05) is operating without friction.

*What didn't:*

- The third-party AI governance gap limits
  the program's ability to respond to vendor-
  side incidents. The vendor LLM swap event
  during the wealth-advisory rollout required
  ad hoc response because the formal vendor
  risk overlay isn't yet built.
- Cross-LOB risk taxonomy interpretation
  varies materially between public markets
  and wealth advisory. Same words, different
  meanings in practice.

### Section 3 — Coverage gaps

Top three gaps:

1. **Third-party AI governance overlay** —
   primary blocker on MANAGE maturity; vendor
   risk assessment doesn't yet include AI-
   specific criteria.
   *Recommendation:* 90-day sprint with
   Vendor Risk Office to build the overlay;
   the partial gap acceptance from mod-109
   Ex-03 needs to convert to actual closure.
2. **Cross-LOB risk taxonomy uniformity** —
   the same risk categories mean different
   operational things across LOBs.
   *Recommendation:* Joint workshop across
   LOB risk leads; produce uniform
   interpretation guidance.
3. **Tier 2 monitoring automation** — Tier 1
   monitoring is mature; Tier 2 systems
   operate with significant manual monitoring,
   which is expensive and inconsistent.
   *Recommendation:* Extend monitoring
   infrastructure to Tier 2 over Q2-Q3.

### Section 4 — Investment posture

*Where we invested in year 1:* The trust
architecture (per mod-106 Ex-05 partner
pattern); the audit ledger (per mod-108 Ex-05);
the bias monitoring (per mod-105 Ex-02).
Substantial, justified investment.

*Where we under-invested:* Vendor AI risk
capability. The third-party gap (per mod-109
Ex-03 and Section 3 above) is partly a year-1
prioritisation choice — we chose to build the
trust architecture first, accepting the vendor-
risk overlay would be year 2 work.

*Where we over-invested:* Tabletop exercises.
We ran three tabletops in year 1; one was
substantive and produced findings, the other
two were largely confirmatory. Year 2: one
substantive tabletop annually plus targeted
scenarios on novel patterns.

*Year 2 focus:* Third-party governance overlay
(primary); cross-LOB taxonomy uniformity;
Tier 2 monitoring automation; one
substantive annual tabletop.

### Section 5 — Leadership and talent

*Year 1 hiring:* 6 net new roles. AI Risk
Lead (1); Algorithm Quality Office leadership
(2); evidence and policy roles (3). All
positions filled within budget.

*Capability gaps:* Vendor risk expertise
specifically — the partial gap acceptance
in mod-109 Ex-03 was partly because we
couldn't recruit the right vendor-AI-risk
specialist in year 1. Market is tight.

*Talent risks:* The AI Risk Lead role is a
key-person dependency. Year 2: deputy AI
Risk Lead recruitment.

### Section 6 — Cultural integration

*Is the program integrated or parallel?*
Substantially integrated with CRO function;
partially integrated with engineering and
operations; not yet fully integrated with
business-unit leadership in private credit and
wealth advisory.

*Evidence:* AI Risk Council attendance by
non-CAIRO functions is consistent; AI Review
Board has cross-functional participation;
some business-unit decisions still treat AI
program as a gatekeeper rather than a
contributor.

*Recommendations:* Year 2 program
ambassador in each LOB; quarterly business-
unit leadership briefings.

### Section 7 — Specific recommendations

Prioritised for year 2:

1. **Close the third-party AI governance gap.**
   90-day sprint. CAIRO function + Vendor Risk
   Office. Highest priority.
2. **Standardise cross-LOB risk taxonomy
   interpretation.** Joint workshop in Q1;
   guidance document by Q2.
3. **Recruit deputy AI Risk Lead.** Mitigate
   key-person dependency.
4. **Extend monitoring infrastructure to Tier
   2 systems.** Q2-Q3.
5. **Reduce tabletop frequency to annual
   substantive + targeted scenarios.**

---

## 3. Reasoning notes

- **Why I rated MANAGE at Level 1 honestly.**
  The third-party gap is real. Rating it
  Level 2 to match the others would not
  survive the §6.3 honesty test. Honest
  rating produces honest year-2 prioritisation.
- **Why I named the over-investment in tabletops
  explicitly.** Programs that name only under-
  investment look defensively-budgeted. Naming
  the over-investment shows the assessment is
  honestly self-critical. The board respects
  this; the next budget conversation goes more
  smoothly with this honesty banked.
- **Why I addressed cross-LOB taxonomy as a
  cultural issue.** It is. Same words mean
  different things across LOBs because the
  business contexts differ. The fix isn't
  more policy; it's joint interpretation work
  with the people who actually use the
  taxonomy.
- **Why deputy AI Risk Lead is the recruiting
  priority.** Year 1 demonstrated that the
  AI Risk Lead is the key load-bearing role.
  Continuity risk on this role is the highest
  single-person risk in the program.
- **Why I name the AI Risk Lead key-person
  dependency in the self-assessment.** Boards
  respect specific risks named honestly. A
  self-assessment that hides key-person risk
  fails the §6.3 test and is discovered when
  the key person leaves.
- **What this self-assessment deliberately
  does not say.** Individual performance
  ratings; specific compensation discussion;
  specific vendor names. Those belong in
  other documents.

---

Maintained by [Girish Nair](https://github.com/garynair)
