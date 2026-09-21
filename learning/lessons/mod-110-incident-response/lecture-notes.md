# Module 110 — Lecture Notes

About 95 minutes of reading. §4 (the notification
matrix) is the most operationally consequential
section; §6 (post-incident review) is where
incidents become program improvement.

---

## §1. What AI incident response is

AI incident response is the operational discipline
of handling AI-related incidents from detection
through closure. It inherits classical IR practice
(NIST SP 800-61, sector IR norms) but differs in
ways that matter operationally.

### 1.1 The classical IR backbone

NIST SP 800-61 specifies a five-phase IR
lifecycle:

1. **Preparation** — readiness before any
   incident.
2. **Detection and analysis** — identifying that
   an incident occurred and what it is.
3. **Containment, eradication, and recovery** —
   stopping the incident and returning to normal.
4. **Post-incident activity** — review and
   lessons-learned.

Plus continuous **coordination and communication**
across the lifecycle.

This backbone applies to AI incidents. Programs
that abandon it produce ad-hoc responses.

### 1.2 What's different about AI incidents

Five characteristics that distinguish AI incident
response from classical IR:

1. **The incident may not have a clear "stop"
   point.** A classical breach has discrete events
   (malware in, malware out). An AI bias incident
   may have been operating for months with no
   single moment of compromise; the system was
   "working" the whole time.
2. **Containment can break the system.** Classical
   IR can isolate a compromised service. AI
   containment may require pausing the AI system,
   which has its own cost — customers cannot get
   service, dependent systems fail, operations
   degrade.
3. **Affected populations may be diffuse and
   identifiable only after analysis.** A classical
   breach affects a defined set of records; an AI
   bias incident may have affected an unknown
   number of customers across an unknown time
   period.
4. **Multiple regulators apply.** Classical
   breaches often have one or two notification
   regimes (cybersecurity + privacy). AI
   incidents may trigger AI-specific (EU AI Act
   Art. 73), classical (NYDFS, GDPR), and
   sector-specific obligations simultaneously.
5. **The "blame surface" is broader.** Classical
   IR can usually identify the compromised
   component. AI incidents implicate the model,
   the training data, the deployment, the
   operating policy, the monitoring — multiple
   layers, multiple owners.

A program that runs AI incidents on pure classical
IR misses these differences. A program that
discards classical IR runs ad hoc.

### 1.3 The CAIRO function's role

The CAIRO function is **not** Sentinel's or
Halverston's IR function. The CISO operates IR.
The CAIRO function:

- **Sets the classification expectations** (mod-107
  §6).
- **Owns AI-program-substantive incident response**
  for incidents classified as AI-program (per
  mod-107 Ex-04).
- **Co-leads joint incidents** with the CISO per
  the boundary patterns from mod-107 §5.
- **Owns external AI-program-specific
  notifications** (EU AI Act Art. 73,
  AI-specific regulator briefings).
- **Owns post-incident review** for AI-program
  dimensions of incidents.

The CAIRO function does **not**:

- Replace the CISO's IR operations.
- Run parallel containment activities.
- Author the security-engineering containment
  decisions.

This is the §5 of mod-107 boundary in operational
detail.

### 1.4 What this module owns and doesn't

This module owns the **operational discipline** of
AI incident response — the phase-by-phase
treatment, the notification matrix, the post-
incident review template, the tabletop pattern.

This module does **not** own:

- The classification taxonomy (mod-107 §6).
- The specific incident response *playbooks* for
  Sentinel's or Halverston's specific
  environment — those are CAIRO + CISO joint work
  downstream of this module.
- The evidence infrastructure that incident
  response produces evidence into (mod-108).

---

## §2. Detection and the first hour

The first hour of an incident is where the
discipline pays off. Programs without first-hour
discipline make decisions that constrain
everything that follows.

### 2.1 Detection sources

AI incidents are detected through multiple
channels:

| Source | Typical detection mode |
|---|---|
| AI program monitoring | Threshold-crossing alerts on bias, drift, performance |
| Security monitoring (SOC) | Classical security indicators + AI-specific signatures |
| Customer complaint | Customer reports of unexpected AI behaviour |
| Whistleblower / staff report | Internal observation of pattern |
| Vendor notification | Vendor discloses an issue affecting the AI system |
| Regulator inquiry | Regulator asks the question that surfaces the issue |
| Media | Public reporting surfaces an issue |
| External researcher | Bug bounty or independent security researcher |

Each detection source carries different urgency
posture. Vendor notifications and regulator
inquiries are typically the most urgent;
monitoring detections are often the least urgent
even when the underlying issue is material.

### 2.2 First-hour decisions

In the first hour:

1. **Verify the incident is real.** False alarms
   are expensive; running an incident response on
   a false positive consumes credibility. The
   first decision is whether to proceed.
2. **Classify provisionally.** Per the mod-107 §6
   taxonomy: security / AI-program / joint. The
   provisional classification routes the
   response.
3. **Assign the single named lead.** Per the
   mod-104 / mod-107 boundary patterns: one
   function leads, others contribute. The lead is
   assigned in the first hour.
4. **Convene the response team.** Who needs to be
   on the call. AI Risk Lead, CISO on-call, GC,
   relevant business-unit lead, model owner.
5. **Decide containment posture.** Three options:
   contain (pause the system), partial-contain
   (restrict scope of the system), or operate
   (continue with elevated monitoring). The
   wrong choice in either direction is
   expensive.

These decisions are made by the **single named
lead** in coordination with the response team.
The lead is empowered to decide; the team
contributes information and expertise.

### 2.3 The verification problem

A subtle problem: in the first hour, the team
often doesn't know whether the incident is real.
Three patterns:

- **Confirmed incident.** The detection signal is
  unambiguous; proceed.
- **Suspected incident.** The signal is ambiguous;
  proceed with provisional classification, plan
  to confirm/disconfirm in the first 4 hours.
- **Likely false positive.** The signal looks like
  a known false-positive pattern; investigate but
  don't escalate.

The discipline: never let "we'll wait until we
know" delay the response beyond the first hour.
Provisional classification with explicit
provisional status is the right posture.

### 2.4 The mute-the-alert temptation

When a monitoring alert fires and the team
suspects a false positive, the temptation is to
mute the alert and investigate quietly. This is
almost always the wrong move:

- Muting the alert removes the historical record
  of when it fired.
- Quiet investigation means others on the team
  don't know an investigation is in progress.
- If the alert turns out to be real, the response
  starts later than it should have.

The discipline: open the incident, classify
provisionally, investigate openly. Closing as
false positive is fine; muting silently is not.

### 2.5 What gets recorded in the first hour

The first hour produces evidence regardless of
outcome:

- The detection event (in the audit ledger per
  mod-108).
- The classification decision (and who made it).
- The response team convene event.
- The lead assignment.
- The containment-posture decision.

This evidence allows post-incident review to
reconstruct the first hour. Programs without
first-hour evidence cannot do this; they end up
with narrative reconstructions weeks later that
don't survive scrutiny.

---

## §3. Containment without overcontainment

Containment is the activity that *stops the
incident from continuing*. For AI systems,
containment is harder than for classical security
incidents and requires more judgment.

### 3.1 The containment options

For AI-related incidents:

- **Full system pause.** The AI system is
  disabled; the human-fallback path operates.
- **Capability restriction.** Some operations of
  the AI system are blocked (e.g., funds-
  transfer disabled but balance-inquiry
  continues).
- **Scope restriction.** The AI system continues
  for some users/cohorts but not others (e.g.,
  pause at one site; continue at others).
- **Elevated monitoring with continued
  operation.** No restriction but the AI system's
  outputs are flagged for human review at a
  higher rate.
- **Rollback to a prior version.** Revert to a
  known-good model version, prior prompt,
  prior configuration.

### 3.2 Choosing among them

The choice depends on:

- **Confidence in the incident.** High confidence
  warrants more restrictive containment;
  uncertainty warrants less.
- **Cost of continued operation if the incident
  is real.** Customer harm? Regulatory liability?
  Trust loss?
- **Cost of containment itself.** Customer-
  experience impact, dependent system impact,
  operational cost.
- **Containment reversibility.** Can the
  containment be relaxed quickly when the
  incident is resolved?
- **Detection capability under continued
  operation.** If the AI keeps running, can the
  team observe whether the incident is still
  occurring?

The right containment posture rarely "feels"
right at the time. Over-containment causes
visible cost; under-containment may cause
invisible cost (continued harm during the
response). Both are legitimate failure modes.

### 3.3 The overcontainment failure mode

A specific failure mode worth naming:
**overcontainment** — pausing or restricting more
than the incident actually warrants. Symptoms:

- The entire AI portfolio is paused for an
  incident affecting one system.
- Containment continues longer than necessary
  because no one wants to be the one who relaxes
  it.
- The cost of containment is materially higher
  than the cost the incident would have
  produced.

Overcontainment has a political logic — no one
gets blamed for being too cautious — but it
imposes real costs. Repeat overcontainment
patterns degrade the program's credibility with
the business and make the next incident's
containment posture harder to defend.

### 3.4 The undercontainment failure mode

The mirror image: **undercontainment** —
operating the AI system through the incident,
producing additional harm during the response.
Symptoms:

- Continued operation while the response team
  investigates.
- Customer harm during the investigation period.
- The post-incident review later finds the
  containment posture inadequate.

Undercontainment has its own political logic —
no one wants to take down a revenue-generating
system. The discipline is being able to defend
the containment posture *under counterfactual
analysis*: if the incident turned out to be
real, would the chosen posture have been
defensible?

### 3.5 The containment decision is reversible

A useful framing: containment decisions are
*provisional*, not final. The response team can
relax containment as the situation clarifies and
can re-tighten it if new facts emerge. Programs
that treat the initial containment decision as
permanent constrain themselves unnecessarily.

The discipline: revisit the containment posture
at every working session of the response team.
"Should we tighten or relax containment given
what we know now?"

---

## §4. The notification matrix

For most AI incidents, multiple notification
obligations apply simultaneously. Pre-computing
the notification matrix is one of the most
important compliance-operations deliverables (per
mod-109).

### 4.1 The notification dimensions

For each incident, the notification matrix
specifies:

| Dimension | Question |
|---|---|
| Who is notified | Specific regulator, customer cohort, business partner, board |
| What triggers | What facts about the incident trigger this notification |
| When | The specific timeline (immediate / 2 days / 15 days / etc.) |
| By whom | Which Sentinel/Halverston function leads |
| In what format | Specific format if regulated |
| With what evidence | Supporting documentation |
| With what approvals | Who must sign before transmission |

### 4.2 The 2026 obligations landscape

The notifications most likely to apply to AI
incidents:

**EU AI Act Art. 73 — serious incident reporting.**

- 2 days for fundamental-rights incidents.
- 15 days for other serious incidents.
- Immediate for critical-infrastructure threats.
- To national competent authority.
- CAIRO function leads.

**NYDFS Part 500 §500.17 — cybersecurity event
notification.**

- 72 hours from determination.
- To NYDFS Superintendent.
- CISO leads with CAIRO content for AI dimension.

**GDPR Art. 33 — personal data breach to DPA.**

- 72 hours from awareness.
- To Member State DPA.
- CISO + privacy + CAIRO.

**GDPR Art. 34 — personal data breach to data
subject.**

- "Without undue delay" — typically days,
  potentially weeks.
- To affected individuals.
- CISO + privacy + CAIRO + customer service.

**Sector-specific.**

- SR 11-7 model events — to OCC.
- FDA SaMD adverse events — to FDA.
- State insurance regulator events — varies.
- Securities events — to SEC.

**Contractual.**

- Customer contracts may require notification of
  customer-affecting incidents.
- Vendor contracts may require notification to
  vendors of incidents affecting their products.

**Internal.**

- Board (especially for material incidents).
- AI Risk Council.
- Audit Committee (for material incidents).

### 4.3 Pre-computing the matrix

The discipline: pre-compute the matrix per
incident *classification* (per mod-107 §6), not
per incident. When a specific incident occurs, the
team consults the matrix for the classification
and triggers the applicable notifications.

This requires the matrix to be *accurate* at
program quiet times — when there's no incident-
pressure and the team can think clearly. A matrix
authored during an incident is a matrix authored
under deadline pressure; pre-computation is the
only way to get it right.

### 4.4 The matrix is itself evidence

Like everything else in the program, the
notification matrix is an evidence artifact. The
matrix is signed, versioned, added to the audit
ledger. When a regulator later asks "why didn't
you notify us of incident X within the
required window?", the matrix shows whether the
notification obligation was correctly identified
and whether the response actually used the matrix.

A program that misses a notification because the
matrix was wrong has a documented oversight; a
program that misses because the matrix wasn't
consulted has a much worse problem.

### 4.5 The hardest decision in notification

The hardest call: **when do we know enough to
notify?** Regulators require notification within
hours of *awareness*; awareness is a judgment
call. Some patterns:

- **Notify provisionally.** Many regulations
  allow follow-up updates. A first notification
  with provisional information meets the
  timeline; subsequent updates fill in details.
- **Notify with caveats.** State what is known,
  what is suspected, what is unknown. Regulators
  prefer this to silence.
- **The 24-hour-decision pattern.** Treat hour 24
  of the incident response as the "are we
  notifying or not" deadline for most
  obligations. By hour 24, the team has enough
  information to decide; further delay is just
  delay.

### 4.6 Customer notification

Customer notification has its own discipline:

- **Timing.** Too early may produce panic without
  resolution; too late may produce trust loss
  when customers discover the issue
  independently.
- **Tone.** Honest about what happened, what's
  being done, what customers should do.
- **Channel.** Match the affected population's
  channels.
- **Coordination.** With the broader
  notification matrix — customer notification
  cannot precede regulatory in some regimes.

mod-105 Ex-04 (contestability) connects directly:
customers who were affected by the incident need
recourse paths that are clear and operational.

---

## §5. Investigation and root-cause analysis

After containment, the response team investigates.
The goal is *understanding what happened* — and
why — in enough depth to feed the post-incident
review and the GOVERN loop.

### 5.1 The investigation discipline

A working investigation:

- **Has a named lead.** Same single-named-lead
  pattern as the rest of the response.
- **Has a defined scope.** Investigation can
  expand but the initial scope is named.
- **Produces evidence as it proceeds.**
  Investigation findings are added to the audit
  ledger.
- **Distinguishes facts from inferences.** What
  is established vs. what is hypothesised.
- **Names what is not yet known.** Honest about
  remaining uncertainty.

Programs that conduct investigations as
narrative without these properties produce
post-incident reviews that don't survive
scrutiny.

### 5.2 The five-whys discipline

The classical root-cause technique: ask "why?"
five times, each time digging deeper. For AI
incidents:

- Why did the AI produce this output? (Because
  X.)
- Why did X happen? (Because Y.)
- Why was Y the case? (Because Z.)
- Why was Z permitted? (Because policy P didn't
  address it.)
- Why didn't policy P address it? (Because the
  policy authoring process Q missed this case.)

The five-whys eventually reaches a level where
the cause is *organisational* (a policy gap, a
process gap, a structural choice) rather than
technical. This is the right level for program
improvement.

### 5.3 The proximate-vs-systemic causation problem

A common investigation failure mode: stopping at
the proximate cause. "The model misclassified
because the input was unusual" is technically true
and operationally useless. The systemic question:
why didn't the program detect the unusual-input
pattern in advance? Why didn't the testing surface
it? Why didn't the workflow have a fallback?

Investigations that surface only proximate causes
produce post-incident reviews that recommend
fixing the proximate cause and miss the systemic
issue.

### 5.4 The blame problem

Investigation has a political dimension. Naming
the proximate cause can identify a specific
person, team, or vendor as "responsible." This is
almost always counterproductive:

- It encourages people to defend rather than
  contribute.
- It misses the systemic issues that allowed the
  proximate cause to occur.
- It produces post-incident actions that punish
  rather than improve.

The discipline: investigate causes, not blame.
The investigation report identifies what
happened and why; consequences for individuals
are a separate process owned by HR and management,
not by the AI incident response.

This is the same discipline NTSB applies to
aviation incident investigation; it's been studied
extensively and is the right posture.

### 5.5 What investigation produces

The investigation produces:

- A **timeline** of the incident.
- A **causal chain** from proximate to systemic.
- A **set of facts** established by evidence.
- A **set of inferences** identified as such.
- A **set of unknowns** not yet resolved.

These feed the post-incident review.

---

## §6. Post-incident review and tabletop readiness

The post-incident review is the artifact that
turns an incident into program improvement. The
tabletop exercise is the practice that ensures the
program can respond to the next incident.

### 6.1 The post-incident review

A working post-incident review has these
properties:

- **Conducted within 30 days** of incident
  closure (faster for material incidents).
- **Includes everyone** materially involved in the
  response and the underlying system.
- **Is led by someone not in the chain of
  responsibility.** The AI Risk Lead can lead the
  review of an incident their function did not
  lead; internal audit can lead complex cases.
- **Produces a written report.** Signed, added to
  the audit ledger.

The report covers:

1. The incident: what happened.
2. The response: what was done.
3. What worked: positive findings (programs
   without these in their reports are not
   serious about review).
4. What didn't: substantive findings.
5. Root causes: the systemic causes from §5.
6. Recommendations: what the program should
   change.
7. Status of recommendations: which have been
   accepted, by whom, with what timeline.

### 6.2 The "what worked" discipline

A common review failure: focusing only on what
went wrong. Programs that produce only-criticism
reviews develop two problems:

- The response team becomes defensive about
  future incidents, slowing response.
- The review misses what should be preserved as
  practice.

A working review names what worked specifically.
The first responder's quick classification, the
CISO on-call's good judgment on containment, the
GC's fast notification authorisation — these are
worth identifying so they get reinforced.

### 6.3 Recommendation discipline

Recommendations from post-incident review must:

- Be **specific** — not "improve monitoring" but
  "add an alert when the demographic-parity gap
  exceeds 2pp at any single site."
- Be **assigned** — to a specific role with a
  specific timeline.
- Be **tracked** — into the program's ongoing
  improvement backlog with status updates.
- Be **closed** — at completion, with evidence
  of completion.

Reviews that produce recommendations without
this discipline produce wallpaper.

### 6.4 The tabletop exercise

A tabletop exercise simulates an incident with
the response team to test readiness without
the cost or risk of a real incident. Properties of
a working tabletop:

- **Realistic scenario.** Based on a real
  incident pattern (often a near-miss from the
  past year, or a peer-institution public
  incident).
- **Cross-functional.** Includes everyone in the
  notification matrix's response path.
- **Time-pressured.** Real incident timelines
  are compressed; tabletop should compress them
  too.
- **Decision-forcing.** The exercise produces
  specific decisions the team has to make in
  real time.
- **Reviewed.** The exercise itself gets a
  post-exercise review.

### 6.5 Tabletop cadence

A working program runs tabletops:

- **Quarterly** for the response team in
  rotation across scenario types.
- **Annually** with broader participation
  (Board Risk Committee observer; external
  facilitator).
- **On-demand** when a new incident type emerges
  (e.g., novel attack pattern surfaced at a
  peer institution).

Programs that don't run tabletops discover
weaknesses during real incidents.

### 6.6 Tabletop anti-patterns

Common failure modes:

- **Performance art.** The tabletop produces a
  good-looking report without testing the team's
  actual response capacity.
- **Tabletop-as-training.** Using tabletops to
  train new team members rather than to test
  existing readiness. (Training is good but
  shouldn't be confused with readiness testing.)
- **Same scenario repeatedly.** The team learns
  the scenario rather than the general response
  pattern.
- **No findings.** Tabletops that find no
  problems are either too easy or being
  conducted as performance.

A tabletop that finds 2–4 substantive issues is
doing its job. Finding zero is suspicious;
finding ten suggests the scenario was unrealistic.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **NIST SP 800-61 Rev. 2** — Computer Security
   Incident Handling Guide. The classical IR
   backbone §1.1 builds on.
2. **EU AI Act Art. 73 + Implementing Acts** —
   the AI-specific notification regime.
3. **NTSB investigation procedures** — the model
   for blame-free root-cause analysis (§5.4).
