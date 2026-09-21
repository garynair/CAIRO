# Exercise 03 — Design Merkle-Chained Ledger Structure — Reference Solution

## 1. Solution overview

A structural design for **Tessera's audit ledger**
conforming to RFC 9162 + RFC 3161 with **hash chain
within daily batches** and **Merkle tree across
batches**. Sealing is daily with **2-witness
countersign** (one Tessera-internal compliance, one
external attestation provider). Designed to be
vendor-agnostic: any vendor meeting the structural
requirements can be plugged in.

---

## 2. The structural design

### Section 1 — Structural requirements

| Requirement | Concern | Failure mode defended against |
|---|---|---|
| Append-only | Modification of historical records would lie about past program behaviour | Tampering after the fact (e.g., retroactively "correcting" a bad decision) |
| Hash chain within batches | Within a day's events, the order matters (e.g., a manifest must be issued before its events) | Reordering attacks |
| Merkle tree across batches | Efficient inclusion + consistency proofs at scale | Need for verifiable proofs without full-ledger transfer |
| External witness signatures (2 minimum) | Ledger operator alone could fabricate consistency | Single-party compromise of the ledger operator |
| RFC 3161 external timestamping | Ledger operator alone could backdate seals | Time-manipulation attacks |
| Public commitment publication | Without public commitments, external parties cannot detect inconsistencies | Silent rewriting between sealed states |
| Daily sealing | Sealing interval limits the "tampering window" | Long-window tampering before sealed state |
| 7-year retention with technical capability for longer | Tessera's banking regulatory obligations | Insufficient retention violating regulator expectations |

### Section 2 — The data model

**Record format (a single leaf):**

```
record = {
  event: <serialized event JSON per Exercise 01>
  emitter_signature: ES256 over canonical event JSON
  leaf_metadata: {
    record_index: u64 (monotonic within batch)
    batch_id: u64
    record_timestamp: RFC 3339
  }
}

leaf_hash = SHA-256(
  canonical_serialize(record)
)
```

The leaf's hash is included in the Merkle tree;
the record's full content remains in the ledger
storage layer.

**Batch format (one batch per day):**

```
batch = {
  batch_id: u64
  date: ISO 8601 date (UTC)
  prior_batch_hash: SHA-256 of previous batch's hash (hash chain across batches)
  record_count: u64
  records: ordered sequence of records
  merkle_root_of_batch: Merkle root over leaf hashes (in record-index order)
}

batch_hash = SHA-256(
  canonical_serialize(
    { batch_id, date, prior_batch_hash, record_count, merkle_root_of_batch }
  )
)
```

The batch hash chains to the previous batch
(preserving cross-day order) and includes the
Merkle root (allowing per-batch inclusion proofs).

**Tree structure (across batches):**

```
tree_at_time_T = {
  global_merkle_root: Merkle root over all batch_hashes (in batch_id order) through T
  batch_count: u64
  last_sealed_batch_id: u64
}
```

The global Merkle root commits to every batch and,
through the per-batch trees, every record.

**Inclusion proof format:**

```
inclusion_proof = {
  record_index: u64
  batch_id: u64
  in_batch_proof: [hash, ...]  # Merkle path from leaf to batch's root
  in_global_proof: [hash, ...]  # Merkle path from batch's hash to global root
  reference_root: hash  # the global root the proof verifies against
  reference_root_signature: signature over reference_root
}
```

Verification: combine the proofs walking the path
from leaf hash up to the reference global root; the
signature confirms which root the proof corresponds
to.

**Consistency proof format:**

```
consistency_proof = {
  from_root: hash
  to_root: hash
  proof_hashes: [hash, ...]
}
```

The proof is constructed per RFC 9162 §2.1.2.
Verification confirms that the to_root represents
a strict extension of the from_root.

**Seal format:**

```
seal = {
  seal_id: UUID
  global_root_committed: hash
  last_batch_id: u64
  seal_timestamp: RFC 3339 + RFC 3161 timestamp
  ledger_operator_signature: signature
  witness_signatures: [
    { witness_id, signature, timestamp },
    ...  # minimum 2 witnesses
  ]
}
```

The seal is itself appended to the ledger as a
special event type and recorded in the next batch.

### Section 3 — The verification protocol

For an external verifier confirming an evidence
record's integrity:

1. **Verify the seal signature.**
   - Inputs: the seal containing the global root
     committed when the evidence was produced.
   - Operations: verify ledger operator's
     signature against the published JWKS;
     verify each witness signature against the
     witness's published key; verify all signatures
     cover the same payload.
   - Failure response: seal verification failure
     means the package is not trustworthy; do not
     proceed.
2. **Verify the inclusion proof.**
   - Inputs: the record, the in_batch_proof, the
     in_global_proof, the seal's global_root_committed.
   - Operations: compute the leaf hash from the
     record; combine with in_batch_proof hashes to
     compute the batch's Merkle root; combine
     batch hash with in_global_proof hashes to
     compute the global root; compare to
     seal's committed root.
   - Failure response: mismatch means either the
     record was modified or the proof is
     fabricated. Either way, do not trust.
3. **Verify consistency.**
   - Inputs: the seal's committed root (at time of
     evidence production) and the current published
     global root.
   - Operations: verify a consistency proof from
     the committed root to the current root per
     RFC 9162 §2.1.2.
   - Failure response: inconsistency means the
     ledger was rewritten between the two states.
4. **Verify the timestamp.**
   - Inputs: the RFC 3161 timestamp on the seal.
   - Operations: verify the timestamp authority's
     signature against published TSA public keys;
     confirm the timestamp falls within the
     ledger's claimed sealing window.
   - Failure response: timestamp verification
     failure means the seal's claimed time is not
     externally attested.
5. **Verify the record's emitter signature.**
   - Inputs: the record's emitter_signature.
   - Operations: verify against the emitter's
     published key.
   - Failure response: emitter signature failure
     means the record may not have been emitted by
     the named system.

### Section 4 — The vendor requirements

The audit-ledger vendor must:

- Conform to RFC 9162 v2 for log structure,
  inclusion proofs, and consistency proofs.
- Support RFC 3161 external timestamping with
  configurable TSA endpoints.
- Support **at least 2 witness countersignatures**
  per seal, with configurable witness identities.
- Produce inclusion and consistency proofs in
  standards-conformant binary or JSON formats
  (RFC 9162-defined).
- Support **full ledger export** in a documented
  format that another RFC-9162-conformant
  implementation could import.
- Publish **JWKS endpoints** for the ledger
  operator's signing keys and for witness keys.
- Maintain **at least 7 years** retention with
  technical capability for extension to 10 years
  without operational distress.
- Support **GDPR-compatible exception handling**
  (per the legitimate-purpose carve-out for
  compliance evidence — Exercise 04 covers).

### Section 5 — Open questions for vendor evaluation

1. **How does the vendor handle key rotation?**
   Specifically: signing key rotation cadence;
   witness key rotation handshake; consistency
   guarantees across rotations.
2. **How does the vendor handle witness
   compromise?** Specifically: revocation
   mechanisms; how a witness that lost its key
   gets replaced; how prior seals signed by the
   compromised witness remain valid (or are
   re-witnessed).
3. **What is the vendor's published-commitment
   mechanism?** Specifically: where are roots
   published; how often; what's the SLA on
   publication; can Tessera observe alternative
   roots?
4. **How does the vendor handle the GDPR
   right-to-erasure conflict with retention?**
   Specifically: cryptographic erasure of
   personal data leaving the audit trail intact;
   indexing structures that allow targeted
   deletion without breaking inclusion proofs.
5. **What's the vendor's roadmap for OpenTelemetry
   GenAI semantic conventions support?** As the
   community settles vocabulary, the ledger
   should support query and analysis on the
   convention's structure.

---

## 3. Reasoning notes

- **Why the hash chain + Merkle tree hybrid.** Pure
  hash chain has linear consistency-proof cost;
  pure Merkle tree loses within-batch order. The
  hybrid preserves both — order within batches
  via the chain; efficient proofs across batches
  via the tree. RFC 9162 uses this pattern.
- **Why 2 witnesses minimum.** Single-witness
  patterns require trusting both the operator and
  the single witness. 2 witnesses with independent
  compromise requirements raises the bar
  meaningfully. More than 2 has diminishing
  returns and substantial operational cost (each
  witness adds latency to the sealing pipeline).
- **Why daily sealing.** Sub-daily sealing
  increases overhead (each seal is a witness-
  signed event); longer-than-daily creates
  unacceptably long tampering windows. Daily is
  the common practitioner pattern and matches
  the audit cadence most regulators expect.
- **Why I separated the ledger operator's
  signing key from the emitter's signing keys.**
  Different security postures, different
  rotation cadences. The emitter signs the
  record at production; the ledger operator signs
  the inclusion proof at verification time;
  these are different concerns with different
  key-management requirements.
- **What this design deliberately under-
  specifies.** The exact cryptographic algorithm
  (the design uses SHA-256 + ES256 as defaults
  with documented rationale; the vendor may
  propose alternatives if standards-conformant).
  Specific storage architecture. Specific
  indexing for query performance.
- **What I would do differently in v2.** Add
  *batch sub-trees* — within a single daily
  batch, organize records into per-emitter sub-
  trees so inclusion proofs for an emitter's
  events don't carry hashes from other emitters'
  events. This would reduce proof size for
  per-system audits at the cost of more complex
  batch structure. The reference omits for
  simplicity but a production system at
  Tessera's scale should consider it.

---

Maintained by [Girish Nair](https://github.com/garynair)
