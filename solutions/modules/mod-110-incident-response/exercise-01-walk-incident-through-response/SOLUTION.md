# Exercise 01 — Walk an Incident Through Response — Reference Solution

## 1. Solution overview

A phase-by-phase walkthrough of Northfield's
bias-incident scenario. The systemic cause
surfaces at the training-data refresh process —
the quarterly refresh removed age-80+ patients
whose triage labels had been the basis for the
initial calibration. The proximate cause was the
calibration drift; the systemic cause was the
absence of a *training-data refresh review gate*
checking for subgroup-representation drift before
deployment.

---

## 2. The response walkthrough

### Hour 0 (09:30) — Detection

- *Detection event:* The Algorithm Quality Office
  monitoring service emits a `monitoring.threshold.crossed`
  event at 09:30:14 — sensitivity gap on age-80+
  subgroup at Site H-12 reaches 6.5pp, exceeding
  the 3pp threshold. The event includes the trailing
  4-week trend showing the gap has been growing
  for 2 consecutive months.
- *Recipients:* The AI Risk Lead (Maria Chen) and
  the Site H-12 Clinical Validation Lead
  (Dr. Sundaresan) receive the alert simultaneously.
- *First response:* Maria opens an incident in the
  Northfield incident tracking system at 09:34;
  emits an `incident.opened` event referencing the
  detection event.

### Hours 0–1 — First-Hour Decisions (09:30–10:30)

**Verification (09:30–09:50).** Maria reviews the
underlying monitoring data with the Algorithm
Quality Office data lead. The 6.5pp gap is
confirmed; it's a real consecutive-month pattern
at Site H-12 specifically. Other sites are within
threshold. Conclusion: incident is real.

**Provisional classification (09:55).** Maria
applies the mod-107 Ex-04 taxonomy. Initial
classification: Category 2 (AI-Program Incident,
sub-category 2.a Bias / fairness). The CISO on-call
is notified within the 15-minute boundary;
preliminary assessment is no security dimension
identified. Classification will be revisited if
new facts emerge (§6.5 of mod-107 lecture notes).

**Single named lead assignment (10:00).** Maria
assigns herself as named lead. The CAIRO Chief AI
Officer is briefed and concurs. The AI Risk Lead
will coordinate with the CISO on-call as needed.

**Containment-posture decision (10:15).** Three
options considered:

- *Full system pause at all sites.* Rejected —
  overcontainment for an incident affecting one
  site.
- *Site H-12 pause specifically.* Selected — the
  monitoring data points specifically to H-12;
  pausing only there is proportionate.
- *Continue at H-12 with elevated monitoring.*
  Rejected — the pattern has been observable for
  two months; continued operation produces
  continued harm risk.

Site H-12 pause issued at 10:18; communicated to
H-12 clinical leadership; backup workflow (manual
triage) operational by 10:35. Pause event
recorded in the audit ledger.

**Response team convene (10:30).** Initial team
convene call:

- Maria (AI Risk Lead, named lead).
- Dr. Sundaresan (H-12 Clinical Validation Lead).
- Algorithm Quality Office Data Lead (Raj Patel).
- CISO on-call (briefed; not active).
- CMO designee (Dr. Park) per the Aldwych-pattern
  clinical-authority boundary.
- GC (Sarah Lin) for notification consultation.

### Hours 1–24 — Containment + Initial Investigation (10:30–09:30+1)

**Initial investigation team:** Maria leads;
Raj Patel investigates the data side; Dr. Park
investigates the clinical-impact side.

**Initial findings (by EOD):**

- The 6.5pp gap is *real* and *site-specific*.
- The pattern began approximately 6 weeks ago
  (corresponds to the recent training-data
  refresh).
- The training-data refresh process removed
  approximately 40% of the age-80+ cases that
  had been in the prior training set (a known
  process behaviour of the refresh — the cases
  were "stale" by the refresh criteria).
- The model's calibration on the
  reduced-age-80+ training data produced lower
  sensitivity for this subgroup at sites with
  high age-80+ presentation volume — of which
  Site H-12 is the highest in Northfield.

**Notification matrix consultation (per §4):**

| Notification | Trigger | Timeline | Decision |
|---|---|---|---|
| EU AI Act Art. 73 | EU-resident affected with discriminatory pattern | 2 days | *Yes — 8 EU-resident insureds at H-12 affected.* Notify by hour 48. |
| State insurance regulator (NY) | NY-resident affected | 72 hours (NYDFS state-level) | *Yes — 23 NY-resident insureds at H-12 affected.* Notify by hour 72. |
| GDPR Art. 33 (DPA) | Personal data breach | 72 hours | *Evaluating* — discriminatory triage may or may not meet "personal data breach" definition. GC consultation in progress. |
| AI Risk Council | Material incident | Auto-convene per §6.5 of mod-107 Ex-04 | *Convened* — meeting set for hour 24. |
| Board Risk Committee | Material AI-program incident | Next regular meeting | *Yes — included in next scheduled Board pack.* |
| Affected patients | Adverse-clinical-outcome notification | Per medical ethics + Northfield policy | *Yes — letter to affected patients within 14 days.* |

**Notifications triggered at hour 24:**

- EU AI Act Art. 73 notification drafted (CAIRO
  authors; GC reviews; CCO concurs); will be
  transmitted in the 24-hour window.
- NYDFS notification drafted (CISO + CAIRO joint;
  ready for transmission).
- Patient notification process initiated (clinical
  letter being drafted with CMO designee).

### Hours 24–168 (one week) — Deep Investigation

**Investigation deepens** with focus on root cause.
Five-whys discipline (§5.2):

- Why did the model produce reduced sensitivity
  on age-80+ at H-12? *Because the model's
  calibration shifted after the training-data
  refresh.*
- Why did the refresh shift the calibration? *Because
  it removed 40% of age-80+ cases that had been
  basis of original calibration.*
- Why did the refresh remove those cases?
  *Because the refresh's "data freshness" rule
  considered cases older than 18 months stale,
  and age-80+ cases tend to be older
  presentations on average.*
- Why did this not surface in pre-deployment
  testing? *Because the pre-deployment
  evaluation used a stratified random sample
  from the new training set, not the prior
  set's distribution; the new set had
  proportionately lower age-80+ representation
  and the evaluation didn't surface this.*
- Why was the pre-deployment evaluation not
  designed to catch this? *Because there is no
  Northfield-side gate that compares the new
  training set's subgroup representation to the
  prior set's representation.*

**Proximate cause:** Model calibration shifted
after training-data refresh removed disproportionate
share of age-80+ cases.

**Systemic cause:** Absence of a
*training-data refresh review gate* that checks
subgroup-representation drift before deploying
re-trained model. The refresh process operates as
if all cases are equivalent in their training
value; this is empirically not the case for
demographically-stratified bias monitoring.

**Resolution (hour 96):** Site H-12 model is
re-trained on the prior training data plus the
age-80+ cases that had been removed; re-validated
against the bias-monitoring thresholds at all
sites; deployed to Site H-12 (hour 168).

### Days 8–30 — Post-Incident Review

**Review process:** AI Risk Council convenes
formal review on day 14. Review led by Internal
Audit lead (Tom Reyes), independent of the CAIRO
function and the Algorithm Quality Office. All
materially involved roles present.

**Findings — what worked:**

- The detection threshold (3pp sensitivity gap)
  was tight enough to catch the pattern within
  one monitoring cycle of its emergence as
  material.
- The single-named-lead pattern operated
  cleanly; Maria's leadership of the response
  was effective and the CISO + CAIRO coordination
  was clean.
- The containment posture (Site H-12 pause only)
  was proportionate; no overcontainment.
- The notification matrix was consulted within
  the first 24 hours; all notifications were
  made within their applicable windows.

**Findings — what didn't:**

- The detection took approximately 6 weeks from
  pattern emergence to materializing as a
  threshold crossing. While operationally
  acceptable, weekly review (per mod-109 Ex-02
  pattern) might have surfaced the trend before
  the crossing.
- The training-data refresh process was
  operating without subgroup-representation
  review; this is the systemic gap.
- The clinical-authority boundary handling was
  fine but the CMO designee was the patient-
  notification authority; the standard process
  should pre-name the patient-notification
  authority to avoid coordination delay.

**Recommendations (with assignment and tracking):**

1. **Adjust monitoring sensitivity.** Add a
   "trend-toward-threshold" leading indicator
   (2pp sustained for 2 weeks triggers
   investigation). *Owner: Algorithm Quality
   Office Clinical Validation Lead. Timeline:
   30 days.*
2. **Implement training-data refresh review
   gate.** No re-trained model deploys without
   subgroup-representation comparison against
   prior training set. *Owner: Algorithm Quality
   Office + CDO joint. Timeline: 90 days.*
3. **Pre-name patient-notification authority in
   incident playbook.** Per type of clinical
   harm, the standard process names the
   notification-authority role. *Owner: AI Risk
   Lead + CMO. Timeline: 30 days.*
4. **Document residual:** Even with the new
   review gate, statistical power for
   extreme-elderly subgroups (95+) is limited
   by case volume; AI Risk Council accepts this
   residual with named monitoring. *Acceptor:
   AI Risk Council. Re-evaluation: annually.*

**Loop closure (mod-103 §6.5):** The recommendations
are tracked in the program's improvement backlog;
status reviewed monthly by the AI Risk Lead;
closed status verified by the AI Risk Council.

---

## 3. Reasoning notes

- **Why the containment posture was site-only.**
  The monitoring data clearly localized the
  pattern. Pausing all 14 sites would have been
  overcontainment by an order of magnitude.
  Site-only is the proportionate response.
- **Why I traced through five whys rather than
  stopping at proximate cause.** §5.3 — proximate
  causes (calibration drift) don't produce
  program improvement. The systemic cause (no
  refresh review gate) is what the
  recommendations address.
- **Why the Art. 73 notification is yes despite
  only 8 EU-resident affected.** Art. 73 triggers
  on fundamental-rights affecting EU-resident;
  the discriminatory pattern qualifies regardless
  of count.
- **Why I included an explicit residual
  acceptance.** Programs that recommend
  remediation for every finding lose credibility;
  some residuals are inherent (statistical power
  for rare subgroups) and accepting them
  honestly is what survives external review.
- **What this narrative deliberately leaves
  open.** The specific implementation of the
  review gate (engineering decision); the
  specific letter language for patient
  notification (clinical-communication
  decision); the specific approver hierarchy
  inside Northfield for re-deployment.

---

Maintained by [Girish Nair](https://github.com/garynair)
