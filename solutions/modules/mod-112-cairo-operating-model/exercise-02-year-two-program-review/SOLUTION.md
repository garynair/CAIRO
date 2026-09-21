# Exercise 02 — Year-2 Program Review — Reference Solution

## 1. Solution overview

End-of-year-2 review for **Tessera Bank**.
Year-2 results: 5 of 6 goals achieved; cross-LOB
integration under-invested. Maturity progressed
from Level 2 to Level 3 on most NIST functions.
First material incident was the vendor LLM swap;
handled credibly. Year-3 priorities lead with
cross-LOB integration and operational efficiency.
One stalling symptom: CAIRO is still personally
handling some operational decisions that should
have been delegated.

---

## 2. The review

### Year-2 results

| §3.1 goal | Year-2 target | Actual | Gap |
|---|---|---|---|
| Operate controls at cadence | Continuous evidence cadence operational on Tier 1 + Tier 2 | Tier 1 yes; Tier 2 partial | Tier 2 monitoring automation is the gap |
| Close year-1 gaps | 4 of 5 year-1 gaps closed | 4 of 5 closed; third-party AI governance gap deferred to year 3 | Per mod-109 Ex-03 |
| Mature the program | NIST Level 2→3 on most functions | Achieved on GOVERN, MAP, MEASURE; MANAGE remains at Level 2 due to third-party gap | Aligned |
| Integrate cross-LOB | Cross-LOB risk taxonomy uniform across LOBs | Partial; same words, different interpretations across public markets, private credit, wealth advisory | Material gap |
| Build second tier of team | 4 net additional hires | Achieved | Aligned |
| Handle material incident credibly | Substantive response track record | Vendor LLM swap incident occurred and was handled per mod-104 Ex-04 + mod-110 patterns | Achieved |

Overall: 5 of 6 goals achieved; cross-LOB
integration is the year-2 underperformance.

### Maturity progression

| NIST function | Start of year 2 | End of year 2 |
|---|---|---|
| GOVERN | Level 2 (Developing) | Level 3 (Defined) |
| MAP | Level 2 | Level 3 |
| MEASURE | Level 2 | Level 3 |
| MANAGE | Level 1 (Initial) | Level 2 (Developing) |

The MANAGE function still lags because of the
third-party AI governance gap that wasn't
closed in year 2. Year 3 must address this.

### Year-2 trap addressed

Per §3.3, year 2 risked trying to fix every
year-1 error comprehensively. We navigated this
by:

- Naming the year-1 errors specifically at the
  start of year 2 (per mod-111 Ex-05 pattern).
- Choosing 4 of 5 to address; explicitly
  accepting the fifth (third-party governance)
  as year-3 work.
- Resisting mid-year pressure to also tackle
  the deferred gap when the cross-LOB issue
  surfaced.

The discipline held; we did not lapse into
"year 1 again". This was substantially aided
by the AI Risk Lead's strong year-1 build
quality, which left less to fix than initially
expected.

### First material incident response

The Vendor X foundation-model swap was the year-2
material incident. Per the mod-104 Ex-04 pattern,
it was a joint incident with the CISO. The CAIRO
function led the AI-program re-evaluation
stream; MRM led the SR 11-7 re-validation
stream. AI Risk Lead was the single named
lead for the overall response.

Post-incident review findings:

- **Worked:** The mod-104 Ex-04 boundary
  resolution (single intake; joint authorship)
  operated cleanly. The trust architecture
  identity-verification layer (per mod-106
  Ex-04) flagged the model-identity change
  within the documented 5-minute window.
- **Didn't work:** The post-swap re-evaluation
  took 21 days against a target of 14 days,
  due to scheduling conflicts across the joint
  team.
- **Recommendation:** Pre-scheduled "vendor
  incident response windows" — 2-day blocks
  per quarter where the joint team's calendars
  are protected for vendor-incident response.
  Owner: CAIRO + CISO joint. Target: Q3 year 3.

Overall, the response demonstrated that year 1's
boundary work paid off. The 21-day timeline is
a stretch but not a failure.

### Year-3 priorities

In priority order:

1. **Close the third-party AI governance gap.**
   The year-1 deferred gap and year-2 deferred
   gap; cannot defer further. Specific
   deliverable: AI-vendor assessment overlay
   to existing vendor risk program, operating
   by Q2 year 3. *Owner:* CAIRO + Vendor Risk Office.
2. **Cross-LOB risk taxonomy uniformity.** The
   year-2 underperformance. Joint workshop with
   LOB risk leads Q1; guidance document Q2;
   uniform interpretation in operation by Q3.
3. **Tier 2 monitoring automation.** Extend the
   monitoring infrastructure from Tier 1 to
   Tier 2. Engineering-led, CAIRO function
   sponsors.
4. **Operating efficiency.** Cost per unit of
   risk-managed AI; specifically the per-system
   onboarding time. Target: from 8 weeks (current)
   to 4 weeks (Q4 year 3).
5. **Deputy AI Risk Lead recruiting.** Key-
   person dependency mitigation per mod-111
   Ex-05 + mod-112 §6.4.

### Stalling-watch

Per §4.3, the warning signs of year-3 stalling.
Honest assessment:

- **CAIRO still personally handling many operational
  decisions.** *Honestly present.* Two specific
  patterns: bias-monitoring threshold-approach
  conversations frequently reach the CAIRO; vendor
  risk decisions on AI vendors frequently reach
  the CAIRO. Both should be delegated to the AI
  Risk Lead and Vendor Risk Lead respectively.
- **New AI systems requiring months to enter
  program discipline.** *Partially present.* The
  Tier 1 onboarding is 8 weeks (target 4 weeks
  by Q4 year 3); Tier 2 and below is closer to
  on-target.
- **Still building foundational artifacts.**
  *Not present.* Foundational artifacts are
  complete; year 3 will refine, not build.
- **Board reporting still has the "look at what
  we built" quality.** *Partially present.* The
  Q4 year-2 board report still leaned on
  "completed X" framing; year-3 reports should
  shift to "operating Y at cadence Z".

Two of the four symptoms are honestly present.
This is a signal to address in year 3, not
hide.

---

## 3. Reasoning notes

- **Why I named cross-LOB taxonomy uniformity as
  the year-2 underperformance.** It was. Naming
  it accurately is the §3 honesty discipline;
  programs that hide year-2 underperformance
  produce year-3 plans that don't address it.
- **Why I named the CAIRO's personal-handling of
  operational decisions as a present stalling
  symptom.** §4.3 — programs that show no
  warning signs of stalling are not seeing
  themselves clearly. Naming this honestly
  creates accountability for the delegation
  work in year 3.
- **Why the year-3 priorities lead with the
  third-party gap.** It's been deferred from
  year 1 and year 2; further deferral signals
  the program can't close substantive gaps.
  The credibility cost of not closing in year 3
  would exceed the cost of doing the work.
- **What this review deliberately doesn't do.**
  Compare Tessera to peer institutions. External
  benchmarking is a separate exercise; this
  review is Tessera-against-Tessera-targets.

---

Maintained by [Girish Nair](https://github.com/garynair)
