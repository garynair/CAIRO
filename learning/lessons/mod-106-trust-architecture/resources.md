# Module 106 — Resources

Annotated reading list for Trust Architecture.

## Tier 1 — Authoritative standards

| Source | Why it matters |
|---|---|
| [NIST SP 800-207 — Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final) | The structural inheritance for §2. Required reading. |
| [W3C Verifiable Credentials Data Model 2.0](https://www.w3.org/TR/vc-data-model-2.0/) | The identity / capability standard §3 references |
| [OAuth 2.1](https://oauth.net/2.1/) + [RFC 9068 (JWT for OAuth)](https://datatracker.ietf.org/doc/rfc9068/) | The token-based identity layer most architectures use |
| [RFC 7519 (JWT)](https://datatracker.ietf.org/doc/html/rfc7519) + [RFC 7515 (JWS)](https://datatracker.ietf.org/doc/html/rfc7515) + [RFC 7517 (JWK)](https://datatracker.ietf.org/doc/html/rfc7517) | The JOSE family standards used for signed manifests |
| [NIST AI RMF MEASURE-2.7 (security)](https://www.nist.gov/itl/ai-risk-management-framework) | The framework hook for trust scoring as a measurement function |

## Tier 2 — Adjacent standards

| Source | Use |
|---|---|
| [SPIFFE / SPIRE](https://spiffe.io/) | Workload identity originally designed for services; adaptable to agents |
| [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html) | Identity-layer protocol on OAuth |
| [Sigstore](https://www.sigstore.dev/) | Attestation chains for build artifacts; pattern reference for runtime attestation |
| [OpenTelemetry GenAI semantic conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/) | Evolving event vocabulary §4.5 |

## Tier 3 — Foundational

| Source | What it gives this module |
|---|---|
| [NIST SP 800-63 (Digital Identity)](https://pages.nist.gov/800-63-3/) | The identity-assurance grounding underlying §3 |
| [Cybersecurity & Infrastructure Security Agency (CISA) ZTMM](https://www.cisa.gov/zero-trust-maturity-model) | Maturity model for §2 application |
| mod-101 §3 (Three Lines of Defense) + mod-104 §3 (validation) | The governance context the architecture must integrate with |

## Tier 4 — Practitioner references (range, not template)

All of these are *one implementation pattern*, never
the canonical answer. The lecture notes draw on them
explicitly as examples of range:

| Source | Pattern illustrated |
|---|---|
| [Cloudflare AI Gateway](https://www.cloudflare.com/products/ai-gateway/) | Gateway-mediated trust + observability + safety; commercial |
| [IBM watsonx.governance](https://www.ibm.com/products/watsonx-governance) | Governance platform with trust components; commercial |
| [AWS Bedrock guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html) | Content-safety + posture controls; hyperscaler-embedded |
| [Anthropic responsible scaling policy](https://www.anthropic.com/rsp) | Capability-tier governance with trust components; frontier-AI pattern |
| Open-source SPIFFE / SPIRE patterns adapted to agents | Identity-only layer with build-it-yourself capability scoping |

## Where to go next

- **mod-107 — AI Security & Adversarial Defense.** The
  adversarial perspective. Trust architecture is the
  positive control surface; security defends it.
- **mod-108 — Audit Ledgers & Evidence.** Tamper-
  evident logging is the audit complement to trust
  architecture.
- **mod-109 — Compliance Operations.** Trust
  architecture is one of the most-asked-for evidence
  surfaces in regulator engagement.

---

Maintained by [Girish Nair](https://github.com/garynair)
