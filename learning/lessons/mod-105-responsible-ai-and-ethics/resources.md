# Module 105 — Resources

Annotated reading list for Responsible AI and Ethics.

## Tier 1 — Authoritative principle documents (read these)

| Source | Why it matters |
|---|---|
| [OECD AI Principles (2024 update)](https://oecd.ai/en/ai-principles) | The closest thing to international consensus; upstream of NIST + EU |
| [UNESCO Recommendation on the Ethics of AI](https://www.unesco.org/en/artificial-intelligence/recommendation-ethics) | Broad international ethics statement; 193-country adoption |
| [IEEE 7000 Series](https://standards.ieee.org/industry-connections/ec/autonomous-systems/) | Standards-grade; IEEE 7000 (process), 7001 (transparency), 7003 (bias) most operational |
| [EU HLEG Ethics Guidelines for Trustworthy AI](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai) | Upstream of EU AI Act |
| [NIST AI RMF preamble](https://www.nist.gov/itl/ai-risk-management-framework) | Names the framework's underlying values |

## Tier 1 — Authoritative technical literature

| Source | Why it matters |
|---|---|
| Chouldechova (2017), *Fair Prediction with Disparate Impact* | The impossibility result — required reading for §3.2 |
| Kleinberg, Mullainathan, Raghavan (2016), *Inherent Trade-offs in the Fair Determination of Risk Scores* | The other impossibility result; same conclusion via different framing |
| Selbst, Boyd, Friedler, Venkatasubramanian, Vertesi (2019), *Fairness and Abstraction in Sociotechnical Systems* | Why algorithmic fairness alone is insufficient |
| Mitchell et al. (2019), *Model Cards for Model Reporting* | Foundational artifact for transparency to multiple audiences |
| Gebru et al. (2018), *Datasheets for Datasets* | Data-side transparency complement to Model Cards |

## Tier 2 — Sector-specific

| Source | Sector | Use |
|---|---|---|
| [CFPB Circular 2022-03](https://www.consumerfinance.gov/compliance/circulars/circular-2022-03-adverse-action-notification-requirements-in-connection-with-credit-decisions-based-on-complex-algorithms/) | Financial services | Explainability / adverse-action; the "black-box defense" rejection |
| [CO Reg 10-1-1](https://doi.colorado.gov/) | Insurance | Algorithmic discrimination testing |
| [FDA SaMD guidance](https://www.fda.gov/medical-devices/digital-health-center-excellence/software-medical-device-samd) | Healthcare | Patient-affected transparency under medical-device frameworks |
| [NYC Local Law 144](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page) | HR | Bias audit + candidate notice |

## Tier 3 — Foundational

| Source | What it gives this module |
|---|---|
| [Asilomar AI Principles](https://futureoflife.org/open-letter/ai-principles/) | Frontier-AI focused; useful for §1.3 discussion of safety vs. ethics |
| Friedman & Hendry (2019), *Value Sensitive Design* | Methodological grounding for §6.1 (ethics in standards) |
| mod-103 §2 (AI risk taxonomy) | Bias, transparency, privacy as risk categories |
| mod-104 §3 (validation patterns) | Subgroup validation as operational form of fairness |

## Tier 4 — Practitioner references (range, not template)

| Source | Pattern |
|---|---|
| [Microsoft Responsible AI Standard v2](https://www.microsoft.com/en-us/ai/responsible-ai) | One well-developed operationalization; hub-and-spoke pattern |
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp) | Frontier-AI capability tiers (adjacent to ethics, not it) |
| [Google AI Principles](https://ai.google/responsibility/principles/) | Hyperscaler principles document; pattern reference only |
| Public Model Cards (Hugging Face library) | Format reference for audience-tailored transparency |

## Where to go next

- **mod-106 — Trust Architecture.** Operationalises trust
  gates and identity for AI systems.
- **mod-107 — AI Security & Adversarial Defense.** Where
  fairness and security overlap.
- **mod-111 — Board Reporting & Risk Appetite.** Where
  ethics positions surface to executive accountability.

---

Maintained by [Girish Nair](https://github.com/garynair)
