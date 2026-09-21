# Exercise 04 — Reverse-Engineer a Regulator Letter — Reference Solution

## 1. Solution overview

The OCC's letter is not a four-item questionnaire. It is a
**probe**: is Trillium's MRM function actually covering its
AI/ML deployments, or have they slipped past it through the
front door of customer-service tooling. The desired posture
is *visible coverage* — Trillium can show its work, in MRM
language, with a real inventory and real incident handling.
The forbidden posture is *defensive minimization* (small
answers, narrow scope, "this is just a chatbot"). The
response plan is built around making the OCC's actual
question easy to answer favorably.

---

## 2. Deliverable 1 — "What they actually want" memo

> **TO:** CEO + CRO
> **FROM:** Chief AI Risk Officer
> **SUBJECT:** OCC AI information request — underlying read
> **DATE:** [date]

### Underlying concern

The OCC's actual question is: *"Has Trillium's MRM function
absorbed its AI/ML deployments, or are AI/ML systems
slipping past MRM through non-traditional channels — and is
the recently-announced customer-service AI a case in
point?"* The four enumerated items in the letter are
designed to test this. Item 1 (a list of all AI/ML models)
checks the scope of what Trillium acknowledges as a model.
Item 2 (MRM policies governing AI/ML) checks whether
existing MRM machinery applies. Item 3 (the customer-service
specifics) checks the most visible recent deployment.
Item 4 (incidents) checks for hidden problems.

### Why now

Three converging signals:

1. **Pilot duration.** Six months in pilot is the
   inflection point where an examiner starts wondering
   whether "pilot" is being used to keep the system
   outside MRM scope.
2. **Recent publicity.** The OCC saw the announcement.
   Examiners do not read announcements for novelty; they
   read them to identify what banks are doing that they
   have not yet reviewed.
3. **Exam cycle timing.** Large Bank Supervision conducts
   targeted reviews; AI deployments are a current focus
   area. Trillium is overdue for one.

### Desired posture

The OCC wants to see a bank that:

- Already considers the customer-service AI a *model* in
  the MRM sense and has applied (at least nominally) MRM
  scrutiny to it.
- Has a real AI inventory and a real MRM policy that
  reaches AI.
- Can name AI-specific incidents and near-incidents, with
  a credible incident-detection capability.
- Has a credible second-line independent of the function
  building the AI.

If the OCC sees this, they get one response and the file
closes. If they see anything materially different, the file
stays open and the next letter is more invasive.

### Forbidden posture

The OCC must not see:

- A "this is just a chatbot, MRM does not apply"
  framing. The MRM framework is broad by design; trying to
  define AI/ML out of it is the surest way into an
  enforcement action.
- A small list of acknowledged AI/ML models. The
  examiner is testing whether we know what we have. If
  our list is shorter than the examiner expects, the
  follow-up question is how we know it is complete.
- Incident counts that are exactly zero. Six months in
  pilot with no near-incidents is implausible; zero
  reads as "we are not measuring."

---

## 3. Deliverable 2 — Response plan

> **TO:** Response team
> **FROM:** Chief AI Risk Officer
> **SUBJECT:** OCC AI information request — response plan
> **DATE:** [date]

### Internal mobilization (30 days, day-by-day)

- **Days 1–3.** Convene response team: CAIRO (lead), CRO,
  MRM Head, Head of Customer Experience (owns the AI
  product), CISO, GC, Head of Audit. Single status meeting
  daily for the first week.
- **Days 4–10.** Produce the AI inventory (Item 1).
  Include not just acknowledged AI/ML production models
  but anything *reasonable observers* would call AI/ML —
  the LLM-based fraud-rule generator, the marketing
  segmentation model the analytics team built last
  quarter, the call-transcription system in Operations.
  If we leave any of these off, the examiner will find
  them.
- **Days 6–15.** Compile MRM policy materials (Item 2).
  Include the current SR 11-7-anchored policy *and* any
  documentation of how the policy has been (or will be)
  applied to AI/ML specifically. If a gap exists, name
  it.
- **Days 8–20.** Customer-service AI documentation (Item 3).
  System description (functional + technical), training
  data (sources, governance, retention), unauthorized-
  disclosure controls (token-level, output filtering,
  monitoring), human review procedures (sampling,
  flagging, escalation). Document the gap if any element
  is currently weak.
- **Days 15–25.** Incident review (Item 4). Pull all
  customer-service AI session logs for the pilot period;
  identify any session that surfaced unintended
  information, escalated incorrectly, or required human
  intervention. Categorize as "incident" or "near-
  incident." Document detection and response.
- **Days 25–30.** Response cover letter, internal review
  (GC, CRO, CEO), sign-off, transmission.

### Scope discipline

A real question: are there models in production at Trillium
that have not previously been classified as AI/ML by MRM —
specifically, the segmentation models, the fraud-rule
generator, the call-transcription system? Yes. The response
includes them in the inventory. The accompanying note
explains the scope question — that MRM has historically
focused on credit and capital models; that the AI program
is in the process of broadening MRM's scope; that the
inventory we are providing reflects the broader scope.

This costs us short-term embarrassment and gains us
long-term credibility. Hiding it is the worse outcome.

### Lede sentence (the cover letter opens with this)

> "Trillium's Model Risk Management function applies to all
> in-scope models, including AI/ML systems; the inventory
> below reflects a recently broadened scope that includes
> systems Trillium had not previously tracked as models,
> and the materials that follow are organised to make our
> current coverage and our remaining work plainly visible."

This sentence does three things: (1) asserts that MRM
covers AI/ML, (2) flags the broadened scope before the
examiner discovers it, (3) signals that we know we have
work remaining and we are not pretending otherwise.

### Things we will not say

True facts, not load-bearing, intentionally withheld:

- **Internal discussions about whether the customer-service
  AI is "a model."** These exist. They were the right
  conversation to have at the time. Surfacing them now
  would imply MRM treatment was a close call when in
  fact MRM treatment is the position we are taking.
- **The fraud-rule generator's accuracy degradation over
  the last quarter.** We are addressing it via the
  ordinary model-monitoring path. Volunteering it in
  this response would invite a separate review.
- **The fact that the customer-service AI vendor changed
  the underlying foundation model mid-pilot.** This was
  vendor-disclosed; we evaluated and accepted. We
  describe the current system. If asked specifically
  about model changes, we answer directly.

### Request to the OCC

A request for *a 30-day extension* if the inventory of
broadened-scope AI/ML models requires meaningful re-review.
Better to ask for the extension up front than to file an
incomplete response. We make the request only if the day-15
status indicates it is necessary.

---

## 4. Reasoning notes

- **The hardest call: scope discipline.** The reference
  takes the position that the marketing segmentation
  model, fraud-rule generator, and call-transcription
  system go into the inventory. They are AI/ML; they were
  not previously called such. The alternative is to call
  them out of scope and risk the examiner finding them.
  The cost of being forthcoming is being asked harder
  questions about MRM coverage. The cost of being
  evasive is enforcement action. The trade is one-sided.
- **Why the lede sentence matters more than anything
  else.** The examiner reads in order. The first sentence
  of the response frames every subsequent paragraph. A
  defensive lede ("Trillium's customer-service AI is a
  limited-scope pilot and is not subject to MRM until
  full production deployment") would generate ten
  follow-up questions in the examiner's mind before
  they read the first inventory row. The reference lede
  produces zero follow-up questions and lets the
  examiner read the materials in the framing we have
  set.
- **Why "things we will not say" is part of the plan.**
  Information disclosure is a controllable surface.
  Volunteering true-but-not-asked facts can shift the
  examiner's read of an entire response. The discipline
  is to answer what was asked, fully and honestly, while
  not opening adjacent doors that the examiner has not
  walked through.
- **What this response plan deliberately under-specifies.**
  The mid-pilot foundation-model change. If the OCC asks
  about model versioning, the answer is direct and full.
  If they do not ask, we describe the current system. A
  third path — proactive disclosure with a "we want to
  flag the following" note — is defensible but generally
  the wrong move at this stage; it tells the examiner
  there is more here than they asked about, which is the
  opposite of the desired effect.
- **A scenario where the recommendation would change.** If
  Trillium had a recent enforcement history (consent
  order, MOU, public action), the trade between "say
  more" and "say less" shifts toward more. The OCC's
  trust budget is already drawn down; volunteering builds
  it back. The reference assumes Trillium has clean
  recent history.

---

Maintained by [Girish Nair](https://github.com/garynair)
