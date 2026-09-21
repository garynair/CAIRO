# Exercise 02 — Quarterly Board Report — Reference Solution

## 1. Solution overview

A 4-page Q2 board report for **Northfield
Mutual** centered on the H-12 bias incident.
Honest about the threshold crossing, the state
insurance regulator inquiry, and the EU AI Act
NCA notification. The primary ask is Board
ratification of an updated bias-monitoring
threshold; secondary ask is approval of an
additional FTE for the AI Risk Lead's team.

---

## 2. The report

> **NORTHFIELD MUTUAL — AI PROGRAM Q2 REPORT**
> *To: Board Risk Committee. From: Chief AI
> Officer. Date: [date].*

### Risk posture summary

| Category | Current state | Δ from Q1 |
|---|---|---|
| Model Performance | Within appetite | unchanged |
| Bias and Fairness | **Outside appetite at Site H-12** (now resolved) | adverse |
| Transparency | Within appetite | unchanged |
| Privacy and Data | Within appetite | unchanged |
| Security | Within appetite | improved (defense-in-depth standard ratified) |
| Vendor and Third-Party AI | Within appetite | unchanged |
| Strategic and Reputational | Within appetite; *external attention level elevated* | adverse |

### Material changes

- **The H-12 bias incident** (May 15-Jun 15)
  was the material event of the quarter. The
  claims-triage v2 system produced under-
  triaged recommendations for patients aged
  80+ at Site H-12 specifically, for
  approximately six weeks before detection.
  Site H-12 was paused on detection;
  re-deployed after re-training. The post-
  incident review surfaced a systemic gap in
  the training-data refresh process which has
  been addressed.
- **The state insurance regulator inquiry**
  arrived June 28 in response to the
  incident. Northfield provided the
  responsive evidence package (per the
  mod-108 Ex-02 reference pattern). The
  inquiry remains open; follow-up is
  expected.
- **The EU AI Act NCA notification** was
  filed within the Art. 73 window (48 hours
  for the fundamental-rights affected
  population).

### Material exceptions

**Exception 1: H-12 bias incident (now
resolved).**

- *Background:* See material changes above.
- *Risk appetite implication:* Sustained
  equalized-odds gap > 5pp is outside
  appetite per the appetite statement.
- *Response:* Site-level containment within
  the first hour; re-training of the local
  model; re-deployment after thresholds
  verified. Post-incident review surfaced
  the systemic cause (training-data refresh
  blind spot) and produced four
  recommendations, all assigned with
  specific targets.
- *Status:* Resolved as of Jun 22; post-
  incident review completed Jun 30;
  recommendations being tracked.

**Exception 2: EU AI Act Art. 73
notification triggered.**

- *Background:* Per Art. 73, fundamental-
  rights incidents require notification
  within 2 days. The H-12 incident triggered
  this.
- *Risk appetite implication:* AI-program
  regulatory action is material; the program
  is operating against an open regulatory
  matter.
- *Response:* Notification filed within 48
  hours per matrix; follow-up coordination
  ongoing per the CCO + CAIRO + GC joint
  process (mod-109 Ex-05 pattern).
- *Status:* Open; expected closure Q3 or Q4.

### Material decisions pending

**Decision 1 — Updated bias-monitoring
threshold.**

The post-incident review recommended adding a
trend-toward-threshold leading indicator (2pp
sustained for 2 weeks triggers investigation,
in addition to the current 3pp single-period
threshold). This requires update to the bias-
monitoring policy and to the appetite
statement's threshold language. Recommend
Board ratification.

**Decision 2 — AI Risk Lead team additional FTE.**

The H-12 response strained the AI Risk Lead's
team for approximately two weeks. The post-
incident review identified that the current
team capacity (2 FTE) is sufficient for
steady-state operation but inadequate for
material incident response. Recommend Board
approval of one additional FTE.

### Material changes ahead

- **ISO 42001 audit** scheduled Q3; the gap
  analysis (per mod-109 Ex-03 pattern)
  identified five gaps, four closing pre-
  audit and one accepted as 12-month residual.
- **State insurance regulator follow-up**
  expected Q3 or Q4; tone and depth depend
  on the regulator's read of the H-12
  response.
- **EU AI Act implementing acts** on Art. 9
  RMS expected Q3; potential updates to
  Northfield's RMS-related controls.

### Asks of the Board

1. **Ratify the updated bias-monitoring
   threshold** (Decision 1 above).
2. **Approve one additional FTE** for the AI
   Risk Lead's team (Decision 2 above).
3. **Acknowledge** the H-12 post-incident
   review and the program's remediation
   actions.
4. **Schedule** Q3 board pre-meeting briefing
   with Board Risk Committee chair on state
   regulator follow-up — to ensure off-cycle
   updates are coordinated.

### Appendices

(Available on request; not included in main
report.)

- Appendix A: H-12 post-incident review (full)
- Appendix B: AI risk register (current state)
- Appendix C: Incident summary (trailing 4
  quarters)
- Appendix D: Notification matrix excerpt
- Appendix E: Vendor register

— end report —

---

## 3. Reasoning notes

- **Why the H-12 incident dominates the
  report.** It was the material event. Trying
  to bury it would be the §3.3 honesty
  failure. Surfacing it with a specific
  response and a specific ask demonstrates the
  program operates substantively.
- **Why I included four asks rather than one.**
  §3.2 — asks discipline. The asks are
  substantive (ratification, FTE, briefing
  schedule) and the board has the
  opportunity to engage with each.
- **Why I left out operational metrics.**
  §1.3 — boards don't need them. The
  appendices have them for reference.
- **Why I kept the "external attention level
  elevated" framing for reputational risk.**
  Honest acknowledgment that the H-12
  incident plus the regulator inquiry plus
  the Art. 73 notification has materially
  increased Northfield's external exposure.
  Pretending otherwise would not survive.
- **What I would do differently.** Add a
  one-line trend indicator on the
  risk-posture-summary table showing
  six-month trajectory, not just quarter-
  on-quarter. A future iteration would
  include this.

---

Maintained by [Girish Nair](https://github.com/garynair)
