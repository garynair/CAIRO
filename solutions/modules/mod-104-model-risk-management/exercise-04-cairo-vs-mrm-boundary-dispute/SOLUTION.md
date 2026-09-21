# Exercise 04 — CAIRO vs MRM Boundary Dispute — Reference Solution

## 1. Solution overview

The reference adopts the **joint position**: this is
both a vendor change (MRM's SR 11-7 process) and a
material model change (CAIRO's AI-program response). The
AI Risk Lead in the CAIRO function is the single named
lead for the overall response; the MRM Lead leads the
SR 11-7-specific re-validation in parallel. The
precedent set is that vendor foundation-model swaps for
LLM-class systems trigger both pathways with named
single-lead coordination.

---

## 2. Artifact 1 — Resolution memo

> **TO:** CRO; AI Risk Council
> **FROM:** Chief AI Risk Officer (with MRM Lead concurrence)
> **SUBJECT:** Vendor X foundation-model swap — boundary
> resolution
> **DATE:** [date]
> **PAGES:** 2

**Resolution.** This is both a vendor change and a
material model change. The AI Risk Lead in the CAIRO
function will be the single named lead for Sentinel's
response, coordinating MRM's SR 11-7 re-validation and
the CAIRO function's AI-program re-evaluation. Both
streams report into the AI Risk Council on a single
status. This pattern becomes the precedent for future
vendor foundation-model swaps on LLM-class systems.

### The MRM Lead's position (steel-manned)

MRM has operated under SR 11-7 for nine years at
Sentinel. The third-party-model-risk process — vendor
re-assessment plus targeted re-validation — is well-
established, has cleared multiple internal audits, and
has the regulator's confidence. Vendor X's foundation-
model swap is materially a vendor-driven model change;
SR 11-7's third-party-model framework was designed
precisely to handle this case. Running a parallel CAIRO-
led re-evaluation introduces process duplication,
risks contradictory findings, and complicates the
regulator interface — SR 11-7 supervisors expect MRM to
own model-quality re-validation for any model under
MRM scope, and Models B and E are under that scope.
The AI program should be informed of the outcome and
should focus on AI-program-level concerns that are not
model-quality questions.

This position is correct on several points: SR 11-7
*does* expect MRM to own model-quality re-validation;
process duplication *is* a real concern; the regulator
interface for SR 11-7 *is* MRM's. The position holds
if and only if the model-quality re-validation is the
complete response.

### The CAIRO's position (steel-manned)

A foundation-model swap is not a parameter update or a
re-train; it is a replacement of the substrate the
production system runs on. Behaviour can shift in ways
SR 11-7-style validation does not naturally surface:
bias patterns specific to the new model's training
distribution; transparency-explainability changes that
affect the bank's adverse-action posture; security
properties (prompt injection, output-filter
effectiveness) that are functions of the model's
behaviour rather than its inputs and outputs in
classical terms. The bank also has EU AI Act exposure
for some customer-facing flows; the EU AI Act's
post-market monitoring expectations are not satisfied
by MRM's third-party-model process alone. A CAIRO-led
AI-program re-evaluation is necessary in addition to
MRM's re-validation.

This position is also correct on several points:
foundation-model swaps *do* change behaviour
qualitatively; AI-specific risk dimensions *are* not
fully covered by SR 11-7 validation patterns; EU AI
Act post-market monitoring *is* the CAIRO function's.
The position holds if and only if it is additive to,
not in conflict with, MRM's process.

### Resolution

Both processes run. The processes are *additive, not
duplicative*, because they address different things:

- MRM's third-party-model re-validation covers
  conceptual soundness, ongoing monitoring posture,
  outcomes analysis on the post-swap behaviour, and
  benchmark comparison against the pre-swap baseline.
  This is the SR 11-7 surface.
- The CAIRO function's AI-program re-evaluation covers
  bias-surface changes (subgroup re-validation per
  Exercise 02 pattern set), transparency-explainability
  posture (counterfactual evaluation re-run),
  security-property changes (adversarial testing
  re-run), and EU AI Act post-market monitoring update
  for the in-scope flows. This is the AI-program
  surface.

The MRM Lead concedes that the AI-program surface is
not covered by the classical SR 11-7 process and that
running both is operationally necessary. The CAIRO
concedes that MRM is the SR 11-7 lead for the model-
quality dimension and that the CAIRO function does not
re-validate what MRM has validated.

The processes share evidence where possible (the
subgroup-validation results from Exercise 02 patterns
inform MRM's benchmark comparison; MRM's outcome
analysis informs the CAIRO's monitoring update). A
single shared status document is maintained by the
AI Risk Lead.

### Operational mechanics

- **Single named lead:** AI Risk Lead (CAIRO function).
- **MRM stream lead:** MRM Lead, executing the SR 11-7
  re-validation.
- **CAIRO stream lead:** AI Risk Lead's deputy, executing
  the AI-program re-evaluation.
- **Reporting:** Shared weekly status to AI Risk
  Council; combined findings to the Council's monthly
  meeting and to the next Board Risk Committee
  meeting.
- **Regulator interface:** MRM Lead represents
  Sentinel to the OCC for the SR 11-7 elements; CAIRO
  represents Sentinel to any EU AI Act post-market
  monitoring reporting; both are present for any
  combined inquiry.

### Precedent

Future vendor foundation-model swaps on LLM-class
systems (which is most LLM-class systems Sentinel
will operate) will follow this dual-stream pattern
with the AI Risk Lead as the single named lead. MRM
and CAIRO Standards are updated to reflect this
precedent at the next quarterly policy refresh.

### Acknowledged loss

The MRM Lead gives up sole ownership of the
re-validation narrative for vendor-model changes
affecting AI-program-relevant surfaces. This is
real — for nine years, MRM has been the single voice
on these matters to the AI Risk Council. The CAIRO
gives up the option of leading the entire response
alone, which in this case would have produced a
faster and more AI-program-coherent narrative at the
cost of regulator-interface continuity. Neither side
got the version of the response they would have
authored unilaterally.

— end memo —

---

## 3. Artifact 2 — Boundary diagram

```
                MRM scope                       CAIRO function scope
            ┌──────────────────┐             ┌──────────────────┐
            │ SR 11-7 framework│             │ AI Risk Register │
            │ MRM policy       │             │ AI Risk Taxonomy │
            │ MRM committee    │             │ AI Review Board  │
            │ Indep. validation│             │ AI policy        │
            │ Outcomes analysis│             │ AI vendor mgmt   │
            └──────────────────┘             └──────────────────┘
                       │                              │
                       └────────── Intersection ──────┘
                            (joint coordination)
                ┌──────────────────────────────────────┐
                │ Model inventory (cross-referenced)   │
                │ Validation expectations (joint)      │
                │ Vendor model change response (joint) │
                │ Incident response (joint, case lead) │
                │ Regulator briefing (joint)           │
                │ Board reporting (joint)              │
                └──────────────────────────────────────┘

Scenario routing:

1. Vendor LLM foundation-model swap
   → dual stream, AI Risk Lead = single named lead
   → MRM: SR 11-7 re-validation
   → CAIRO: AI-program re-evaluation (subgroup, transparency,
     security, EU AI Act PMM)
   → joint status to AI Risk Council

2. ML model incident detected by MRM monitoring
   → MRM leads investigation
   → CAIRO informed; consulted on AI-program-relevant
     implications
   → joint regulator brief if EU AI Act Art. 73 or
     equivalent triggers

3. Bias pattern surfaced by AI-program monitoring
   → CAIRO leads investigation
   → MRM consulted on model-quality implications
   → joint review at AI Risk Council; treatment plan
     update may trigger MRM re-validation

4. New regulator letter on AI/ML
   → If primarily SR 11-7 (OCC, FRB): MRM responds, CAIRO
     informed
   → If primarily AI-specific (EU AI Act authorities,
     state insurance): CAIRO responds, MRM informed
   → If mixed: joint response, CAIRO lead

5. Board quarterly report on AI/ML risk
   → CAIRO drafts; MRM Lead concurs; CRO signs off
   → MRM-specific model-risk roll-up is an embedded
     section authored by MRM Lead
```

---

## 4. Reasoning notes

- **Why the joint position over either unilateral
  position.** Each unilateral position has structural
  problems that the joint position avoids. The MRM-
  only position misses AI-specific surfaces that
  classical SR 11-7 was not designed for; the CAIRO-
  only position breaks the regulator-facing SR 11-7
  posture that nine years of MRM history rests on.
  The joint position is the only one that survives
  both internal scrutiny and external review.
- **Why the AI Risk Lead, not the CAIRO, is named lead.**
  The CAIRO is too senior to be the operational single
  lead for a specific vendor-event response.
  Designating the AI Risk Lead (a CAIRO direct report)
  preserves CAIRO oversight without consuming CAIRO
  calendar on operational coordination. The MRM Lead
  is also too senior; their stream lead is themselves
  for political-weight reasons (the MRM Lead must be
  *visible* as a stream lead given their nine-year
  tenure).
- **Why I named the precedent explicitly.** Future
  vendor model swaps will happen. A resolution that
  works for this case but does not establish a
  precedent invites re-litigation next time. Naming
  the precedent forecloses that.
- **Why the acknowledged-loss section matters.** The
  MRM Lead has agreed to a real loss of unilateral
  control. The CAIRO has agreed to a real loss of
  unilateral framing. Acknowledged losses build the
  resolution's durability. Resolutions where one side
  is silently "given everything they wanted" tend not
  to hold.
- **What the steel-manning does politically.** The MRM
  Lead reads the memo and sees their position
  represented fairly. The CRO reads the memo and sees
  both positions taken seriously, then resolved with
  reasoning that both can defend. The AI Risk Council
  reads the memo and sees a CAIRO who can navigate
  internal political complexity, which is a separate
  good from technical correctness.
- **What this memo deliberately under-specifies.** The
  specific re-validation acceptance criteria. Those
  belong in the validation plan (Exercise 02 pattern
  set as a starting point); the memo establishes
  governance, not technical content.
- **A counter-scenario where my position would
  change.** If Sentinel had had a recent MRM finding
  that the CAIRO function had questioned, *and* the AI
  Risk Council had sided with the CAIRO, the political
  dynamic would be different — the joint position
  would risk the MRM Lead reading it as another
  encroachment. The acknowledged-loss framing matters
  more in that case; without it, the resolution would
  not be durable.

---

Maintained by [Girish Nair](https://github.com/garynair)
