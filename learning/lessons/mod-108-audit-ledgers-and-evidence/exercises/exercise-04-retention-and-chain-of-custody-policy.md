# Exercise 04 — Author Retention and Chain-of-Custody Policy

**Estimated time**: 3 hours
**Deliverable**: A policy document (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Halverston Capital**
(continuity from mod-103 / mod-105 / mod-106 /
mod-107). Halverston's AI program is approaching
ISO 42001 certification. The certification auditor
has asked to review Halverston's evidence
retention and chain-of-custody policy. You have
not formally documented it.

The CRO has asked you to author the policy this
week.

## Your assignment

Produce a policy document with the following
structure.

### Section 1 — Scope and definitions (≤ ¼ page)

- Scope: which evidence categories the policy
  covers (audit-ledger events, evidence packages
  produced for external audiences, supporting
  artifacts referenced by evidence).
- Out of scope: ephemeral operational logging.
- Key definitions (epoch, seal, chain of custody,
  retention duration).

### Section 2 — Retention durations (≤ 1 page)

For each evidence category at Halverston, specify:

- **Retention duration** — minimum and maximum.
- **Source of obligation** — regulatory (citing
  specific authorities), litigation hold,
  internal policy.
- **Sealing posture** — what happens at the end of
  the retention period (deletion, archival to
  cold storage, etc.).

Halverston's three LOBs have different obligations.
Address each:

- **Public markets** — SEC retention requirements
  for trading-related records.
- **Private credit** — SR 11-7 + state lending
  regulation retention.
- **Wealth advisory** — SEC (Advisers Act) +
  FINRA retention.

Plus cross-LOB:

- **Board reporting evidence**.
- **Regulator-response evidence packages**.

### Section 3 — Chain of custody (≤ 1 page)

The discipline for handling evidence:

- **Production** — how evidence is generated from
  the ledger; who can request production; what
  approvals are required.
- **Internal handling** — how evidence packages
  move within Halverston; controlled-channel
  requirements; copy-control discipline.
- **External handling** — how evidence is
  transmitted to regulators, auditors, customers,
  litigants; transmission channels; receipt
  acknowledgment.
- **Post-delivery** — how Halverston tracks the
  evidence after delivery (for re-use, for
  destruction, for re-issue).
- **Records of custody** — what custody records
  Halverston itself retains.

### Section 4 — Sealing operations (≤ ½ page)

- **Sealing cadence** — when seals are produced.
- **Witness arrangement** — who countersigns;
  internal vs external witnesses.
- **Seal publication** — how seals become
  externally verifiable.
- **Seal failure response** — what happens if
  sealing fails on a given day.

### Section 5 — Litigation hold and exception handling (≤ ¼ page)

- How litigation hold is invoked.
- How litigation hold extends retention.
- How exceptions (e.g., GDPR right-to-erasure
  conflicting with retention) are handled.
- Who approves exceptions.

## Constraints

- The policy must be **operationally executable**
  — a Halverston employee should be able to read
  the policy and know what to do.
- Retention durations must cite **specific
  regulatory authority** for each obligation.
- Chain of custody must address **all four**
  custody phases (production, internal, external,
  post-delivery).
- Exception handling must include the **GDPR vs
  retention** tension explicitly. The legitimate-
  purpose carve-out for evidence is one of the
  ways this is resolved; document it.
- The policy must be **3 pages**. ISO 42001
  auditors prefer short policies that get
  followed over long policies that get ignored.

## Rubric

| Criterion | Weight |
|---|---|
| Scope and definitions — clear | 10% |
| Retention durations — specific, regulator-cited | 25% |
| Chain of custody — all four phases | 25% |
| Sealing operations — specific cadence + witnesses | 15% |
| Litigation hold and exception handling | 15% |
| Length discipline — ≤ 3 pages | 10% |

## Where to submit

`solutions/modules/mod-108-audit-ledgers-and-evidence/exercise-04-retention-and-chain-of-custody-policy/SOLUTION.md`

Reference solution treats Halverston's three LOBs
with explicit obligation tables; uses daily
sealing with 2 internal + 1 external witnesses;
addresses the GDPR-vs-retention tension via the
legitimate-purpose carve-out for compliance
evidence.

## Reading before you start

- Lecture notes §5 (retention, sealing, chain of
  custody) — all of it.
- mod-102 (regulatory landscape) for the specific
  sources of retention obligation.
- ISO 42001 — at minimum the auditor expectation
  language.
