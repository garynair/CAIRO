# Chapter 1 — The Four Lineages of AI Regulation

## Why this chapter exists

There is no single body of "AI law." What most executives
call *AI regulation* in 2026 is the collision of four
different lineages, each with its own vocabulary, its own
enforcement style, and its own theory of what regulating AI
is for. Working CAIROs have to recognise which lineage a
given question is coming from, because the same question
about the same system gets very different answers depending
on the lineage doing the asking.

If you learn one thing from this module before you touch any
specific statute, learn the map.

## The four lineages

Each lineage has a **central organising principle** — the
thing it treats as the primary object of regulation. That
principle determines the vocabulary, the trigger conditions,
and who gets to enforce.

| Lineage | Central object | Lineage tell (vocabulary) |
|---|---|---|
| Rights-based | The affected person | *notice, explanation, contestability, adverse action* |
| Sector-based | The regulated activity | *medical device, model, insurance product, credit decision* |
| Capability-based | The AI system's technical capability | *tier, compute threshold, FLOPs, autonomy level* |
| Jurisdiction-based | The residency of the affected person or the market of placement | *applicability, extraterritorial scope, placing on the market* |

### Lineage 1 — Rights-based

Regulations whose central organising principle is **the
rights of individuals affected by automated decision-making**.
The regulation asks: was the person treated fairly, can they
understand the decision, can they contest it.

Current examples:

- **GDPR Article 22** — the right not to be subject to a
  decision based solely on automated processing that
  produces legal or similarly significant effects.
- **Equal Credit Opportunity Act (ECOA) / Regulation B** —
  disparate-treatment and disparate-impact framing applied
  to credit-decisioning models; the CFPB has treated
  algorithmic adverse-action notices explicitly under this
  frame.
- **NYC Local Law 144** — bias audit and candidate notice
  for automated employment decision tools.
- **EU AI Act, Article 27** — the fundamental-rights impact
  assessment required for certain deployers of high-risk
  systems.

Lineage tell: the regulation talks about the *affected
person*, requires notice or explanation, and creates a
contestation pathway.

### Lineage 2 — Sector-based

Regulations whose central organising principle is **the
sector the AI is used in**, with AI treated as a special
case of an existing regulated activity. The sector regulator
usually predates AI regulation by decades and reads AI
through the lens of its existing supervisory frame.

Current examples:

- **FDA Software as a Medical Device (SaMD) framework** —
  AI/ML SaMD under the medical-device regulatory frame.
- **OCC / FRB SR 11-7** — model risk management for
  banking; AI/ML models are a category of *model* under this
  supervisory guidance.
- **FRB SR 22-6** — current Fed expectations on AI/ML model
  validation, layered on SR 11-7.
- **EU Medical Device Regulation (MDR)** intersecting with
  the EU AI Act for AI medical devices.
- **NAIC Model Bulletin on the Use of AI Systems by
  Insurers** — the insurance-sector model regulation,
  state-adopted.
- **NYDFS 23 NYCRR Part 500** — cybersecurity supervision
  for NY-supervised financial services, with AI-relevant
  amendments.

Lineage tell: the regulation talks about the *activity being
regulated* — medical device, model, insurance product,
banking service — and folds AI in as a subcategory.

### Lineage 3 — Capability-based

Regulations whose central organising principle is **what the
AI system can do**, with risk thresholds tied to technical
capability levels. This is the newest lineage and the most
technically involved.

Current examples:

- **EU AI Act Title III** — the four-tier risk
  classification (prohibited, high-risk, limited-risk,
  minimal-risk) is a capability-and-context test.
- **EU AI Act Article 51** — the systemic-risk designation
  for General-Purpose AI models above a compute threshold
  (verify current implementing acts for the threshold in
  force).
- **Anthropic Responsible Scaling Policy** and analogous
  voluntary frameworks — technically self-regulation, but
  structured around capability thresholds and follow the
  same logic.

Lineage tell: the regulation talks about *capability tiers,
compute thresholds, FLOPs, autonomy levels, systemic risk*.

### Lineage 4 — Jurisdiction-based

Regulations whose central organising principle is **which
jurisdiction's residents are affected**, or **which market
the AI is placed on**, often reaching extraterritorially.

Current examples:

- **EU AI Act (Article 2)** — applies to providers placing
  AI on the EU market and to deployers using it in the EU,
  regardless of where they are established.
- **GDPR** — the original modern extraterritorial data
  framework; applies where EU data subjects are targeted.
- **California Consumer Privacy Act / CPRA and California
  AI Transparency Act** — apply to businesses that meet
  thresholds for California-resident data.
- **China's PIPL** and the associated Generative AI
  Measures — extraterritorial reach where Chinese residents
  are affected.

Lineage tell: the regulation talks about *applicability* in
geographic and residency terms, often with explicit
extraterritorial scope and often with representative /
local-representative appointment obligations.

## The lineages are not clean categories

Almost every serious AI statute belongs to more than one
lineage. The EU AI Act is simultaneously capability-based
(risk tiers), rights-based (Article 27 fundamental-rights
impact assessment), sector-based (Article 6(1) overlaps
with existing sectoral law), and jurisdiction-based
(Article 2). The value of the map is not that regulations
sort cleanly — they don't — but that a specific
*obligation* usually has a dominant lineage that tells you
which vocabulary to answer in.

When a regulator asks *"how did the affected person learn of
the decision"* they are asking a rights-based question.
When they ask *"who validated the model before it was
deployed"* they are asking a sector-based question. Same
model, same day, two different vocabularies.

## Why the map matters

Most live AI products are subject to **all four lineages
simultaneously**. A loan-decisioning model at a US bank
with California customers and EU operations sits at the
intersection of ECOA (rights-based), SR 11-7 (sector-based),
the EU AI Act (capability-based and jurisdiction-based),
and CCPA (jurisdiction-based). The mistake is to treat "AI
regulation" as one thing and design one program for it.
The discipline is:

1. Identify which lineage is asking the current question.
2. Answer in that lineage's vocabulary.
3. Keep a single obligations register that carries the
   underlying obligation once and tags which lineages it
   satisfies (Chapter 6 develops this).

Exercise 02 forces this discipline directly: you will map a
single product's obligations across three lineages in one
register.

## Concrete example — one model, four lineage reads

A gradient-boosted underwriting model at a US specialty
insurer with EU-resident insureds and California customers.

- **Rights-based read.** Does the model produce
  adverse-action notices that a customer can understand and
  contest? Does it treat protected classes lawfully?
- **Sector-based read.** Has the model been through
  validation consistent with SR 11-7 / SR 22-6 and the
  NAIC Model Bulletin on AI? Does the state insurance
  regulator have visibility into how it is used?
- **Capability-based read.** Where does it sit in the EU AI
  Act risk tiers? Is it Annex III(5) high-risk? What are
  its Article 9 risk-management obligations?
- **Jurisdiction-based read.** Which jurisdictions' laws
  apply based on where the insureds live? Do we have a
  California-facing disclosure obligation on top of an
  EU-facing conformity assessment?

Every one of those questions is legitimate. None of them is
answerable by only reading one statute. The CAIRO's job is to
hold the four reads simultaneously and produce one program
that answers all of them without contradiction.

## Summary

- Modern AI regulation is not one body of law. It is four
  lineages colliding: rights-based, sector-based,
  capability-based, jurisdiction-based.
- Each lineage has its own central object and its own
  vocabulary — recognise the lineage before answering the
  question.
- Most serious AI systems are subject to all four lineages
  at once. Design the program to answer all four; do not
  pick a favourite.
- Chapter 6 turns the map into a discipline. Exercise 02
  makes you do it on a single product.
