# Chapter 4 — The Impact Assessment Template

## Why this chapter exists

The impact assessment is the working artifact of MAP. It is
short, structured, and forces the program to name specific
failure modes against specific risk categories. It is also
the artifact regulators reach for first: EU AI Act
Article 27 requires a **fundamental-rights impact
assessment** for many deployers of high-risk systems;
Article 9 requires the risk-management-system's identifying
work; NIST MAP-5.1 asks for likelihood and magnitude per
risk. The impact assessment is where all three converge.

Programs that treat the template as boilerplate produce
assessments that pass into the file drawer and are never
read again. Programs that treat the template as a
*discipline for naming what could go wrong* produce
assessments that materially reduce incident frequency.

Exercise 02 makes you author the template for a working
company. This chapter gives you the structure and the
discipline.

## What a working template does

Four things, in order:

1. **Forces the classification to be applied.** The
   assessment cannot proceed until the system is
   classified against the taxonomy (Chapter 2) and the
   regulatory list (mod-102).
2. **Forces specific failure modes to be named per
   applicable category.** Not "the model could be biased"
   — "the model under-rates applications from ZIP codes
   with majority-non-English-speaking populations".
3. **Forces likelihood and severity to be rated *before*
   controls are considered.** The unmitigated rating is
   the anchor for MANAGE later; without it, residual risk
   cannot be defended.
4. **Names existing controls and gaps honestly.** The
   assessment is not a treatment plan (controls belong to
   MANAGE), but it is the diagnostic that lets MANAGE
   scope its work.

Templates that omit any of the four produce assessments
that regulators read as decorative. Templates that enforce
all four survive a regulator's *"show me your last
assessment for this system"*.

## The seven-section template

The template has seven sections. Each is short and
constrained.

### Section 1 — System summary

One paragraph.

- Name and inventory ID.
- Owner (role, not person).
- Intended use in one or two sentences.
- Who the affected population is.
- Whether the output is advisory, decisional, or
  autonomous.

The section is short by design. Long system summaries
create the illusion that the assessment covered the system;
short ones force the substance into Sections 3–7.

### Section 2 — Applicable risk categories

A single table:

| # | Taxonomy category (Chapter 2) | Applicable? | If not, one-sentence reason |
|---|---|---|---|
| 1 | Performance | yes / no | ... |
| ... | ... | ... | ... |

Every category is addressed — either included or
explicitly excluded with a reason. Silent exclusion is not
allowed. Reviewers should be able to see, at a glance,
which categories the assessment covers.

### Section 3 — Specific failure modes per applicable category

The heart of the assessment. For each applicable category
from Section 2, two to four specific failure modes.

Every failure mode has:

- A **name** (a short label).
- A **description** in one or two sentences, specific
  enough that a peer could recognise it in production data.
- The **affected population** — who is harmed if it
  occurs.
- The **detection signal** — how you would know it had
  occurred (this becomes MEASURE's target in Chapter 5).

Specificity is the whole point. *"The model could produce
biased outputs"* is not a failure mode; it is a category
restatement. *"The model produces lower approval
recommendations for applicants from ZIP codes with
predominantly non-English-speaking populations, driven by
the cash-flow aggregator's OCR failure on non-English
receipts"* is a failure mode: it names the pattern, the
population, and the mechanism.

If a category has fewer than two failure modes named, the
category has probably not been thought about. Push back.

### Section 4 — Likelihood and severity rating

For each failure mode from Section 3, a rating:

- **Likelihood.** 3-point (low / medium / high) or 5-point
  (very low / low / medium / high / very high). Pick one
  and use it consistently.
- **Severity.** Same scale. Severity is *given occurrence*
  — how bad if it happens.
- **Composite rating.** Product or matrix cell.

The rating is *unmitigated*. This is critical. If the
assessment rates likelihood after considering the existing
control, the residual-risk math in MANAGE breaks — you
cannot show a treatment reducing risk if the *before*
rating already includes the treatment.

Discipline: rate as if no controls were in place. Section 5
names what controls actually exist. Chapter 6's treatment
plan uses the unmitigated rating as the anchor and shows
the reduction.

### Section 5 — Existing controls (honest)

A short list of controls currently in place, per failure
mode or per category. This is a *diagnostic*, not a
treatment plan.

- Include controls that are actually running, not planned.
- Include the control name, the owner, and the source of
  evidence that it is running.
- Include controls even if you suspect they are not
  working. That is a gap, addressed in Section 6.

The section makes the impact assessment usable by MANAGE
because MANAGE needs to know what already exists before
designing what to add.

### Section 6 — Gaps

The parallel list to Section 5. What is missing.

- Named as gaps, not as recommendations.
- Traceable to specific failure modes.
- Not disguised as *"further study required"* — a gap is
  a control the program does not have that the risk
  arguably calls for.

Honest gaps are what regulators reward. A gap-free
assessment across nine risk categories is either a
trivial system or a dishonest assessment.

### Section 7 — Recommendations to MEASURE and MANAGE

Short list. What the assessment recommends the next two
functions do.

- To MEASURE: which failure modes should be metric
  targets, at what cadence.
- To MANAGE: which gaps from Section 6 should be closed,
  with what priority.

The recommendations are input, not output. MEASURE and
MANAGE are free to accept, adjust, or defer with a written
rationale. What matters is that MAP has *handed them
something to work on*.

## The specificity discipline

Sections 3 and 4 are where impact assessments succeed or
fail as artifacts. The discipline is *specific failure
modes*, not risk categories restated.

A test the template can enforce: could a reviewer *simulate
production and detect this failure mode*? If yes, it is
specific enough. If no, it is a category restatement.

Contrast:

| Bad (generic) | Good (specific) |
|---|---|
| "The model may be biased" | "The model recommends lower amounts for applicants whose cash-flow data is OCR-extracted from non-English receipts" |
| "Privacy concerns exist" | "Employee free-text notes containing customer PII flow into the chat agent's context window and could surface in unrelated agent responses" |
| "The model could hallucinate" | "The medical-info chatbot generates dosage recommendations for medications not on our formulary at ~3% of dosage queries" |
| "Security risk exists" | "Prompt-injection through email signatures causes the agent to disclose the last customer it spoke to" |

Every good example above suggests a specific measurement.
The generic ones do not. If your Section 3 entries do not
suggest measurements to your MEASURE lead, they are not
specific enough.

## Rating without motivated reasoning

Section 4 has one main failure mode: authors rate down to
what they can defend rather than what they see. The
unmitigated likelihood of a bias failure in a live system
is rarely *low*, but *low* is comfortable to write.

Two disciplines resist this.

- **Rate blind first.** Author the ratings *before*
  looking at any dashboards or eval results. Rating from
  first principles — how the system could fail given its
  design, data, and context — produces higher and more
  honest ratings.
- **Second-line review.** Have someone from second line
  (Chapter 3 of mod-101) sample-check the ratings. They
  are institutionally distant from the system and free to
  disagree.

A rating that has never been disagreed with by anyone is
not a rating; it is a self-report.

## Length discipline

A working impact assessment for one system is 4–8 pages.
Longer assessments are not more thorough — they are less
read. A 40-page assessment gets summarised into 3 pages by
the AI Review Board and only the summary is used. Author
the 3-page assessment directly.

## What the template must *not* do

Two failure modes to actively design against.

- **Do not propose controls.** MAP names risks; MANAGE
  names controls. If the template asks *"what control
  will you implement"* in Section 3, it collapses the
  loop. The Section 7 recommendations are input to
  MANAGE, not commitments made by MAP.
- **Do not use category-level scores.** Rolling up
  failure-mode-level ratings into a single "bias rating
  of high" for the category obscures the specific pattern
  that matters. Board reports summarise per category
  (Chapter 7); assessments do not.

## Where the template lives in the operating rhythm

- Authored **at every material system change** (Chapter 3
  defines material).
- Authored **at least annually** for every in-scope
  system, even without a material change.
- Reviewed by the **AI Review Board** at the cadence the
  policy hierarchy defines (Chapter 7 has the rhythm
  table).
- Version-controlled with author, date, and the
  classification version it was written against.

An assessment older than twelve months on an in-scope
system is a program failure the CAIRO owns.

## The relationship to Article 27 FRIA and Microsoft RAI IA

Two external templates are useful comparison material,
though neither should be copied wholesale.

- **EU AI Act Article 27** requires a *fundamental-rights
  impact assessment* from certain deployers of high-risk
  systems. It is scoped to the fundamental-rights subset
  of the impact assessment work, not the full one. A
  program impact-assessment template that already includes
  Section 3 failure modes in fundamental-rights terms
  produces the FRIA as a rolled-up view.
- **Microsoft Responsible AI Impact Assessment Template**
  (published under the Microsoft Responsible AI Standard
  v2) is a widely-cited public template. Reading it once
  is useful as pattern range; copying it defeats the point
  of Exercise 02, which is to make you own the template.

## Summary

- The impact assessment is the working artifact of MAP
  and the direct substrate for EU AI Act Article 9(2)(a)
  and (for deployers) Article 27.
- The template has seven sections: system summary,
  applicable categories, specific failure modes per
  category, unmitigated ratings, existing controls, gaps,
  recommendations to MEASURE and MANAGE.
- The specificity discipline in Section 3 is what
  separates a diagnostic assessment from a decorative one
  — each failure mode should be detectable in production
  data.
- Ratings in Section 4 are *unmitigated*, rated blind
  first, and challenged by second line. A rating no one
  has ever disagreed with is a self-report.
- The template must not propose controls (that is
  MANAGE) or roll failure modes up into category scores
  (that obscures the pattern).
- Length discipline is 4–8 pages; longer assessments are
  less read, not more thorough.
- Exercise 02 has you author the template and apply it to
  a working system.
