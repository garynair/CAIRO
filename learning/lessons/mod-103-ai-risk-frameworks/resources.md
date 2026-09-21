# Module 103 — Resources

Annotated reading list for AI Risk Frameworks. Framework-
first, practitioner-second. Cite the source, not the
summary, when defending a program decision.

## Tier 1 — Authoritative (read these)

| Source | Why it matters for this module |
|---|---|
| [NIST AI 100-1 (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) | The framework body is short and referenced throughout the module. Read §3 (Characteristics of Trustworthy AI Systems) before Chapter 2; read §4 (Core) before Chapters 3–7. |
| **NIST AI RMF Playbook** (linked from the AI RMF landing page above) | Operationally rich, sub-function by sub-function. Chapters 3–7 name specific sub-functions (MAP-1.1, MAP-5.1, MEASURE-2.5, MANAGE-1.x, GOVERN-5.x, etc.); read the Playbook entries for the ones your systems touch. |
| [NIST AI 600-1 — Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) | Generative-AI-specific risk vocabulary. Useful for extending the taxonomy in Chapter 2 to cover generative systems, and for the misuse category in Chapter 5. |
| [ISO/IEC 23894:2023 — AI Risk Management Guidance](https://www.iso.org/standard/77304.html) | Complements NIST with AI-specific risk-management vocabulary layered on ISO 31000. Read §6 (Risk assessment) and §7 (Risk treatment) before Chapter 6. |
| [ISO/IEC 42001:2023 — AI Management System](https://www.iso.org/standard/81230.html) | Management-system standard for AI. The auditability discipline of Chapters 1, 3, 5, 6, and 7 tracks Annex A of 42001; if your program can pass a 42001 certification audit, it has made the framework-to-program conversion. |
| [ISO 31000:2018 — Risk Management Guidelines](https://www.iso.org/standard/65694.html) | The generic risk-management standard 23894 sits on. Useful for the appetite / tolerance vocabulary in Chapter 8 and for ERM roll-up framings in Chapter 2. |

## Tier 2 — Authoritative, sector- or regime-specific

| Source | Use |
|---|---|
| [EU AI Act — Regulation (EU) 2024/1689, Article 9](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | The risk-management-system obligation for high-risk systems. Chapters 3–6 crosswalk NIST to Article 9 sub-elements; mod-102 Chapter 3 develops the full crosswalk. |
| [EU AI Act, Article 27](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | The fundamental-rights impact assessment for deployers of high-risk systems. Read alongside Chapter 4 as one specific downstream form of the impact assessment. |
| [OCC / FRB SR 11-7](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107.pdf) | Supervisory guidance on model risk management. The residual-risk and effectiveness-monitoring disciplines in Chapter 6 apply broadly even outside financial services. mod-104 develops SR 11-7 in operational depth. |
| [FRB SR 26-2 (2026, current — supersedes SR 11-7 and SR 22-6)](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm) | Current Fed expectations on AI/ML model validation layered on SR 11-7. Useful for the MEASURE-side eval-set discipline in Chapter 5. |
| [OMB M-25-21](https://www.whitehouse.gov/omb/) | Federal AI use-case management, minimum practices, and the CAIO designation. Relevant to Chapter 2 taxonomy (rights-impacting / safety-impacting) if you operate in or with the US federal environment. mod-102 Chapter 9 has the framing. |

## Tier 3 — Foundational (read once, refer back)

| Source | What it gives this module |
|---|---|
| [COSO ERM — Enterprise Risk Management](https://www.coso.org/guidance-erm) | ERM framing that lets you reconcile the AI risk taxonomy to the enterprise risk taxonomy (Chapter 2) and integrate the AI appetite into the enterprise appetite (Chapter 8). |
| [COSO / WBCSD "Applying ERM to ESG" (2018) — read as a *pattern*, not for content](https://www.coso.org/guidance-erm) | Not directly AI, but a good worked example of grafting a new risk domain onto an existing ERM taxonomy. Use as pattern reference for Chapter 2. |
| [IIA Three Lines Model (2020)](https://www.theiia.org/en/content/position-papers/2020/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense/) | The 3LOD application carries through to GOVERN ownership in Chapter 7 and to the head-of-ai-governance role in Chapter 8. |

## Tier 4 — Practitioner and comparison references

| Source | Pattern illustrated |
|---|---|
| [Microsoft Responsible AI Standard v2 — Impact Assessment Template](https://www.microsoft.com/en-us/ai/principles-and-approach) | One widely-cited public impact-assessment template. Read once for pattern range before Exercise 02; do not copy. |
| [Google SAIF (Secure AI Framework)](https://safety.google/cybersecurity-advancements/saif/) | Security-overlay control framing; useful for the Security category in Chapter 2 and for building the pre-/deployment/-post-deployment control catalog in Chapter 6. |
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp) | Capability-tier residual-risk discipline. Useful for Chapter 6 §residual, and for the *Catastrophic risk* adaptation of the taxonomy discussed in Chapter 2. |
| [MITRE ATLAS](https://atlas.mitre.org/) | Adversarial-ML tactic and technique catalog. A source for Security-category sub-categories in Chapter 2 and for the misuse metrics discussed in Chapter 5. |
| [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | Application-security-oriented enumeration. A source for Security-category sub-categories in Chapter 2. Do **not** put OWASP items at the top level of your taxonomy — Chapter 2 explains why. |
| [ICO AI + Data Protection Toolkit / DPIA guidance](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/) | Pattern reference for the privacy sections of the impact assessment (Chapter 4) and for integrating DPIA obligations with the AI IA. |

## Where to go next

- **mod-104 — Model Risk Management.** Deepens MANAGE
  (Chapter 6) for financial-services contexts under
  SR 11-7.
- **mod-105 — Responsible AI & Ethics.** Layers ethics
  over the loop this module builds.
- **mod-108 — Audit Ledgers & Evidence.** Hardens the
  evidence trail behind the six-artifact chain in
  Chapter 7.
- **mod-109 — Compliance Operations.** Operationalises
  the artifact set against specific regulatory regimes.
- **mod-111 — Board Reporting.** Develops the quarterly
  board report (Chapter 7) and the appetite statement
  sign-off pattern (Chapter 8).

---

Maintained by [Girish Nair](https://github.com/garynair)
