# Module 104 — Lecture Notes

About 110 minutes of reading. §1 (what SR 11-7 actually
says) is dense; the rest builds on it. Expect to come back
to §1 as a reference.

---

## §1. What SR 11-7 actually says (and why it works)

SR 11-7 — the Federal Reserve and OCC's *Supervisory
Guidance on Model Risk Management* (2011) — is one of the
shortest, most influential, and most misunderstood
documents in the AI governance space. It is twenty-one
pages. Most of what people *say* it requires is downstream
interpretation. The first discipline of this module is
reading what it actually says.

### 1.1 What SR 11-7 is for

SR 11-7's central premise:

> *"The use of models invariably presents model risk,
> which is the potential for adverse consequences from
> decisions based on incorrect or misused model outputs and
> reports."*

It identifies two sources of model risk:

1. **Fundamental error** — the model has a flaw that
   produces inaccurate outputs.
2. **Misuse** — the model is used outside its design
   intent, or its outputs are misinterpreted by decision-
   makers.

The whole document is structured around managing both. AI
governance programs that focus only on fundamental error
(better validation, better testing) without misuse (better
governance of *how* outputs are used) miss half of what
SR 11-7 is trying to do.

### 1.2 The four pillars of an MRM framework

SR 11-7 §III specifies that a *firm-wide* MRM framework
must include:

1. **Robust model development, implementation, and use**
   (§III).
2. **Sound model validation processes** (§IV).
3. **Strong governance, policies, and controls** (§V).
4. **A firm-wide MRM framework integrating the above**
   (§VI).

The four pillars are not a checklist. They are *load-
bearing structures*. A framework missing any of them
collapses under regulator scrutiny.

### 1.3 What counts as a "model" under SR 11-7

The most over-debated topic in MRM. SR 11-7 defines a
model as:

> *"a quantitative method, system, or approach that
> applies statistical, economic, financial, or
> mathematical theories, techniques, and assumptions to
> process input data into quantitative estimates."*

The implication for AI/ML:

- A neural network producing a credit score is **a model**.
- An LLM producing customer-facing text where the text
  influences a decision is **a model**.
- An LLM used purely as a calculator-style assistant (no
  decision influence) is **arguably not a model** under
  SR 11-7 — but the trend is for examiners to read this
  broadly.

The lecture notes §4 of mod-102 referenced the *black-box
defense* CFPB has rejected. The same logic applies to MRM
scoping: trying to define a system out of "model" scope to
avoid MRM is a losing strategy. When in doubt, MRM scope
applies.

### 1.4 The three lines, applied to MRM

SR 11-7 explicitly assigns roles across the three lines of
defense:

| Line | Function | Role under SR 11-7 |
|---|---|---|
| First | Model owners (developers, users) | Build, document, and use the model correctly |
| Second | MRM function | Independent validation, ongoing monitoring, MRM policy |
| Third | Internal audit | Periodic assurance that the first two lines are working |

The CAIRO function (per mod-101 §4) sits in the second line
alongside MRM — not on top of it. §5 of these notes
treats this in operational depth.

### 1.5 Why SR 11-7 works (and why it has aged well)

SR 11-7 has aged well for AI/ML for three reasons:

1. **It is framework-agnostic.** The principles do not
   assume a specific model class. A 1990s logistic-
   regression model and a 2025 LLM both fit the
   definition.
2. **It separates *what* must be done from *how*.** The
   four pillars are required; the implementation is left
   to the firm. This survives technology change in a way
   that a more prescriptive standard would not.
3. **It centers documentation and replication.** SR 11-7
   demands that another competent professional could
   reproduce the model's development, validation, and
   monitoring from the documentation alone. This
   discipline scales to ML — and is one of the few
   external pressures forcing ML programs to document
   adequately.

### 1.6 What SR 11-7 does not address well

For honesty:

- **Continuous-learning systems.** SR 11-7 was written
  for stationary models. FDA's Predetermined Change
  Control Plan guidance is closer for adaptive
  systems; SR 11-7 supervisors are working out their
  posture in real time as of 2026.
- **LLMs and generative outputs.** SR 11-7's
  validation framework assumes the model's output is
  *evaluable* against ground truth. Many LLM outputs
  are not. The MRM community is actively developing
  techniques.
- **Vendor / third-party AI.** SR 11-7 §V covers
  third-party models but predates the foundation-
  model-as-service pattern. SR 22-6 partially
  addresses; the operational gap remains.

These gaps are real. They are not reasons to ignore SR
11-7; they are reasons to extend it carefully.

---

## §2. Model tiering for ML / AI

SR 11-7 does not mandate a specific tiering system. It
requires that "the firm's MRM framework should incorporate
tiering" — and leaves the details to the firm. Tiering is
the spine of an MRM program because it determines how
much validation, governance, and monitoring effort each
model gets.

### 2.1 What a tier means

A model's tier is shorthand for *the level of MRM
investment the model warrants*. A higher-tier model gets:

- More rigorous independent validation before deployment.
- More frequent ongoing monitoring.
- More senior governance oversight.
- More detailed documentation.

A lower-tier model gets correspondingly less.

A tiering scheme is **defensible** if it (a) reflects
real differences in model risk and (b) applies
consistently across the portfolio.

### 2.2 A working tiering scheme

A working three-tier scheme that adapts to ML:

| Tier | Criteria | MRM treatment |
|---|---|---|
| **Tier 1 — Critical** | (i) model output directly drives an externally-binding decision (credit, claims, clinical); (ii) failure has material customer, regulatory, or reputational consequence; (iii) any of the above for a system covered by EU AI Act high-risk classification | Full independent validation pre-deployment; quarterly MRM monitoring review; annual full re-validation; senior MRM committee approval for material changes |
| **Tier 2 — Important** | (i) model output substantively informs a decision (but human in loop has authority); (ii) failure has identifiable but bounded operational impact; (iii) EU AI Act limited-risk for systems with affected parties | Independent validation pre-deployment; semi-annual MRM monitoring; biennial full re-validation; MRM lead approval for material changes |
| **Tier 3 — Standard** | All other in-scope models | Targeted validation (proportionate); annual MRM monitoring; trigger-based re-validation; documented model-owner approval for changes within envelope |

(A four-tier scheme — splitting Critical into "Catastrophic"
and "Critical" — is more common in large banks.)

### 2.3 ML-specific tiering considerations

Three considerations that classical-model tiering misses
for ML:

- **Data freshness as a tiering input.** A model trained on
  monthly batch data and re-trained quarterly has
  different risk dynamics than a model re-trained
  weekly. Higher re-training cadence often warrants
  higher tier, even if intended use is similar.
- **Model size and inscrutability.** A 100-billion-
  parameter foundation model embedded in a product is
  *materially less explainable* than a 100-feature
  gradient-boosted model with similar use. Some firms
  add inscrutability as a tiering input.
- **Vendor / on-prem provenance.** A model whose internal
  details the firm does not have access to (closed-
  weights LLM) carries higher validation and monitoring
  challenge than an on-prem model. Some firms tier
  vendor models one step higher than equivalent in-house
  models to account for the validation gap.

Exercise 01 forces tiering against an explicit scheme.

### 2.4 Tiering anti-patterns

- **Tiering by business sponsor seniority.** A model
  sponsored by an SVP must not therefore be Tier 1. Tier
  reflects *the model's risk*, not political weight.
- **Tiering everything as Tier 1 "to be safe".** Forces
  MRM into impossible workload; the program degrades
  silently as resourcing fails.
- **Tiering everything Tier 3 "during pilot".** "Pilot"
  becomes a permanent tier-avoidance category. SR 11-7
  scopes include pilots that affect customers.
- **Re-tiering downward without documented rationale.**
  Common during model updates. Examiner will read this
  as motivated.

---

## §3. Independent validation when challenger models break

SR 11-7 §IV requires that material model outputs be
*independently validated*. The classical pattern in
financial-services MRM is the **challenger model**: an
alternative model built independently by MRM and run
against the same data, with disagreement between the
challenger and the production model investigated as
evidence the production model may be wrong.

The challenger pattern works well for well-bounded
econometric and statistical models. It works less well
for ML models, and works poorly for LLMs. Programs that
try to force LLM validation into a challenger-model
pattern miss what SR 11-7 actually asks for.

### 3.1 What independent validation actually means

SR 11-7 §IV identifies four elements of validation:

1. **Evaluation of conceptual soundness** — is the model
   well-founded for its intended use?
2. **Ongoing monitoring** — is the model continuing to
   perform as expected?
3. **Outcomes analysis** — are the model's outputs
   consistent with what actually happens?
4. **Benchmarking and comparison** — does the model
   produce outputs comparable to other defensible
   approaches?

Note what is **not** required by the source text:

- A challenger model is not required. It is **one
  technique** within element 4. SR 11-7 lists challenger
  models as an example, not a mandate.
- A specific frequency of re-validation is not required.
  Risk-tier and triggering events drive it.
- Validation is not the same as testing. Validation
  evaluates the model's *fitness for purpose*, which
  testing alone cannot do.

### 3.2 Validation patterns that work for ML

A taxonomy of validation patterns, with applicability
notes:

| Pattern | What it does | ML applicability |
|---|---|---|
| **Challenger model** | Build an alternative; compare disagreement | Good for tabular ML; moderate for image models; poor for LLMs |
| **Benchmarking against published baselines** | Compare against academic or industry benchmarks | Good when benchmark exists and is appropriate; risky when benchmark fits poorly |
| **Counterfactual evaluation** | Probe the model with synthetic inputs that vary one factor | Good for explainability validation; partial for general robustness |
| **Stress / adversarial testing** | Subject the model to deliberately hostile inputs | Essential for LLMs; good for any production model |
| **Subgroup validation** | Evaluate performance on stratified populations | Required for fairness; often missing from initial validation |
| **Out-of-distribution (OOD) testing** | Test on data deliberately outside training distribution | Important for production drift detection |
| **Red-team evaluation** | Adversarial human probing | Increasingly required for LLM-driven systems |
| **Human evaluation by domain experts** | Domain experts grade outputs against a rubric | Often the only valid approach for LLM outputs without ground truth |
| **Process validation** | Validate the *development process* rather than just the outputs | Important when artifact-based validation is impossible |

Most ML model validations use **several patterns together**.
A single-pattern validation is rarely adequate.

### 3.3 What independence means for ML

SR 11-7 requires that validation be performed by personnel
*independent of the model owner*. For ML this often means:

- **The model owner cannot validate their own model.**
  This rules out the common pattern of "the model team
  validates the model and MRM reviews the validation".
  MRM must do, or commission, the validation.
- **Independence does not require a different organization.**
  A separate team within the same engineering function
  can be sufficient if there is real independence — no
  shared performance review, no shared OKRs.
- **Vendor validation does not substitute for firm
  validation.** A foundation-model vendor's evaluation
  results are useful evidence; they are not validation.

The independence test, in practice: *if the model fails
in production, can the validation team be reasonably
accused of bias toward the model owner?* If yes,
independence is insufficient.

### 3.4 Validation cadence

SR 11-7 requires re-validation on:

- Material model change.
- Material change in intended use.
- Material change in the operating environment.
- Periodic basis (typically annual for material models).

For ML models, *material change* triggers warrant
particular care:

- **Training-data refresh** — material if the refresh
  shifts the distribution materially. Most training
  refreshes meet this bar.
- **Foundation-model swap** (vendor) — material always.
- **Fine-tuning** — material if it changes the
  generation surface.
- **Prompt template change** for LLM systems — material
  if it changes the system's behavioural envelope.

The last one is the most under-recognised. An LLM system
where the prompt template can be changed without
re-validation has effectively defeated the MRM framework.

---

## §4. The model lifecycle with ML-specific stops

SR 11-7 implies a model lifecycle (development →
implementation → use → monitoring → retirement). Working
MRM programs make the lifecycle explicit. For ML, several
stops in the lifecycle deserve more emphasis than they get
in classical financial models.

### 4.1 The lifecycle stops

| Stop | What happens | ML-specific consideration |
|---|---|---|
| **1. Concept / sponsor approval** | Business case; intended use; expected risk tier | LLM use-cases especially benefit from rigorous intended-use definition; the prompt determines the system as much as the model does |
| **2. Data acquisition** | Source identification; provenance documentation; rights review | Training-data IP and consent issues; documented in technical file (mod-102) |
| **3. Development** | Model building; internal testing | Computationally expensive; iterations less reviewable than for classical models |
| **4. Independent validation** | Per §3 above | Multiple patterns combined; cannot rely on a single technique |
| **5. Implementation** | Deployment into the operating environment | LLM systems: prompt template versioning, model-version pinning, output filtering |
| **6. Use** | Operating with first-line controls | Workflow design (asymmetric escalation, human-in-loop, override discipline) |
| **7. Ongoing monitoring** | Performance, drift, fairness, security | Leading + lagging indicators per mod-103 §4 |
| **8. Re-validation** | Periodic + trigger-based | More frequent for ML due to drift dynamics |
| **9. Retirement** | Decommissioning | Often missing in ML programs; models silently outlive their utility |

### 4.2 The two ML lifecycle stops that programs most often skip

**Stop 5 — Implementation review.** Classical models go
from validation to use in one step; the deployment is the
implementation. ML systems often have a deployment
infrastructure (serving stack, prompt template,
post-processing) that is **as load-bearing as the model
itself**. Implementation review covers this. Without it,
the validation evaluates one artifact and production runs
a different artifact.

**Stop 9 — Retirement.** Most ML programs accumulate
models. Models are "deprecated" in name but continue to
serve traffic, or live in a staging environment that is
referenced by production code, or persist in a vendor
contract that has not been renegotiated. A working
lifecycle includes a *named retirement gate* with an
inventory delete and a deployment-removal verification.

### 4.3 The lifecycle's role in audit

A well-defined lifecycle makes audits cheaper. Internal
audit can verify the lifecycle was followed for any
specific model rather than re-validating from scratch. A
program where lifecycle stops are not documented gets a
re-perform-from-scratch audit, which is expensive and
informative in unwanted ways.

---

## §5. The CAIRO × MRM boundary

The most predictable conflict in a CAIRO's first year is
with the MRM function. Both are second-line. Both
oversee model-related risk. Their scope overlaps. mod-101
§4 named this; this section operationalises the boundary.

### 5.1 What MRM owns

MRM owns:

- The MRM framework, policies, and standards for *all*
  models (financial and otherwise).
- Independent validation of models within MRM scope.
- Ongoing monitoring oversight (verifying that first-line
  monitoring is working).
- Model inventory completeness within MRM scope.
- MRM committee operations.
- Reporting to senior management and regulators on
  *model risk*.

### 5.2 What the CAIRO function owns

The CAIRO function owns:

- AI-specific risks that are not exclusively model risk:
  bias and fairness at the program level, transparency to
  affected parties, AI-specific compliance (EU AI Act),
  AI vendor and ecosystem risk.
- AI-specific governance bodies (AI Review Board, AI
  Risk Council).
- The AI risk taxonomy (mod-103 §2).
- The AI risk register (mod-103 §6.2).
- AI program reporting to the Board.
- AI regulator engagement strategy.

### 5.3 The intersection

The overlap is genuine and predictable:

| Topic | CAIRO and MRM both have legitimate ownership claims |
|---|---|
| ML model validation | MRM does the validation; CAIRO sets AI-specific validation expectations (e.g., subgroup fairness as a required validation pattern) |
| Model inventory | MRM owns the inventory of models; CAIRO owns the inventory of AI systems, which overlaps but is not identical |
| AI-specific risks within a model | Bias risk within a credit model is both a CAIRO concern and a fair-lending MRM concern |
| Incident response | MRM may have a model-incident process; CAIRO may have an AI-incident process |
| Vendor AI | MRM has third-party model governance; CAIRO has AI vendor governance |
| Regulator interface | MRM is the historical interface for SR 11-7; CAIRO is the interface for EU AI Act |

### 5.4 Operating the boundary

The patterns that work:

- **Single-incident channel.** When an issue surfaces,
  one function leads investigation and the other is
  informed. The lead is determined by the *primary
  framing* of the issue (model error → MRM; bias pattern
  → CAIRO; combined → joint, with a single named lead).
- **Joint validation expectations.** MRM does the
  validation; the CAIRO has *contributed* to defining the
  expectations the validation must meet. Specifically:
  for AI-specific risk categories (bias, transparency,
  AI-specific security), the CAIRO defines required
  validation patterns; MRM executes.
- **Cross-referenced inventories.** MRM's model
  inventory and the CAIRO's AI system inventory point to
  each other. A row in one references the corresponding
  row in the other. They are not the same artifact.
- **Joint regulator briefings.** When SR 11-7 and EU AI
  Act both touch an issue, the CAIRO and MRM lead present
  together. The regulator hears one organisation, not
  two.

### 5.5 The collision patterns

The patterns that fail:

- **Re-validation of MRM-validated models by the CAIRO
  function.** Creates duplicative work; signals lack of
  trust; produces conflicting findings.
- **Separate model inventories that diverge.** The two
  inventories drift; an audit reveals the divergence;
  the program loses credibility.
- **MRM rejecting AI-specific validation patterns
  ("that's not in SR 11-7").** SR 11-7 explicitly leaves
  validation technique to the firm. Refusing
  subgroup-validation or red-team evaluation because
  classical MRM did not do them is the wrong stance.
- **CAIRO function setting model-validation standards
  unilaterally.** Without MRM concurrence, the standards
  do not get applied. Both functions agree, or neither
  does.

### 5.6 The reporting line question

A recurring debate: should the CAIRO function and MRM
report to the same executive (CRO), or to different
executives?

| Pattern | Tradeoff |
|---|---|
| Both report to CRO | Easier coordination; risk of organizational gravity pulling AI work into "another MRM team" |
| CAIRO to CRO; MRM to a peer (e.g., CFO in some banking structures) | More independence; harder coordination |
| Joint AI committee chaired by CRO with CAIRO and MRM Head as co-chairs | Coordination forcing function; works in mid-sized firms |

There is no universally correct answer. The most common
mature pattern is *both report to CRO + joint
operating committee*.

Exercise 04 forces a specific boundary dispute to a
recommendation.

---

## §6. MRM beyond banking

SR 11-7 is a banking guidance. Its applicability outside
banking is *not* automatic — but the discipline it
encodes is one of the most useful imports a non-bank can
make. Several adaptations follow.

### 6.1 What translates well

- **The four pillars** (development, validation,
  governance, framework integration). These are
  framework-agnostic.
- **The model definition.** Useful in any context — the
  *quantitative method whose outputs drive decisions*
  framing scopes well.
- **The independence requirement for validation.** This
  is the discipline that separates serious programs from
  ceremonial ones.
- **Documentation discipline.** Reproducibility-by-
  another-competent-professional is the right standard
  outside banking too.
- **Tiering.** The principle applies; the criteria adapt.

### 6.2 What does not directly translate

- **The MRM "committee" architecture.** Banks have
  Model Risk Committees with named senior membership.
  Non-banks may not, and forcing them into existence is
  often wrong. Use existing risk-committee architecture
  with an MRM agenda item.
- **The challenger-model paradigm.** As §3 noted, this is
  less applicable for ML. Outside banking it is *also*
  often inapplicable because classical alternative models
  do not exist for the use case.
- **The "model" vocabulary.** Healthcare prefers "device
  algorithm" or "decision-support tool"; insurance
  varies; public sector uses "automated decision
  system". Use the local vocabulary.

### 6.3 Healthcare adaptation

Healthcare has its own analog to SR 11-7 in the FDA's
SaMD framework and the EU MDR — but they cover narrower
scope (medical devices). A healthcare system using AI for
operational decisions (capacity, scheduling, triage non-
device-classified) needs an MRM-like discipline that the
device frameworks do not provide.

Pattern that works: an MRM-equivalent function under the
Chief Medical Officer or Chief Quality Officer, with the
CAIRO function setting AI-specific overlays. The
*independence* concept maps to "clinical safety review of
AI separate from AI development".

### 6.4 Insurance adaptation

Insurance is closest to banking — actuarial models have
their own validation tradition. NAIC Model Law on AI
Systems and CO Reg 10-1-1 require MRM-like discipline.
The state insurance regulator is the analogous supervisor
to OCC/FRB.

The most common gap: AI underwriting models do not get
the same validation rigor as actuarial models. The CAIRO
function's job is to close that gap, often by partnering
with the existing actuarial-validation function.

### 6.5 Public sector adaptation

Public sector deployments (benefits eligibility,
recidivism risk, child-welfare screening) have the
strongest direct-affected-person impact but often the
weakest MRM machinery. Adaptation requires building MRM
discipline more or less from scratch, with particular
attention to:

- Transparency to affected persons (FOIA + due-process
  requirements).
- Algorithmic-discrimination testing (often state-
  mandated).
- Inventory of automated decision systems (Canadian
  Directive, NYC LL35-2018, NJ S1438 pattern).

Exercise 05 builds an MRM-equivalent for one non-bank
context.

### 6.6 Industrial adaptation

Industrial AI (predictive maintenance, quality control,
process optimization) has the most cleanly-defined
ground truth in many cases — the prediction can be
checked against the outcome. This makes validation
*easier* than in financial services. The discipline that
typically gets skipped is *misuse* tracking — operators
relying on AI recommendations beyond the validated
operational envelope. SR 11-7's misuse framing
(§1.1 of these notes) is directly applicable.

---

## References

- **OCC/FRB SR 11-7** (the source — twenty-one pages, read
  it). Section III on framework, Section IV on validation,
  Section V on governance.
- **FRB SR 22-6** — current AI/ML expectations.
- **EBA Guidelines on Model Risk Management** (2023) —
  European parallel; useful comparison.
- **FDA Predetermined Change Control Plan guidance** —
  analog for continuous-learning systems.

Full reading list in [`resources.md`](./resources.md).
