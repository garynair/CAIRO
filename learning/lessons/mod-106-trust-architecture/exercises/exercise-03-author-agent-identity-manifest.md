# Exercise 03 — Author an Agent Identity + Capability Manifest

**Estimated time**: 3 hours
**Deliverable**: A manifest format specification + a
worked example + a verifier code-sketch (≤ 3 pages)

---

## The scenario

You are advising **Tessera Bank's** Identity team on the
manifest format the agentic customer-service agent will
present at each operation. The CISO has narrowed the
choice to three patterns from §3.3 of the lecture notes:

- **Anthropic agent attestation pattern** style
  (signed attestations of model identity +
  configuration).
- **Cloudflare AI Gateway** style (gateway-mediated;
  the gateway becomes the identity authority).
- **Roll-your-own** with W3C VC + JWT.

The Identity team has asked you to **author the manifest
format**, using whichever pattern you recommend, with
specific fields and a worked example. The Identity team
will implement; the CAIRO function's contribution is to
specify what the manifest must contain to be operationally
adequate.

## Your assignment

Produce three artifacts.

### Artifact 1 — Manifest format specification (≤ 1½ pages)

A specification document covering:

1. **Pattern chosen** — one of the three above (or a
   defensible hybrid). State up front with one-paragraph
   defence.
2. **Required fields** — for each, name, type, format,
   purpose. At minimum:
   - Issuer
   - Subject (agent identity composite)
   - Audience (which trust gates accept this manifest)
   - Expiration
   - Capabilities (with explicit scope language)
   - Delegation chain (if applicable)
   - Signature
3. **Optional fields** — what the manifest may include
   for richer authorisation.
4. **Signing mechanism** — algorithm, key management,
   key rotation.
5. **Verification protocol** — the steps the trust gate
   must perform to verify the manifest.
6. **Revocation handling** — how revocation is signalled
   and how the trust gate respects it.

### Artifact 2 — Worked example (≤ 1 page)

A concrete manifest for the Tessera agent operating on
behalf of a specific customer:

- Show the manifest in JSON (or appropriate format for
  the chosen pattern).
- Annotate each field with what it specifies.
- Include a representative delegation chain (Tessera as
  bank → customer → agent instance) if applicable to
  the chosen pattern.
- Show the signature header and explain what the
  signature covers.

The worked example need not include actual cryptographic
signatures (placeholder values are fine); the field
structure and chain semantics are what matter.

### Artifact 3 — Verifier code-sketch (≤ ½ page)

Pseudocode (or actual code in your preferred language)
for the trust gate's verification function:

```
function verify_manifest(manifest, current_time, gate_context):
    # ... verification steps
    return ALLOW | DENY | STEP_UP, reason
```

Cover, at minimum:

- Signature verification.
- Expiration check.
- Audience check.
- Delegation chain validation.
- Revocation check.
- Capability lookup against the requested operation.

The pseudocode does not need to be executable; it should
make the verification semantics inspectable.

## Constraints

- The manifest must be **machine-verifiable** without
  reference to any other authority at runtime, except
  for revocation status and JWKS lookup.
- Capability fields must be **specific enough** that a
  gate can decide *yes* or *no* deterministically.
  "Can perform banking operations" is not specific.
- The expiration must be **short** — minutes to hours,
  not days, for a high-throughput agent.
- The verifier code must address the **case where
  delegation is presented but verification fails for
  an intermediate hop** — what happens then.
- The chosen pattern must be **honestly defended**.
  If the recommendation is "buy a commercial gateway
  product", the defence must address vendor capture
  (§6.4). If "build with W3C VC + JWT", the defence
  must address maintenance burden.

## Rubric

| Criterion | Weight |
|---|---|
| Pattern chosen with substantive defence | 15% |
| Manifest fields — complete, specific | 25% |
| Signing + verification — addressed concretely | 15% |
| Worked example — annotated, representative | 20% |
| Verifier code-sketch — covers six verification steps | 20% |
| Honest treatment of trade-offs in the chosen pattern | 5% |

## Where to submit

`solutions/modules/mod-106-trust-architecture/exercise-03-author-agent-identity-manifest/SOLUTION.md`

Reference solution recommends **roll-your-own with W3C
VC + JWT** for Tessera based on (a) Tessera's existing
identity infrastructure (the bank already operates a
production OIDC stack), (b) the customisation needed for
banking-specific capability vocabulary, and (c) the
vendor-capture concern. The defence explicitly addresses
the maintenance burden and the cryptographic-expertise
requirement.

## Reading before you start

- Lecture notes §3 (identity and capability scoping).
- W3C Verifiable Credentials Data Model 2.0 — §§3–5.
- RFC 7519 (JWT) for token structure.
- Cloudflare AI Gateway identity documentation, and
  one open-source reference (e.g., SPIFFE / SPIRE
  adapted for agents) for comparison.
