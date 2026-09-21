# Exercise 03 — CAIRO vs CISO Boundary Dispute — Reference Solution

## 1. Solution overview

The recommendation is a **split-authorship
resolution**: the CISO authors the security-
engineering implementation guidance; the CAIRO function
authors the program-level requirements. Specific
products do not appear in the CAIRO's standard;
specific techniques live in the CISO's implementation
guide. This mirrors the mod-104 Ex-04 CAIRO × MRM
resolution. The acknowledged loss: both sides give up
sole authorship of an "AI security standard" of their
own design.

---

## 2. Artifact 1 — Resolution memo

> **MEMO**
> **TO:** CRO, AI Risk Council, Bank Risk Committee
> **FROM:** Chief AI Risk Officer (with CISO concurrence)
> **SUBJECT:** AI Security Standard — boundary
> resolution
> **PAGES:** 2

**Resolution.** Sentinel will produce **two
complementary documents** governing AI/ML security:
the **AI Security Program Requirements** (authored
by the CAIRO function) and the **AI Security
Engineering Implementation Guide** (authored by the
CISO organisation). The CAIRO document specifies *what*
must be defended; the CISO document specifies *how*
the defences are implemented. The two documents are
versioned together, reviewed jointly, and maintained
in parallel. This pattern becomes the precedent for
future AI-program standards questions.

### The CISO's position (steel-manned)

The CISO has been Sentinel's accountable function
for security for nine years. Information security at
Sentinel — including securing systems that process
sensitive customer information, regulated under
NYDFS Part 500 — is a CISO mandate that pre-existed
the AI program and continues to apply to AI/ML
systems. The proposed "AI Security Engineering
Standard" is within the CISO's existing scope: the
standard specifies controls for securing AI/ML
systems, which is what the CISO does for every
other category of system at Sentinel. Carving AI/ML
security out from this scope creates a parallel
security function for AI — exactly the kind of
encroachment the CISO has organisational
responsibility to resist. The CAIRO has program-level
inputs but does not own AI security; security is
the CISO's accountability.

This position is correct on several points:

- The CISO is Sentinel's accountable security
  function and AI/ML systems do fall within that
  scope.
- Parallel-security-function encroachment is a real
  organisational risk.
- The CISO's nine years of supervisor-facing track
  record on Sentinel security is a real asset.

### The CAIRO's position (steel-manned)

Three objections, as stated in the scenario.

**Group 1 — Boundary objections.** Specific
elements of the proposed standard overlap with
work the AI program is already doing:

- *Red-teaming requirements.* The CAIRO function has
  produced the program-level red-teaming policy
  (per mod-107 Ex-02 pattern). A CISO-authored
  red-teaming requirement creates duplicative or
  inconsistent guidance.
- *Vendor AI security assessment.* The AI vendor
  risk program (per the obligations register from
  mod-102 §6.1) has AI-specific assessment criteria
  the CAIRO function authors.
- *AI incident response integration.* The AI
  incident classification taxonomy (mod-107 Ex-04
  pattern) is being authored by the CAIRO function.

These are not *security* questions in the classical
sense; they are *AI-program* questions with
security implications. The boundary discipline (§5
of mod-107 lecture notes) places them on the CAIRO
side.

**Group 2 — Substantive objections.** The proposed
standard names specific products and specific
configurations. This is a category error: standards
specify *what must be done*, not *which products
are used*. A standard that names products becomes
out-of-date when product choices evolve, and
encourages reading-the-standard-by-product rather
than reading-by-purpose. The mod-101 §6 (failure
modes) framing applies: vendor-named standards are
the *vendor capture* pattern.

**Group 3 — Cross-LOB objections.** Sentinel runs
both classical-ML systems (credit gradient-boost,
fraud anomaly detector) and LLM-based systems
(customer-service agent, internal LLM assistant).
Their security requirements differ. A single
standard written from one security-engineering
perspective will under-serve one of the two
classes.

### Why the split-authorship resolution holds

The CAIRO's substantive objections (Groups 2 and 3)
are correct on the merits. The CISO's accountability
objection is also correct: security at Sentinel is
the CISO's responsibility. Both are right;
neither's full position is sustainable on its own.

The split-authorship resolution preserves both. The
CISO's organisation authors the engineering
implementation — including the specific
configurations, specific techniques, specific
vendor choices (where products are named) that
engineers need. The CAIRO's function authors the
program requirements — including what must be
defended, what evidence is required, what
red-teaming policy applies. The two documents
together constitute Sentinel's AI security posture.

This is the same pattern as mod-104 Ex-04 (CAIRO ×
MRM vendor-swap response): two functions, each
within scope, coordinating through clearly-defined
artifacts. The pattern is established and the
regulators recognise it.

### Operational mechanics

- **CAIRO document — "AI Security Program
  Requirements".** Authored by the CAIRO function;
  reviewed annually; updated on program change.
  Approval: AI Risk Council. Content covers:
  what categories of attack must be defended
  against (referencing the threat model artifacts
  from mod-107 Ex-01 pattern); what evidence is
  required for each category; tiered application
  (per mod-104 §2); program-level red-teaming
  policy; AI vendor assessment criteria;
  AI-specific incident classification.
- **CISO document — "AI Security Engineering
  Implementation Guide".** Authored by the CISO
  organisation; reviewed annually + on material
  technology change. Approval: CISO. Content
  covers: specific implementation techniques for
  the defence categories the CAIRO document
  identifies; specific products and configurations
  where applicable; engineering procedures;
  detection and response operations.
- **Joint review** — both documents are reviewed
  side-by-side at the annual review. Coverage
  gaps and overlaps are surfaced.
- **Cross-references** — the CISO document cites
  the CAIRO document for *why* certain controls
  exist; the CAIRO document cites the CISO document
  for *how* program requirements are met in
  practice.
- **Incident response** — the CAIRO incident
  classification taxonomy determines lead. The
  CISO's IR processes execute on security
  classifications. Joint incidents follow the §6
  pattern from the lecture notes.

### Precedent

Future AI-program standards questions where the
CAIRO program and CISO organisation both have
legitimate ownership will follow this split-
authorship pattern. The pattern applies
broadly — model risk standards (mod-104 already
applied it), AI security standards (this
resolution applies it), AI vendor standards (next
in line).

### Acknowledged loss

The CISO gives up sole authorship of a single,
unified "AI Security Standard" of their own
design. This is a real loss: the CISO's nine-year
practice has been single-document standards in
their domain, and the split pattern introduces a
sister document the CISO does not control. The
CAIRO gives up the option of having the program
write security guidance unilaterally; the CAIRO
must coordinate with the CISO on every program
requirement that maps to a security control. Both
sides accept the coordination cost as the price
of the substantive correctness of the split.

— end memo —

---

## 3. Artifact 2 — Boundary diagram

```
                  CISO scope                       CAIRO function scope
              ┌──────────────────┐             ┌─────────────────────┐
              │ Infrastructure   │             │ AI risk taxonomy    │
              │ Network          │             │ AI Risk Register    │
              │ Identity         │             │ AI Review Board     │
              │ Endpoint         │             │ AI policy hierarchy │
              │ IR operations    │             │ AI vendor program   │
              │ Vuln management  │             │ AI threat model     │
              │ Pen testing      │             │ AI red-team policy  │
              │ SecOps + SOC     │             │ Regulator-facing    │
              └──────────────────┘             └─────────────────────┘
                       │                              │
                       └────────── Intersection ──────┘
                            (split authorship)
                ┌──────────────────────────────────────┐
                │ AI security control specification    │
                │ (CAIRO requirements; CISO impl guide)  │
                │                                       │
                │ Topic                CAIRO doc  CISO doc│
                │ --------------------------------------│
                │ What attacks defend  X                │
                │ Specific products             X       │
                │ Red-teaming policy   X                │
                │ Red-team execution            X       │
                │ AI vendor criteria   X                │
                │ Vendor assessment             X       │
                │ Incident class       X                │
                │ Incident response             X       │
                │ Reg notification              joint   │
                └──────────────────────────────────────┘

Scenario routing:

1. Prompt injection defence
   → CAIRO: requires defence against the threat
   → CISO: implements the technique (input filter,
     output filter, etc.)
   → Joint review on whether implementation meets
     requirements

2. AI vendor security assessment
   → CAIRO: defines AI-specific assessment criteria
   → CISO: executes assessment using existing
     vendor-risk infrastructure with criteria

3. AI security incident
   → Initial classification per CAIRO taxonomy
   → CISO IR executes
   → Joint regulator notification per CAIRO
     obligations register

4. Red-teaming exercise
   → CAIRO authors the exercise design
     (Ex-02 pattern)
   → CISO executes (with external participants
     where applicable)
   → Joint findings disposition

5. New threat category emerges in MITRE ATLAS
   → CAIRO updates threat model coverage in the
     CAIRO document
   → CISO updates implementation guide if new
     defences are warranted
   → Joint review at next annual standards review
```

---

## 4. Reasoning notes

- **Why the split-authorship pattern over either
  unilateral position.** Each unilateral position
  is structurally wrong. CISO-alone produces
  vendor-captured standards that don't
  differentiate by tier or by LOB. CAIRO-alone
  produces requirements engineers won't follow
  because they're not engineering-grade. Split
  is the only resolution that preserves both
  correctness conditions.
- **Why this mirrors mod-104 Ex-04.** Both
  resolutions split authorship: technical
  authority on the technical side (MRM does the
  validation; CISO does the security
  engineering); program authority on the program
  side (CAIRO defines the validation expectations;
  CAIRO defines the security requirements). The
  pattern is reusable and the precedent matters.
- **Why I named "specific products" as a CAIRO
  objection.** The Group 2 substantive objection
  is correct on its merits regardless of the
  boundary question. Standards that name products
  age poorly and produce vendor lock-in. The
  steel-manning includes this position because
  it's not just a boundary turf objection — it's
  a substantive standards-craft objection.
- **Why I separated the cross-LOB concern from
  the boundary concern.** The Group 3 cross-LOB
  objection is also substantive: Sentinel really
  does have classical-ML and LLM-based systems
  with different security requirements. A
  CISO-authored standard could in principle
  address this; in practice it would be hard
  to maintain that perspective across an
  organisation with single-discipline expertise.
- **Why the acknowledged-loss section names the
  CISO's nine-year practice change.** §6.3 of
  mod-105 — acknowledged losses build durable
  resolutions. The CISO's nine years of practice
  is the substantive thing being changed; not
  naming it would let it be silently re-asserted
  later.
- **What this resolution under-specifies.** The
  format of the cross-references between the two
  documents, the specific JIRA epics for each
  doc's maintenance, the operational SLAs for
  joint review. These are operational details
  that the CAIRO and CISO organisations work out
  after the resolution is approved.
- **What would change my position.** If
  Sentinel were a 5,000-person organisation
  (not 25,000), the coordination cost of
  split-authorship might exceed the substantive
  benefit, and a single-authorship pattern
  (most likely CISO-authored with CAIRO
  appendix) would be more defensible. Sentinel's
  scale supports the cost.

---

Maintained by [Girish Nair](https://github.com/garynair)
