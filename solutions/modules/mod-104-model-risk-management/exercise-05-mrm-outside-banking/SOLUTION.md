# Exercise 05 — Apply MRM Outside Banking — Reference Solution

## 1. Solution overview

For **Cardinal Health Network**, the reference adapts SR
11-7's four pillars into a healthcare-vocabulary program
anchored in the existing Chief Quality Officer's office,
with the CAIRO function providing AI-specific overlays. The
hardest section is independence (§4) — Cardinal's clinical
authority and AI development are organisationally
intertwined, so the reference proposes structural workflow
constraints rather than personnel independence.

---

## 2. The program design

> **Cardinal Health Network — AI Risk Management Program**
> *Healthcare-context MRM equivalent*
> *Prepared by: Chief AI Risk Officer, in consultation with
> Chief Quality Officer and Chief Medical Officer*
> *For:* CEO briefing to state healthcare regulator
> *Pages: 3*

### Section 1 — Translation

At Cardinal, the SR 11-7 vocabulary translates as:

- **"Model"** becomes **"AI / ML algorithm"** or, where
  device-classified, **"device algorithm."** The clinical
  context distinguishes these from analytic dashboards
  used by clinicians (which are tools, not algorithms).
- **"MRM function"** has no single existing analog. The
  closest match is the **Clinical Quality Office under
  the Chief Quality Officer**, which currently performs
  clinical-safety review of new clinical-decision-
  support tools but not in an SR 11-7 framework. The
  reference proposes that the Clinical Quality Office
  becomes the **Algorithm Quality Office** (a renaming
  that signals expanded scope) and operates the four-
  pillar discipline.
- **"AI program function"** is the new CAIRO function under
  the CRO.
- **"Model risk"** becomes **"algorithm risk"** — and is
  framed explicitly as a category within **patient
  safety risk** + **operational risk**, the existing
  enterprise risk vocabularies.

Disciplines that translate directly:

- The four pillars (development / validation / governance /
  framework integration).
- The model definition adapted as above.
- The independence requirement.
- Documentation discipline.
- Tiering.

Disciplines that adapt:

- **Committee architecture.** Cardinal has a Clinical
  Quality Council and a Patient Safety Committee.
  Algorithm-related questions integrate with these,
  rather than spawning a parallel Model Risk Committee.
- **Challenger-model paradigm.** Most clinical AI
  systems do not have a meaningful classical-model
  alternative. The reference replaces challenger with
  *evidence-base benchmarking* (comparing AI output
  patterns to published clinical evidence).

### Section 2 — The four pillars at Cardinal

#### Pillar 1 — Robust development, implementation, and use

- **Existing function:** Information Services (IT)
  + Clinical Informatics, with input from Clinical
  Quality Office.
- **Gap:** No documented development discipline
  comparable to SR 11-7 §III. Clinical Informatics
  produces clinical-decision-support tools without a
  standard development standard.
- **New work:** The Algorithm Quality Office authors a
  *Cardinal Algorithm Development Standard*
  (analogous to the bank standard but in clinical
  vocabulary). Required: documented intended use;
  documented training-data provenance; documented
  testing approach; documented implementation
  artifacts.

#### Pillar 2 — Sound validation processes

- **Existing function:** Clinical Quality Office
  performs *clinical safety review* on new clinical-
  decision-support tools. Device algorithms additionally
  go through FDA / EU MDR review externally.
- **Gap:** Clinical safety review covers patient-safety
  outcomes but does not perform algorithm-quality
  validation (drift, subgroup performance,
  generalisation). Internal independence is informal.
- **New work:** Algorithm Quality Office establishes a
  standing *validation team* (3–4 FTE initially) that
  performs independent validation of all in-scope
  algorithms before deployment. For algorithms also
  going through FDA / EU MDR, the internal validation
  is in addition, with the FDA / MDR submission as one
  input.

#### Pillar 3 — Strong governance, policies, controls

- **Existing function:** Clinical Quality Council
  (chaired by CMO) governs clinical-quality matters;
  Patient Safety Committee (chaired by Chief Quality
  Officer) governs patient-safety matters.
- **Gap:** Neither has algorithm-specific charter,
  decision rights, or policy hierarchy.
- **New work:** Algorithm Quality Office establishes
  the *Algorithm Governance Standard* (policy
  hierarchy: charter, development standard, validation
  standard, monitoring standard, exception standard).
  Algorithm-specific decisions route through Clinical
  Quality Council (medical-clinical questions),
  Patient Safety Committee (operational-safety
  questions), or AI Review Board (AI-program
  questions), based on the framing of the question.

#### Pillar 4 — A firm-wide framework integrating the above

- **Existing function:** Cardinal's enterprise risk
  framework, owned by the CRO.
- **Gap:** Algorithm risk is not currently a named
  category in the enterprise framework.
- **New work:** CAIRO function works with CRO to add
  algorithm risk as a category in the enterprise risk
  framework, with roll-up of algorithm-specific findings
  into the standard board risk report. The Algorithm
  Quality Office's output integrates with this category.

### Section 3 — Tiering

Cardinal's three-tier scheme:

| Tier | Criteria | Examples |
|---|---|---|
| **Tier 1 Critical** | (i) FDA-cleared SaMD or EU MDR Class IIa+; (ii) algorithm output directly influences acute clinical decisions (triage, prescribing, urgent diagnosis); (iii) failure can produce patient harm of clinically-significant magnitude | Triage support tools (continuation of Aldwych scenario); diagnostic CDSS for time-sensitive conditions; medication-dosing recommendation systems |
| **Tier 2 Important** | (i) algorithm output substantively informs non-acute clinical decisions; (ii) FDA SaMD Class I or EU MDR Class I; (iii) failure has identifiable but non-acute patient or operational impact | Operational predictive models (capacity, scheduling); diagnostic CDSS for non-acute conditions; quality-improvement analytics tools |
| **Tier 3 Standard** | (i) algorithm supports administrative or back-office decisions; (ii) no direct clinical impact; (iii) failure produces bounded operational nuisance | Billing-claim coding assistants; documentation transcription; back-office process automation |

Two example systems per tier:

- **Tier 1:** Sepsis-prediction CDSS in adult ICUs;
  retinal-imaging DR screener (continuity from mod-103
  Exercise 05 Kerridge scenario).
- **Tier 2:** OR-utilisation prediction model; readmission-
  risk model for case management.
- **Tier 3:** Inbox triage assistant for clinician
  in-baskets; documentation transcription.

### Section 4 — Independence and the clinical-authority boundary

The hardest section. At Cardinal:

- The Chief Medical Officer holds clinical authority.
- The Clinical Informatics group reports under the CIO
  and develops most internally-built clinical-decision-
  support tools.
- The Chief Quality Officer oversees patient safety and
  clinical-quality review.
- The new Algorithm Quality Office reports to the
  Chief Quality Officer.

The independence problem: a fully-independent algorithm
validation team would not exist at Cardinal's scale —
the people who know enough clinical context to validate
a clinical algorithm are often the same people involved
in its development. Pretending otherwise produces
ceremonial independence that fails the
after-failure test.

The reference's approach: **structural workflow
constraints** rather than personnel independence.
Specifically:

- Algorithm Quality Office's validation team includes
  clinical informaticists, but those individuals do
  not serve on both the validation team and the
  development team for the same algorithm. Reasonable
  rotation maintains skill while preserving per-
  algorithm independence.
- For Tier 1 algorithms, an external clinical
  validator is engaged (an external CDSS-validation
  contractor or partnering academic centre). The
  external is not a substitute for internal
  validation but a supplement that supports the
  after-failure-bias test.
- Clinical authority remains with the CMO. Algorithm
  Quality Office can block deployment on algorithm-
  quality grounds; CMO can block on clinical grounds;
  neither can override the other; ties go to the CEO.
- The Algorithm Quality Office reports to the Chief
  Quality Officer, not to the CIO under whom Clinical
  Informatics sits. This breaks the natural
  development-validation collusion path.

**Honest acknowledgment**: this is not perfect
independence. A regulator pressing on independence
would find the rotation pattern and the external-
validator scope insufficient if Cardinal were a 50,000-
bed integrated delivery network. For an 800-bed regional
system, the structural constraints are the
operationally honest answer; the cost of more
independence is more than the marginal benefit
delivers.

### Regulator framing — "is this MRM?"

If asked by the state healthcare regulator: *Cardinal
has implemented an algorithm-risk-management program
analogous in structure to financial-services Model Risk
Management (SR 11-7), adapted to clinical context. The
four pillars are present. Independence is preserved
structurally rather than purely by organisational
separation, which is the appropriate posture for
Cardinal's scale and clinical context. The program is
not a literal MRM function — banking vocabulary does
not map cleanly to healthcare — but it implements the
same discipline.*

— end of program design —

---

## 3. Reasoning notes

- **Why I housed the program under the Chief Quality
  Officer.** The CQO's office already does clinical-
  safety review; that is the closest existing
  discipline. Putting algorithm risk under the CIO would
  re-create the development-validation collusion
  problem. Under the CMO would conflate clinical
  authority and algorithm oversight. Under the CRO
  would have been defensible but would have created a
  fourth governance body (Algorithm Quality Office +
  Clinical Quality Council + Patient Safety Committee
  + Enterprise Risk Committee), which is more
  machinery than Cardinal needs.
- **Why I renamed Clinical Quality Office to Algorithm
  Quality Office.** Vocabulary signals scope. Asking
  the existing CQO to take on AI/ML algorithm risk
  without renaming would have it absorbed into existing
  workload and silently de-prioritised. The rename is
  cheap and clarifies.
- **Why I rejected the parallel-MRM-committee
  pattern.** Some hospital systems have created
  Algorithm Review Committees as parallel governance.
  At Cardinal's scale, this is one committee too many.
  Routing through existing committees (with explicit
  charter updates) is more sustainable.
- **The independence trade-off.** The reference
  acknowledges that the structural constraints are
  not perfect independence. A regulator pressing on
  this would find weaknesses; the honest framing is
  that the marginal independence cost beyond what is
  proposed exceeds the marginal benefit at Cardinal's
  scale. Programs that overclaim independence in
  contexts where it is not structurally available
  lose credibility when tested.
- **What this program does not solve.** EHR-vendor-
  embedded AI features. Cardinal's EHR vendor ships
  features powered by AI that the EHR vendor controls.
  Cardinal cannot validate or even fully inspect
  these. The program would address this through a
  vendor-AI specific control set, mostly contractual
  (notice on feature changes, ability to disable),
  but the validation problem is not fully solvable
  from Cardinal's side. This is one of the open
  industry problems the reference does not pretend to
  resolve.
- **What I would change for a larger health system.**
  At a 5,000+ bed integrated delivery network, an
  externally-staffed Algorithm Quality Office becomes
  defensible (more scale to amortise the cost). An
  academic medical centre might also house the
  function within the clinical-research apparatus.
  Adaptation is context-specific.

---

Maintained by [Girish Nair](https://github.com/garynair)
