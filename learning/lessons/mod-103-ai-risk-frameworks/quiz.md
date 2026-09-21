# Module 103 — Quiz

Twenty-five questions covering the chapters. Answer key
lives in the paired solutions repo.

---

## Section A — Framework vs program (Chapter 1)

**Q1.** Which of the following best describes the gap
between a "complete framework" and a "complete program"?

  a. Frameworks are theoretical; programs are practical.
  b. Frameworks specify functions; programs need
     artifacts, owners, cadences, and responses.
  c. Frameworks are external; programs are internal.
  d. There is no meaningful gap; frameworks are programs.

**Q2.** The "measure-first" failure mode happens because:

  a. MEASURE is the most demonstrable function.
  b. MEASURE is the least expensive function.
  c. MEASURE is required by NIST AI RMF.
  d. MEASURE is the only function regulators care about.

**Q3.** Short answer: in one sentence, explain why a
taxonomy is necessary even when the framework
(NIST AI RMF) is already in place.

---

## Section B — AI risk taxonomy (Chapter 2)

**Q4.** Which of the following is **not** a property of a
good taxonomy?

  a. Mutually exclusive top-level categories.
  b. Maps to enterprise risk taxonomy.
  c. Exhaustive in three or more levels of depth.
  d. Small enough to remember.

**Q5.** True or false: a risk should be allowed to belong
to multiple top-level categories if it materially fits
more than one.

**Q6.** Short answer: name one taxonomy mistake from
Chapter 2 and explain in one sentence why it distorts the
program.

**Q7.** The starting nine-category taxonomy in Chapter 2
anchors seven of its categories to a specific external
list. Which list?

  a. OWASP LLM Top 10.
  b. NIST AI 100-1 §3 characteristics of trustworthy AI.
  c. EU AI Act Annex III use cases.
  d. ISO 31000 risk categories.

---

## Section C — MAP in practice (Chapter 3)

**Q8.** Which artifact is **not** part of MAP?

  a. AI system inventory.
  b. System classification.
  c. Risk-treatment plan.
  d. Impact assessment.

**Q9.** When should classification be revisited?

  a. Never; classification is one-time.
  b. Annually.
  c. On any material system change, regulatory change, or
     context change.
  d. Only on regulatory request.

**Q10.** Short answer: in one sentence, explain why *material*
must be defined in policy in advance rather than
case-by-case.

---

## Section D — Impact assessment template (Chapter 4)

**Q11.** Which of the following is a *specific* failure
mode (Chapter 4 discipline), not a category restatement?

  a. "The model may be biased against protected classes."
  b. "The model recommends lower amounts for applicants
     whose cash-flow data is OCR-extracted from
     non-English receipts."
  c. "Privacy risk exists in this system."
  d. "Security concerns require investigation."

**Q12.** Why must the likelihood-severity rating in the
impact assessment be **unmitigated** (before controls)?

  a. Because regulators require unmitigated ratings.
  b. Because the residual-risk math in MANAGE breaks if
     the *before* rating already includes the treatment.
  c. Because it makes the ratings higher.
  d. Because NIST MAP-5.1 uses that language.

**Q13.** Short answer: name one thing the impact assessment
template must *not* do, and explain in one sentence why.

---

## Section E — MEASURE and leading indicators (Chapter 5)

**Q14.** Which of the following is a **true leading
indicator**?

  a. Number of bias complaints filed by affected users.
  b. Drift in input feature distribution.
  c. Customer-complaint rate.
  d. Number of overturned model decisions.

**Q15.** Why should a metric's threshold be defined
**before** data is collected on it?

  a. To meet regulatory requirements.
  b. To enable consistent dashboarding.
  c. To prevent motivated thresholds set to whatever the
     current value happens to be.
  d. To allow vendor comparisons.

**Q16.** True or false: A dashboard that no one reviews
on a defined cadence is still useful as a record.

**Q17.** Short answer: name one of the three eval-set
risks from Chapter 5 and explain in one sentence how it
distorts metrics.

**Q18.** Under EU AI Act Article 9(2)(b), the measurement
plan must evaluate risks under intended use **and**:

  a. Any conceivable use, however remote.
  b. Reasonably foreseeable misuse.
  c. Only intended use.
  d. Only competitor-benchmarked use.

---

## Section F — MANAGE and residual risk (Chapter 6)

**Q19.** A **control catalog** is best described as:

  a. A list of every control the program has ever
     considered.
  b. A structured library of treatments the program knows
     how to apply, organised by taxonomy and lifecycle
     stage.
  c. A list of controls required by regulators.
  d. A vendor-supplied list of available products.

**Q20.** A risk-treatment plan **must** name residual
risk explicitly because:

  a. NIST AI RMF requires it in exactly that language.
  b. Every meaningful AI risk has residual, and programs
     that claim zero residual are not credible to
     regulators or boards.
  c. ISO 42001 requires exactly that phrasing.
  d. Boards require it.

**Q21.** Short answer: in one sentence, describe the
"treat everything" trap from Chapter 6.

**Q22.** Which of the following is **not** required for
an exception in the exception register?

  a. Business justification.
  b. Expiration date or re-evaluation trigger.
  c. Named approver at appropriate level.
  d. Independent third-party validation.

---

## Section G — GOVERN and closing the loop (Chapter 7)

**Q23.** The AI risk register is:

  a. A list of every AI risk that has ever been
     considered.
  b. The single source of truth for material risks,
     operated by the head-of-ai-governance and signed by
     the CAIRO.
  c. A regulatory deliverable owned by Legal.
  d. A board-only artifact.

**Q24.** Which of the following is **not** part of the
recommended quarterly board report structure?

  a. Current risk posture rolled up by taxonomy category.
  b. Material changes since last quarter.
  c. A clear request of the board.
  d. A comprehensive dashboard of every program metric.

**Q25.** Short answer: describe one concrete way the
loop closes in Chapter 7, and explain how you would know
it had failed to close.

---

## Section H — Risk appetite statement (Chapter 8)

**Q26.** In the AI risk appetite statement described in
Chapter 8, who **signs** and who **ratifies**?

  a. CAIRO signs; CRO ratifies.
  b. CEO signs; the board (typically Risk Committee)
     ratifies; the CAIRO signs off on operational
     applicability.
  c. Board signs; CAIRO ratifies.
  d. Head-of-ai-governance signs; CAIRO ratifies.

**Q27.** What is the role of the head-of-ai-governance
with respect to the appetite statement?

  a. They author the statement.
  b. They approve the statement instead of the CEO.
  c. They operate the risk register that the appetite is
     applied to, and produce the appetite-application
     memo and the quarterly appetite-alignment summary.
  d. They have no role in the appetite process.

**Q28.** Short answer: in one sentence, describe one
common failure mode of a risk appetite statement from
Chapter 8 and how you would fix it.

---

## Section I — End-to-end synthesis

**Q29.** True or false: A traceable chain from control
back to policy — through treatment plan, measurement
plan, impact assessment, classification, inventory, and
taxonomy — is what a regulator is looking for in a mature
program.

**Q30.** Short answer: pick any one system you know
(from mod-101/mod-102 exercises or your own work) and
name (a) one applicable taxonomy category, (b) one
specific failure mode inside it, (c) one leading
indicator that would detect it, and (d) one residual
risk that would remain after treatment.
