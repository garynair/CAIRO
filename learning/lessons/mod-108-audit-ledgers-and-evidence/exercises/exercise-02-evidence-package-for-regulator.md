# Exercise 02 — Author an Evidence Package for a Regulator Request

**Estimated time**: 4 hours
**Deliverable**: A complete evidence package
(≤ 4 pages)

---

## The scenario

You are the CAIRO at **Northfield Mutual** (continuity
from mod-101 / mod-103 / mod-105 / mod-107). The
state insurance regulator has issued a written
inquiry about Northfield's AI-assisted claims-
triage system. The relevant background: the v1
triage system was decommissioned after a bias
incident; the v2 rebuild has been operating for
9 months.

The regulator's letter requests:

> *Please provide evidence that Northfield Mutual's
> AI-assisted claims-triage system v2 has, over the
> trailing 6 months, (a) operated within its
> documented capability scope, (b) been subject to
> the demographic-stratified monitoring committed
> to in the May 2025 charter update, (c) not
> produced disparate-impact patterns affecting
> insureds aged 70 and above. Response is due
> within 30 days. Northfield should be prepared to
> defend the integrity of the evidence at follow-
> up examination.*

You have 30 days. The audit ledger has been
operating throughout the period (assume the
Exercise 03 design has been operational).

## Your assignment

Produce a complete evidence package responding to
the regulator. The package consists of multiple
sections that together form a single signed
document.

### Section 1 — Cover document (≤ ½ page)

State:

- The regulator's request (referenced by their
  letter ID).
- Northfield's response scope.
- The date of the package.
- The point of contact for follow-up.

### Section 2 — Scope statement (≤ ¼ page)

What is in scope of this package and what is not:

- The specific system covered.
- The time period.
- What aspects of the system's operation are
  attested.
- What is explicitly out of scope and why.

### Section 3 — Evidence for (a) — capability scope (≤ 1 page)

Demonstrate that the system operated within its
documented capability scope:

- Reference the capability manifest version that
  applied during the period.
- Show, for the period, the count and percentage
  of operations that were authorised within scope
  vs. denied as out-of-scope.
- Provide evidence-record references for a
  statistical sample (you may use illustrative
  placeholders for the actual record IDs).
- Include inclusion-proof placeholders.

### Section 4 — Evidence for (b) — demographic monitoring (≤ 1 page)

Demonstrate that demographic-stratified monitoring
was performed per the May 2025 charter:

- Reference the monitoring policy version.
- Show the monthly monitoring runs for the
  period (count and outcome).
- For any month showing a threshold crossing,
  reference the AI Review Board's response.
- Include inclusion-proof placeholders.

### Section 5 — Evidence for (c) — no disparate impact on age 70+ (≤ ¾ page)

Demonstrate that the system did not produce
disparate-impact patterns:

- The monitoring metric used (per mod-105 Ex-02
  pattern for clinical scoring adapted to
  insurance — equalized odds across age strata).
- Per-month subgroup performance data with
  explicit thresholds.
- Honest treatment of any threshold crossing
  (per §1 — evidence is not justification; if a
  threshold was crossed, the package shows the
  evidence and the response).
- Inclusion-proof placeholders.

### Section 6 — Supporting artifacts (≤ ¼ page)

References to:

- The system identity manifest.
- The relevant policy versions.
- The May 2025 charter update.
- The AI Review Board meeting minutes for the
  period.

### Section 7 — Chain of custody and signature (≤ ¼ page)

- Production history of the package.
- Verification protocol the regulator can follow.
- Package signature reference.
- Witness countersignature reference (per §2.3).

## Constraints

- The package must address **all three** elements
  of the regulator's request — (a), (b), (c).
- Honest treatment of evidence is required. If
  the monitoring showed any threshold crossing
  during the period, the package surfaces it and
  references the response. (For the exercise, you
  may invent realistic scenarios.)
- The verification protocol must be **specific**
  — what cryptographic operations the regulator
  performs to verify the package.
- Length: 4 pages hard limit. Packages over 4
  pages signal inability to scope evidence.
- The package must be **signable as a single
  artifact** — sections refer to each other but
  the whole package is one signed document.

## Rubric

| Criterion | Weight |
|---|---|
| Cover and scope — clear, bounded | 10% |
| Evidence for (a) — specific, with proof references | 20% |
| Evidence for (b) — specific, with proof references | 20% |
| Evidence for (c) — honest treatment of any threshold crossing | 25% |
| Supporting artifacts referenced | 10% |
| Verification protocol specified | 10% |
| Length discipline — ≤ 4 pages | 5% |

## Where to submit

`solutions/modules/mod-108-audit-ledgers-and-evidence/exercise-02-evidence-package-for-regulator/SOLUTION.md`

Reference solution includes one month where the
demographic threshold was crossed and the AI Review
Board responded with a documented site-level pause.
The reference treats this honestly rather than
hiding it — the discipline §1 named.

## Reading before you start

- Lecture notes §4 (evidence packages) — all of it.
- mod-102 §2.7 (EU AI Act Art. 73) and §4 (sector-
  specific) — for state-regulator context.
- mod-105 Ex-02 reference (bias metric design) —
  for the demographic-monitoring context.
- mod-107 Ex-04 reference (Northfield's incidents)
  — for the broader incident context.
