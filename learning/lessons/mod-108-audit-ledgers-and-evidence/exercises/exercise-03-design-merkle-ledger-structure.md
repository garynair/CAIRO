# Exercise 03 — Design a Merkle-Chained Ledger Structure

**Estimated time**: 3 hours
**Deliverable**: A ledger structure design + verification
protocol (≤ 3 pages)

---

## The scenario

You are advising **Tessera Bank's** CISO on the
ledger structure that will receive the events from
Exercise 01. Tessera has decided (in principle) to
build the policy and orchestration layer in-house
and to use a commercial vendor for the audit ledger
(per mod-106 Ex-05 pattern). The CISO wants to
**specify the structural requirements** before the
vendor selection process. The CAIRO's contribution:
the structural design the vendor must meet.

## Your assignment

Produce a structural design with:

### Section 1 — Structural requirements (≤ ¾ page)

State, with reasoning:

- **Append-only.** No mutation; subsequent
  modifications detectable.
- **Hash chain within batches** — events within a
  batch preserve order.
- **Merkle tree across batches** — efficient
  inclusion / consistency proofs.
- **External witness signatures** — multiple
  independent witnesses counter-sign root commits.
- **External timestamping** — RFC 3161 TSA
  countersigns root commits.
- **Public commitment publication** — the
  ledger's roots are periodically published in a
  way external parties can verify.
- **Sealing cadence** — daily or sub-daily.
- **Retention** — at least 7 years (sufficient for
  Tessera's banking regulatory obligations) with
  technical capability for longer if required.

For each requirement, name the **specific concern**
it addresses and the **specific failure mode** it
defends against.

### Section 2 — The data model (≤ ¾ page)

Define:

- **Record format.** What fields each leaf has;
  how the leaf hash is computed.
- **Batch format.** Sequence of records; batch
  hash chain; batch-level metadata.
- **Tree structure.** How batches are organized
  into the Merkle tree.
- **Inclusion proof format.** What the proof
  contains.
- **Consistency proof format.** What proves that
  tree state at T2 is a strict extension of T1.
- **Seal format.** What a sealed commitment
  contains.

Diagram-style notation is fine (Markdown is
acceptable).

### Section 3 — The verification protocol (≤ ¾ page)

The protocol an external verifier follows to
confirm the integrity of an evidence record:

1. **Verify the seal signature** — confirm the
   seal containing the record's batch was signed
   by the ledger and witnesses.
2. **Verify the inclusion proof** — confirm the
   record's hash is in the batch and the batch
   is in the tree under the sealed root.
3. **Verify consistency** — confirm the sealed
   root at the time of evidence production is
   consistent with the current published root.
4. **Verify the timestamp** — confirm the RFC 3161
   TSA timestamp.
5. **Verify the record's signature** — if the
   record itself is signed (by the emitter),
   verify that signature.

For each step, specify the cryptographic
operations and the failure-mode response.

### Section 4 — The vendor requirements (≤ ¼ page)

Translate the structural design into vendor-
contract requirements:

- The vendor must conform to RFC 9162 (or a
  documented equivalent).
- The vendor must produce inclusion and
  consistency proofs in standards-conformant
  formats.
- The vendor must support external timestamping
  per RFC 3161.
- The vendor must support multiple-witness
  countersignatures (number of witnesses
  configurable; minimum 2 for Tessera).
- The vendor must support full ledger export in
  a documented format for migration.

### Section 5 — Open questions for the vendor evaluation (≤ ¼ page)

Three to five questions the vendor evaluation
should answer before commitment:

- How does the vendor handle key rotation?
- How does the vendor handle witness compromise?
- What is the vendor's published ledger
  publication mechanism?
- How does the vendor handle deletion / GDPR
  right-to-erasure requests (per the GDPR
  legitimate-purpose carve-out for evidence)?

## Constraints

- The design must be **standards-conformant** to
  RFC 9162 and RFC 3161.
- The design must not include **specific products**.
  This is a vendor-agnostic structural design.
- Each structural requirement must be **justified**
  by a specific concern.
- The verification protocol must be **executable**
  — a vendor or external party could follow it
  step-by-step.
- The data-model section must include **explicit
  hash and signature semantics** — not "records are
  hashed" but "the leaf hash is SHA-256 of the
  canonicalised JSON serialisation of the
  record."

## Rubric

| Criterion | Weight |
|---|---|
| Structural requirements — comprehensive + justified | 25% |
| Data model — specific, executable | 25% |
| Verification protocol — executable | 25% |
| Vendor requirements — translatable to contract | 15% |
| Open questions for evaluation | 10% |

## Where to submit

`solutions/modules/mod-108-audit-ledgers-and-evidence/exercise-03-design-merkle-ledger-structure/SOLUTION.md`

Reference solution requires 2-witness countersign
for Tessera (one internal compliance, one external
attestation provider); daily sealing cadence;
SHA-256 + ES256.

## Reading before you start

- Lecture notes §2 (the tamper-evident ledger
  pattern) — all of it.
- RFC 9162 — at least §4 (Verification) and §5
  (Algorithm Agility).
- RFC 3161 — §2 (Time-Stamp Token).
- mod-106 §6 (build vs buy) — the framework
  applies here too.
