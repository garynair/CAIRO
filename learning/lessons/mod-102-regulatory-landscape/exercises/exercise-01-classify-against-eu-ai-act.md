# Exercise 01 — Classify Five Systems Against EU AI Act Annex III

**Estimated time**: 3 hours
**Deliverable**: Classification table for five hypothetical
systems + reasoning per system (one page total)

---

## Why this exercise exists

The EU AI Act's risk tier is the single most important fact
about any AI system you operate in the EU. Tier determines
the obligations; obligations determine the program. A CAIRO
who cannot classify systems quickly and defensibly will spend
the first year of the role consulting external counsel on
every classification, which is both slow and expensive.

This exercise builds the classification skill on five
deliberately edge-case systems.

## The five systems

For each, you have a one-paragraph description. You will
classify each as **prohibited**, **high-risk**, **limited-risk**,
or **minimal-risk** under the EU AI Act, citing the relevant
Article and (where applicable) Annex III area.

### System A — Resume-screening assistant

A SaaS tool used by a 5,000-person retail chain in Germany.
The tool ingests CVs submitted to job postings and produces a
ranked short-list of "best-fit" candidates for the recruiter
to consider. The recruiter retains full hiring authority and
the system's ranking is described in the operating manual as
"an assistant to recruiter judgment." 90% of recruiters
report following the system's top recommendation in interview
slot allocation.

### System B — Customer-service chat agent

A consumer-facing LLM-based chat agent on a Spanish bank's
website. Handles balance inquiries, transaction explanations,
and dispute initiation. Does not approve credit, does not
make adverse decisions about customers. Identifies itself as
an AI assistant at the start of every session.

### System C — Worker-attention monitor

An in-cab AI system installed in trucks of a Polish logistics
firm. Uses the cab camera to detect signs of driver
inattention or fatigue. Triggers an in-cab audio alert and
logs events to fleet management. Used for driver coaching and
in disciplinary processes.

### System D — Predictive-maintenance model

A model running on aircraft engine telemetry at a UK aviation
services firm. Predicts component failure 100 flight hours in
advance. Output is a maintenance recommendation reviewed by
licensed aviation engineers; no automated action is taken on
the aircraft.

### System E — Triage support in an emergency department

An AI system in use at a hospital in the Netherlands. Reads
incoming patient vitals and chief complaint at intake and
suggests an ESI (Emergency Severity Index) level. Triage
nurses retain decision authority. The hospital's clinical
quality team measures override rates monthly.

## Your assignment

Produce a classification for each of the five systems with:

1. **The risk tier** (prohibited, high-risk, limited-risk,
   minimal-risk).
2. **The Article + Annex citation** that supports the
   classification.
3. **The Art. 6(3) analysis** if relevant — does the system
   fall within an Annex III area but qualify for the
   exemption?
4. **Two-sentence reasoning** per system: the key fact that
   determined the tier.
5. **What would change the tier** — what fact in the system
   description, if changed, would move the system to a
   different tier?

Produce one classification table:

| System | Tier | Article(s) | Annex III area | Art. 6(3) applies? | Key fact |
|---|---|---|---|---|---|
| A — Resume screening |  |  |  |  |  |
| B — Bank chat agent |  |  |  |  |  |
| C — Driver monitor |  |  |  |  |  |
| D — Engine predictive maintenance |  |  |  |  |  |
| E — ED triage support |  |  |  |  |  |

Followed by a half-page of reasoning that addresses item 5
for each system.

## Constraints

- Cite **specific** Articles and Annex III areas (e.g., "Art.
  6(2) via Annex III(4)", not "the EU AI Act high-risk
  provisions").
- For Art. 6(3) analysis, name **which** of the four
  exemption conditions you are relying on.
- If a system is on the boundary, **classify it conservatively
  and explain the conservatism**. Conservative classifications
  cost time; aggressive classifications can cost the EU
  market.
- Do not consult any pre-built classification database. The
  point is the skill, not the lookup.

## Rubric

| Criterion | Weight |
|---|---|
| Tier choice — correct or defensibly close | 35% |
| Article/Annex citation — specific, accurate | 25% |
| Art. 6(3) analysis — applied where relevant, explicit reasoning | 15% |
| Key-fact identification — the determinative fact is named | 15% |
| "What would change the tier" — surfaces a real alternative classification | 10% |

## Where to submit

`solutions/modules/mod-102-regulatory-landscape/exercise-01-classify-against-eu-ai-act/SOLUTION.md`

Reference solution available there. As with mod-101
exercises, defensible classifications can vary; score
yourself on the rubric.

## Reading before you start

- [Chapter 2 — EU AI Act: risk tiers and Annex III classification](../02-eu-ai-act-risk-tiers.md).

EU AI Act:

- Art. 5 (prohibited practices)
- Art. 6 (high-risk classification rules) + Annex III
  (high-risk areas)
- Art. 50 (transparency obligations / limited-risk)

The Act text is the authoritative source. If a third-party
guide disagrees, the Act wins.
