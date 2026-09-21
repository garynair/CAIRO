# Module 108 — Lecture Notes

About 100 minutes of reading. §2 (the Merkle / hash-chain
pattern) is the technically densest section; §4 (evidence
packages) is the most operationally consequential.

---

## §1. What evidence is for

Evidence in the audit / regulatory sense is *not* the
same as operational logging. Both record what
happened. They differ in three properties:

1. **Provenance.** Evidence has cryptographically
   verifiable provenance — the record was emitted by
   the system claimed to have emitted it, at the time
   claimed. Operational logs typically lack this.
2. **Completeness.** Evidence is complete with respect
   to a defined scope — for every operation that
   matters, an evidence record exists. Operational
   logs are often best-effort.
3. **Tamper resistance.** Evidence is structured so
   that subsequent modification is detectable. Most
   operational logs are not.

A CAIRO program that uses production logs as evidence
will eventually be embarrassed by a regulator review
that discovers the logs were rotated, modified, or
incomplete.

### 1.1 Why evidence matters operationally

The CAIRO function produces or curates evidence for
three audiences:

- **Regulators.** EU AI Act Art. 12 requires
  automatic logging for high-risk systems with
  log retention obligations. NYDFS Part 500 §500.06
  requires cybersecurity audit trails. State
  insurance regulators require records of AI
  decisions. The CFPB requires evidence underlying
  adverse-action notices. Each has different
  expectations.
- **Auditors** (internal and external). Internal
  audit's posture (mod-101 §3 — third line of
  defence) requires verifiable evidence that the
  program operated as documented. External
  auditors (SOC 2, ISO 27001, ISO 42001 once
  certification is pursued) have specific evidence
  requirements.
- **The Board.** Quarterly board reporting (per
  mod-103 §6.3) is rounded up from evidence;
  programs that cannot trace their reports to
  evidence have no recourse when questioned.

### 1.2 What "good evidence" looks like

A working test: if the system that produced the
evidence were replaced tomorrow with a hostile
replacement that wanted to lie about history, would
the existing evidence be tampered-with-detectably?

If yes, the evidence is good. If no, it is
operational logging.

### 1.3 What evidence is not

Honest distinctions:

- **Evidence is not the same as audit.** Audit is
  the *activity* of evaluating evidence; evidence
  is the *artifact*. A program can have good
  evidence and bad audit (audit-team capability
  problems) or vice versa.
- **Evidence is not justification.** Evidence
  records what happened; it does not justify why.
  Justification lives elsewhere (in policy
  documents, in decision memos, in incident
  reports). The evidence layer references those
  artifacts but does not substitute for them.
- **Evidence is not the model.** Models are
  artifacts of computation; evidence is artifacts
  of provenance. They are different concerns;
  programs that conflate them produce poorly-
  structured both.
- **Evidence is not infrastructure.** The audit
  ledger is infrastructure; the discipline of
  generating, signing, retaining, and producing
  evidence on demand is the program work. Many
  programs buy ledger infrastructure and stop
  there — the discipline does not exist without
  organisational practice.

### 1.4 Why this discipline matters for the CAIRO

The CAIRO program lives or dies by its evidence layer
in regulator engagement. Programs that can produce
on-demand evidence pass regulator reviews; programs
that cannot do not. mod-101 §6 named *governance
theatre* as a failure mode; programs without
evidence are particularly vulnerable to it — the
theatre is only theatre because it cannot be backed
by evidence when challenged.

---

## §2. The tamper-evident ledger pattern

The cryptographic technique that makes evidence
trustworthy at scale is the **tamper-evident
ledger**: a data structure where the integrity of
any single record can be efficiently verified
against a small public commitment, and subsequent
modifications are detectable.

The pattern has decades of cryptographic theory
behind it. The practical implementations relevant
in 2026 are based on **Merkle trees** and **hash
chains**.

### 2.1 The Merkle tree

A Merkle tree is a tree of hashes where each leaf
is the hash of a data record, and each internal
node is the hash of its children's hashes. The
root hash commits to every leaf — change any leaf
and the root changes.

```
                   root_hash
                  /          \
              h(h1+h2)    h(h3+h4)
              /    \      /    \
            h1    h2    h3    h4
            |     |     |     |
          rec1  rec2  rec3  rec4
```

Two properties that matter operationally:

- **Inclusion proofs are small.** To prove that a
  specific record is in the tree, you provide
  log₂(n) hashes (the *audit path*). For 1 billion
  records, an inclusion proof is 30 hashes.
- **Consistency proofs are small.** To prove that a
  later tree is a strict extension of an earlier
  tree (no history rewriting), the proof size is
  log₂(n) hashes.

Both properties make Merkle trees the right
structure for evidence: external verifiers can check
inclusion or consistency without needing the full
ledger.

### 2.2 Hash chains

A hash chain is a simpler structure: each record
includes the hash of the previous record. Change
any record and every subsequent record's chain
links break.

```
rec1: { data: ..., prev_hash: 0 } → h1
rec2: { data: ..., prev_hash: h1 } → h2
rec3: { data: ..., prev_hash: h2 } → h3
...
```

Compared to Merkle trees:

- **Sequential structure** — operations append at
  the end; ordering is preserved.
- **Larger consistency proofs** — verifying that
  record N is unchanged requires walking back N
  records (or N/k for an indexed hash chain).
- **Simpler implementation** — no tree balancing,
  no path arithmetic.

Most working audit ledgers use *both*: hash chains
within batches (preserving operation order); Merkle
trees across batches (efficient external
verification).

### 2.3 RFC 9162 and Certificate Transparency

The technical reference for production tamper-
evident ledgers in 2026 is **RFC 9162 — Certificate
Transparency Version 2.0**. CT has run since 2013
at internet scale, logging every TLS certificate
issued; the structural patterns transfer cleanly to
AI audit.

Key concepts:

- **Append-only log.** Records can only be added;
  modification of existing records is detectable
  and treated as compromise.
- **Public commitments.** The log periodically
  publishes its root hash (signed) to a public
  channel.
- **Witness signatures.** Multiple independent
  witnesses observe the log's commitments and
  countersign; tampering requires compromising
  the log AND multiple witnesses.
- **Monitors.** External parties continuously
  watch for inconsistencies and disclose them.

AI audit ledgers using RFC 9162 patterns get
considerable assurance from the architecture alone.

### 2.4 What the pattern does not do

The Merkle / RFC 9162 pattern provides **integrity
and inclusion** assurance. It does not provide:

- **Confidentiality.** Anyone with access to the
  ledger sees what's in it.
- **Authenticity of records.** The pattern
  guarantees a record was in the log; it does not
  guarantee the record reflects reality. A
  compromised emitter can write false records that
  the ledger faithfully preserves.
- **Right interpretation.** Evidence records
  enable analysis; they do not guarantee the
  analysis is correct.

Programs that treat "we have a Merkle ledger" as
sufficient evidence assurance are confusing the
infrastructure with the discipline.

### 2.5 Practitioner patterns

A range of implementations:

- **VeriSwarm Vault** — Merkle-chained ledger with
  hash-chain ordering; signed exports; one
  practitioner pattern.
- **Sigstore Rekor** — open-source, Merkle-based
  transparency log designed for software supply
  chain; adaptable to AI events.
- **OpenZeppelin / Eth-based ledgers** — blockchain
  evidence at higher latency and cost; relevant
  for some regulated contexts where public
  verifiability is paramount.
- **AWS CloudTrail with integrity validation** —
  hyperscaler-managed; less flexible but
  operationally familiar.
- **Roll-your-own** with RFC 9162 + standard
  cryptographic libraries — full control,
  highest maintenance cost.

Exercise 03 designs a ledger structure; the
reference uses a Merkle + hash chain hybrid based
on RFC 9162 patterns.

---

## §3. Event vocabulary

The integrity layer (§2) is necessary but not
sufficient. The events you put *in* the ledger
must be the right events. Programs with sound
Merkle structures and impoverished event
vocabularies fail audits because they cannot
answer the questions the auditor asks.

### 3.1 The granularity problem

Two failure modes at opposite ends:

- **Under-granular.** Events are aggregated; one
  event records "agent operated successfully" for
  a hundred operations. The auditor cannot trace
  individual decisions.
- **Over-granular.** Events are emitted for every
  function call, every cache hit, every internal
  message. The ledger overflows, query performance
  degrades, and the auditor cannot find what
  matters because everything is in the way.

The right granularity for CAIRO evidence is **at the
level of operations that have program-relevant
consequences** — one event per agent action that
affects principals, resources, or external state.

A working test: would the program want to
reconstruct *this* operation at year+3 if the
program were challenged? If yes, emit; if no,
operational logging is sufficient.

### 3.2 The completeness problem

A working event vocabulary covers:

- **Authorisation events.** Per-operation decisions
  by trust gates (per mod-106 §5.2 — the gate's
  decision and reasoning).
- **Capability assertions.** Manifest issuance,
  revocation, and verification events.
- **Tool invocations.** Per-tool calls by agents,
  with input and output references (the references
  themselves are stored separately; the event
  records what was called and what the result
  was).
- **Model interactions.** Calls to underlying
  models (which model version, configuration, the
  input/output references).
- **State changes.** Material changes to data the
  agent reads from or writes to.
- **Configuration changes.** Changes to agent
  system prompts, tool lists, capability scopes.
- **Incident-relevant events.** Detections by
  monitoring (drift, anomalies, threshold
  crossings) — even when no immediate action is
  required.

A program where any of these is missing has
incomplete evidence.

### 3.3 What goes in an event

Each event should include, at minimum:

| Field | Why |
|---|---|
| Event ID | Unique identifier within the ledger |
| Event type | Vocabulary classification |
| Timestamp | When the event occurred (system clock); ideally also TSA timestamp |
| Actor | The agent / service / user that produced the event |
| Subject | The entity the event concerns |
| Operation | The specific action |
| Result | Success / failure / deferral |
| Reason / context | Sufficient context to interpret the event later |
| References | Pointers to related larger artifacts (model identity, configuration hash, etc.) |
| Signing key reference | The key used to sign the event |
| Prior event hash | For the hash chain |

The reference-rather-than-include pattern matters:
events should be small; large artifacts (model
weights, full input data, full output data) live
in object storage and are referenced by hash from
the events.

### 3.4 The vocabulary registry

A working program maintains a **vocabulary
registry**: the catalog of event types the program
recognises, with definitions, expected fields, and
emission rules. The registry is itself versioned
and recorded (changes to the vocabulary are
themselves events).

Without a registry:

- New systems emit events using novel field names
  that the analysis layer doesn't recognise.
- Event types proliferate over time; auditors
  cannot tell which types are equivalent.
- Vocabulary drift creates analysis gaps that
  surface only at audit time.

A registry is part of the CAIRO function's standards
work (mod-105 §6.1 — ethics in standards), even
though the standard itself is technical.

### 3.5 Practitioner patterns

The current event-vocabulary landscape:

- **OpenTelemetry GenAI semantic conventions** —
  the closest to community consensus for LLM and
  agent event types; still evolving.
- **VeriSwarm 22-event vocabulary** — a working
  practitioner pattern with explicit event types
  for agent trust scoring (covered in mod-106
  §4.5).
- **CloudEvents 1.0** — generic event envelope;
  used as a base by several AI-specific
  vocabularies.
- **Roll-your-own** with project-specific event
  types.

No standard has settled in 2026. The CAIRO's
position: pick a *baseline* (OpenTelemetry GenAI or
a practitioner reference) and extend with program-
specific events as needed; document the extensions
in the vocabulary registry.

---

## §4. Evidence packages

The operational artifact the CAIRO function produces
when a specific audience asks for evidence is the
**evidence package**. It is a curated, signed,
self-contained collection of evidence that answers
a specific question.

### 4.1 Why packages, not raw ledger access

Three reasons to package rather than grant access:

1. **Scope.** Auditors and regulators ask specific
   questions. Raw access produces noise; packages
   produce signal.
2. **Confidentiality.** The ledger may contain
   information the audience is not entitled to.
   Packages can be curated to the audience's
   appropriate scope.
3. **Verifiability.** Packages are signed and
   timestamped at production. The audience
   receives an artifact with provenance, not a
   query result that may have changed.

### 4.2 What goes in a package

A complete evidence package includes:

- **Cover document** — what question this package
  answers, who requested it, when it was
  produced.
- **Scope statement** — what is in scope and what
  is not.
- **Evidence records** — the relevant events from
  the ledger.
- **Inclusion proofs** — cryptographic proofs that
  each evidence record is in the ledger.
- **Consistency proof** — a proof that the ledger
  state at package production is consistent with
  prior signed ledger states.
- **Supporting artifacts** — model identity
  attestations, manifest snapshots, configuration
  references that the evidence records reference.
- **Chain of custody** — the production and
  handling history of the package itself.
- **Package signature** — cryptographic signature
  by the program over the entire package.

### 4.3 Common evidence-package use cases

Typical CAIRO evidence package types:

| Use case | Audience | Typical scope |
|---|---|---|
| Regulator inquiry response | EU AI Act authority, OCC, FDA, etc. | Specific operations or time period named by the regulator |
| Customer adverse-action explanation | Customer (or customer's counsel) | The specific decision affecting the customer |
| Internal audit sampling | Internal audit | Statistical sample of operations |
| Insurance claim (cyber, professional liability) | Insurance carrier | Operations relevant to the claim |
| Litigation discovery | Counsel + opposing party | Court-defined scope |
| Board quarterly | Board Risk Committee | Aggregate program metrics, exception cases |

Each has different completeness, confidentiality,
and format requirements.

### 4.4 Pre-built vs. ad-hoc packages

The most common evidence packages should be **pre-
designed templates**, not assembled from scratch
each time. Programs that assemble each package ad
hoc spend regulatory-deadline time on package
construction; programs with templates spend the
same time on review.

Standard template categories:

- **Regulator quarterly attestations** — pre-
  built; updated continuously; signed monthly.
- **Adverse-action explanation packages** — pre-
  built; produced automatically per adverse
  decision.
- **Annual SOC 2 / ISO 42001 evidence sets** —
  pre-built per the audit framework.
- **EU AI Act Art. 12 logging compliance
  evidence** — pre-built; produced on demand.

Ad-hoc construction is for unusual inquiries that
do not fit a template.

### 4.5 The verification protocol

A working evidence package includes the **steps
the audience must take to verify it**:

1. Verify the package's outer signature.
2. Verify each evidence record's inclusion proof
   against the ledger's commitments.
3. Verify the ledger consistency proof against
   prior signed ledger states.
4. Verify the timestamps on supporting attestations.
5. Verify the chain of custody (the package was
   handled appropriately between production and
   receipt).

The protocol is documented in the package itself,
in plain language. Audiences who do not perform the
verification have the option; programs that do not
document the protocol are signalling that the
verification is not expected.

---

## §5. Retention, sealing, chain of custody

A working evidence layer is not just the ledger
infrastructure; it is also the organisational
practice around the ledger. Three disciplines:
retention, sealing, chain of custody.

### 5.1 Retention

Retention is *how long* evidence must be kept.
Sources of retention obligation include:

- **Regulatory.** EU AI Act Art. 12 requires
  high-risk-system logs for 6 months minimum (and
  longer if other EU law specifies). SR 11-7
  expectations for banking models are typically
  longer. State insurance regulations vary.
- **Litigation hold.** Active or reasonably-
  anticipated litigation may require retention
  beyond regulatory minimum.
- **Internal policy.** Programs may choose longer
  retention to support program lessons-learned and
  trend analysis.

A working retention policy combines all three with
explicit reasoning. Retention is *not* "keep
forever" — keeping more than needed is itself a
risk (privacy, breach exposure).

Notable retention durations as of 2026:

| Source | Typical retention |
|---|---|
| EU AI Act Art. 12 | 6 months minimum; longer if other EU law applies |
| GDPR (where evidence contains personal data) | "no longer than necessary" — typically 5–7 years for financial-services-AI evidence |
| US banking SR 11-7-related | 5–7 years typical |
| FDA SaMD | Throughout system's useful life + 2 years |
| State insurance | Varies; typically 5–10 years |

### 5.2 Sealing

Sealing is the practice of *finalising* an
evidence epoch — committing to the contents of a
specific time period in a way that subsequent
modifications would be detectable.

The pattern that works: at the end of each defined
epoch (typically daily), the program produces a
**sealed commitment** — a signed statement of the
Merkle root at that moment, countersigned by
witnesses, with an external timestamp authority
(RFC 3161). The seal is itself appended to the
ledger as an event.

Sealing has several operational benefits:

- **Independent verification.** The seal can be
  published to a public channel; external parties
  can confirm the program's commitments.
- **Tampering detection at the seal boundary.**
  Even sophisticated ledger compromise becomes
  detectable when the seal is checked.
- **Audit reference.** When the auditor asks
  "what was the ledger state at date D?", the
  seal at D is the answer.

### 5.3 Chain of custody

Chain of custody is the documented history of who
handled the evidence between its emission and the
moment it reaches the audience. The discipline is
particularly important for litigation evidence; in
regulatory contexts, it provides assurance that
the program produced the evidence rather than
fabricated it.

A working chain of custody records:

- The system that emitted the evidence.
- The signing key used.
- Any intermediate handling (export, transfer,
  copy).
- The recipients and the timestamps.
- The final delivery.

Each transfer should be signed by both the
transferor and the recipient; the chain becomes
itself an audit-able record.

### 5.4 What can go wrong

Common chain-of-custody failures:

- **Email transmission of evidence.** Email is
  not a controlled channel; chain of custody
  breaks. Evidence should be transmitted through
  controlled channels (a documented portal, a
  signed secure transfer).
- **Internal email forwarding.** The original
  evidence package is signed; once it is copied
  into email body content, the signature is
  meaningless. The package as an attached file
  preserves the chain.
- **Casual handling of leftover copies.**
  Recipients of evidence make copies; chain of
  custody ends at the official recipient; what
  happens after is the recipient's responsibility.

---

## §6. Build, buy, or partner

The CAIRO contributes to the audit-ledger build /
buy / partner decision using the same framework as
mod-106 §6.

### 6.1 Build

The organisation engineers its own audit-ledger
infrastructure using cryptographic standards
(RFC 9162, RFC 3161, JWS) and in-house
implementation.

- *Strengths:* Maximum control; no vendor
  dependency; architecture matches the
  organisation's specific needs; intellectual
  property is the firm's.
- *Weaknesses:* Substantial engineering investment;
  cryptographic expertise required; the integrity
  guarantees depend on the implementation's
  correctness.
- *Best for:* Organisations with strong
  cryptographic engineering capacity or contexts
  where vendor dependency on evidence
  infrastructure is itself a risk.

### 6.2 Buy

The organisation licences a commercial audit-
ledger product (VeriSwarm Vault, Sigstore Rekor as
managed service, AWS CloudTrail with integrity
validation, IBM watsonx.governance audit
features, or sector-specific vendors).

- *Strengths:* Fast deployment; vendor support;
  architecture is battle-tested with other
  customers; vendor handles cryptographic
  correctness.
- *Weaknesses:* Vendor lock-in (particularly
  acute for evidence infrastructure — moving
  ledger contents is materially harder than moving
  most other infrastructure); product roadmap may
  diverge from organisation needs.
- *Best for:* Organisations without specialised
  cryptographic engineering capacity; contexts
  where speed matters; standardised compliance
  use cases.

### 6.3 Partner

Common partner patterns:

- **Buy the ledger, build the event vocabulary
  and analysis.** The cryptographic guarantees
  come from the vendor; the program controls
  what goes in and what comes out.
- **Buy the ledger and the analysis, build the
  evidence-package assembly.** Vendor provides
  evidence-handling primitives; program
  authors the audience-specific packages.
- **Buy from one vendor for in-scope-of-vendor
  systems; build for systems outside that scope.**
  Heterogeneous infrastructure.

### 6.4 The migration risk

The most insidious risk in buying audit-ledger
infrastructure is **migration risk** — the cost
of moving from one vendor to another is materially
higher than for most infrastructure. Evidence has
long retention requirements; moving years of
sealed evidence with preserved integrity properties
is a multi-quarter project at minimum.

Mitigations:

- **Standards-based export formats.** The vendor
  must produce evidence in standards-conformant
  formats (CloudEvents, RFC 9162-style commitments,
  RFC 3161 timestamps) so re-import into another
  system is technically feasible.
- **Documented migration playbook** — even if no
  migration is planned, the playbook ensures the
  organisation knows what migration would
  require.
- **Periodic export verification** — periodically
  produce a full export and verify it independently;
  this exercises the export pathway and surfaces
  problems before they matter.

### 6.5 The CAIRO contribution

As in mod-106 §6.5, the CAIRO contributes:

- The *requirements* — what evidence the
  infrastructure must produce, what audiences it
  must serve, what regulatory obligations it must
  satisfy.
- The *risk assessment* — vendor dependency,
  migration risk, integrity-assumption analysis.
- The *program-level position* — how the chosen
  architecture is described in the program
  charter, in board reports, and to regulators.

The choice itself is engineering and security led,
with CAIRO input.

Exercise 05 asks you to author the CAIRO's
contribution to a build / buy / partner decision
for a specific organisation.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **RFC 9162 — Certificate Transparency Version
   2.0.** The structural reference for tamper-
   evident ledgers.
2. **EU AI Act Art. 12.** The record-keeping
   obligation for high-risk systems.
3. **RFC 3161 — Time-Stamp Protocol.** The
   external-timestamp authority pattern §5.2
   relies on.
