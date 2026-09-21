# Exercise 01 — Year-1 Operating Plan — Reference Solution

## 1. Solution overview

A year-1 operating plan for **Northfield Mutual**.
Hub-and-spoke operating model. Quarterly milestones
cover the six §2.1 things in order. 4-role hiring
sequence in year 1. Explicit deferrals to year 2:
post-market monitoring formalisation, EU AI Act
documentation, comprehensive automation. Budget
posture tied to risk reduction.

---

## 2. The plan

### Operating model — hub-and-spoke

Northfield is mid-market P&C insurer with three
business lines (personal lines, commercial, and
specialty). The hub-and-spoke pattern fits because:

- **Multi-LOB structure** with different regulatory
  exposures (commercial has more EU-resident
  customers; specialty has more state-regulator
  intensity).
- **Existing risk function** under the CRO is
  hub-and-spoke for non-AI risks; the AI program
  follows the pattern.
- **Mid-market scale** doesn't justify fully
  federated; the hub handles enterprise
  consistency.

Hub: CAIRO function reporting to CRO. Spokes: per-LOB
AI risk partners (recruitable in year 2 or 3).

### Quarterly milestones

**Q1: Foundation establishment.**

- Q1 W1-W2: Charter authorship; AI Risk Council
  formed.
- Q1 W3-W6: First AI Risk Council meeting; meeting
  cadence established.
- Q1 W7-W12: AI Review Board formed; first AI
  inventory pass complete; impact assessment
  template authored.

*Deliverable:* Operating governance machinery;
inventory baseline.

**Q2: Policy hierarchy + appetite statement.**

- Q2 W1-W4: AI policy hierarchy drafted (top
  policy + four standards).
- Q2 W5-W8: AI risk appetite statement drafted
  per mod-111 Ex-01 pattern.
- Q2 W9-W12: CAIRO × MRM boundary discussion
  formalised per mod-104 Ex-04; CAIRO × CISO
  boundary scoped per mod-107 Ex-03.

*Deliverable:* Authority foundation; boundary
machinery operating.

**Q3: Operational infrastructure.**

- Q3 W1-W6: Bias monitoring per mod-105 Ex-02
  operational on Tier 1 systems.
- Q3 W7-W10: Trust architecture decisions made
  per mod-106 Ex-05 (build/buy/partner). For
  Northfield's scale: likely buy from a
  commercial provider.
- Q3 W11-W12: Evidence layer (audit ledger)
  decisions made per mod-108 Ex-05. Likely
  partner pattern.

*Deliverable:* Tier 1 systems operationally
monitored.

**Q4: Board engagement + first formal review.**

- Q4 W1-W4: First quarterly board report
  per mod-111 Ex-02 pattern.
- Q4 W5-W8: AI risk appetite statement adopted
  by the Board.
- Q4 W9-W12: First annual self-assessment per
  mod-111 Ex-05 + mod-112 §2.4 pattern.

*Deliverable:* Board engagement operational;
year-1 self-assessment complete.

### Hiring sequence

| Hire | Quarter | Role |
|---|---|---|
| 1 (Q1) | AI Risk Lead | Risk professional; will carry day-to-day |
| 2 (Q1-Q2) | Policy Lead | Compliance background; standards authorship |
| 3 (Q2-Q3) | Evidence Lead | Engineering or audit background |
| 4 (Q3-Q4) | Regulatory Engagement Lead | Legal or compliance background |

Five hires in year 1; tight against budget but
sustainable.

### What year 1 explicitly will not do

- **Trust architecture custom build.** Defer to
  vendor selection in year 1; consider custom in
  year 3+ if needed. Custom build in year 1 would
  consume resources that should go to foundation.
- **Comprehensive automation.** Per mod-109 §4.3
  trap. Year 1 builds practice; year 2 considers
  automation per mod-109 Ex-04.
- **EU AI Act post-market monitoring formalisation
  as separate artifact.** Per mod-109 Ex-03 gap
  analysis — accept as Year 2 work. Operational
  monitoring exists; the *named artifact* is
  deferred.
- **Multi-language transparency standard.**
  Northfield is US-Spanish bilingual; full
  multi-language (per any EU operations) is
  year-2 work.
- **Comprehensive tabletop exercises.** Per
  mod-110 §6.5 — one substantive tabletop in
  year 1. Additional tabletops would be
  performance art.

### Mid-year-1 inflection point preparation

Around month 6-8 (Q3) the foundation work will
feel invisible. The preparation:

- The Q3 quarterly board report will explicitly
  use the "material changes" section to show
  foundation progress — "X impact assessments
  complete; trust architecture partner contract
  executed; first AI Review Board cycle complete".
- The CAIRO's monthly briefing with the CRO will
  pre-discuss the perceived invisibility before
  it becomes an issue.
- A specific 1:1 with the Board Risk Committee
  chair in late Q2 to frame what Q3-Q4 will look
  like.

The preparation is *anticipatory communication*,
not pivoting to visible deliverables.

### Year-1 self-assessment criteria

Year 1 succeeded if:

1. **The governance machinery operates.** AI
   Risk Council monthly; AI Review Board
   bi-weekly; both with documented decisions.
2. **The appetite statement is adopted by the
   board.** Authority foundation in place.
3. **Tier 1 systems are inventoried and impact-
   assessed.** Per mod-103 Ex-02 template.
4. **Bias monitoring operates on Tier 1
   customer-facing systems.** Per mod-105 Ex-02.
5. **The first four hires are in role.** Carry
   year 2 work.
6. **Quarterly board reports operate.** Per
   mod-111 Ex-02 discipline.
7. **The CAIRO × MRM and CAIRO × CISO boundaries
   are documented per mod-104 Ex-04 and
   mod-107 Ex-03 patterns.**

If any of these are not in place at end of year
1, year 1 has not fully succeeded — and the
year-2 plan accommodates the gap.

### Budget posture

Year-1 budget framing:

- **Tied to risk reduction.** Each major investment
  named with the risk it addresses (per mod-103
  taxonomy) and the magnitude of risk reduction
  expected.
- **Phased.** Q1 lighter (early hiring); Q2-Q3
  heavier (operational infrastructure); Q4
  moderate (consolidation).
- **The cost of not investing.** For each
  material investment, the exposure if
  deferred — per the mod-111 Ex-04 prepared-
  response pattern.

The budget conversation with the CFO and Board
treats AI program investment as enterprise risk
management, not as a discretionary AI initiative.

---

## 3. Reasoning notes

- **Why hub-and-spoke for Northfield.** The
  multi-LOB + multi-regulator pattern fits
  hub-and-spoke better than centralised
  (consistency at the cost of speed) or
  federated (consistency loss). Northfield's
  existing risk-function pattern reinforces
  the choice.
- **Why I deferred trust architecture custom
  build to year 3+.** mod-106 §6 framework
  applies — Northfield doesn't have the
  cryptographic engineering capacity in year 1
  to build trust architecture from scratch. Buy
  initially; consider custom later if needed.
- **Why I named specific things year 1 will not
  do.** §2.2 — every year-1 plan needs the
  defer list as much as the do list. Programs
  that try to do everything in year 1 fail.
- **Why the inflection point preparation is
  anticipatory communication rather than
  pivoting.** §2.3 — the discipline is staying
  on foundation work while making the work
  visible. Pivoting to visible deliverables
  produces year-2 programs with weak
  foundations.
- **What this plan deliberately under-specifies.**
  The specific vendor selections (engineering
  decisions); the specific compensation
  benchmarks for hires (HR decisions); the
  specific PMO mechanics. Operational details
  beyond the CAIRO-level plan.

---

Maintained by [Girish Nair](https://github.com/garynair)
