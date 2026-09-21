# Exercise 05 — Build / Buy Decision for the Audit Ledger

**Estimated time**: 3 hours
**Deliverable**: A decision matrix + recommendation
memo (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Halverston Capital**
(continuity from Exercise 04). The decision: the
audit-ledger infrastructure to support the
program. Per the partner pattern from mod-106
Ex-05, Halverston is buying components rather
than building them all. The audit ledger is one
candidate to buy.

The CTO and CISO have presented three options:

- **Build** in-house using RFC 9162 + RFC 3161 +
  standard cryptographic libraries. Estimated
  12–18 months to production; ~$3M initial
  engineering + $1.5M annual maintenance;
  requires 3–4 specialised cryptographic engineers.
- **Buy** from a commercial vendor. Shortlist:
  Sigstore Rekor (as managed service via a third
  party) and one hyperscaler-managed option. Estimated 4–6
  months to production; $0.8–1.5M annual
  licensing + $0.3M integration.
- **Partner.** Buy the cryptographic ledger
  components; build the event-emission and
  evidence-package assembly layers in-house.
  Estimated 6–9 months; $0.8M annual licensing
  + $1M built engineering + $0.5M annual
  maintenance.

You have been asked to **author the CAIRO's
recommendation** to the CTO + CISO + CRO.

## Your assignment

Produce two artifacts.

### Artifact 1 — Decision matrix (≤ 1 page)

A matrix comparing the three options on at least
nine dimensions:

- Time-to-deploy
- 5-year total cost
- Annual operating cost
- Vendor dependency
- Migration risk (the §6.4 concern)
- Standards conformance (RFC 9162, RFC 3161)
- Customisation for Halverston event vocabulary
- Regulator defensibility
- Engineering / talent posture

For each cell, give a specific value or
characterisation.

### Artifact 2 — Recommendation memo (≤ 2 pages)

A memo to the CTO, CISO, and CRO containing:

1. **Recommendation** in the first sentence.
2. **Reasoning** organised around the dimensions
   that determined the choice.
3. **What is given up** by the choice.
4. **CAIRO-program-specific contribution** per §6.5.
5. **Migration-risk analysis and mitigation**
   per §6.4.
6. **Acknowledged uncertainties** with management
   plans.

## Constraints

- The recommendation must be one of the three —
  not "depends" or "evaluate further".
- Migration risk must be addressed substantively.
  This is the most insidious risk per §6.4 and
  must not be glossed.
- The reasoning must address Halverston's **multi-
  LOB** structure — public markets, private
  credit, and wealth advisory have different
  event volumes and different regulator
  expectations.
- The reasoning must address **retention
  duration**. Halverston has 7+ year retention
  obligations; the chosen architecture must
  support this without operational distress.
- The recommendation must cite **specific
  standards** (RFC 9162, RFC 3161) the
  architecture conforms to.

## Rubric

| Criterion | Weight |
|---|---|
| Matrix — at least nine dimensions, specific values | 25% |
| Recommendation — clear, defensible | 15% |
| Reasoning — addresses multi-LOB + retention | 25% |
| What is given up — substantive | 10% |
| CAIRO contribution — substantive per §6.5 | 10% |
| Migration risk — addressed with mitigation | 15% |

## Where to submit

`solutions/modules/mod-108-audit-ledgers-and-evidence/exercise-05-build-vs-buy-audit-ledger/SOLUTION.md`

Reference solution recommends **partner** for
Halverston. The reasoning: buy the ledger
cryptographic primitives (which is a well-bounded
component where vendor expertise adds value);
build the Halverston-specific event vocabulary
emission and the evidence-package assembly
(which are program-specific). Migration risk is
addressed via standards-conformant export
requirements and a documented migration playbook.

## Reading before you start

- Lecture notes §6 (build, buy, partner).
- Exercise 03 reference (the structural design
  the vendor must conform to).
- mod-106 Ex-05 reference (the partner pattern at
  the broader trust architecture level).
