# Exercise 01 — Build an AI Risk Taxonomy

**Estimated time**: 3 hours
**Deliverable**: A one-page taxonomy + a half-page
reasoning note

---

## The scenario

You are the CAIRO at **Halverston Capital**, a $40B asset
manager with three lines of business:

- **Public markets** (equity + fixed income) using
  systematic strategies that include ML-derived signals.
- **Private credit** with an AI-assisted underwriting
  workbench (similar in shape to the Crestbridge workbench
  in mod-102 Exercise 02, but for private credit
  origination).
- **Wealth advisory** using a third-party LLM-based
  customer-conversation assistant in the advisor
  workstation.

Halverston has an existing **enterprise risk taxonomy** from
the CRO with six top-level categories: Market, Credit,
Operational, Compliance, Liquidity, Strategic. The CRO has
asked you to author an **AI risk taxonomy** that:

1. Captures AI-specific risks the existing taxonomy
   under-covers.
2. Maps cleanly into the existing enterprise categories so
   the board can see AI risk roll up.
3. Is operationally usable across the three lines of
   business.

## Your assignment

Produce a one-page AI risk taxonomy with:

1. **Top-level categories** — 7 to 9 maximum (per
   Chapter 2's *small enough to remember* principle).
2. **For each top-level category**: a one-sentence
   definition + 2 to 4 sub-categories.
3. **A mapping column** that maps each AI-top-level into
   the existing enterprise category it primarily rolls up
   into. Each AI top-level maps to *one* enterprise
   category (mutually exclusive at the top level).
4. **A "where it applies" annotation** — which of the
   three lines of business each top-level category is
   most material to.

After the taxonomy, write a half-page reasoning note
addressing:

1. The hardest call. Where two AI risks could plausibly be
   split or combined, why did you go the way you did?
2. The mapping to the enterprise taxonomy — was any
   AI-top-level *not* a clean fit, and how did you handle
   the seam?
3. What you deliberately **left out**. Restraint is part
   of the exercise.

## Required structure

A single table:

| # | AI top-level category | One-line definition | Sub-categories | Enterprise roll-up | Public mkts | Private credit | Wealth advisory |
|---|---|---|---|---|---|---|---|
| 1 |  |  |  |  |  |  |  |
| ... |  |  |  |  |  |  |  |

Followed by the reasoning note.

## Constraints

- **7 to 9 top-level categories.** Hard limit.
- Each top-level category **must** roll up to exactly one
  enterprise category. No splits.
- Sub-categories: 2 to 4 per top-level. Resist three-level
  taxonomies (per the taxonomy-mistakes list in
  Chapter 2).
- The "where it applies" annotation must distinguish *material*
  applicability from *technical* applicability. Privacy risk
  applies technically to all three; it is most material to
  one of them.
- The reasoning note must name **what you left out**, not
  only what you included.

## Rubric

| Criterion | Weight |
|---|---|
| Top-level count discipline (7–9) | 10% |
| Mutual exclusivity at top level | 20% |
| Enterprise roll-up — every AI-top maps to one ent-top | 20% |
| Sub-categories — concrete, 2–4 per category | 15% |
| "Where it applies" — distinguishes material from technical | 15% |
| Reasoning note — names the hardest call honestly | 15% |
| Restraint — names what was left out | 5% |

## Where to submit

`solutions/modules/mod-103-ai-risk-frameworks/exercise-01-build-an-ai-risk-taxonomy/SOLUTION.md`

Reference solution available. The reference uses 8 AI
top-level categories and explicitly leaves out a
"Catastrophic risk" category that would otherwise be added
in a frontier-AI context — the reasoning explains the
choice.

## Reading before you start

- Chapter 2 (AI Risk Taxonomy as the Unifying Spine),
  especially the *starting taxonomy* table and the
  *adapting the taxonomy* section.
- mod-101 Chapter 3 (Three Lines of Defense), to
  understand how the taxonomy plays with second-line
  ownership.
- Chapter 8 §3 (category-level tolerances) — the
  taxonomy you produce here is the vocabulary the
  appetite statement will use. Categories with no
  plausible tolerance line are a sign to consolidate.
