# Exercise 02 — Design a Notification Matrix

**Estimated time**: 3 hours
**Deliverable**: Notification matrix (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank**. The CCO (per
mod-109 Ex-05 split-authorship resolution) and you
have agreed that the CAIRO function will author the
AI-specific notification matrix. The matrix
operationalizes who gets notified, when, by whom,
for each incident classification per the mod-107
Ex-04 taxonomy.

## Your assignment

Produce a matrix covering:

### Section 1 — Scope and use (≤ ¼ page)

- Which incidents the matrix covers (AI-program
  + joint per mod-107 §6).
- Who maintains the matrix.
- How to consult it during an incident.

### Section 2 — The matrix proper (≤ 2 pages)

For each of the **9 incident sub-categories** from
mod-107 Ex-04 (security 1.a-d, AI-program 2.a-d,
joint 3.a-d — the matrix uses sub-categories
because notification triggers differ within
top-level categories), provide a row per
applicable notification:

| Sub-category | Notification trigger | Recipient | Timeline | Led by | Format | Approvals required |
|---|---|---|---|---|---|---|
| 2.a Bias incident | EU-resident insured / customer affected with discriminatory pattern | EU AI Act NCA | 2 days from incident determination | CAIRO | Per EU AI Act Annex IX | CAIRO + CCO + GC |
| 2.a Bias incident | Any US state-supervised customer affected | State insurance / banking regulator | Per state (typically 72h) | CCO + CAIRO | Per state | CCO + CAIRO |
| ... | ... | ... | ... | ... | ... | ... |

Cover at minimum:

- EU AI Act Art. 73 (all relevant sub-categories).
- NYDFS Part 500 §500.17 (security sub-categories).
- GDPR Art. 33 (where personal data affected).
- GDPR Art. 34 (data subject notification).
- Sector-specific (SR 11-7 model events; state
  banking + insurance regulators).
- Contractual customer notification (per Tessera's
  largest customer-contract notification clauses).
- Internal: Board, Audit Committee, AI Risk
  Council.

### Section 3 — Edge cases (≤ ½ page)

Three edge cases the matrix explicitly addresses:

- **Multi-jurisdiction.** Customer affected is
  both EU-resident and US — which notifications
  apply.
- **Vendor-side incident.** Vendor LLM provider
  has the incident; how Tessera's notifications
  apply (or don't).
- **Discovery during examination.** Regulator
  discovers an incident during their examination
  before Tessera independently detected; what
  the notification posture is.

### Section 4 — Maintenance (≤ ¼ page)

How the matrix stays current:

- Review cadence.
- Trigger events (regulation change, new
  jurisdiction, new sub-category).
- Approval for changes.
- Version control + audit-ledger insertion.

## Constraints

- All 9 sub-categories must be covered.
- All cells must be **specific** — no "as
  appropriate" or "per applicable regulation".
- Timelines must cite the specific authority
  (Art. 73; §500.17; etc.).
- At least one cell must show a *no-notification-
  required* determination with reasoning (some
  sub-categories don't require external
  notification under most circumstances).

## Rubric

| Criterion | Weight |
|---|---|
| Coverage — all 9 sub-categories | 25% |
| Cell specificity — no "as appropriate" | 25% |
| Authority citations | 15% |
| Edge cases addressed substantively | 20% |
| Maintenance cadence | 10% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`solutions/modules/mod-110-incident-response/exercise-02-design-notification-matrix/SOLUTION.md`

Reference solution covers ~25 notification
obligations across the 9 sub-categories.

## Reading before you start

- Lecture notes §4 (notification matrix).
- mod-107 §6 + Ex-04 (the classification taxonomy
  this matrix operates against).
- mod-102 §2.7 (Art. 73), §4 (sector regulations).
