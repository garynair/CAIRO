# Exercise 01 — Map Trust Boundaries — Reference Solution

## 1. Solution overview

For **Tessera's** agentic customer-service agent, the
reference maps **8 trust boundaries**. The two highest-
blast-radius operations are the funds-transfer (real
money moves; irretrievable consequence) and the
profile-update (address change can enable fraud).
Funds-transfer is named higher by margin. The dynamic-
identity discussion centers on the LLM vendor-model
identity layer (Vendor X foundation model versions)
and the configuration identity layer (Tessera-side
system prompt + tool list).

---

## 2. Artifact 1 — Trust-boundary diagram

```
                            CUSTOMER
                               │
                               │  TLS + customer auth (web/mobile)
                               │  ─────────── BOUNDARY 1 ───────────
                               ▼
              ┌──────────────────────────────────┐
              │   Tessera customer chat surface  │
              │   (web + mobile clients)         │
              └──────────────────────────────────┘
                               │
                               │  TLS + signed session token (Tessera-side mTLS)
                               │  ─────────── BOUNDARY 2 ───────────
                               ▼
              ┌──────────────────────────────────┐
              │   Tessera agent orchestrator     │
              │   (in-house service; routes      │
              │    operations to tools)          │
              └──────────────────────────────────┘
                  │                       │
                  │ mTLS + JWT            │ mTLS + JWT to vendor X
                  │ Tessera-internal      │
                  │ ──── BOUNDARY 3 ─-    │ ──── BOUNDARY 4 ────
                  │                       │
                  ▼                       ▼
       ┌────────────────────┐   ┌────────────────────────────┐
       │  Tessera tool      │   │ Vendor X LLM inference     │
       │  services          │   │ (foundation model + system │
       │                    │   │  prompt)                   │
       └────────────────────┘   └────────────────────────────┘
        │       │       │       │
        │  ──── BOUNDARY 5 ────  (mTLS + capability manifest at each tool call)
        │       │       │
        ▼       ▼       ▼
    ┌─────┐ ┌─────┐ ┌─────────┐
    │ACCT │ │DSPT │ │TRANSFER │ ──── BOUNDARY 6 (catastrophic — internal step-up)
    │READ │ │API  │ │  API    │
    └─────┘ └─────┘ └─────────┘
        │       │       │
        │  ──── BOUNDARY 7 ──── (Bank's core systems trust boundary)
        ▼       ▼       ▼
    ┌────────────────────────────────────┐
    │  Core banking systems              │
    │  (ledger, customer master, etc.)   │
    └────────────────────────────────────┘
                  │
                  │  ──── BOUNDARY 8 ──── (Audit / event ledger boundary)
                  ▼
    ┌────────────────────────────────────┐
    │  Tessera audit ledger              │
    │  (per mod-108)                     │
    └────────────────────────────────────┘
```

### Per-boundary attributes

| # | Crossing party | Method | Blast radius if bypassed |
|---|---|---|---|
| 1 | Customer ↔ chat surface | TLS + customer auth (OIDC + MFA for sensitive sessions) | Account takeover; full customer-facing exposure |
| 2 | Chat surface ↔ orchestrator | TLS + Tessera-side signed session token | Session hijack to authorised agent capabilities |
| 3 | Orchestrator ↔ Tessera tools | mTLS + JWT (with capability scope per operation) | Unauthorised tool invocation on behalf of customer |
| 4 | Orchestrator ↔ Vendor X LLM | mTLS + JWT (Vendor-X-issued client credential) | Information disclosure to Vendor X beyond contracted scope |
| 5 | Per-tool capability check | Signed capability manifest verified at tool API entry | Per-tool unauthorised invocation; same blast radius as Boundary 3 but per-tool granularity |
| 6 | Transfer API trust gate | Step-up: fresh re-attestation + customer-side step-up (push notification confirmation) | Unauthorised funds movement up to $5,000 / day; **highest blast radius** |
| 7 | Tool APIs ↔ core banking | mTLS + bank-internal API gateway (existing infrastructure) | Core systems exposure; bank-wide impact |
| 8 | Per-operation audit-event signing | Operations write signed events to the audit ledger | Lost forensic trail; not directly bypassing operation but loss of evidence |

## 3. Artifact 2 — Accompanying memo

### Composable-question analysis (two boundaries)

**Boundary 3 (orchestrator → Tessera tools):**

- **Identity:** The orchestrator presents a JWT signed
  by Tessera's identity service, naming (agent
  service principal, customer-on-whose-behalf,
  session ID). Verified at each tool's API entry via
  JWKS lookup.
- **Capability:** The JWT carries a capability scope
  field listing the operations authorised for this
  session — e.g., `["read:accounts:{customer_id}",
  "send:messages:{customer_id}",
  "transfer:funds:{customer_id}:up_to_5000"]`. Tools
  reject operations not in scope.
- **Context:** The orchestrator includes (a) session
  age, (b) the customer's authentication tier (was
  MFA used?), (c) the operation classification. Tools
  apply runtime policy based on context.

**Boundary 6 (transfer API trust gate):**

- **Identity:** Same composite identity as Boundary 3,
  but with a **freshness requirement**: the
  attestation must have been issued within the last
  5 minutes. Stale attestations fail.
- **Capability:** Specific transfer authorisation
  scoped to the source and destination accounts and
  the amount. The capability is *not* extendable —
  one authorisation produces one transfer.
- **Context:** Customer-side step-up — a push
  notification to the customer's registered device
  must be confirmed before the transfer authorises.
  This is the §5.5 step-up pattern applied to the
  highest-blast-radius operation.

### Highest-blast-radius operations

**Funds-transfer** is the highest. Reasoning:

- The action is *irretrievable*: once money has
  moved, recovery requires customer cooperation, the
  receiving account, and potentially legal process.
- The action is *materially adverse*: $5,000 per
  transfer × 3 per day = $15,000 / day potential
  loss per customer.
- The action is *fraudster-attractive*: agent-mediated
  transfer is precisely the operation a sophisticated
  adversary would target with prompt injection.

**Profile-update** is the second-highest. Reasoning:

- Address change is the standard precursor to
  account-takeover fraud (intercept new cards,
  intercept account communications).
- The change is *retroactively detectable* but
  damage is downstream — by the time profile-change
  is discovered, fraud has already moved.

The dispute operation, although customer-visible, has
*lower* blast radius because (a) Tessera's dispute
process includes human review at the resolution
stage, and (b) initiated disputes are reversible
through the same human review.

### Dynamic-identity problem

The agent's composite identity has three time-varying
components:

1. **Vendor X foundation model identity.** Vendor X
   may swap the underlying foundation model with
   30-day notice (per the contract). The boundary
   design must capture model version in the agent's
   identity claim and re-attest after material model
   change.
2. **Tessera-side configuration identity.** The
   agent's system prompt + tool list is versioned;
   changes to the system prompt produce a different
   *configuration identity*. The boundary design
   must verify the configuration hash at each
   operation against the deployed reference.
3. **Customer-on-whose-behalf.** Each session has a
   different customer principal; identity composition
   includes the customer at session-establishment
   time.

The boundary design handles these by composing the
identity claim at session-establishment and re-
attesting on material change events (model swap,
configuration change, customer re-authentication).

### Trust-boundary failure scenario for the CISO

**Scenario:** Vendor X swaps the foundation model
without the 30-day notice (contract violation; rare
but possible). The orchestrator continues using the
agent's session-established identity, which now
points to a model identity that does not exist —
verification fails silently or succeeds against a
stale attestation.

**Why this matters:** If verification fails *silently*
(the gate allows the operation despite the failure),
the agent is now authorising operations under an
identity that no longer maps to its actual runtime.
If the swap changes behaviour, the program's posture
collapses without warning.

**What I want the CISO to address:** the model-
identity verification must *fail closed* and emit a
high-priority alert when the model identity claim
does not match the runtime model. This requires
either contractual or technical model-version
attestation from Vendor X at each inference call.

---

## 4. Reasoning notes

- **Why 8 boundaries and not 6 or 12.** The reference
  enumerates the *distinct* trust crossings.
  Combining boundaries 3 and 5 would lose the
  per-tool granularity that allows capability scope
  to be enforced at the tool level. Splitting
  boundary 7 into multiple per-tool internal
  boundaries would be over-decomposition for a
  CAIRO-level analysis.
- **Why funds-transfer is named higher than profile-
  update.** Both are high; the funds-transfer has
  greater immediate financial irretrievability.
  Reasonable people might rank them equally; the
  reference takes a position to demonstrate the
  exercise.
- **Why the dynamic-identity discussion goes long.**
  This is the §2.2 adaptation point — the place
  where NIST 800-207 was not designed for agentic
  AI. A CAIRO who can articulate this specifically is
  doing the job §1.4 named.
- **What the trust-boundary diagram does not show.**
  The mod-105 fairness boundary (the bias-monitoring
  layer at the model-output stage) and the
  mod-104 model-quality validation boundary
  (MRM-side). These are governance-of-the-agent
  boundaries rather than runtime-trust boundaries;
  including them would conflate the two senses of
  trust (§1.1). They are legitimate concerns; they
  belong on a different diagram.
- **The CISO failure scenario I almost picked
  instead.** Customer device compromise — the
  customer's phone is compromised and a step-up push
  notification is approved by an attacker rather
  than the customer. This is a real risk and is
  arguably more frequent than the Vendor X swap
  scenario. I selected the Vendor X scenario because
  it surfaces the *dynamic identity* problem the
  module is specifically about; customer device
  compromise is the CISO's existing concern and
  doesn't require trust-architecture-specific
  insight.

---

Maintained by [Girish Nair](https://github.com/garynair)
