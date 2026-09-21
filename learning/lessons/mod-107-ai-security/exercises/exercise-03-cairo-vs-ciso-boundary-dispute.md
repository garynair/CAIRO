# Exercise 03 — Resolve a CAIRO-vs-CISO Boundary Dispute

**Estimated time**: 3 hours
**Deliverable**: A boundary-resolution memo + a
one-page boundary diagram (≤ 3 pages combined)

---

## The scenario

You are the CAIRO at **Sentinel Mutual Bank** (the
context from mod-104). The CISO and you have reached
an impasse on the following question. The CEO has
asked you to **resolve it via a memo and a boundary
diagram** that will be presented to the AI Risk
Council and the Bank Risk Committee.

## The dispute

Sentinel's CISO has proposed authoring a new
**"AI Security Engineering Standard"** that will
govern all AI/ML systems at Sentinel. The standard
covers:

- Input validation requirements
- Output filtering requirements
- Adversarial-input detection
- Model-version security controls
- Vendor AI security assessment
- Red-teaming requirements
- AI incident response integration with the existing
  IR program
- Prompt-injection defence controls

You (the CAIRO) have multiple objections, which fall
into three groups.

**Group 1 — Boundary objections.** Some of the
standard's content overlaps with what the AI
program is already producing — specifically, the
red-teaming requirements (you authored the program-
level red-teaming policy per Exercise 02 in mod-107
of the curriculum), the vendor AI security
assessment (this overlaps with the AI vendor risk
program), and AI incident response (you are
authoring an AI incident classification taxonomy per
Exercise 04 of this module).

**Group 2 — Substantive objections.** The proposed
prompt-injection defence controls list specific
techniques (specific input-filter products, specific
output-filter configurations). You believe these are
*implementation choices*, not standards — standards
specify *what* must be done, not *which products*
are used.

**Group 3 — Cross-LOB objections.** The standard is
written from a single security-engineering
perspective and does not differentiate between
classical-ML systems and LLM-based systems. Sentinel
runs both; the controls applicable to a credit
gradient-boost model are different from those
applicable to a customer-service LLM agent.

The CISO's position: the CISO's organisation is the
security accountable function at Sentinel; AI/ML
security falls under that scope; the standard is
within the CISO's mandate.

Your position is some combination of Groups 1–3.

## Your assignment

Produce two artifacts.

### Artifact 1 — Boundary-resolution memo (2 pages)

A memo that:

1. **States the resolution** in the first sentence.
2. **Steel-mans the CISO's position** — fairly,
   in the CISO's voice, addressing why authoring
   the standard is within their mandate.
3. **Steel-mans your own position** — substantively
   addressing the three groups of objections.
4. **Explains the resolution** — including which
   elements of each position survive.
5. **Names the operational mechanics**: who
   authors what part of the standard, who owns the
   standard's maintenance, how it integrates with
   existing AI-program standards.
6. **Acknowledges the loss** — what each side
   gives up.
7. **Names the precedent** — future similar
   standards questions will be guided by this
   resolution.

### Artifact 2 — Boundary diagram (1 page)

Per the §5 framework, a diagram showing:

- The CISO's scope on AI/ML security.
- The CAIRO function's scope on AI/ML security.
- The intersection topics and how they route.
- Specific scenario routing (e.g., prompt
  injection defence: who authors what part).

## Constraints

- The resolution must be **defensible to both the
  CISO and the CRO**.
- The boundary diagram must be **operationally
  usable** — describe an arrangement that fits
  within existing governance machinery, not new
  process.
- The memo must **steel-man both positions
  substantively** before resolving.
- The memo must name a **precedent**.
- The substantive objection (specific products
  vs. standard-specifying-what) must be addressed
  — the CAIRO's objection to specific products
  cannot be evaded.

## Rubric

| Criterion | Weight |
|---|---|
| Resolution stated up front | 10% |
| CISO steel-man — fair, substantive | 15% |
| CAIRO steel-man — addresses all three groups | 15% |
| Resolution reasoning — what survives + what yields | 25% |
| Operational mechanics — clear who-does-what | 20% |
| Boundary diagram — operationally usable | 10% |
| Acknowledged loss | 5% |

## Where to submit

`solutions/modules/mod-107-ai-security/exercise-03-cairo-vs-ciso-boundary-dispute/SOLUTION.md`

Reference solution adopts a *split* resolution:
CISO authors the security-engineering implementation
guidance (input/output filtering products,
adversarial-input detection techniques, IR
integration mechanics); CAIRO function authors the
program-level requirements (what must be filtered,
what red-teaming policy applies, what vendor
assessment criteria apply). The split mirrors the
mod-104 CAIRO × MRM resolution. Specific
prompt-injection defence techniques fall to the
CISO.

## Reading before you start

- Lecture notes §5 (CAIRO × CISO boundary).
- mod-104 Exercise 04 reference (the parallel CAIRO ×
  MRM boundary dispute).
- mod-101 §3 (3LOD) and §4 (peer-role boundaries).
