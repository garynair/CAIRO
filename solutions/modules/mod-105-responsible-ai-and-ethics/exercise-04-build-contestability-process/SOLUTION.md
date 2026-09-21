# Exercise 04 — Build a Contestability Process — Reference Solution

## 1. Solution overview

A contestability process for **Northfield Mutual's
AI-fraud-flagged claims**. The named decider is a
**Claims Review Specialist** in Claims Operations
(deliberately not in the AI program). The path is
multi-channel (online + phone + written). Resolution
target: 5 business days. The worked example walks a
poor-lighting-photo case through to a re-routed-to-
standard-review outcome.

---

## 2. Process design

> **Northfield Mutual — AI Fraud-Flag Contestability Process**
> *Version 1.0. Owned by Chief AI Risk Officer; operated by
> Claims Operations.*

### The six elements

**Element 1 — The named decision.**

What is being contested: the **classification of the
claim's photographic evidence as warranting fraud
review**. Not the broader fraud-review pathway, not
the claim's eligibility, not the settlement amount —
specifically the photo-classification outcome that
routed the claim into fraud review rather than into
express settlement or standard review.

This precision matters. An affected insured contesting
"the claim being delayed" is harder to operationalise
than an affected insured contesting "the photo being
classified as unusual." Naming the specific decision
makes the contestation tractable.

**Element 2 — The named decider.**

The **Claims Review Specialist** in Claims Operations.

This role:

- Is staffed (5 FTE initially) within Northfield's
  Claims Operations function.
- Reports to the VP of Claims Operations.
- Does **not** report through the CAIRO function — this
  preserves contestation independence from the AI
  program that produced the original classification.
- Is trained in (a) the AI system's documented
  capabilities and limitations, (b) Northfield's
  fraud-review criteria, and (c) the contestation
  process itself.

Each contestation is assigned to a specific Claims
Review Specialist with a named contact (name, email,
direct phone). The affected insured deals with a
human, not a desk.

**Element 3 — The path.**

Multi-channel:

- **Online:** a dedicated contestation form on
  Northfield's customer portal, requiring (a) the
  claim number, (b) a brief explanation of why the
  insured is contesting, (c) any additional
  information or photographs they wish to provide.
  The form is plain-language (8th-grade reading
  level reviewed); does not require AI vocabulary.
- **Phone:** a dedicated contestation phone line
  (Northfield's existing claims contact center,
  with a specialized routing keyword) where the
  insured can reach a Claims Review Specialist
  directly. Calls are recorded for the file.
- **Written:** mail-in form available on request
  for insureds without online access.

Required information is minimal — claim number plus
the contestation. Additional supporting information
(better lighting photos, witness statements, etc.)
is welcomed but never required.

**Element 4 — The timeline.**

| Stage | Timeline | Owner |
|---|---|---|
| Acknowledgement of contestation receipt | Within 1 business day | Claims Operations intake |
| Initial review by Claims Review Specialist | Within 3 business days | Claims Review Specialist |
| Re-classification decision communicated to insured | Within 5 business days from receipt | Claims Review Specialist |
| Claim re-routing (if applicable) | Same day as decision | Claims Operations |
| Settlement (if applicable) | Per re-routed pathway | Claims Operations |

Average AI-fraud-flagged claim delay is 23 days. The 5-
business-day resolution target is materially shorter
than the harm window.

**Element 5 — The resource.**

- The contestation process is **free** to the
  insured.
- No legal representation is required; insureds may
  bring representation if they choose.
- The Claims Review Specialist provides bilingual
  service (Northfield's primary languages: English +
  Spanish; additional language access via
  interpreter service).
- No documentation requirement beyond claim number
  and brief explanation.

**Element 6 — The outcome.**

The Claims Review Specialist can:

1. **Maintain the fraud-review classification** —
   with documented reasoning. Notice to insured
   includes the reasoning and the alternative
   recourse options (see below).
2. **Re-route the claim to standard review** — if
   the Specialist determines the AI's
   classification was incorrect given context
   (lighting, vehicle type, claim narrative).
3. **Re-route the claim to express settlement** — if
   the fraud concern is fully resolved.
4. **Refer the case to a Senior Claims Review
   Specialist or to the Fraud Investigation
   Manager** — if the case is unclear or has
   indicators not surfaced in the original
   classification.

Outcomes 2, 3, 4 are *changes to the AI's original
decision* — meaningful, not procedural.

### Recourse alternatives

Outside the formal contestation process, affected
insureds at Northfield can:

- **Provide better photographs** — encouraged but not
  required.
- **Speak to their broker** — if applicable to the
  insured (commercial brokers, agent-of-record
  representatives).
- **File a complaint with the state insurance
  regulator** — Northfield is supervised by NY, CA,
  and several other state insurance regulators; the
  insured has direct access to their state regulator.
- **Choose a different insurer at renewal** — the
  ultimate market-based recourse.

These are recorded in the contestation process
documentation provided to insureds so they know their
options. Honest acknowledgment: the regulator-complaint
path is the strongest external check on this process.

### Contestability anti-patterns avoided

| Anti-pattern (§5.4) | How this process avoids it |
|---|---|
| Contestation channels that route to the same model | The Claims Review Specialist makes a *human* decision; the model is one input, not the decider |
| Contestation timelines that exceed the harm window | 5 business days vs. 23-day average delay; structurally shorter than the harm |
| Contestation requiring expertise the affected party does not have | Form requires only claim number + brief explanation; no AI vocabulary required |
| Contestation without resourcing | 5 FTE Claims Review Specialists staffed at launch |

### Pre-launch verification

Before the process goes live:

- The form has been usability-tested with five non-
  technical users (all of whom successfully submitted
  test contestations).
- The phone routing has been tested.
- The Claims Review Specialists have completed
  training (including the AI-system-capabilities
  module).
- The first month is treated as a soft launch with
  daily case-review by Claims Operations leadership.

---

## 3. Worked example

> **Case:** A small-business owner — call her Maria
> Rodriguez, owner of a regional landscaping company
> — submits a claim with photos taken at 7:42pm
> in November (low light, with mobile-phone flash) of
> her commercial van rear-ended in a parking lot.

### Stage 1 — Original AI decision (5 minutes after claim submission)

The vision model classifies the photo's damage pattern
as "unusual" — the low-light flash artefacts mask the
damage geometry, and the angle is one the model has
seen less frequently. The model flags the claim for
fraud review with confidence 0.62 (above Northfield's
0.55 threshold). The standard claims-flow routes the
claim into the fraud-review pathway. Maria is notified
that her claim is "under additional review."

### Stage 2 — Maria contests (Day 3 after submission)

Maria, frustrated by the delay and confused by the
"additional review" framing, contests through
Northfield's online contestation form. Her message:

> *"I submitted this claim 3 days ago and I am told
> it is under additional review for fraud. There is
> no fraud. The accident happened in the parking lot
> after our last shift. I have time-stamped photos,
> witness statements from two of my employees, and a
> police report. I need this claim resolved — I'm
> running a small business and the van is essential.
> Please review."*

She uploads the additional documents.

### Stage 3 — Acknowledgement (Day 3)

Within 1 business day, Maria receives an email
confirming her contestation was received and providing
the name and direct contact information of her
assigned Claims Review Specialist, **Daniel Chen**.
The email includes the expected timeline (3 business
days for initial review; 5 business days for the
decision).

### Stage 4 — Specialist review (Days 4–5)

Daniel reviews:

- The original photos. He identifies the lighting and
  angle issues that produced the model's "unusual"
  classification.
- The additional documentation Maria provided —
  time-stamped photos, witness statements, police
  report. The narrative is internally consistent.
- The model's classification reasoning (via the
  model's documented explainability output). The
  model's concern centered on visual ambiguity, not
  on a pattern indicating fraud.
- The historical pattern of similar low-light parking-
  lot claims at Northfield. The model has
  historically over-flagged this category.

Daniel reaches a conclusion: the AI's classification
was incorrect given context. The claim should be
re-routed to standard review.

### Stage 5 — Decision and notification (Day 5)

Daniel communicates the decision:

> *"Hello Maria — thank you for the contestation and
> the additional documentation. I have reviewed your
> claim and the photographs you originally submitted.
> The flag for additional review was driven by the
> lighting conditions in the original photos, which
> made the damage pattern harder to read. Based on
> the additional documentation you provided
> (time-stamped photos, witness statements, police
> report), I am re-routing your claim to standard
> review. You should receive a settlement decision
> within 5 business days. I'm here if you have any
> further questions."*

The claim is re-routed. Maria receives standard-review
processing and a settlement decision on Day 10 after
the original submission — meaningfully earlier than
the average AI-fraud-flagged 23-day delay.

### Stage 6 — Loop closure (Days 5–30)

Daniel logs the contestation outcome with two flags:

- The model's classification was overturned (this
  becomes a data point for model-performance monitoring).
- The model's classification reasoning centered on
  lighting / angle ambiguity (this is added to the
  *pattern register* the Algorithm Quality Office
  reviews monthly).

If this pattern recurs — multiple claims contested
and overturned on lighting / angle grounds — the
Algorithm Quality Office surfaces a finding for
model improvement (training-data augmentation, lighting-
robustness validation pattern, threshold adjustment).
The contestation outcomes feed back into the program's
GOVERN loop (per mod-103 §6.5).

---

## 4. Reasoning notes

- **Why the Claims Review Specialist is in Claims
  Operations, not the AI program.** Independence.
  An AI-program-staffed contestation reviewer carries
  the structural concern that they are evaluating
  their own program's output. Claims Operations
  staffing has a different center of gravity — Claims
  Ops wants the claim resolved correctly; AI program
  wants the AI's reputation defended. The right
  incentives are with Claims Ops for this case.
- **Why the 5-business-day target.** Materially
  shorter than the 23-day average harm window. Faster
  would be better but Claims Review Specialist
  workload constraints make sub-5-day commitments
  unreliable. The honest commitment is what the
  process can deliver consistently.
- **Why the form requires only claim number + brief
  explanation.** §5.4 anti-pattern: contestation
  requiring expertise the affected party does not
  have. Most insureds do not know what to write to
  contest an AI decision. The minimal form puts the
  burden on the Specialist to do the review work,
  not on the insured to construct an argument.
- **Why the worked example includes the loop-closure
  step.** mod-103 §6.5 — the loop closes when
  individual cases feed program-level change. The
  Maria case is one of many; the *pattern register*
  is how individual contestations become program
  evidence. A contestability process disconnected
  from GOVERN is a customer-service feature, not a
  governance mechanism.
- **What this process deliberately under-specifies.**
  The Specialist's specific decision-making rubric.
  Specialists exercise judgement informed by
  Northfield's fraud-review criteria, the AI's
  documented behaviour, and the insured's evidence.
  Codifying the rubric would over-constrain.
- **What I would do differently in v2.** Add a
  proactive notification path: when a claim is
  fraud-flagged, the insured receives explanation of
  the contestation option *at the time of flagging*,
  not just on inquiry. The current process requires
  the insured to seek out the contestation option;
  the v2 process would surface it.
- **The hardest call.** Whether to require the
  Specialist's decision to be reviewed by AI program
  before being communicated. Considered, rejected.
  Adding the program-level review step (a) slows the
  process, (b) reasserts the dependence the
  independence design was meant to avoid, and (c) is
  unnecessary — Claims Ops Specialists are trained
  appropriately and can make defensible decisions.
  The program-level review happens at the *pattern*
  level via the Algorithm Quality Office, not at the
  individual-case level.

---

Maintained by [Girish Nair](https://github.com/garynair)
