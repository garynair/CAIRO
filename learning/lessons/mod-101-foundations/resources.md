# Module 101 — Resources

Annotated reading list for AI Governance Foundations.
**Framework-first.** Practitioner references are explicitly
marked as such and are intended as range, not template.

## Tier 1 — Authoritative (read these)

| Source | Why it matters for this module |
|---|---|
| [NIST AI Risk Management Framework 1.0 (NIST AI 100-1)](https://www.nist.gov/itl/ai-risk-management-framework) + the [AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) | The operating-system framework. Chapter 2 is built on this. |
| [ISO/IEC 42001:2023 — AI Management System](https://www.iso.org/standard/81230.html) | Required for Exercise 02 (charter drafting). §5 (Leadership) is the structural anchor for the 3LOD discussion in Chapter 3. |
| [ISO/IEC 23894:2023 — AI Risk Management Guidance](https://www.iso.org/standard/77304.html) | Companion to ISO 42001; explains *how* to do AI-specific risk management within an AIMS. |
| [ISO/IEC 38507:2022 — Governance implications of the use of AI by organizations](https://www.iso.org/standard/56641.html) | The governance-body-facing standard; anchors Chapter 5's peer-boundary work and Chapter 7's engagement contracts. |
| [OECD AI Principles (2024 update)](https://oecd.ai/en/ai-principles) | The values upstream of every Tier-1 framework. Read once; cite when grounding exercises in principles. |
| [IIA Three Lines Model (2020)](https://www.theiia.org/en/content/position-papers/2020/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense/) | The 3LM vocabulary used in Chapter 3. The 2020 update renamed 3LOD to 3LM — the rename matters. |

## Tier 2 — Authoritative, sector- and jurisdiction-specific

Read for the sector or jurisdiction that applies to you (or
for Exercise 04 where you map stakeholders across sectors).

| Source | Sector / jurisdiction |
|---|---|
| [EU AI Act — Regulation (EU) 2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Any organization placing AI on the EU market; covered fully in mod-102 |
| [OCC/FRB SR 11-7 — Supervisory Guidance on Model Risk Management](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107.pdf) | Financial services (US); foundational for mod-104 |
| [FRB SR 26-2 (2026, current — supersedes SR 11-7 and SR 22-6)](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm) | Financial services — current Fed expectations on model risk management |
| [NYDFS 23 NYCRR Part 500](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | Financial services (NY-supervised); cybersecurity/AI amendments |
| [OMB M-25-21 — Accelerating Federal Use of AI](https://www.whitehouse.gov/omb/) | US federal agencies; CAIO designation and agency AI governance shape (search the OMB memo library for the current M-25-21 text) |
| [FDA Good Machine Learning Practice (GMLP)](https://www.fda.gov/medical-devices/digital-health-center-excellence) | Healthcare / SaMD |
| [California AI Transparency Act + SB 243](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202320240SB243) | Consumer-facing AI, US state-level |

## Tier 3 — Foundational, non-AI

Useful for the 3LOD, operating-model, and engagement-contract
discussions because the source material predates AI and is
well-tested.

| Source | What it gives this module |
|---|---|
| [COSO ERM — Applying ERM to AI (2024 supplement)](https://www.coso.org/guidance-erm) | Bridges traditional ERM with AI-specific risks; useful for Chapter 5 (peer boundaries with CRO), Chapter 8, and Exercise 05 |
| [COSO Internal Control — Integrated Framework (2013)](https://www.coso.org/internal-control) | The internal-control vocabulary the CAE (Chapter 5) operates in |
| [IEEE 7000-2021 — Model Process for Addressing Ethical Concerns in System Design](https://standards.ieee.org/ieee/7000/6781/) | Ethics-standards family; useful counterweight to a purely-compliance framing |
| [ISO 31000:2018 — Risk Management Guidelines](https://www.iso.org/standard/65694.html) | The general risk-management vocabulary that ISO/IEC 23894 specializes for AI |

## Tier 4 — Practitioner references (range, not template)

These are real implementations of governance / responsible AI
programs. **None of them is the canonical answer.** Read for
range. Chapters 4 and 6 draw on these.

| Source | What pattern it illustrates |
|---|---|
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp) | Frontier-AI capability-tier governance |
| [Microsoft Responsible AI Standard v2](https://www.microsoft.com/en-us/ai/responsible-ai) | Hyperscaler hub-and-spoke RAI program |
| [Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/) | Security-overlay framework with separate RAI governance |
| [IBM watsonx.governance overview](https://www.ibm.com/products/watsonx-governance) | One vendor implementation of AI governance tooling; useful for the vendor-capture failure mode in Chapter 8 |

If you find yourself citing a Tier 4 source for a governance
*structural* choice (organization design, reporting line,
control catalog), stop and ask whether you would defend the
choice on its own merits if the practitioner had not
published it. If not, the Tier 1 source you should have
cited probably exists.

## By chapter — where to look first

| Chapter | Primary source(s) |
|---|---|
| 1. What AI governance is | OECD AI Principles; NIST AI 100-1 preamble |
| 2. NIST AI RMF | NIST AI 100-1 + Playbook; ISO 42001 crosswalk |
| 3. Three Lines of Defense | IIA Three Lines Model (2020); ISO 42001 §5 |
| 4. When to appoint a CAIRO | ISO/IEC 38507; practitioner survey (Tier 4) |
| 5. Peer boundaries | ISO/IEC 38507; COSO ERM AI Supplement; sector guidance for CISO / CPO peers |
| 6. Operating models | ISO 42001 §5; NIST AI RMF Playbook GOVERN sub-functions; Tier 4 practitioner illustrations |
| 7. Engagement contracts | IIA Three Lines Model (2020) — matrix relationships; general executive-role literature |
| 8. Failure modes | Synthesis across the above; COSO ERM AI Supplement for the compliance-only pattern |

## Where to go next

- **mod-102 — Regulatory Landscape.** Drills into EU AI Act,
  NIST AI RMF + Playbook deep cuts, sector-specific
  regulation, and jurisdictional mapping.
- **mod-103 — AI Risk Frameworks.** Operationalizes the four
  NIST functions into a working program.
- **mod-104 — Model Risk Management.** SR 11-7-style MRM
  applied to ML models.

---

Maintained by [Girish Nair](https://github.com/garynair)
