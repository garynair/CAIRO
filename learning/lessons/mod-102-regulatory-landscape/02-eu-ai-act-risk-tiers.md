# Chapter 2 — The EU AI Act: Risk Tiers and Annex III Classification

## Why this chapter exists

The European Union AI Act (Regulation (EU) 2024/1689) is
the first comprehensive AI-specific statute from a major
jurisdiction. It came into force in stages from 2024
onward. The prohibited-practices provisions applied first;
the general-purpose AI provisions followed; the high-risk
system provisions in Title III phase in through 2026 and
2027.

Any CAIRO with EU exposure — and "EU exposure" reaches every
firm placing AI on the EU market or serving EU-resident
users, regardless of where the firm is domiciled — has to
be able to classify a system quickly and defensibly. Tier
determines the entire rest of the obligation stack.

This chapter builds the classification skill. Chapter 3
covers Article 9 (the risk-management system for high-risk
systems). Later modules pick up Article 72 (post-market
monitoring) and Article 73 (serious-incident reporting).

## Structure of the Act (the parts a CAIRO must know)

The Act is organised into titles. The five operationally
relevant ones for a CAIRO:

- **Title I (Arts 1–4)** — Scope, definitions, and scope
  of application. Article 2 controls the extraterritorial
  reach.
- **Title II (Art 5)** — Prohibited AI practices.
- **Title III (Arts 6–49)** — High-risk AI systems. Where
  most of your work lives.
- **Title V (Arts 51–56)** — General-Purpose AI models.
- **Title VIII (Arts 70–82)** — Post-market monitoring,
  information-sharing, and enforcement.

Annexes cited most often in operational work: **Annex III**
(the operational high-risk list), **Annex IV** (technical
documentation contents), **Annex VI / VII** (conformity
assessment procedures).

## The four risk tiers

The Act sorts AI systems into four tiers. Knowing the tier
determines everything else — the obligations, the
documentation, the conformity assessment route, the
post-market monitoring, whether the system can be placed on
the EU market at all.

| Tier | What it means | Where it lives in the Act |
|---|---|---|
| **Prohibited** | Cannot be placed on the market or used in the EU at all | Art. 5 |
| **High-risk** | Allowed, but subject to extensive obligations | Title III (Arts 6–49) + Annex III |
| **Limited-risk** | Allowed; transparency obligations only | Art. 50 |
| **Minimal-risk** | No specific obligations under the Act | (residual) |

A system that sits above the highest tier that fits it wins
— if a chat interface both interacts with users (Art. 50
transparency) and is used for credit-scoring (Annex III(5)),
it is high-risk, not limited-risk.

## Prohibited practices (Art. 5)

The categories a CAIRO should be able to name from memory:

- Social scoring by public authorities based on personal
  characteristics.
- Real-time remote biometric identification in publicly
  accessible spaces by law enforcement (with narrow
  authorised exceptions).
- Systems that exploit vulnerabilities of specific groups
  (age, disability, socio-economic situation).
- Systems that materially distort behaviour through
  subliminal or manipulative techniques causing significant
  harm.
- Untargeted scraping of facial images from the internet or
  CCTV to build facial-recognition databases.
- Emotion recognition in workplaces and educational
  settings (with narrow safety and medical exceptions).
- Biometric categorisation systems that infer sensitive
  attributes (race, political opinions, trade-union
  membership, religion, sex life or sexual orientation).
- Predictive policing based solely on profiling of a
  natural person.

If a system falls into any of these categories, no
compliance program saves it — the system cannot be deployed
in the EU. The gate is *categorical*, not risk-managed.

## High-risk classification (Art. 6 + Annex III)

A system is high-risk if it falls under either:

- **Art. 6(1)** — used as a safety component of a product
  regulated under EU sectoral law (medical devices,
  machinery, in-vitro diagnostics, aviation, vehicles,
  toys, radio equipment, and others listed in Annex I) **and**
  required to undergo third-party conformity assessment
  under that sectoral law, or
- **Art. 6(2) via Annex III** — used in one of the listed
  high-risk areas below, *unless* the Art. 6(3) exemption
  applies.

Annex III lists these high-risk areas (the operational list
CAIROs use most):

1. **Biometrics** — remote biometric identification,
   biometric categorisation for sensitive attributes,
   emotion recognition (subject to Art. 5 prohibitions).
2. **Critical infrastructure** — safety components of
   critical digital infrastructure, road traffic, and the
   supply of water, gas, heating, or electricity.
3. **Education and vocational training** — admission,
   evaluation, and monitoring of prohibited student
   behaviour.
4. **Employment, worker management, and access to
   self-employment** — recruitment (targeting, sifting,
   ranking), promotion, termination, task allocation,
   performance monitoring.
5. **Access to and enjoyment of essential private services
   and essential public services and benefits** — credit
   scoring, eligibility for public benefits, emergency
   services triage, life and health insurance pricing and
   risk assessment.
6. **Law enforcement** — risk assessment of natural
   persons, polygraph and similar tools, evidence
   evaluation, profiling in the investigation of criminal
   offences.
7. **Migration, asylum, and border control management** —
   polygraph and similar, risk assessment, examination of
   applications.
8. **Administration of justice and democratic processes** —
   assisting judicial authorities in interpreting facts and
   applying law; influencing the outcome of elections or
   referenda.

Memorising the eight areas is not optional for anyone with
EU exposure. Exercise 01 forces classification against them.

## The Art. 6(3) exemption

An important carve-out. A system that would otherwise fall
under Annex III is **not** high-risk if it does *not* pose
a significant risk of harm to health, safety, or
fundamental rights — specifically because it satisfies at
least one of these conditions:

(a) The AI system is intended to perform a **narrow
    procedural task**.
(b) The AI system is intended to **improve the result** of a
    previously completed human activity.
(c) The AI system is intended to **detect decision-making
    patterns or deviations** from prior patterns and is not
    meant to replace or influence the previously completed
    human assessment without proper human review.
(d) The AI system is intended to **perform a preparatory
    task** to an assessment relevant for the Annex III use
    cases.

The exemption does not apply to systems that carry out
profiling of natural persons — profiling always keeps the
system in high-risk.

Providers relying on Art. 6(3) must **document** the
assessment and register the system in the EU database
established under Art. 71. The market surveillance
authority may reclassify the system as high-risk if the
assessment is not defensible.

## Limited-risk (Art. 50) transparency obligations

Systems that are not high-risk but touch users directly
carry disclosure obligations:

- AI systems that **interact directly with natural persons**
  must inform users they are dealing with an AI, unless
  obvious from the context or the system is for authorised
  crime detection.
- **Emotion-recognition and biometric-categorisation**
  systems must inform natural persons of their operation.
- **Synthetic content (deep fakes)** must be labelled as
  artificially generated or manipulated.
- **AI-generated text on matters of public interest**
  published without human editorial responsibility must be
  labelled.

Transparency obligations are cheap to satisfy in principle
and expensive to satisfy in retrofit. Build the disclosure
plumbing into the interaction layer early.

## General-Purpose AI (Title V)

A separate tier for providers of general-purpose AI models.
All GPAI providers carry obligations around documentation,
copyright policy, and a summary of training data. Models
above a compute threshold (verify current implementing acts
for the value in force — the Act empowers the Commission to
update it) are classified as having **systemic risk** and
trigger additional obligations: continuous evaluation,
adversarial testing, cybersecurity protections, and
serious-incident reporting analogous to Art. 73.

For CAIROs at firms **using** GPAI models rather than
building them, the relevant provision is **deployer
obligations**: when a GPAI model is integrated into a
high-risk system, the integrator can find themselves in a
provider-like position for the integrated system. Exercise
02 forces this question directly.

## Enforcement and fines

Penalties scale with the violation tier:

- Prohibited practices (Art. 5) — up to **€35M or 7% of
  worldwide annual turnover**, whichever is higher.
- Other obligations, including high-risk system violations
  — up to **€15M or 3% of turnover**.
- Provision of incorrect or misleading information to
  authorities — up to **€7.5M or 1% of turnover**.

For SMEs and start-ups the caps are the lower of the two
figures rather than the higher. Member states designate
national competent authorities that share enforcement with
the AI Office at the European Commission.

## A worked classification

Consider a resume-screening SaaS used by a German retailer
to produce a ranked short-list of candidates. Recruiters
"retain full authority" and the operating manual describes
the system as an *"assistant to recruiter judgment."*

- **Art. 5?** Not prohibited — no biometric categorisation
  of sensitive attributes, no manipulative practice, no
  social scoring.
- **Annex III?** Yes — Annex III(4), employment /
  recruitment.
- **Art. 6(3) exemption?** The vendor may argue *"improves
  the result of a previously completed human activity"* or
  *"preparatory task."* Two things kill the argument:
    - Empirical evidence that recruiters follow the top
      ranking materially raises the *"influence"* concern
      of Art. 6(3)(c).
    - The system is profiling candidates — Art. 6(3) is
      **inapplicable to profiling of natural persons** in
      any case.
- **Conclusion:** High-risk under Art. 6(2) via Annex
  III(4). The Art. 6(3) argument is not available.

Exercise 01 puts five such systems in front of you.

## The failure mode

The most common classification error is *reading the
description the vendor gives and stopping there*. Vendors
have every incentive to describe systems in ways that make
Art. 6(3) look plausible. The regulator will read the
description you produced, the deployment metrics you
actually collected, and the operating manual you actually
published. If those disagree with the classification, the
classification loses.

Classify against the *operational reality*, not the
brochure.

## Summary

- The Act sorts systems into four tiers: prohibited,
  high-risk, limited-risk, minimal-risk. Tier determines
  everything else.
- Art. 5 prohibitions are categorical; no compliance
  program saves a prohibited system.
- Annex III is the operational high-risk list — memorise
  the eight areas.
- Art. 6(3) offers a narrow carve-out but is unavailable
  where the system profiles natural persons; document any
  reliance on it.
- Classify against the operational reality of the system,
  not the vendor's description.
- Transparency obligations under Art. 50 are separate,
  cheap in principle, expensive in retrofit — plan for
  them early.
