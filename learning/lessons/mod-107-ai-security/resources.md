# Module 107 — Resources

Annotated reading list for AI Security and
Adversarial Defense.

## Tier 1 — Authoritative attack taxonomies

| Source | Why it matters |
|---|---|
| [MITRE ATLAS](https://atlas.mitre.org/) | The structured vocabulary §2.1 builds on; case-study base |
| [OWASP LLM Top 10 (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | The LLM-specific priority list §2.2 |
| [NIST AI 100-2 E2023](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) | Adversarial ML taxonomy + mitigation recommendations §2.3 |
| [NIST AI 600-1 (Generative AI Profile)](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) | GenAI-specific risk vocabulary; complements NIST AI 100-2 |

## Tier 2 — Authoritative process / governance

| Source | Use |
|---|---|
| [NIST SP 800-39 (Risk Management)](https://csrc.nist.gov/publications/detail/sp/800-39/final) | Defense-in-depth grounding §3 |
| [NIST SP 800-53 (Security Controls)](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) | Control catalog; AI-specific controls are emerging |
| [EU AI Act Articles 15 (cybersecurity) + 73 (incident reporting)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Required reading for the §6 classification + reporting work |
| [NYDFS Part 500 §500.17](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | Cybersecurity incident notification for NY-supervised entities |
| [GDPR Art. 33/34](https://gdpr-info.eu/art-33-gdpr/) | Personal-data breach notification |

## Tier 3 — Foundational

| Source | What it gives this module |
|---|---|
| mod-104 §5 (CAIRO × MRM boundary) | Structural pattern for §5 |
| mod-106 (Trust Architecture) | The positive control surface this module operates within |
| mod-103 §2 (taxonomy) | Security as a risk category |
| [IIA Three Lines Model](https://www.theiia.org/en/content/position-papers/2020/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense/) | The 3LOD application carries to CISO ownership |

## Tier 4 — Practitioner references (range, not template)

| Source | Pattern illustrated |
|---|---|
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp) | Capability-tier red-teaming cadence |
| [Microsoft AI Red Team practices](https://learn.microsoft.com/en-us/security/ai-red-team/) | One enterprise red-team operating model |
| [Google AI red-teaming guidance](https://safety.google/cybersecurity-advancements/saif/) | Hyperscaler red-team pattern |
| [HackerOne AI Safety Bounty patterns](https://www.hackerone.com/) | External-researcher patterns adapted for AI |
| [Cloudflare AI Gateway safety features](https://www.cloudflare.com/products/ai-gateway/) | Gateway-mediated output filtering pattern |

## Where to go next

- **mod-108 — Audit Ledgers and Evidence.**
  Tamper-evident logging complements incident
  classification.
- **mod-109 — Compliance Operations.** The
  cross-walks between security incidents and
  regulatory obligations live here.
- **mod-110 — Incident Response.** Operational
  treatment of incident response across both
  security and AI-program dimensions.
- **`ai-infra-security-learning`** (paired
  curriculum) — engineering-depth treatment of
  the same surface.

---

Maintained by [Girish Nair](https://github.com/garynair)
