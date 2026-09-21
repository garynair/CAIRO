# Exercise 05 — Resolve a Hard Ethics Case — Reference Solution

## 1. Solution overview

The recommendation is **approve with conditions**.
Specifically: deploy the financial-advice assistant
with (a) disclosure to clients, (b) advisor-attestation
discipline at sign-off, (c) monitoring of the
differential-adoption pattern, and (d) named pause
authority if specific patterns emerge. The third
concern (differential adoption affecting fiduciary
obligation interpretation) is the one *named as a
partially-resolved disagreement* — the position taken
is documented but the underlying question is not
declared settled.

---

## 2. The decision memo

> **MEMO**
> **TO:** AI Risk Council; CC: CEO, CRO, Head of Wealth
> Advisory, Chief Compliance Officer
> **FROM:** Chief AI Risk Officer
> **DATE:** [date]
> **SUBJECT:** Wealth Advisory LLM assistant — production
> deployment recommendation
> **PAGES:** 3

I recommend the AI Risk Council approve the Wealth
Advisory LLM assistant for production deployment with
four conditions. The pilot results are real and the
operational benefits are material; the ethical concerns
raised are also real, and the conditions address them
specifically. One of the three concerns is, in my
judgement, a question on which reasonable people will
disagree — and the memo is honest about that.

### Concern 1 — Adviser-of-record framing

**Position:** This concern *is* substantive but does
not block deployment. Halverston needs to require an
explicit **advisor-attestation discipline** at sign-off:
when an advisor adopts AI-drafted reasoning, the
advisor explicitly attests — checkbox + brief signed
statement — that they have personally evaluated the
reasoning and concur with each material point. The
attestation is logged and audit-available.

**Steel-manned counter-argument (Wealth Advisory's
view):** Advisors have always used templates,
research material, and assistants. The advisor's
adoption of a conclusion has always been the
substance; the source of the reasoning is incidental.
The new assistant is no different in kind, only in
quality, from the prior templates and tools. Adding
attestation discipline implies the advisor's
relationship to AI-drafted material is *qualitatively*
different from their relationship to template-drafted
material — and Wealth Advisory does not concede this.

**Why my position prevails:** The lecture notes' §1.4
framing applies here. The advisor's relationship to
template material was incidental because templates
*did not* carry independent persuasive weight; the
client knew the advisor was using common industry
language. The new assistant's output is qualitatively
different in two ways: it is materially more
persuasive (the pilot results demonstrate this), and
it is *individualized* to the client's situation in
ways templates are not. A client reading
individualized, persuasive reasoning forms beliefs the
templates would not have produced. The advisor's
attestation discipline preserves the *substance* of
advisor sign-off; without it, the substance is hollow.

The condition is operationally low-cost (a checkbox +
brief statement per AI-assisted communication) and
provides Halverston a record that the advisor took
responsibility specifically — for the moment of
inquiry that this signs becomes load-bearing.

### Concern 2 — Disclosure to clients

**Position:** Clients **must** be told that AI
assistance was involved in producing the
communication. The disclosure should be brief, factual,
and present on every AI-assisted communication.

**Steel-manned counter-argument (Wealth Advisory's
view):** The advisor is the source of the advice; the
AI is a tool. Disclosing the tool would be like
disclosing that an advisor uses a research database or
an Excel model. Worse: it might create unnecessary
client anxiety about AI in a context where the
substance of the advice has not changed. No regulator
has required it; required disclosure adds operational
complexity without commensurate client benefit.

**Why my position prevails:** Three reasons. First,
the LLM is *not* a tool like a research database.
Research databases provide information the advisor
synthesises; the LLM provides the synthesis itself.
Clients have a legitimate interest in knowing what
relationship they are in. Second, California's AI
Transparency Act ambiguously requires it for CA-
resident clients; Halverston operating *both ways*
(disclosure for CA, not for others) is a compliance-
risk pattern — better to standardize on disclosure.
Third, the disclosure framing matters: a brief
factual statement ("This communication was drafted
with assistance from a Halverston-approved AI tool
under your advisor's review and adoption") rather
than alarmist language. Clients deserve the
information; the question is the framing, and
Halverston controls the framing.

The acknowledged cost is operational: every AI-
assisted communication carries the disclosure. The
client-experience cost is small if the framing is
right; the trust cost of being discovered not
disclosing is meaningfully larger.

### Concern 3 — Differential adoption

**Position (partially-resolved disagreement):** The
differential-adoption pattern is real, the fiduciary-
obligation question it raises is substantive, and I do
not believe it is fully resolved at this time. I
recommend deployment with **monitoring** of the
pattern + **a named pause authority** if specific
thresholds are crossed, *and I recommend the AI Risk
Council document the position as one that may need to
be revisited as the pattern develops.*

This is the §6.5 *naming-a-disagreement* discipline
applied directly. I will not pretend the question is
settled.

The substantive issue: under Halverston's fiduciary
obligations, every client is entitled to the
advisor's personalized care. If newer advisors using
the assistant for ~80% of communications are
effectively providing AI-mediated advice while senior
advisors using it for ~10% are providing more
human-mediated advice, then the *kind* of fiduciary
care varies systematically by which advisor a client
has. This may or may not be a fiduciary problem.
Several positions are defensible:

- **Position A:** AI-mediated advice signed by a
  competent advisor is fiduciary-adequate; the
  underlying obligation is to the standard of care,
  not to the source of the reasoning. Differential
  adoption is not a fiduciary issue.
- **Position B:** Fiduciary care is fundamentally
  *relational* and depends on the advisor's actual
  engagement with the client's situation;
  AI-mediated advice may meet substantive standards
  while failing the relational standard, and
  differential adoption may produce a sub-standard-
  of-care pattern for clients of high-AI-using
  advisors.
- **Position C:** The question is fact-dependent and
  depends on the actual quality of the AI-mediated
  advice and the advisor's engagement; cannot be
  answered in the abstract.

I am inclined toward Position C and recommend the
council not commit to A or B until the monitoring
provides evidence. The conditions below allow
deployment while preserving the option of revisiting.

**Monitoring conditions for differential adoption:**

- Quarterly review of per-advisor adoption rate
  distribution, broken down by advisor tenure, AUM
  per client, and client segment.
- Quarterly review of client-outcome indicators
  (client retention, complaint rate, satisfaction
  scores) stratified by advisor adoption rate.
- Quarterly review of any client-protection issues
  surfaced by Compliance.

**Named pause authority:** If the monitoring shows
either (a) materially-worse client-outcome indicators
for high-adoption-rate advisors' clients, or (b)
client-protection issues that correlate with adoption
rate, the AI Risk Council can pause deployment for
re-evaluation.

### Deployment posture summary

| Concern | Recommendation | Condition |
|---|---|---|
| Adviser-of-record | Approve with condition | Advisor-attestation discipline at sign-off |
| Disclosure | Approve with condition | Brief, factual disclosure on every AI-assisted communication |
| Differential adoption | Approve with monitoring | Quarterly monitoring + named pause authority |

### Precedent set

Future Halverston AI deployments where AI output is
*signed* by a human (advisor, broker, agent, employee)
will follow this precedent:

- **Attestation discipline** is required where the
  human is signing reasoning they did not
  independently form. Specifically — where AI output
  is materially more persuasive than the comparable
  pre-AI output, or where the AI output is
  individualized to the recipient's situation.
- **Disclosure** is required where the AI output is
  delivered to an external party in a context where
  the relationship matters. (Internal AI tools used
  by employees in their own workflow do not require
  external disclosure; external-facing
  communications do.)
- **Differential-adoption monitoring** is required
  where the deployment context allows differential
  adoption and where the relationship matters.

This precedent applies across Wealth Advisory,
Private Credit, and Public Markets. The CAIRO program
will update the relevant program standards within 30
days.

### Acknowledged cost

The conditions are not free for the business.
Specifically:

- **Operational cost.** Attestation discipline adds
  ~30 seconds per communication; for advisors
  drafting 20 communications per day, this is
  ~10 minutes per day per advisor. Across 2,400
  advisors, ~400 hours per day of total attestation
  time.
- **Adoption friction.** Some advisors who would
  have used the assistant for 80% of communications
  may reduce their use under the attestation
  discipline. The productivity gains the pilot
  documented may be partially attenuated.
- **Disclosure cost.** Some clients may interpret the
  disclosure as a signal that the advisor's
  attention is reduced; this could affect client
  perception of the relationship in a small fraction
  of cases.

These costs are real. I am asking the council to
accept them as the price of preserving (a) advisor
sign-off as substantive rather than ceremonial,
(b) client trust as built on honest disclosure, and
(c) the option to revisit the differential-adoption
question as monitoring data accumulates.

— end memo —

---

## 3. Reasoning notes

- **Why approve-with-conditions rather than pause.**
  The pilot results are real; the operational
  benefits are real; the ethical concerns are also
  real but can be addressed by conditions that do
  not eliminate the benefits. A pause posture would
  be defensible (the §6.3 *under-business-pressure*
  framing recommends caution), but in this case the
  conditions are operationally feasible and the
  underlying activity is one Halverston's competitors
  are also pursuing. Pausing without specific
  evidence of harm is the *over-cautious* failure
  mode that produces "study-further" deferrals — and
  §5.4 of the lecture notes (and the exercise
  constraints) specifically warns against this.
- **Why disclosure is conditioned rather than
  rejected.** The Wealth Advisory steel-manned
  argument has substance — disclosure carries
  real costs. But the disclosure cost is small
  relative to the trust cost of being discovered
  not disclosing, and the CA AI Transparency Act
  is heading toward ambiguity. Standardizing on
  disclosure is the *honest* move.
- **Why differential adoption is the named
  disagreement.** Reasonable people genuinely
  disagree on whether AI-mediated advice meets the
  relational dimension of fiduciary obligations.
  This is a question the industry has not settled;
  Halverston cannot settle it unilaterally. The
  monitoring posture lets us proceed while
  preserving the option to revisit, and it is more
  honest than asserting a confident position the
  evidence does not yet support.
- **Why the precedent matters.** Without naming the
  precedent, every future similar deployment
  re-litigates the question. The §6 discipline of
  documenting the reasoning in enough detail that a
  future Board can understand the precedent is
  load-bearing.
- **Why the cost acknowledgment matters.** §6.6 — a
  CAIRO ethics function that survives external
  scrutiny shows specific operational
  implementations, documented reasoning, and a
  record of holding the position under pressure.
  Pretending the conditions are costless lets the
  Council under-weight them; naming the costs forces
  honest evaluation.
- **The hardest call.** Whether the differential
  adoption section names a disagreement or commits
  to Position A or Position B. Position A
  (substantive standard of care is sufficient) is
  what most banks operating today *implicitly*
  commit to. Position B (relational standard is
  also required) is what fiduciary scholarship
  arguably supports. The reference declines to
  settle this because it cannot be settled by one
  CAIRO memo at this stage; declining is itself a
  position.
- **What this memo deliberately under-specifies.**
  The exact thresholds for the monitoring (what
  level of differential adoption triggers a pause,
  what level of client-outcome disparity triggers a
  pause). These are calibration questions for the
  first six months of monitoring; setting them now
  would be motivated by absence of data.
- **What would change my recommendation.** If
  Halverston had had a recent enforcement or
  litigation history on fiduciary care, I would
  recommend pause rather than approve-with-
  conditions — the trust budget would be lower and
  the burden of proof would shift. Halverston's
  current standing is clean.

---

Maintained by [Girish Nair](https://github.com/garynair)
