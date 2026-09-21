# Module 105 — Lecture Notes

About 100 minutes of reading. §3 (bias and fairness) is
the technically densest section; §6 (operationalizing
ethics) is the most operationally consequential.

---

## §1. What AI ethics is and is not

AI ethics is the discipline that asks *what we should and
should not build, and how we should and should not deploy
what we build*. It sits adjacent to AI governance and AI
compliance, but is not identical to either.

### 1.1 The honest distinctions

mod-101 §1 named the neighbors of AI governance. The same
distinctions are useful here, this time centered on
ethics:

| Discipline | Question | Source of authority |
|---|---|---|
| Compliance | Are we doing what we are required to do? | External law and regulation |
| Risk management | Are the consequences of our choices acceptable? | Enterprise risk appetite + materiality |
| Ethics | Should we do this, regardless of whether we are required to? | Values + reasoning |
| Governance | How do we decide and account for our choices? | Organisational charter |

Ethics's source of authority is the most fragile. There is
no external regulator to defer to, no quantitative model to
calculate against, no charter to point to. Ethics requires
**reasoning** — and CAIRO ethics work requires showing the
reasoning, not just announcing the conclusion.

### 1.2 What ethics is for, operationally

A working CAIRO ethics function does three things:

1. **Surfaces value choices** that are implicit in product
   and platform decisions. "We default to using customer
   data X for purpose Y" is a value choice presented as a
   technical default. Naming the choice is the first move.
2. **Insists on specific responses to specific situations.**
   "Be fair" is not a response. "When evaluating
   applications from cohort A, the model's positive-
   prediction rate must not fall below Z relative to
   cohort B's rate unless specifically justified" is a
   response.
3. **Holds the position when it is uncomfortable.** The
   most important ethics work is keeping a decision honest
   when the business pressure is to soften it. Programs
   that cannot do this become *ethics theater*.

### 1.3 What ethics is not

Honest distinctions:

- **Ethics is not safety.** Safety is about catastrophic
  harm thresholds; ethics is about how routine harms are
  distributed and how they are remediated. Catastrophic-
  risk programs (Anthropic-style RSPs) are *adjacent* to
  ethics work but are not it.
- **Ethics is not compliance with ethics laws.** Where
  ethics shows up in law (EU AI Act fairness obligations,
  CFPB fair-lending enforcement), compliance frameworks
  take over. The CAIRO's ethics work is what happens
  *outside* what regulation has yet codified.
- **Ethics is not principles documents.** A principles
  document is not an ethics program. The principles are
  the *cheap* part; the operational implications are
  where the cost and value live.
- **Ethics is not consensus.** Many ethics questions do not
  have consensus answers and forcing one is itself
  unethical. The CAIRO's job is sometimes to *name* a
  disagreement rather than resolve it.

### 1.4 Why this matters for the CAIRO

The CAIRO is one of the few executive roles whose principal
output is *judgement in the absence of external rules*.
CISOs follow security frameworks; CFOs follow accounting
standards; CAIROs face questions that no framework has
answered. The ability to do ethics work *specifically*,
not just principally, is the discipline that distinguishes
a credible CAIRO from a sympathetic one.

---

## §2. The principles landscape

You will encounter many AI ethics principles documents.
Several of them are well-respected and load-bearing in
specific contexts. Several others are produced primarily
for the producing organisation's reputational benefit.
Knowing which is which is part of the skill.

### 2.1 The documents that actually matter in 2026

| Document | Year | Why it matters |
|---|---|---|
| OECD AI Principles | 2019 (updated 2024) | Upstream of NIST AI RMF and EU AI Act; the closest thing to international consensus |
| UNESCO Recommendation on the Ethics of AI | 2021 | The broadest international ethics statement; adopted by 193 countries |
| IEEE 7000 series | 2021–2026 | Standards-grade ethics; especially IEEE 7000 (process), 7001 (transparency), 7002 (data privacy), 7003 (bias) |
| EU HLEG Ethics Guidelines for Trustworthy AI | 2019 | Upstream of EU AI Act; superseded operationally by the Act but still cited |
| NIST AI RMF preamble | 2023 | Names the values the framework operationalizes |
| Asilomar AI Principles | 2017 | Frontier-AI focused; useful in capability-tier governance discussions |
| Microsoft Responsible AI Standard v2 | 2022 | Practitioner reference; one well-developed operationalization |

There are dozens of others. Most either substantially
overlap with the above or are organisation-specific
documents adapted from the above.

### 2.2 The convergence problem

Most ethics principles documents say roughly the same
things at the principle level:

- Be fair / non-discriminatory
- Be transparent / explainable
- Respect privacy
- Be accountable
- Be safe / robust
- Respect human autonomy
- Be beneficial / promote well-being

The convergence at this level is genuine — there is real
international consensus on these as the *categories* of
concern. The convergence is also misleading: when the
principles are operationalized, the documents diverge
sharply on the specifics.

A useful pattern: convergence at the principle level is
*evidence the principles are meaningful*. Divergence at
the operationalization level is *evidence the
principles are operationally non-trivial*. The discipline
is not to pick one set of principles, but to navigate the
operational divergence honestly.

### 2.3 Where principles diverge in practice

Three examples of operational divergence:

**On bias.**

- OECD AI Principles: AI should be "non-discriminatory"
  but provides no operational definition.
- EU HLEG: emphasizes "equal opportunity"; operationally
  closest to disparate-impact analysis.
- IEEE 7003: bias is treated as a measurable property
  with multiple competing metrics; emphasizes documenting
  trade-offs.
- Microsoft RAI: treats fairness as a property of the
  *system in context*; requires per-use-case analysis.

Each of these would lead to a different bias-validation
design for the same model. §3 of these notes treats this
in operational depth.

**On transparency.**

- OECD: transparency to those "adversely affected".
- EU AI Act: detailed technical documentation (Art. 11
  + Annex IV) plus transparency to deployers (Art. 13)
  and human oversight (Art. 14) — explicitly separated.
- IEEE 7001: transparency as a property requiring
  audience-specific explanations.
- NIST AI RMF: emphasizes interpretability as one of
  several "trustworthy characteristics".

§4 of these notes treats transparency by audience.

**On autonomy and human oversight.**

- OECD: human-centered values; human oversight is a
  general norm.
- EU AI Act Art. 14: specific human-oversight
  requirements for high-risk systems.
- IEEE 7000 §6: requires explicit identification of
  decisions delegated to AI vs. those reserved to
  humans.
- Asilomar Principle 16: humans should retain control
  over how AI systems affect them.

The operational design implications are very different.

### 2.4 Choosing a "framing principle set"

A working CAIRO ethics function picks a *framing principle
set* — a small set of principles the program treats as
authoritative for its own decisions. This is *not* the
same as picking one document and disregarding others.
It is the discipline of being *explicit* about which
principles you will treat as operationally load-bearing.

A defensible framing principle set has these properties:

- **Locatable** in at least one authoritative document
  (so the framing is not idiosyncratic).
- **Small** (5–7 principles maximum).
- **Operationalizable** — for each principle, the
  program names what specific operational test it
  satisfies.
- **Reviewable** — periodically revisited as the
  program matures.

Exercise 01 asks you to compare three documents and find
the *operational disagreement*. That disagreement is
where the framing-principle-set choice actually matters.

---

## §3. Bias and fairness beyond demographic parity

Bias and fairness is the most technically rich area of AI
ethics. It is also the area where ethics theater is most
common — programs claim bias mitigation by computing one
metric, ignoring the metric's known limitations, and
declaring victory.

This section is operationally dense because the operational
choices are dense. The principle "AI should be fair" gives
no guidance on which metric to compute or what threshold to
hold to. The discipline is making those choices specifically.

### 3.1 The basic metrics

Several bias metrics in regular use. None is correct in
isolation; all carry assumptions.

| Metric | What it measures | Common name |
|---|---|---|
| Demographic parity | Equal positive-prediction rate across groups | Statistical parity |
| Equal opportunity | Equal true-positive rate across groups (within the qualified population) | Equality of opportunity |
| Equalized odds | Equal true-positive AND false-positive rates across groups | Equalized odds |
| Predictive parity | Equal positive predictive value (precision) across groups | Predictive parity / calibration |
| Treatment equality | Equal ratio of false-negative to false-positive across groups | Treatment equality |
| Counterfactual fairness | Output should not change in the counterfactual world where the group attribute is different | Counterfactual fairness |
| Individual fairness | Similar individuals get similar predictions | Individual fairness |

Each is grounded in a different intuition about what
fairness *means*. Each has been argued for in the academic
literature. None can be the answer alone.

### 3.2 The impossibility result

The most important result in algorithmic fairness is
*Chouldechova (2017) / Kleinberg, Mullainathan, Raghavan
(2016)*: in any context where group base-rates of the
target outcome differ, you cannot simultaneously satisfy:

1. Predictive parity (equal precision across groups).
2. Equal false-positive rates.
3. Equal false-negative rates.

You can have any two; you cannot have all three. This is
not a flaw in current algorithms — it is mathematically
unavoidable.

The practical implication: **every fairness choice is a
trade-off**. There is no metric set that satisfies all
ethically-resonant fairness definitions simultaneously
in any context with unequal base rates — and unequal
base rates are the norm in most real decisioning
contexts.

A program that claims to have eliminated bias on all
metrics is either (a) operating in a base-rate-equal
context (rare), (b) using a metric set that hides the
trade-off, or (c) wrong.

### 3.3 Choosing a metric set

The honest approach: pick a metric set that reflects the
*specific* fairness commitment you are making, and own
the trade-off.

A useful pattern: choose **2–3 metrics** that together
characterize the bias surface, with explicit awareness
that no choice satisfies all definitions.

Examples of defensible metric sets:

- **For credit decisioning**: predictive parity (so the
  precision of "approve" predictions is similar across
  groups — this addresses CFPB's adverse-action concern)
  + equal opportunity for the qualified population (so
  qualified applicants from minority groups get
  approved at the same rate as qualified majority
  applicants).
- **For clinical triage**: equalized odds (so both
  over- and under-triage rates are matched across
  groups — clinical safety requires both).
- **For content moderation**: equal-opportunity-style
  metric for protected-speech contexts + treatment-
  equality for harmful-content categories.

The right metric set is context-dependent. The discipline
is naming why a chosen set is appropriate for the
context.

### 3.4 Beyond metrics: process fairness

Fairness is not entirely captured by output metrics.
Process-fairness concerns:

- **Procedural fairness.** Was the affected party
  treated according to a consistent process?
- **Representational fairness.** Are the model's outputs
  perpetuating stereotypes in their representation of
  groups (e.g., generative outputs that consistently
  represent doctors as male)?
- **Distributive fairness.** Are the benefits of the
  system distributed in a way the organisation can
  defend?

The mod-103 §2 taxonomy treats bias as one risk category
because the operational machinery is similar. The
operational machinery is *not* sufficient — the value
choices about which fairness conception to enforce sit
above the machinery.

### 3.5 Subgroup discovery

The hardest practical fairness problem: you do not know in
advance which subgroups will exhibit disparate impact.

The classical pattern is *pre-specified protected classes*
(race, sex, age, etc.). The classical pattern is
necessary but not sufficient for AI systems, where:

- Models can produce disparate impact along axes nobody
  thought to test.
- Combinations of attributes can produce disparate impact
  even when each attribute alone does not.
- Behavioral and linguistic patterns can create
  effectively-protected groups (Section 2 of mod-103
  exercise-02 worked example named this for the chat
  agent).

Subgroup discovery patterns:

- **Slice-finding tools** that identify subgroups where
  model performance differs significantly from overall.
- **Clinical-population stratification** in healthcare
  contexts.
- **Self-reported community-level evaluation** when
  feasible.

Subgroup discovery is an *under-specified* discipline. No
single tool reliably finds all relevant subgroups. The
discipline is to run *several* methods, treat their union
as the analysis space, and document the methods used.

---

## §4. Transparency and explainability — what is owed to whom

Transparency is one of the most over-claimed and under-
specified properties in AI governance. "The model is
explainable" without specifying *what is explained* and
*to whom* is the most common form of ethics theater.

The discipline: transparency is *audience-specific*. What
is owed to a regulator is not what is owed to a customer
is not what is owed to an internal validator. Programs
that conflate these produce documents that satisfy none of
the audiences.

### 4.1 The audience taxonomy

| Audience | What they need | Why |
|---|---|---|
| Regulator | The complete technical and process documentation | To verify compliance and to investigate after incidents |
| Internal validator (MRM, audit) | Reproducibility-by-another-competent-professional | To independently verify the model's fitness |
| Senior management / board | Risk-shaped summary with material findings | To exercise oversight |
| External business partners (deployers under EU AI Act) | Operating instructions and limitations | To use the system correctly |
| Affected parties (customers, employees, patients) | Decision-specific explanations + recourse | To understand and contest decisions |
| Affected communities | Aggregate-level transparency about system behaviour | To exercise democratic accountability |
| Internal developers | Model behaviour analysis | To improve the system |
| Curious external public | High-level system descriptions | To exercise informed citizenship |

Each audience requires *different content* at *different
depth*. A single "explainability report" that tries to
serve all audiences serves none.

### 4.2 Regulator-grade transparency

The EU AI Act establishes the most demanding regulator
transparency requirements in current law. Art. 11 + Annex
IV require a technical file covering ~12 documented
items per high-risk system (mod-102 §2.4). Member-state
authorities can request access at any time.

A program that can produce the Annex IV technical file
on demand passes regulator-grade transparency. A program
that produces it under deadline pressure does not. The
discipline is *continuous* maintenance, not on-demand
construction.

### 4.3 Affected-party transparency

The most contested category. What is owed to a customer
denied credit by an AI system? To a patient flagged for
intervention? To an employee whose performance review
included AI-generated assessment?

Three principles that survive operational pressure:

1. **The decision must be explainable in terms the
   affected party can act on.** "The model gave you a
   low score" is not actionable. "Your score was lowered
   primarily by the recent drop in your average account
   balance and the high number of recent credit
   inquiries" is — the affected party can address those.
2. **The explanation must be true.** Post-hoc rationalisations
   that bear no relation to the actual model's reasoning
   are ethically worse than no explanation. Some
   explainability techniques (LIME, SHAP) produce
   explanations that are *consistent* with the model's
   outputs but may not reflect the model's actual reasoning.
3. **The explanation must come with a path forward.** The
   affected party needs to know what they can do —
   contest, appeal, modify the inputs, wait for re-
   evaluation. Explanation without recourse is information
   without empowerment.

### 4.4 The mechanical-explainability trap

A common pattern: the program adopts SHAP, LIME, or
similar attribution technique; outputs feature-attribution
charts to affected parties; declares transparency
achieved.

This fails the §4.3 principles in subtle ways:

- The feature attribution is *consistent with* the model
  but may not be its actual reasoning.
- The attribution is technically correct but cognitively
  opaque to affected parties.
- The attribution does not specify what the affected
  party should *do*.

This is not an argument against SHAP and LIME. They are
useful tools. The argument is against treating the *tool
output* as transparency in the §4.3 sense. Transparency
is a property of the relationship between the system and
the audience, not a property of an attribution chart.

### 4.5 Process transparency vs. model transparency

Often missed in AI governance: *how a decision was
reached procedurally* is sometimes more important than
*what the model computed*. A patient who knows the
clinical workflow that produced an AI-assisted
recommendation may need that more than a heatmap of the
model's attention.

A working transparency standard includes process
transparency as a first-class category.

### 4.6 What this section recommends

The operational form: **a transparency standard that
defines, per audience type, the content + depth +
delivery format the program will provide**. Exercise 03
asks you to author one.

The standard is *short* — typically 2–3 pages — and
*specific*. Standards that include "as required" or "as
appropriate" are not standards; they are wishes.

---

## §5. Contestability and recourse

Contestability is the affected party's ability to
challenge a decision. Recourse is what they can do about
it. Together they define whether the system is operating
*on* affected parties or *with* them.

### 5.1 Why contestability is hard

Contestability requires several things that AI systems
often lack:

- A **named decision** the affected party can identify.
  ("The bank denied my application" — clear. "The
  system surfaced concerns about your transaction" —
  unclear what is being contested.)
- A **named decider** the affected party can address.
  ("Speak to your loan officer" — clear. "The AI
  recommended denial; the underwriter agreed" — who
  do you contest?)
- A **path** for raising the contestation. Form?
  Email? Phone? Web?
- A **timeline** for resolution. Within what window?
- A **resource** for the affected party. Free? Paid?
  Self-serve? Mediated?
- An **outcome** that can change the decision. Override?
  Re-evaluation? Compensation?

A system missing any of these has not implemented
contestability; it has implemented a complaints process.

### 5.2 Recourse

Recourse is what the affected party can do *outside*
contestation. The two interact: a system with strong
contestation but weak recourse forces every concern into
the contestation channel; a system with strong recourse
but weak contestation lets the affected party route
around the formal process.

Recourse mechanisms include:

- **Modifying the inputs the system uses.** ("I can pay
  off this card to improve my credit profile.")
- **Waiting for the system to re-evaluate.** ("My
  credit score will update after the next reporting
  cycle.")
- **Choosing a different channel.** ("I can apply at a
  competitor.")
- **Using a different relationship.** ("I can ask my
  banker directly.")

Recourse design is often invisible to the system
designer because it is *what the affected party does to
work around the system*. Honest CAIRO ethics work surfaces
recourse explicitly and assesses whether the recourse
options are reasonable.

### 5.3 Contestability in regulated contexts

Several regulations explicitly require contestability:

- **EU AI Act Art. 14** — human oversight obligations
  for high-risk systems.
- **GDPR Art. 22** — right not to be subject to solely
  automated decisions (with conditions); right to
  obtain human intervention.
- **CFPB / Reg B / ECOA** — adverse-action notices
  include the right to obtain the model's reasons.
- **EU AI Act Art. 86** — right to explanation of
  individual decisions for affected persons.

Where contestability is regulated, the design must meet
the regulation's specific requirements. Where it is not,
the program is making an ethical choice that the
regulator has not yet codified.

### 5.4 Contestability anti-patterns

- **Contestation channels that route to the same model.**
  An automated appeals process that uses the same model
  re-evaluating the same inputs is not contestation.
- **Contestation timelines that exceed the harm window.**
  An employment-decision contestation that takes 90 days
  to resolve while the affected party is unemployed is
  not effective.
- **Contestation that requires expertise the affected
  party does not have.** A contestation form that asks
  the affected party to identify which of the model's
  features were incorrectly weighted is asking the wrong
  party to do the work.
- **Contestation without resourcing.** A contestation
  process that exists on paper but has no staffing is
  worse than acknowledging that contestation is not
  available.

### 5.5 Building contestability in

The discipline: contestability is **a design property**,
not a feature added at the end. A system designed with
contestability in mind looks different from a system
that is otherwise complete and then has a contestation
page added.

Design properties that support contestability:

- Decisions are **logged with sufficient context** that a
  human reviewer can re-evaluate.
- Affected parties **know they are being affected** by
  an AI system at the time of the decision.
- The **reviewing role is named** and reachable.
- The **timeline is bounded** by policy.
- The **outcome is reported** to the affected party.

Exercise 04 asks you to build a contestability process
for a specific context.

---

## §6. Operationalizing ethics

The CAIRO function does not operate ethics in the abstract.
It operationalizes ethics in three concrete places:

1. **In the program standards** (the policy hierarchy
   from mod-101 / mod-103).
2. **In the decisions the AI Review Board makes**.
3. **In the responses to specific situations** where
   the program is being tested by business pressure.

### 6.1 Ethics in standards

The program's standards (development standard, validation
standard, monitoring standard, etc.) encode value choices.
A development standard that requires subgroup performance
evaluation has made a value choice that some development
processes that do not require it have not.

The discipline: standards should *name* the value choices
they encode. A development standard that requires
subgroup evaluation should state — in the standard
itself — *why*. ("To ensure fairness in performance across
affected populations, per Cardinal's adopted fairness
framing — see §6.3 of the program charter.") The naming
makes the standard durable; standards whose value
choices are implicit get watered down over time without
anyone noticing.

### 6.2 Ethics in Review Board decisions

The AI Review Board (mod-101 §5) decides specific cases.
Each decision either *honors* or *erodes* the program's
ethical commitments. A working Board:

- **Names ethical questions explicitly** when they
  arise. Decisions that involve ethical trade-offs get
  flagged as such in the meeting minutes, not glossed
  as technical questions.
- **Documents the reasoning** for ethical decisions in
  enough detail that a future Board can understand the
  precedent.
- **Resists pressure to relax** previously-decided
  positions without explicit re-decision. A Board that
  silently drifts on a fairness threshold has lost the
  position.

### 6.3 Ethics under business pressure

The hardest ethics work happens when the business wants
to do something that the program's ethical posture
disfavors. Typical patterns:

- The product team wants to deploy a model the
  validation flagged as marginal on fairness.
- The vendor relationship requires using a foundation
  model whose training data the vendor will not
  disclose.
- A regulator inquiry is pending and the temptation is
  to soften the program's findings.

A CAIRO who folds in these moments produces a program
that holds positions only when nothing depends on
holding them. The discipline is documenting the
position, the pressure, the reasoning, and the
decision — and being willing to escalate to the CRO,
CEO, or Board when the program's commitments are
being tested.

### 6.4 Ethics committees — when they help, when they don't

A common pattern: organisations create an *AI ethics
committee* (academic ethicists + community members +
internal leaders) intended to advise on hard cases.

When they help:

- The committee has *defined scope* and is consulted on
  cases that fit that scope.
- The committee's recommendations are *advisory but
  documented* — the Board considers them on the
  record.
- Membership rotates and includes external voices.

When they don't:

- The committee is consulted on everything, becoming a
  bottleneck.
- The committee is consulted on nothing, becoming
  ceremonial.
- The committee's recommendations are treated as
  binding without organisational accountability for
  the decision.

The reference position: ethics committees are *useful
adjuncts* to a working CAIRO function, not a substitute.
A program that outsources its ethics work to an
external committee has not done ethics work.

### 6.5 Naming a disagreement

The most underused ethics tool: *naming a disagreement
honestly*. The CAIRO function is sometimes asked to
declare a position on a question where reasonable people
disagree. The temptation is to pick one position and
defend it as the right answer.

The discipline of naming a disagreement:

- State the question.
- State the positions and their supporters' reasoning.
- State the considerations that would resolve the
  disagreement *if* they could be settled.
- State the program's current position and the basis.
- Acknowledge that the position may be revisited.

This is itself an ethical posture. It treats the
affected stakeholders (employees, customers, regulators,
the public) as participants in an honest process rather
than recipients of a manufactured certainty.

### 6.6 The reference for survival

A CAIRO ethics function that survives external scrutiny
shows three things:

1. **Specific operational implementations** of the
   program's stated values.
2. **Documented reasoning** for the choices that
   implement them.
3. **A record of holding the position** under pressure
   in the past.

A program missing any of the three is a program in name
only. The exercises in this module are structured
around producing the artifacts that demonstrate the
three.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **OECD AI Principles (2024 update)** — the closest
   thing to international consensus on principles.
2. **IEEE 7000 series** — the most operationalizable
   ethics standards in current use.
3. **Chouldechova (2017)** — *Fair Prediction with
   Disparate Impact*. The impossibility result.
