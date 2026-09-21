# Exercise 04 — Stakeholder Map — Reference Solution

## 1. Solution overview

For **Tessera Bank**'s small-business loan-decisioning
deployment, the RACI below assigns exactly one Accountable
per activity, keeps MRM validation independent of the model
owner, and preserves a named Accountable for fair-lending
obligations. The influence/interest map in §3 places the
roles by their actual power to influence the decision and
their substantive interest in the outcome — not by org
seniority.

## 2. RACI matrix

Legend: **R** Responsible, **A** Accountable, **C** Consulted,
**I** Informed.

| Activity | CAIRO | CRO | CDO | CTO | CISO | GC | CCO | Head of Underwriting | Head of Fair Lending | MRM Lead | Model Owner | Vendor Risk Lead | AI Review Board | Board Risk Cmte |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1. Model selection | C | I | C | I | I |  |  | C |  |  | **R/A** |  | I | I |
| 2. Training-data curation (incl. external data) | C | I | **A** |  |  |  |  | C |  |  | R |  | I | I |
| 3. Bias / fair-lending evaluation | C | I |  |  |  | C | C |  | **A** | R | R |  | C | I |
| 4. Model validation (independent challenge) | C | I |  |  |  |  | I |  |  | **R/A** |  |  | C | I |
| 5. Consumer-notice language |  |  |  |  |  | **R/A** | C |  | C |  |  |  | I | I |
| 6. Vendor due diligence | C |  | C |  | C | C |  |  |  |  |  | **R/A** | I | I |
| 7. Operational monitoring plan | C | I |  |  |  |  |  | C | C | C | R |  | **A** | I |
| 8. Go / no-go deployment decision | C | C |  | I | I | I | C | I | I | C | I | I | **R/A** | C |
| 9. Incident-response plan | **R/A** | C |  |  | C | C | C | C | C |  | C |  | I | I |

**Notes on specific rows:**

- **Row 1 (model selection).** Accountable sits with the
  model owner. The CAIRO is consulted (sets standards) but
  does not pick the modeling approach — that is a first-line
  decision per §4 of the lecture notes.
- **Row 3 (bias / fair-lending).** Accountable is the Head
  of Fair Lending. Both MRM and the model owner are
  Responsible (they do the work); this is one of the few
  rows with two R's, which is acceptable. GC is consulted
  because the legal interpretation of ECOA disparate impact
  matters to the conclusion.
- **Row 4 (model validation).** Accountable is the MRM Lead
  with no R/A on the model owner — preserving SR 11-7
  independence. This is the most important row in the
  matrix.
- **Row 8 (go / no-go).** Accountable is the AI Review
  Board, not any individual. The CAIRO chairs the Board but
  the Board's authority is collective. The Board Risk
  Committee is *consulted* (the deployment is material
  enough to bring to the Committee), not just informed.

## 3. Influence / interest map

```
                       INFLUENCE
              LOW                       HIGH
        ┌────────────────────┬────────────────────┐
   HIGH │ Head of Fair       │ CAIRO                │
        │ Lending            │ CRO                │
        │ MRM Lead           │ Head of            │
        │ Vendor Risk Lead   │   Underwriting     │
        │                    │ AI Review Board    │
        │ KEEP INFORMED      │ MANAGE CLOSELY     │
INTEREST├────────────────────┼────────────────────┤
        │ CDO                │ CTO                │
        │ CCO                │ GC                 │
        │ CISO               │ Board Risk Cmte    │
        │ Model Owner        │                    │
        │                    │                    │
    LOW │ MONITOR            │ KEEP SATISFIED     │
        └────────────────────┴────────────────────┘
```

**Quadrant notes:**

*High influence, high interest — manage closely.* The CAIRO,
CRO, Head of Underwriting, and AI Review Board are the
deciding coalition. Underwriting is here because of the
sales-and-service incentive issue named in the scenario:
underwriters who follow the recommendation close more loans,
which means Underwriting has both high influence over
deployment success and high interest in the model's
accuracy. The CRO is here because this is the first
deployment that materially tests the AI risk function under
the regulator's eye.

*High influence, low interest — keep satisfied.* The CTO,
GC, and Board Risk Committee. The CTO can block on
infrastructure grounds but does not care about the
deployment specifics. The GC cares about the consumer
notice but not the modeling approach. The Board Risk
Committee is high influence (formal authority) but low
*operational* interest — they want to see this go well and
not be surprised.

*Low influence, high interest — keep informed.* The Head of
Fair Lending, MRM Lead, and Vendor Risk Lead all have
deep substantive interest and clear formal authority over
their slice — but the *deployment* decision is not theirs.
Frequent, substantive updates are required to keep them
oriented and to surface any objection early.

*Low influence, low interest — monitor.* The CDO, CCO,
CISO, and the model owner. (The model owner is "low
influence" relative to the *deployment decision* — they
have very high influence over the model itself, of course,
but the go / no-go is not theirs to make. This is a place
where the framework's labels can be misleading; the note
matters.)

## 4. Reasoning notes

- **Why fair-lending gets the A on bias evaluation.** Three
  options exist: GC, CCO, or Head of Fair Lending. Fair
  Lending is the specific function with direct ECOA / Reg B
  expertise *and* the operational incentive to detect
  disparate-impact issues before they reach a regulator. GC
  is consulted but not accountable; the legal interpretation
  is a service function, not the program owner.
- **Why MRM is single-R-and-A on validation.** SR 11-7's
  central insight is that independent validation cannot be
  performed by the model owner. The model owner appears on
  the row for evaluation work (R), but the *validation*
  conclusion is MRM's and only MRM's.
- **Why the Board Risk Committee is C, not A, on go / no-go.**
  Operational deployment decisions belong inside the
  organization. The Board's role is oversight, not
  decision-making. If the deployment is material enough that
  the Board *should* be the A, then it should be
  re-classified upward (an "AI risk-tier 1 deployment") and
  routed differently — but for this case, AI Review Board
  is the right A.
- **What this RACI deliberately under-specifies.** The
  consumer-notice row could expand into 4–5 sub-activities
  (drafting, legal review, regulatory pre-clearance,
  customer-research user testing, post-launch monitoring).
  I compressed it to keep the matrix readable. A working
  program would explode this row.
- **The hardest restraint.** Limiting any row to ≤ 3 C's
  forces real choices. Several rows were tempted toward
  more (especially fair-lending evaluation). Choosing
  exactly the three that matter is the discipline.

---

Maintained by [Girish Nair](https://github.com/garynair)
