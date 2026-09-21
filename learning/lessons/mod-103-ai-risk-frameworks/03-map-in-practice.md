# Chapter 3 — MAP in Practice

## Why this chapter exists

MAP is the NIST AI RMF function that says *what we have,
what it is, what could go wrong with it*. Everything
downstream depends on MAP: MEASURE cannot pick metrics
without MAP's classification, and MANAGE cannot design
treatments without MAP's failure modes. In an EU AI Act
context, MAP is also the substrate for Article 9(2)(a) —
identification and analysis of the known and reasonably
foreseeable risks (mod-102 Chapter 3 has the crosswalk).

MAP produces three artifacts. This chapter walks each in
turn, then names the discipline that separates a working
MAP function from a decorative one. The impact assessment
— the third artifact — gets its own chapter (Chapter 4)
because it is where most CAIROs spend the most authoring
time.

## The three MAP artifacts

MAP does not produce one document; it produces three
interlocking ones.

1. **The AI system inventory** — every AI system the
   organization operates.
2. **The system classification** — what regulatory and
   risk categories each system carries.
3. **The impact assessment** — for each system, a
   structured naming of how things could go wrong.

The artifacts compound. Inventory feeds classification;
classification scopes the impact assessment; the impact
assessment feeds MEASURE (Chapter 5) and MANAGE
(Chapter 6). A program missing any of the three has a
break in the chain.

## The inventory

The inventory is the *baseline*. If the program cannot
answer *how many AI systems are we operating* on demand,
nothing downstream is credible.

A working inventory is one row per system with a small,
fixed set of attributes.

| Attribute | What it is |
|---|---|
| System ID | Stable identifier, generated once, never reused |
| Name + description | Human-readable, updated when the description drifts |
| Owner (first line) | Named role, not a person; roles outlive people |
| Business unit | For roll-up |
| Use case | What the system does in one sentence |
| In-scope per program scope rules? | yes / no / out-of-scope-with-reason |
| Regulatory classifications | EU AI Act tier, sector applicability, jurisdiction |
| Risk categories (from Chapter 2 taxonomy) | Applicable categories |
| Status | Pilot / production / deprecated / retired |
| Last impact assessment | Date + result |
| Vendor / third-party dependencies | For MANAGE-3.x traceability |

Two disciplines make the inventory sustainable:

- **Easy to update.** Adding a new system should not
  require a full impact assessment first. The inventory
  is a *register*, not a portfolio review; the impact
  assessment happens after the inventory row exists.
- **Hard to forget.** A monthly attestation from each
  business unit — *"the inventory is complete for our
  scope, or here is what is missing"* — creates a signed
  record that the inventory is current. Without the
  attestation, the inventory silently drifts.

Programs that skip either discipline will have inventories
missing 20–40% of production systems within twelve months.
The shadow systems are usually where the incidents happen.

## Classification

Classification places a system against two lists:

- The regulatory classifications from mod-102 — EU AI Act
  tier under Art. 6 and Annex III, sector regimes (SR 11-7,
  SaMD, NAIC, etc.), state laws (NYC LL 144, CO AI Act,
  CA AITA), and jurisdictional applicability.
- The AI risk taxonomy from Chapter 2 — which top-level
  categories apply.

Two disciplines govern classification.

### Classification is conservative

When a system could *plausibly* carry a category, the
classification includes it. The cost of carrying a category
that turns out not to apply is the effort of an impact
assessment section that concludes *not applicable*. The
cost of missing a category that does apply is an incident
in that category later, with the finding that classification
missed it.

Regulators read conservative classification as diligence.
They read minimalist classification as an attempt to reduce
scope.

### Classification is revisited

Classification is not a one-time act. It is triggered by:

- Any **material system change** — data source, model
  architecture, output use, user population. Materiality
  is defined by policy in advance (a common threshold: any
  change that would require a re-validation under the
  program's model-risk standard).
- Any **material regulatory change** — a new statute, a
  new enforcement action against an analogous system, a
  new guidance document that reads on the system.
- Any **material context change** — new deployment
  geography, new user category, new adjacent system it
  relies on or that relies on it.

A working classification history is versioned: what changed,
when, why, who authorised. Regulators frequently ask *"when
did you last classify this system"* — the answer *"at
launch, four years ago"* rarely lands well.

## Naming *material* in policy

The word *material* appears three times above and is doing
significant work. A program that has not defined *material*
in policy will re-negotiate the meaning every time the
classification trigger is invoked, and the program will
converge on *nothing is material* under time pressure.

A working *material change* definition names concrete
thresholds. For example:

- Any change to the training-data population definition.
- Any change to the model class (e.g., linear → tree
  ensemble → neural network → LLM).
- Any change that shifts the output from advisory to
  decisional, or from decisional to autonomous.
- Any change that changes the affected population by more
  than a policy-defined percentage.
- Any change to a system on which a downstream regulated
  decision depends.

The thresholds are the CAIRO's to set, subject to review by
the AI Risk Council. Once set, they are used consistently.

## What MAP is *not*

MAP is not the place to *resolve* risks. MAP names them. A
common failure mode is to use the impact assessment as a
mini-MANAGE — the assessment writer surfaces a risk and
then proposes a control in the same breath, then declares
the risk resolved.

This forecloses the more careful MEASURE and MANAGE steps
and collapses the program into a single act. It also
produces artifact-shaped compliance theatre: the assessment
document exists, the risk appears mitigated, the treatment
plan and residual-risk decision never happen.

Discipline: in MAP, *name* the risk. The control is named
by MANAGE. The measurement of whether the risk is present
is designed by MEASURE. Separating them by discipline —
even when the same person is authoring all three — keeps
the loop honest.

## The crosswalk to Article 9

For any high-risk EU AI Act system, MAP is what produces
the raw material for Article 9(2)(a) — identification and
analysis of the known and reasonably foreseeable risks.
mod-102 Chapter 3 is the detailed crosswalk; two callouts
matter here.

- Article 9 requires risks framed in terms of **health,
  safety, or fundamental rights**. A NIST-shaped MAP list
  of *"model latency regression"* is not an Article 9
  risk. Translation to the health / safety / fundamental
  rights frame is a MAP-side responsibility.
- Article 9 requires that **reasonably foreseeable
  misuse** is treated on equal footing with intended use.
  The classification and impact assessment must both cover
  it. A red-team scenario in which the system is
  jailbroken into contraindicated behaviour is an Art. 9
  exhibit even if the vendor never intended that mode.

If you have a high-risk system in scope, the MAP outputs
must be *readable as* the Article 9(2)(a) evidence. The
next audit will require it.

## Concrete example — one system through MAP

The AI-assisted small-business loan-decisioning system
from Chapter 2's example, viewed through MAP.

1. **Inventory row.** System ID `SB-LOAN-01`; owner *Head
   of SMB Lending*; use case *first-pass credit
   recommendation for loans under $250K*; status
   *production*; regulatory classifications *ECOA / Reg B;
   SR 11-7 model tier 2; state-level: NY, CA, IL for
   in-state lending*; risk categories *1, 2, 3, 4, 6, 7,
   8*.
2. **Classification.** Not EU AI Act high-risk (no EU
   customers). SR 11-7 tier 2 (material decision impact
   but with a human override). Fair-lending obligations
   dominant.
3. **Impact assessment scope.** All eight applicable risk
   categories worked in the assessment; the ninth
   (strategic risk) declared *not applicable* with a
   one-sentence justification.

The three artifacts refer to each other by ID. The
classification versions are dated. The impact assessment
cites the inventory row and the classification version it
was written against. Chapter 4 develops the assessment
itself.

## Summary

- MAP produces three artifacts that compound: the
  inventory, the classification, and the impact
  assessment.
- The inventory is a register, not a portfolio review;
  the discipline is *easy to update, hard to forget*, with
  a monthly attestation per business unit.
- Classification is conservative (include the category
  when it could plausibly apply) and versioned (revisited
  on material change).
- The word *material* must be defined in policy or the
  trigger will drift under pressure.
- MAP names risks; it does not resolve them. Control
  design is MANAGE, metric design is MEASURE. Collapsing
  them destroys the loop.
- For any high-risk EU AI Act system, the MAP outputs are
  the substrate for Article 9(2)(a). Frame risks in
  health / safety / fundamental rights terms and cover
  reasonably foreseeable misuse.
