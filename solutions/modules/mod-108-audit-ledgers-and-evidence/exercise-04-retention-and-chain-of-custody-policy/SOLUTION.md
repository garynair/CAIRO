# Exercise 04 — Retention and Chain-of-Custody Policy — Reference Solution

## 1. Solution overview

A 3-page policy for **Halverston Capital** covering
retention per LOB with specific regulatory citations,
chain of custody across all four phases, daily sealing
with 2 internal + 1 external witness, and explicit
GDPR-vs-retention reconciliation via the legitimate-
purpose carve-out for compliance evidence.

---

## 2. The policy

> **HALVERSTON CAPITAL — EVIDENCE RETENTION AND
> CHAIN-OF-CUSTODY POLICY v1.0**
> *Owned by Chief AI Risk Officer with General Counsel
> and Chief Risk Officer concurrence. Approved by
> Audit Committee 2026-06-15. Reviewed annually.*

### 1. Scope and definitions

**In scope:** AI program audit-ledger events
(per the Exercise 01 vocabulary pattern); evidence
packages produced for external audiences;
supporting artifacts referenced by evidence
(manifests, policy documents, AI Review Board
minutes); chain-of-custody records.

**Out of scope:** Ephemeral operational logging
(application logs, network telemetry, cache
behaviour); non-AI-program governance documents
(those follow Halverston's general records-
management policy).

**Definitions:**

- **Epoch:** A defined time period within which
  evidence is sealed together. Halverston uses
  daily epochs (00:00–23:59 UTC).
- **Seal:** A signed commitment to the contents of
  an epoch, countersigned by witnesses, timestamped
  by an external TSA.
- **Chain of custody:** The documented history of
  who handled an evidence artifact between its
  emission and the moment of audience receipt.
- **Retention duration:** The minimum time
  Halverston commits to preserving evidence in a
  retrievable, integrity-verifiable state.

### 2. Retention durations

#### 2.1 Per-LOB retention table

| LOB / Category | Retention | Source of obligation |
|---|---|---|
| **Public markets — trading-related AI events** | 7 years | SEC 17 CFR 240.17a-4 + FINRA 4511 (broker-dealer records) |
| Public markets — non-trading AI evidence | 7 years (aligned with above for operational consistency) | Internal policy |
| **Private credit — credit-decisioning AI events** | 7 years | SR 11-7 + Reg B (12 CFR 1002.12) credit-decisioning record retention |
| Private credit — underwriting workbench evidence | 7 years | Same |
| **Wealth advisory — advisor-facing AI events** | 7 years from date of advisor's separation or 7 years from creation, whichever is later | SEC Investment Advisers Act 17 CFR 275.204-2 + FINRA 4511 |
| **Cross-LOB — board reporting evidence** | 10 years | Halverston Board Governance Policy + Audit Committee Charter |
| **Cross-LOB — regulator-response evidence packages** | 7 years from regulator inquiry close; longer if litigation hold | Internal policy + general litigation-readiness |
| **Cross-LOB — AI Risk Council and AI Review Board minutes** | 10 years | Internal policy + ISO 42001 Annex A control alignment |
| **Cross-LOB — incident classification and response records** | 10 years | EU AI Act Art. 12 (high-risk system logs) + sector-specific incident retention |

#### 2.2 Maximum retention

Halverston commits to **not retaining beyond**:

- 10 years for any AI-program evidence (cross-LOB
  baseline), unless extended by litigation hold or
  regulatory directive.
- Beyond the period required by the relevant
  retention authority where personal data is
  involved — to reduce GDPR / state privacy law
  exposure.

#### 2.3 End-of-retention posture

At end of retention:

- **Cryptographic erasure** of personal-data
  components (such that the inclusion proof
  remains valid but the personal data is
  irrecoverable).
- **Ledger structure preservation** — the event
  records' positions in the ledger, their
  cryptographic commitments, and the inclusion
  proofs remain intact.
- **Disposal certificate** — Halverston produces a
  signed disposal certificate stating what was
  cryptographically erased and when.

This pattern preserves the integrity of the audit
trail (the records existed; the program operated
as documented) while honouring the deletion
obligation.

### 3. Chain of custody

#### 3.1 Production

Evidence is *produced* by Halverston's evidence-
production service. Production is triggered by:

- A specific external request (regulator,
  auditor, customer, litigant).
- A scheduled production (e.g., quarterly
  attestation per §4.4 of mod-108).
- A specific internal request (CAIRO investigation,
  AI Review Board case file).

Each production request is itself recorded in the
audit ledger as a `production.requested` event,
including the requester (named role at
Halverston), the scope, the authorisation, and the
expected delivery.

Authorisation for production:

- *External-audience packages:* CAIRO function +
  General Counsel concurrence.
- *Internal-audience packages:* AI Risk Lead (or
  delegate).
- *Litigation-discovery packages:* General Counsel
  + outside-counsel coordination.

#### 3.2 Internal handling

Evidence packages move within Halverston only
through controlled channels:

- **Halverston Evidence Portal** — the
  internal-only repository for evidence packages
  awaiting external delivery. Access is
  role-controlled and audit-logged.
- **Sealed delivery containers** — physical
  delivery for printed evidence (rare; used only
  when a regulator requires hard-copy).

Internal email distribution of evidence packages
is **prohibited**. Forwarding an evidence package
via email breaks its chain of custody (per §5.4 of
the lecture notes); the package's signature
becomes meaningless to the recipient and the
package must be re-produced.

Internal copies for review:

- Reviewers (AI Risk Council members, internal
  audit) access packages through the Evidence
  Portal with audit-logged access.
- Reviewers do not download local copies;
  reviews are performed in the Portal.

#### 3.3 External handling

External transmission:

- **For US regulators:** transmission via the
  regulator's preferred secure portal where
  available (e.g., SEC EDGAR for SEC matters,
  FINRA EFT for FINRA matters), otherwise via
  controlled-transfer with PGP-encrypted SFTP
  and receipt acknowledgment.
- **For EU AI Act authority:** transmission per
  the authority's published mechanism; PGP-
  encrypted email with receipt acknowledgment
  acceptable.
- **For auditors (ISO 42001, SOC 2, internal):**
  transmission via the Halverston Auditor Portal
  with read-only access during the audit window.
- **For customers and customers' counsel:**
  PGP-encrypted email to the requester's
  documented address; receipt acknowledged
  before evidence consideration begins.
- **For litigation:** through external counsel,
  per litigation-hold and discovery protocols.

Each transmission produces a `package.transmitted`
event in the audit ledger, recording the
recipient, channel, timestamp, and receipt
acknowledgment reference.

#### 3.4 Post-delivery

After delivery:

- Halverston retains a sealed copy of the
  delivered package (for re-issue if requested,
  for litigation-readiness, for the disposal
  certificate at end of retention).
- Halverston tracks **whether the recipient
  acknowledged receipt** and whether the
  recipient requested re-issue or modification.
- Halverston does **not** track the recipient's
  internal handling of the package after delivery
  — that is the recipient's responsibility.

#### 3.5 Records of custody

Halverston retains, for each evidence package:

- The production request and authorisation.
- The package itself (signed and sealed).
- The transmission event records.
- The receipt acknowledgments.
- Any subsequent inquiry references (regulator
  follow-up, auditor questions, litigation
  references).

These custody records are themselves evidence and
subject to the same retention obligations as the
underlying evidence packages.

### 4. Sealing operations

**Sealing cadence:** Daily, at 23:59 UTC, the
ledger operator produces a seal commitment for the
day's epoch.

**Witness arrangement:**

- **Internal witness 1:** Halverston's Compliance
  Audit team signing service.
- **Internal witness 2:** Halverston's Internal
  Audit signing service (independent of
  Compliance).
- **External witness:** A contracted external
  attestation provider (engaged independently of
  the audit-ledger vendor).

Each witness's signature is over the day's seal
payload and is itself timestamped via RFC 3161 TSA.

**Seal publication:**

- Daily seals are published to Halverston's
  transparency endpoint at
  `https://transparency.halverston.com/.well-known/sct-log/`.
- External monitors (including the contracted
  attestation provider) verify publication
  consistency.

**Seal failure response:**

- If sealing fails on any day, the event is
  classified as a Category 1 security incident
  per the mod-107 Ex-04 taxonomy (1.a
  Infrastructure compromise).
- The CISO IR response is triggered immediately;
  the CAIRO function is notified within 15 minutes.
- Operations continue but with elevated
  monitoring; the failed seal is re-attempted
  with detailed investigation logs.
- A seal-failure event is recorded in the next
  successful seal's batch.

### 5. Litigation hold and exception handling

#### 5.1 Litigation hold

Litigation hold is invoked by General Counsel and
extends retention indefinitely for the affected
evidence categories. The hold is itself recorded
in the audit ledger as a `litigation_hold.invoked`
event. Release of the hold is similarly recorded.

#### 5.2 GDPR-vs-retention exception handling

The GDPR right-to-erasure (Art. 17) is exercised
by data subjects on personal data Halverston
holds. Evidence containing personal data of those
data subjects creates a tension between GDPR
obligation and retention obligation.

Halverston relies on the **legitimate-purpose
carve-out** for compliance evidence (GDPR Art.
17(3)(b) — compliance with legal obligations
requiring processing). The carve-out is invoked
when:

- The evidence is retained per a specific
  regulatory retention obligation (cited in §2.1).
- The retention period has not expired.
- The evidence cannot be reproduced if erased.

Where the carve-out is invoked, the data subject
is informed of the basis. Where the carve-out
does not apply (e.g., evidence held only under
internal policy and beyond regulatory minimum),
the personal data is cryptographically erased
per §2.3.

**Exception authorisation:** GDPR-vs-retention
exception decisions are made by Halverston's Data
Protection Officer in consultation with General
Counsel; the decision is recorded as an event in
the audit ledger.

— end policy —

---

## 3. Reasoning notes

- **Why 7-year baseline and not 5.** Several of
  Halverston's regulatory obligations require 5
  or 6 years; the additional 1–2 years gives
  margin for litigation-readiness without
  requiring exceptional cases for ordinary
  retention. The cost difference between 5 and
  7 years is small at the audit-ledger scale.
- **Why 2 internal + 1 external witness, not 3
  external.** Internal witnesses are operationally
  available; their compromise requires
  Halverston-internal collusion (or systemic
  failure). External witnesses are more
  expensive and create vendor-dependency
  concerns of their own. 1 external is the right
  balance for Halverston's scale and risk
  profile.
- **Why daily sealing and not hourly.** Per the
  Exercise 03 reasoning notes — daily matches
  audit cadence; sub-daily increases overhead
  disproportionately to the benefit. Some
  programs at higher-frequency-trading scale
  might justify sub-daily; Halverston does not.
- **Why I prohibited internal email of evidence
  packages.** §5.4 — email breaks the chain.
  The Evidence Portal pattern preserves the
  chain at the cost of slight operational
  friction. Reviewers initially resist the
  friction; the resistance fades when the first
  audit asks for chain-of-custody records.
- **Why I addressed GDPR explicitly.** Many CAIRO
  programs hand-wave this. The legitimate-
  purpose carve-out is real but not unlimited.
  Naming the boundaries in the policy means
  Halverston can defend the position before a
  data-protection authority's inquiry; programs
  that hand-wave end up making the same
  argument under deadline pressure.
- **What this policy deliberately under-
  specifies.** The specific JWKS endpoints and
  transparency-endpoint URLs; the specific
  Evidence Portal access roles; the specific TSA
  vendor. These are operational details that
  evolve faster than the policy should.
- **What I would do differently in v2.** Add a
  *retention review cadence* — the policy is
  reviewed annually, but specific retention
  durations may need quarterly review if
  regulatory landscape shifts. A v2 would
  formalize the quarterly review for retention
  durations specifically.

---

Maintained by [Girish Nair](https://github.com/garynair)
