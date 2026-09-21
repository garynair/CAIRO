# Module 108 — Resources

Annotated reading list for Audit Ledgers and
Evidence.

## Tier 1 — Authoritative standards

| Source | Why it matters |
|---|---|
| [RFC 9162 — Certificate Transparency v2.0](https://datatracker.ietf.org/doc/rfc9162/) | The structural reference for tamper-evident ledgers |
| [RFC 3161 — Time-Stamp Protocol](https://datatracker.ietf.org/doc/rfc3161/) | External timestamp authority pattern for sealing |
| [RFC 6962 — Certificate Transparency v1](https://datatracker.ietf.org/doc/rfc6962/) | The historical CT reference; useful background |
| [EU AI Act Art. 12 (Record-keeping)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | The high-risk-system logging obligation |
| [NIST SP 800-92 (Computer Security Log Management)](https://csrc.nist.gov/publications/detail/sp/800-92/final) | Foundational logging discipline |

## Tier 2 — Authoritative, sector-specific

| Source | Sector / use |
|---|---|
| [NYDFS Part 500 §500.06 (Audit trail)](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | NY-supervised financial services audit-trail requirement |
| [SR 11-7 §V (Governance, Policies, Controls)](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107.pdf) | Banking model documentation requirements |
| [FDA SaMD documentation guidance](https://www.fda.gov/medical-devices/digital-health-center-excellence/software-medical-device-samd) | Medical-device documentation expectations |
| [SOC 2 Trust Services Criteria](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) | SOC 2 evidence framework |

## Tier 3 — Event vocabulary and analysis

| Source | Use |
|---|---|
| [OpenTelemetry GenAI semantic conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/) | Evolving community vocabulary for LLM and agent events |
| [CloudEvents 1.0](https://cloudevents.io/) | Generic event envelope used as a base by several AI vocabularies |
| [Sigstore Rekor documentation](https://docs.sigstore.dev/logging/overview/) | Open-source Merkle-based transparency log |

## Tier 4 — Practitioner references (range, not template)

| Source | Pattern |
|---|---|
| VeriSwarm Vault | Merkle-chained ledger with hash-chain ordering + signed exports |
| [Sigstore Rekor](https://www.sigstore.dev/) | Open-source transparency log adaptable to AI events |
| [AWS CloudTrail with integrity validation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-log-file-validation-intro.html) | Hyperscaler-managed audit-trail |
| [IBM watsonx.governance audit features](https://www.ibm.com/products/watsonx-governance) | Enterprise governance platform with evidence components |

## Where to go next

- **mod-109 — Compliance Operations.** Uses the
  evidence layer this module establishes for
  regulator-facing operations.
- **mod-110 — Incident Response.** Uses evidence
  for post-incident review and regulator
  notification.
- **mod-111 — Board Reporting.** Uses evidence
  for board-level reporting traceability.

---

Maintained by [Girish Nair](https://github.com/garynair)
