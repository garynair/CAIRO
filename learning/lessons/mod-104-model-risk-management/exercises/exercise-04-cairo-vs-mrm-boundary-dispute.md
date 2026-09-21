# Exercise 04 — Resolve a CAIRO-vs-MRM-Lead Boundary Dispute

**Estimated time**: 3 hours
**Deliverable**: A boundary-resolution memo + a one-page
boundary diagram (≤ 3 pages combined)

---

## The scenario

You are the CAIRO at **Sentinel Mutual Bank**. The MRM Lead
(Director Tier; reports to CRO; 12 years at the bank,
9 in MRM) and you (newly appointed, 6 months in role) have
reached an impasse on a specific question. The CRO has
asked you to **resolve it via a memo and a boundary
diagram** that will be presented to the AI Risk Council
next week.

## The dispute

Sentinel uses **third-party LLM Vendor X** for its
customer-service chat agent (Model B from prior
exercises) and for its internal-document LLM assistant
(Model E from prior exercises). The vendor swapped its
underlying foundation model two months ago with the
contractual 30-day notice; Model B and Model E now run
on a new foundation model.

The disagreement:

**MRM Lead's position**: This is a *vendor change* and
falls under MRM's third-party-model-risk process. MRM
performs a vendor-risk re-assessment and a targeted
re-validation; the change closes within the existing
SR 11-7 process. The CAIRO function is *informed* but does
not need to act.

**CAIRO's position**: This is a *material model change*
that triggers AI-specific risks (changed bias surface,
changed transparency-explainability profile, possibly
changed regulatory-compliance posture under EU AI Act if
in scope). MRM's vendor-risk process is necessary but
not sufficient. The CAIRO function should *lead* a
specifically-AI re-evaluation of both Model B and Model
E behaviour against the bank's AI program controls;
MRM handles the model-quality dimension in parallel.

A third position exists that neither has stated:

**Joint position**: This is *both*. MRM leads the SR
11-7 re-validation; the CAIRO function leads an AI-program
re-evaluation; the two have a single named lead for the
overall response.

## Your assignment

Produce two artifacts.

### Artifact 1 — Boundary-resolution memo (2 pages)

A memo that:

1. **States the resolution** in the first sentence.
2. **Steel-mans the MRM Lead's position** — fairly and
   in their voice. (Resist caricature.)
3. **Steel-mans your own position** — fairly and in your
   voice.
4. **Explains the resolution** — including which
   elements of each position survive and which yield.
5. **Names the operational mechanics**: who does what
   work for this specific case, who is the single named
   lead, how the AI Risk Council oversees, what the
   precedent is for future vendor-model swaps.
6. **Acknowledges the loss** — what each side gave up
   to reach the resolution. Resolutions without
   acknowledged losses tend not to hold.

### Artifact 2 — Boundary diagram (1 page)

A diagram (Markdown table or bulleted hierarchy is fine —
the visual matters less than the structure) showing:

- The two functions' scope at the boundary.
- The intersection (where both have legitimate claims).
- How specific scenarios (model change, incident,
  regulator letter, board reporting) route through the
  boundary.

Use the §5.3 intersection-topic table from the lecture
notes as a starting structure.

## Constraints

- The resolution must be **defensible to both the MRM
  Lead and the CRO**. A memo that one of them would
  obviously reject is not a working resolution.
- The boundary diagram must not require additional
  process to operate — it must describe an arrangement
  that fits within existing governance machinery.
- The memo must explicitly **steel-man both positions
  before resolving**. Resolutions that skip the
  steel-manning are read as one-sided.
- The memo must name a **precedent** — future vendor-
  model swaps will follow this pattern unless explicitly
  revisited.

## Rubric

| Criterion | Weight |
|---|---|
| Resolution stated up front | 10% |
| MRM steel-man — fair, substantive | 15% |
| CAIRO steel-man — fair, substantive | 10% |
| Resolution reasoning — names what survives + what yields from each side | 25% |
| Operational mechanics — single named lead + clear who-does-what | 20% |
| Boundary diagram — operationally usable | 15% |
| Acknowledged loss — present | 5% |

## Where to submit

`solutions/modules/mod-104-model-risk-management/exercise-04-cairo-vs-mrm-boundary-dispute/SOLUTION.md`

Reference solution adopts the *joint* position and
explicitly names the AI Risk Lead in the CAIRO function
as the single named lead for this case, with MRM
performing the model-quality re-validation in parallel.

## Reading before you start

- Lecture notes §5 (CAIRO × MRM boundary) — all of it.
- mod-101 §3 (3LOD) and §4 (peer-role boundaries).
