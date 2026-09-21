# Exercise 03 — Author an Agent Identity + Capability Manifest — Reference Solution

## 1. Solution overview

For **Tessera Bank**, the reference recommends **roll-
your-own with W3C VC + JWT**. The decision is grounded
in Tessera's existing identity infrastructure (a
production OIDC stack), the customisation needed for
banking-specific capability vocabulary, and the
vendor-capture concern. The defence is honest about
maintenance burden and cryptographic-expertise
requirements.

---

## 2. Artifact 1 — Manifest format specification

### Pattern chosen — and why

**W3C Verifiable Credentials Data Model 2.0 + JWT-VC
serialisation, signed with ES256.**

Defence: Tessera already operates a production OIDC
identity stack with signing keys, JWKS endpoints, and
key rotation policy. Building the agent manifest
layer on top of this infrastructure leverages
existing cryptographic operations expertise. The
banking-specific capability vocabulary (e.g.,
`transfer:funds:{customer}:up_to_5000`) requires
custom claims that commercial offerings would either
accommodate inflexibly or charge for. Vendor capture
is a stated CAIRO concern; building keeps Tessera in
control of the trust anchor.

Honest limitations of this choice: Tessera takes on
the maintenance burden, the cryptographic-expertise
requirement, and the responsibility for revocation
infrastructure. The 5-FTE engineering investment
projected by the CTO is real.

Alternative paths considered:

- *Anthropic agent attestation pattern.* Signed
  attestations of model identity and configuration;
  would be fast to deploy. Rejected because
  (a) Tessera's banking-specific capability
  vocabulary would require custom extensions the
  pattern doesn't natively support, (b) vendor
  lock-in on the trust-anchor layer is a high
  concentration risk.
- *Cloudflare AI Gateway.* Gateway-mediated identity
  is operationally attractive but makes Cloudflare
  the trust authority. Rejected for the same
  vendor-concentration reason.

### Required fields

| Field | Type | Format | Purpose |
|---|---|---|---|
| `@context` | array | W3C VC standard | Identifies the credential as VC; includes Tessera-specific extension URI |
| `type` | array | W3C VC | `["VerifiableCredential", "AgentCapabilityCredential"]` |
| `issuer` | string | DID or HTTPS URI | Tessera's identity service issuer DID |
| `validFrom` | datetime | RFC 3339 | Start of validity |
| `validUntil` | datetime | RFC 3339 | End of validity (≤ 1 hour from issuance) |
| `credentialSubject.id` | string | Composite agent ID | Identifier for the agent instance (model + config + session) |
| `credentialSubject.modelIdentity` | object | `{vendor, modelName, modelVersion}` | The LLM identity |
| `credentialSubject.configIdentity` | object | `{promptVersionHash, toolListHash}` | Tessera-side configuration identity |
| `credentialSubject.principal` | object | `{type, id, authMethod, authTime}` | The customer or service principal on whose behalf |
| `credentialSubject.capabilities` | array | List of capability objects | What the agent is permitted to do |
| `credentialSubject.delegationChain` | array (optional) | Chain of intermediate authorities | If applicable |
| `audience` | string | Trust gate URI | Which gate(s) accept this manifest |
| `jti` | string | UUID | Unique credential identifier |

Capability object structure:

| Sub-field | Type | Purpose |
|---|---|---|
| `action` | string | The action class (read / send / dispute_initiate / transfer / profile_update) |
| `resource` | string | The resource scope (e.g., `customer_account:{customer_id}`) |
| `constraints` | object | Action-specific constraints (e.g., `{maxAmountPerOp: 5000, maxPerDay: 3}`) |
| `delegationDepth` | integer | How many further delegations are permitted (typically 0 for agent operations) |

### Optional fields

| Field | Purpose |
|---|---|
| `credentialSubject.evidence` | Additional evidence attestations (e.g., MFA result reference) |
| `credentialSubject.posture` | Snapshot of the agent's posture at issuance (configuration hash, deployment environment) |
| `revocationListIndex` | Position in Tessera's revocation list for fast lookup |

### Signing mechanism

- **Algorithm:** ES256 (ECDSA with P-256 + SHA-256).
- **Key management:** Tessera's existing KMS holds
  signing keys. Keys are rotated quarterly. The
  current and previous signing keys are both
  published via JWKS.
- **Serialisation:** JWT-VC per W3C VC-JWT
  specification.

### Verification protocol

1. Parse JWT-VC; extract header and payload.
2. Resolve issuer's JWKS endpoint; fetch keys.
3. Verify signature against current and (up to one
   rotation back) previous keys.
4. Verify `validFrom <= now <= validUntil`.
5. Verify `audience` matches this gate's identifier.
6. Verify revocation status via revocation list
   (with cache up to 30 seconds for performance).
7. Walk delegation chain (if present), verifying each
   hop's signature and validity.
8. Look up the requested operation in `capabilities`;
   verify match.
9. If all pass, ALLOW + emit signed audit event.

### Revocation handling

- Tessera maintains a revocation list at
  `https://identity.tessera.bank/.well-known/jwks-revocation.json`
  with revoked credential `jti` values.
- The trust gate caches the list for up to 30
  seconds.
- Catastrophic operations (per the 4-axis decision
  logic) require a fresh (uncached) revocation
  check.
- Revocation list is signed and timestamped.

---

## 3. Artifact 2 — Worked example

```json
{
  "@context": [
    "https://www.w3.org/ns/credentials/v2",
    "https://tessera.bank/credentials/agent-capability/v1"
  ],
  "type": ["VerifiableCredential", "AgentCapabilityCredential"],
  "issuer": "did:web:identity.tessera.bank",
  "validFrom": "2026-06-01T18:00:00Z",
  "validUntil": "2026-06-01T19:00:00Z",
  "jti": "urn:uuid:9c8e2d1a-7b3f-4d6c-9a5f-2e8b7c1d4a9e",
  "audience": "https://gate.tessera.bank/trust-gate",
  "credentialSubject": {
    "id": "agent:tessera:customer-service-v2:session:abc123",
    "modelIdentity": {
      "vendor": "VendorX",
      "modelName": "X-Pro",
      "modelVersion": "2026.02"
    },
    "configIdentity": {
      "promptVersionHash": "sha256:e3b0c44298fc1c149a...",
      "toolListHash": "sha256:9f86d081884c7d659a..."
    },
    "principal": {
      "type": "customer",
      "id": "customer:tessera:7f9e2d4a-3b1c-4f6e-8c5a-2e8b7c1d4a9e",
      "authMethod": "mfa+webauthn",
      "authTime": "2026-06-01T17:55:12Z"
    },
    "capabilities": [
      {
        "action": "read",
        "resource": "customer_account:7f9e2d4a-...",
        "constraints": {},
        "delegationDepth": 0
      },
      {
        "action": "send_message",
        "resource": "customer:7f9e2d4a-...",
        "constraints": {"channelOnly": "chat_response"},
        "delegationDepth": 0
      },
      {
        "action": "dispute_initiate",
        "resource": "customer_account:7f9e2d4a-...",
        "constraints": {"maxPerDay": 1},
        "delegationDepth": 0
      },
      {
        "action": "transfer",
        "resource": "customer_owned_accounts:7f9e2d4a-...",
        "constraints": {
          "maxAmountPerOp": 5000,
          "maxPerDay": 3,
          "betweenCustomerOwnedAccountsOnly": true
        },
        "delegationDepth": 0
      },
      {
        "action": "profile_update",
        "resource": "customer:7f9e2d4a-...",
        "constraints": {
          "allowedFields": ["address", "contact_preferences"],
          "stepUpRequired": true
        },
        "delegationDepth": 0
      }
    ]
  }
}
```

Signature (placeholder; in production this is the JWS
of the credential per W3C VC-JWT):

```
eyJhbGciOiJFUzI1NiIsImtpZCI6InRlc3NlcmEtaWRlbnRpdHktMjAyNi1xMSJ9...
```

The signature covers the entire credential payload. The
JWS header includes the key identifier (`kid`) that
the gate uses to look up the signing key in Tessera's
JWKS.

---

## 4. Artifact 3 — Verifier code-sketch

```python
from typing import NamedTuple
from enum import Enum

class Outcome(Enum):
    ALLOW = "allow"
    DENY = "deny"
    STEP_UP = "step_up"

class VerifyResult(NamedTuple):
    outcome: Outcome
    reason: str

def verify_manifest(manifest_jwt: str, requested_operation: dict,
                    current_time: datetime, gate_context: dict) -> VerifyResult:
    # Step 1: Parse and verify signature
    try:
        header, payload = decode_jwt_unverified(manifest_jwt)
    except Exception as e:
        return VerifyResult(Outcome.DENY, f"invalid manifest: {e}")

    issuer = payload.get("issuer")
    if issuer not in TRUSTED_ISSUERS:
        return VerifyResult(Outcome.DENY, "issuer not trusted")

    try:
        jwks = fetch_jwks(issuer)  # cached with TTL
        verified_payload = verify_jws(manifest_jwt, jwks, header["kid"])
    except SignatureError:
        return VerifyResult(Outcome.DENY, "signature verification failed")

    # Step 2: Expiration check
    valid_from = parse_rfc3339(verified_payload["validFrom"])
    valid_until = parse_rfc3339(verified_payload["validUntil"])
    if current_time < valid_from:
        return VerifyResult(Outcome.DENY, "manifest not yet valid")
    if current_time > valid_until:
        return VerifyResult(Outcome.DENY, "manifest expired")

    # Step 3: Audience check
    if verified_payload.get("audience") != gate_context["gate_uri"]:
        return VerifyResult(Outcome.DENY, "audience mismatch")

    # Step 4: Revocation check
    cred_id = verified_payload["jti"]
    op_class = requested_operation["action"]
    fresh_check_required = op_class in CATASTROPHIC_OPS
    rev_status = check_revocation(
        cred_id,
        cache_max_age_seconds=0 if fresh_check_required else 30
    )
    if rev_status == "revoked":
        return VerifyResult(Outcome.DENY, "credential revoked")
    if rev_status == "unknown" and fresh_check_required:
        return VerifyResult(Outcome.DENY, "revocation status unknown for catastrophic op")

    # Step 5: Delegation chain validation
    chain = verified_payload["credentialSubject"].get("delegationChain", [])
    for hop in chain:
        try:
            verify_delegation_hop(hop, current_time)
        except DelegationError as e:
            # CRITICAL: chain failure must DENY, not silently proceed
            return VerifyResult(Outcome.DENY, f"delegation chain failed at hop: {e}")

    # Step 6: Capability lookup
    capabilities = verified_payload["credentialSubject"]["capabilities"]
    matching_cap = find_matching_capability(capabilities, requested_operation)
    if matching_cap is None:
        return VerifyResult(Outcome.DENY, "no matching capability")

    # Constraint enforcement
    if not constraints_satisfied(matching_cap["constraints"], requested_operation):
        return VerifyResult(Outcome.DENY, "constraints not satisfied")

    # Step-up required flag in capability
    if matching_cap["constraints"].get("stepUpRequired"):
        return VerifyResult(Outcome.STEP_UP, "capability requires step-up")

    return VerifyResult(Outcome.ALLOW, "verified")
```

**Note on the delegation-chain failure case:** if any
intermediate hop fails verification, the entire
manifest is rejected. The reference deliberately
does *not* attempt to authorise based on partial-
chain validity; partial validity in delegation chains
is the source of well-known authorisation bypass
patterns.

---

## 5. Reasoning notes

- **Why W3C VC + JWT rather than a commercial
  attestation product.** Tessera's existing OIDC
  infrastructure is the determining factor. A bank
  that did not have this could reasonably choose a
  commercial attestation or gateway product (Cloudflare
  or another vendor) — the build cost would be higher
  and the time-to-deploy worse. Tessera's specific
  context makes building the
  right choice. This is the *context-dependent*
  decision the §6 framework describes.
- **Why ES256 specifically.** ES256 is the most
  widely-supported VC signing algorithm. RS256 is
  also acceptable but larger signatures; Ed25519 is
  modern but less interoperable with banking
  infrastructure. ES256 is the safe choice.
- **Why 1-hour validity.** Short enough that
  revocation is implicit for most cases (lose
  attestation in an hour); long enough that
  re-issuance is not constantly happening. Some
  operations (catastrophic) may require fresh
  re-attestation regardless.
- **Why the capability vocabulary is banking-specific.**
  A generic capability format ("can do X") would
  fail to express the constraints (max amount,
  max per day, between-customer-owned-accounts-
  only). Bank capabilities are domain-specific.
  Commercial schemas can be extended but each
  extension introduces vendor-specific schema
  knowledge.
- **Why the verifier code rejects on delegation-
  chain failure.** This is the §3.4-adjacent
  failure mode: partial-chain validity has
  historically been a source of authorisation
  bypass. Reject-on-any-failure is the safe and
  the right posture.
- **What this manifest deliberately under-specifies.**
  The JWKS endpoint format details, the rotation
  cadence policy, the specific JOSE library
  Tessera uses. These are engineering decisions
  at a lower level than the CAIRO specification.
- **What I would do differently in v2.** Add an
  `evidence` block in the credential subject for
  binding to the customer's authentication-time
  evidence (WebAuthn attestation, etc.). This
  would let the gate verify that the principal's
  authentication evidence is still valid, not
  just that it occurred.

---

Maintained by [Girish Nair](https://github.com/garynair)
