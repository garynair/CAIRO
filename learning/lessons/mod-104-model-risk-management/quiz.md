# Module 104 — Quiz

Twenty questions. Answer key in the paired solutions repo.

---

## Section A — What SR 11-7 actually says (§1)

**Q1.** SR 11-7 identifies **two** sources of model risk.
Which?

  a. Fundamental error and misuse
  b. Fundamental error and adversarial attack
  c. Misuse and regulatory non-compliance
  d. Adversarial attack and data quality

**Q2.** Which of the following is **not** one of SR 11-7's
four pillars of an MRM framework?

  a. Robust model development, implementation, and use
  b. Sound model validation processes
  c. Strong governance, policies, and controls
  d. Independent third-party audit firm engagement

**Q3.** Short answer: in one sentence, explain why
attempting to define a system out of "model" scope to
avoid MRM is described as a losing strategy.

**Q4.** Which line of defense does SR 11-7 place the MRM
function in?

  a. First
  b. Second
  c. Third
  d. Fourth

---

## Section B — Model tiering (§2)

**Q5.** Which of the following is **not** a property of a
defensible tiering scheme?

  a. Reflects real differences in model risk
  b. Applies consistently across the portfolio
  c. Always uses three tiers
  d. Is documented in the MRM policy

**Q6.** Which ML-specific consideration is mentioned in
§2.3 as a possible additional tiering input?

  a. Number of model parameters
  b. Model size / inscrutability
  c. Programming language used
  d. Vendor pricing

**Q7.** True or false: "Tiering everything as Tier 1 to be
safe" is described as a defensible conservative posture.

---

## Section C — Independent validation (§3)

**Q8.** Which of the following is **explicitly identified
as one of the four elements of validation** in SR 11-7 §IV?

  a. Challenger model construction
  b. Evaluation of conceptual soundness
  c. Vendor third-party attestation
  d. Production traffic logging

**Q9.** Which validation pattern is described in §3.2 as
"often the only valid approach for LLM outputs without
ground truth"?

  a. Counterfactual evaluation
  b. Subgroup validation
  c. Human evaluation by domain experts
  d. Out-of-distribution testing

**Q10.** Short answer: in one sentence, explain the
*independence test* described in §3.3 for validation
personnel.

**Q11.** Which of these is described as a **material
change** that triggers re-validation for LLM systems,
beyond the classical triggers?

  a. New customer onboarding
  b. Prompt template change
  c. Server hardware upgrade
  d. Marketing campaign launch

---

## Section D — The model lifecycle (§4)

**Q12.** Which two lifecycle stops does §4.2 identify as
"most often skipped"?

  a. Concept approval and data acquisition
  b. Implementation review and retirement
  c. Development and use
  d. Validation and ongoing monitoring

**Q13.** Short answer: in one sentence, describe why
*implementation review* matters more for ML systems than
classical models.

---

## Section E — CAIRO × MRM boundary (§5)

**Q14.** Which of these is described as a **collision
pattern** that fails?

  a. Joint validation expectations between CAIRO and MRM
  b. Cross-referenced inventories that point to each other
  c. Re-validation of MRM-validated models by the CAIRO
     function
  d. Joint regulator briefings

**Q15.** Which of the following is owned by **MRM**, not
the CAIRO function (per §5.1–§5.2)?

  a. The AI risk taxonomy
  b. Independent validation of models within MRM scope
  c. The AI risk register
  d. AI vendor and ecosystem risk

**Q16.** Short answer: in two sentences, describe one
example of the *intersection* between CAIRO and MRM scope
from §5.3 and how it can be operated cleanly.

---

## Section F — MRM outside banking + comprehensive (§6 + cross)

**Q17.** Which adaptation is described as most direct from
banking MRM to insurance?

  a. The MRM committee architecture
  b. The challenger-model paradigm
  c. The four-pillar framework
  d. The 21-page document length

**Q18.** True or false: SR 11-7's *misuse* framing
applies directly to industrial AI deployments where
operators use AI beyond the validated operational
envelope.

**Q19.** Which of these is **not** part of SR 11-7's
required validation cadence?

  a. Material model change
  b. Material change in intended use
  c. Material change in operating environment
  d. Quarterly regardless of change

**Q20.** Short answer: in two sentences, name one
pattern from §5.6 (reporting line question) and explain
the trade-off it carries.
