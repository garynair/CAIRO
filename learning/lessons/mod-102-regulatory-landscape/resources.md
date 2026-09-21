# Module 102 — Resources

Annotated reading list for the Regulatory Landscape module.
Framework-first; the Tier-1 list is the closest to
non-negotiable in the whole track.

## Tier 1 — Authoritative (read these)

| Source | Why it matters for this module |
|---|---|
| [EU AI Act (Regulation (EU) 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Chapters 2 and 3 are built on this. Required for Exercises 01 + 02 + 03. |
| [NIST AI RMF 1.0](https://www.nist.gov/itl/ai-risk-management-framework) + the [Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) | The operating framework anchor. Chapter 3 crosswalks the four functions to EU AI Act Article 9. |
| [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) | Layered with the EU AI Act in mod-101 Chapter 2; cited here for the §9 Performance Evaluation lens on continuous monitoring. |
| [OECD AI Principles (2024 update)](https://oecd.ai/en/ai-principles) | Upstream of every Tier-1 framework; helpful in Exercise 04 when reverse-engineering regulator intent. |
| [OMB M-25-21 — Accelerating Federal Use of AI](https://www.whitehouse.gov/omb/) | Chapter 9 is built on this. Search the OMB memo library for the current M-25-21 text; verify the title and issue date before citing in a filing. |

## Tier 2 — Authoritative, sector-specific

Read at least one of these for the sector that applies to
you. Exercise 02 will force you to read at least one in
detail.

### Financial services

| Source | Use |
|---|---|
| [OCC/FRB SR 11-7](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107.pdf) | The MRM baseline; recurs across the track |
| [FRB SR 26-2 (2026, current — supersedes SR 11-7 and SR 22-6)](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm) | Current AI/ML model validation expectations |
| [NYDFS 23 NYCRR Part 500](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | NY-supervised entities; AI amendments live here |
| [CFPB Circular 2022-03 (Adverse Action Notices)](https://www.consumerfinance.gov/compliance/circulars/circular-2022-03-adverse-action-notification-requirements-in-connection-with-credit-decisions-based-on-complex-algorithms/) | The "no black box defense" position |

### Healthcare

| Source | Use |
|---|---|
| [FDA Software as a Medical Device guidance](https://www.fda.gov/medical-devices/digital-health-center-excellence) | AI/ML SaMD baseline |
| [FDA Predetermined Change Control Plan guidance](https://www.fda.gov/regulatory-information/search-fda-guidance-documents/marketing-submission-recommendations-predetermined-change-control-plan-artificial-intelligence) | Continuous-learning model regulation |
| [EU MDR (Regulation (EU) 2017/745)](https://eur-lex.europa.eu/eli/reg/2017/745/oj) | For AI medical devices on the EU market |

### Insurance

| Source | Use |
|---|---|
| [NAIC Model Bulletin on the Use of AI Systems by Insurers](https://content.naic.org/) | State-adopted insurance-sector model regulation; adoption pattern varies state-to-state |
| [Colorado Division of Insurance Reg 3 CCR 702-10](https://doi.colorado.gov/) | State-level non-discrimination testing for life-insurance underwriting with external consumer data and AI |

### HR / employment

| Source | Use |
|---|---|
| [NYC Local Law 144 (AEDT)](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page) | First operational bias-audit-and-notice law |
| EU AI Act Annex III(4) | EU employment-related AI as high-risk |
| [Illinois AI Video Interview Act](https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=4015) | Notice-and-consent state-level statute |

### US state comprehensive regime

| Source | Use |
|---|---|
| [Colorado AI Act (SB 24-205)](https://leg.colorado.gov/) | First US state analogue to the EU AI Act; comprehensive high-risk AI system regime |
| [California AI Transparency Act (SB 942)](https://leginfo.legislature.ca.gov/) | Notice-and-watermarking obligations for large generative AI providers |
| [Utah Artificial Intelligence Policy Act (SB 149)](https://le.utah.gov/) | Notice + regulated-profession disclosure statute |

## Tier 3 — Foundational, non-AI

| Source | What it gives this module |
|---|---|
| [GDPR (Regulation (EU) 2016/679), Art. 22](https://gdpr-info.eu/art-22-gdpr/) | Automated decisions concerning data subjects; the rights-based lineage anchor |
| [GDPR Articles 33–34](https://gdpr-info.eu/art-33-gdpr/) | Breach-notification timelines that any EU AI Act incident-response plan must respect |
| [EU NIS2 Directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj) | EU cybersecurity directive; incident-reporting overlay for essential / important entities |
| [IIA Three Lines Model (2020)](https://www.theiia.org/en/content/position-papers/2020/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense/) | 3LOD; carried over from mod-101 |
| [ECOA / Regulation B](https://www.consumerfinance.gov/rules-policy/regulations/1002/) | The rights-based framing for credit decisions the CFPB reads AI models under |

## Tier 4 — Practitioner references (range, not template)

| Source | What pattern it illustrates |
|---|---|
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp) | Capability-tier governance; useful for Chapter 1 lineage 3 |
| [Microsoft Responsible AI Standard v2](https://www.microsoft.com/en-us/ai/responsible-ai) | Cross-jurisdictional program; useful for Chapter 6 mapping discipline |
| [Google SAIF](https://safety.google/cybersecurity-advancements/saif/) | Security-overlay framework |

## By chapter — where to look first

| Chapter | Primary source(s) |
|---|---|
| 1. Four lineages of AI regulation | OECD AI Principles; NIST AI 100-1 preamble; GDPR Art. 22; SR 11-7 |
| 2. EU AI Act risk tiers | EU AI Act Arts 5–6 + 50, Annex III |
| 3. Article 9 and NIST crosswalk | EU AI Act Arts 9–13 + 72; NIST AI RMF Playbook (MAP, MEASURE, MANAGE, GOVERN) |
| 4. Sector-specific regulation | SR 11-7, SR 22-6, NYDFS Part 500, FDA SaMD + GMLP + PCCP, EU MDR, NAIC bulletin |
| 5. US state patchwork | CA AI Transparency Act; CO AI Act; NYC LL 144; Illinois AI Video Interview Act; Utah SB 149 |
| 6. Multi-regime obligations mapping | Practitioner synthesis; the four Tier-1 sources and one Tier-2 sector source |
| 7. Reading a regulator letter | SR 11-7 as the framing lens; CFPB Circular 2022-03 for a peer-lineage read |
| 8. Regulatory monitoring cadence | EU AI Office feed; sector regulator enforcement lists; framework publication feeds |
| 9. OMB M-25-21 federal CAIRO | OMB M-25-21 |

## Where to go next

- **mod-103 — AI Risk Frameworks.** Operationalizes the NIST
  AI RMF functions into a working program.
- **mod-104 — Model Risk Management.** Deep on SR 11-7 / SR
  22-6 applied to ML.
- **mod-110 — Incident Response.** Operational treatment of
  EU AI Act Art. 73 + GDPR Art. 33–34 + NIS2 + sector
  notification rules.

---

Maintained by [Girish Nair](https://github.com/garynair)
