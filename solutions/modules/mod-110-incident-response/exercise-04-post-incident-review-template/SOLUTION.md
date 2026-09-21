# Exercise 04 — Post-Incident Review Template — Reference Solution

## 1. Solution overview

A standard template with 8 sections + a worked
example applying it to Northfield's bias
incident (Ex-01 scenario). The worked example
includes one explicit residual acceptance — the
inherent statistical-power limitation for the
extreme-elderly subgroup that no remediation can
fully address.

---

## 2. Artifact 1 — The template

> **Northfield Mutual — Post-Incident Review
> Template v1.0**
> *Owned by CAIRO function. To be used for all
> material AI incidents.*

### Section 1 — Incident summary

*Fields:*

- Incident ID
- Date detected
- Date contained
- Date closed
- Classification (per mod-107 Ex-04 taxonomy)
- Affected systems
- Affected populations / volume

*Author prompt:* In one paragraph, describe what
happened, in plain language a Board member could
understand.

*What good looks like:* "On [date] at 09:30,
Northfield's claims-triage v2 system was found to
be producing under-triaged recommendations for
patients aged 80+ at Site H-12 specifically. The
pattern had been growing for approximately 6
weeks before detection. Site H-12 was paused at
10:18 the same day; the model was re-trained and
re-deployed at H-12 by hour 168."

### Section 2 — Response summary

*Fields:*

- Single named lead
- Response team composition
- Timeline of major decisions (with timestamps)
- Containment posture chosen + reasoning
- Notifications triggered

*Author prompt:* Summarize the response timeline
with reference to specific roles and decisions.

*What good looks like:* See Exercise 01 reference
solution — phase-by-phase narrative is the level.

### Section 3 — What worked

*Fields:*

- 2–5 specific things that worked
- Per item: what happened, why it worked, why
  it's worth preserving

*Author prompt:* Identify what specifically
operated well. This section is mandatory; reviews
without it produce defensive culture (§6.2).

*What good looks like:* "The 3pp sensitivity-gap
threshold was set tight enough to catch the
pattern within one monitoring cycle of its
emergence as material — this is the right
calibration and should be preserved."

### Section 4 — What didn't work

*Fields:*

- 2–5 specific things that didn't work
- Per item: what happened, what the gap was, what
  the consequence was

*Author prompt:* Identify substantive problems.
Don't soften; the review is for learning, not
appearances.

*What good looks like:* "The detection took ~6
weeks from pattern emergence to threshold
crossing. While the threshold-crossing detection
worked, weekly trend analysis at the operating
cadence (per mod-109 Ex-02) would have surfaced
the trend earlier; this didn't happen because the
operating-cadence review wasn't yet trained on
trend-toward-threshold patterns."

### Section 5 — Root causes (proximate and systemic)

*Fields:*

- Proximate cause(s)
- Five-whys chain
- Systemic cause(s)

*Author prompt:* Apply §5.2 of mod-110 lecture
notes. Stop at the level where the cause is
organisational, not technical.

*What good looks like:* See Exercise 01 reference —
"the proximate cause was model calibration drift
after training-data refresh; the systemic cause
was absence of a training-data refresh review
gate that compares subgroup representation
between training sets."

### Section 6 — Recommendations

*Fields (one row per recommendation):*

- Recommendation
- Owner (named role)
- Target close date
- Priority (P0 / P1 / P2 / P3)
- Linked finding (which §3 or §4 item drives
  this)
- Status (initially: Open)

*Author prompt:* Per §6.3 — specific, assigned,
tracked. No "improve monitoring" — name the
specific change.

*What good looks like:* "Add leading-indicator
trend monitoring (2pp sustained for 2 weeks
triggers investigation) — Owner: Algorithm Quality
Office Clinical Validation Lead — Target: 30
days — P1 — Linked: §4 finding on 6-week
detection lag."

### Section 7 — Residual risks accepted

*Fields:*

- Residual risk
- Acceptor (named role or body)
- Date accepted
- Re-evaluation trigger

*Author prompt:* Per mod-103 §5.3 — name residuals
explicitly. Programs that recommend remediation
for every finding lose credibility. Some risks
can't be fully remediated; name them.

*What good looks like:* "Statistical power for
extreme-elderly subgroups (95+ years) is limited
by case volume; complete bias detection at this
subgroup is not achievable through monitoring
alone — Acceptor: AI Risk Council — Re-evaluation:
annually with the bias-monitoring policy review."

### Section 8 — Sign-off

- Review lead (signed)
- AI Risk Lead (signed)
- AI Risk Council acknowledgment (date)
- Internal Audit observer (signed if applicable)

---

## 3. Artifact 2 — Worked example

> **Northfield Mutual — Post-Incident Review
> Incident NM-IR-2026-06-15-001 (Claims Triage v2
> Bias Pattern at H-12)**
> *Review lead: Tom Reyes, Internal Audit. Date:
> 2026-07-15.*

### §1 — Incident summary

Incident NM-IR-2026-06-15-001. Detected 2026-06-15
09:30 local; contained (Site H-12 pause) 10:18
same day; closed (model re-deployed) 2026-06-22.
Classification: Category 2 (AI-Program, sub-cat
2.a Bias / fairness). Affected system: claims-
triage v2 at Site H-12. Affected population: ~430
patients aged 80+ presenting at H-12 between
approximately 2026-04-30 and 2026-06-15.

### §2 — Response summary

Single named lead: Maria Chen, AI Risk Lead.
Response team: Maria, Dr. Sundaresan (H-12
Clinical), Raj Patel (Algorithm Data), Sarah Lin
(GC), Dr. Park (CMO designee), CISO on-call (not
active). Major decisions: detection 09:30;
verification 09:50; classification 09:55; lead
10:00; containment-posture (H-12 pause) 10:18;
team convene 10:30; notification matrix consulted
by hour 6; first notifications triggered
hour 24; investigation deep-dive days 1-7;
re-deployment day 7. Containment posture: Site
H-12 only — reasoning was that monitoring data
clearly localized; pausing all sites would be
overcontainment. Notifications triggered: EU AI
Act Art. 73 NCA (hour 48); NYDFS §500.17 (hour
72); patient letters days 5-14; AI Risk Council
auto-convened hour 24; Board Risk Committee
included in next regular meeting; CFPB not
applicable (insurance not credit).

### §3 — What worked

1. **Detection threshold calibration.** The 3pp
   sensitivity-gap threshold caught the pattern
   within one monitoring cycle of its emergence
   as material. Preserve.
2. **Single-named-lead pattern.** Maria's
   leadership of the response was effective;
   CISO + CAIRO + CMO designee coordination was
   clean. Preserve the pattern.
3. **Containment proportionality.** Site H-12
   only — not all sites — was the right call.
   Overcontainment was explicitly avoided.
4. **Pre-computed notification matrix.** All
   notification decisions were made by
   consulting the matrix; no real-time matrix
   construction; no missed obligations.

### §4 — What didn't work

1. **Detection lag.** Six weeks from pattern
   emergence to threshold crossing. Weekly trend
   analysis at the operating cadence wasn't yet
   trained to surface trend-toward-threshold
   patterns; this is a gap.
2. **Training-data refresh blind spot.** The
   refresh process didn't surface the
   subgroup-representation change; this is the
   systemic gap that produced the incident.
3. **Patient-notification authority unclear.** The
   CMO designee took on the patient-notification
   authority but this wasn't pre-named in the
   incident playbook; coordination delayed
   notification by ~24 hours.

### §5 — Root causes

**Proximate cause:** Model calibration shifted
after training-data refresh removed disproportionate
share of age-80+ cases at high-volume sites
(specifically Site H-12).

**Five-whys chain:** (Per Exercise 01 reference
solution §3, hours 24-168.)

**Systemic cause:** Absence of a *training-data
refresh review gate* comparing subgroup
representation between training sets before
deployment. Northfield's existing pre-deployment
evaluation used stratified random samples from
the new training set rather than comparing
distributions.

### §6 — Recommendations

| Rec | Owner | Target | Priority | Linked | Status |
|---|---|---|---|---|---|
| Add trend-toward-threshold leading indicator (2pp sustained for 2 weeks → investigation) | AQO Clinical Validation Lead | 30 days | P1 | §4(1) | Open |
| Implement training-data refresh review gate | AQO + CDO joint | 90 days | P0 | §4(2), §5 systemic | Open |
| Pre-name patient-notification authority in incident playbook per harm type | AI Risk Lead + CMO | 30 days | P1 | §4(3) | Open |
| Establish quarterly tabletop including patient-notification simulation | AI Risk Lead | 60 days | P2 | §4(3) preventive | Open |

### §7 — Residual risks accepted

**Residual:** Statistical power for extreme-
elderly subgroups (specifically age 95+) is
limited by clinical case volume; complete bias
detection at this subgroup is not achievable
through monitoring alone, regardless of threshold
calibration. The new refresh review gate will
improve detection but won't fully eliminate this
limitation.

**Acceptor:** AI Risk Council.

**Date accepted:** 2026-07-15.

**Re-evaluation trigger:** Annual bias-monitoring
policy review; or if Northfield's age-95+ case
volume materially increases (e.g., dedicated
geriatric service expansion).

### §8 — Sign-off

Review lead: Tom Reyes, Internal Audit (signed).
AI Risk Lead: Maria Chen (signed).
AI Risk Council: acknowledged 2026-07-22.

---

## 4. Reasoning notes

- **Why I included the explicit residual
  acceptance.** Programs that recommend
  remediation for every finding are not
  credible; some risks (like statistical power
  for rare subgroups) cannot be fully remediated.
  Naming them honestly survives external
  scrutiny in ways that pretending they can be
  fully fixed does not.
- **Why "what worked" comes before "what didn't
  work".** §6.2 — reviews that focus only on
  what went wrong produce defensive culture.
  Leading with what worked acknowledges the
  team's competent response before turning to
  improvement.
- **Why the recommendations include a preventive
  one (the quarterly tabletop with patient-
  notification).** Recommendations should
  address the systemic dimension, not just
  remediate the proximate failure.
- **What this template under-specifies.** The
  signature pages (cryptographic format, key
  references); the audit-ledger ingestion path;
  the specific tracking system. Operational
  details that the program's evidence
  infrastructure (mod-108) provides.
- **What I would change in v2.** Add a *peer
  review* section — a peer institution's
  similar pattern, if any, surfaced through the
  monitoring cadence from mod-102 §6.2. This
  would let post-incident reviews leverage
  industry pattern-recognition.

---

Maintained by [Girish Nair](https://github.com/garynair)
