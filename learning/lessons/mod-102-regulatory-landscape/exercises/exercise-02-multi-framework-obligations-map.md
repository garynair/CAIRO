# Exercise 02 — Multi-Framework Obligations Map

**Estimated time**: 3 hours
**Deliverable**: A single merged obligations register +
half-page operating-conclusion memo

---

## The scenario

You are the CAIRO at **Crestbridge Group**, a 9,000-person
specialty-insurance group headquartered in London with
operations in the UK, EU (offices in Dublin), and the US
(Connecticut and California). Crestbridge is launching an
**AI-assisted underwriting workbench** for one of its lines
(specialty marine cargo). The workbench:

- Ingests submission documents (broker emails, schedules,
  shipping documents).
- Uses an LLM-based extractor to populate the underwriter's
  workbench fields.
- Runs a gradient-boosted risk-scoring model on the
  populated fields to produce a recommended premium range.
- Surfaces both the populated fields and the premium range
  to the underwriter, who retains decision authority.

The submission flow includes brokers and insureds in the UK,
EU, and the US (multi-state, including CA).

## Your assignment

Produce a single **merged obligations register** for the
underwriting workbench. The register must consolidate
obligations across at least **three regulatory regimes
simultaneously**:

1. **EU AI Act** (Crestbridge has EU operations and
   EU-resident insureds).
2. **NIST AI RMF** (Crestbridge's parent program is anchored
   on NIST per the existing CAIRO charter).
3. **One sector regulator's regime** — pick one:
   - NYDFS Part 500 + NAIC Model Law (US insurance focus)
   - UK FCA + PRA AI guidance (UK insurance focus)
   - CA Reg + state-level patchwork (US state focus)

You may add additional regimes if you think they materially
apply.

## Required structure

The register is a table:

| ID | System | Obligation | Source (regulation + article/section) | Trigger condition | Responsible business unit | Status | Evidence required |
|---|---|---|---|---|---|---|---|
| O-001 | Workbench | (e.g., Art. 9 RMS) | EU AI Act Art. 9(2) | High-risk classification under Annex III(5)(a)? | Underwriting + AI Risk | Not started | Documented RMS, residual-risk evaluation |
| O-002 | Workbench | ... | ... | ... | ... | ... | ... |

The register should have **at least 12 rows** but **no more
than 25**. Restraint is part of the exercise.

## Required memo

After the register, write a **half-page operating-conclusion
memo** addressing:

1. The **classification call** — is this system high-risk
   under EU AI Act? Defend in one paragraph.
2. The **double-coverage problem** — name two obligations
   that appear under more than one regulatory regime. How
   are you handling them (one obligation satisfies all
   regimes, or each regime gets its own evidence)?
3. The **gaps** — what obligations does Crestbridge have
   *no current capability* to satisfy? Name the top three.
4. The **first kept-promise** — what is the first concrete
   artifact you commit to producing in the next 30 days, and
   which obligation does it satisfy?

## Constraints

- Cite **specific articles / sub-functions / sections**, not
  framework names alone.
- The register **must merge** obligations across regimes,
  not replicate them. Two regimes asking for the same
  artifact is one row, not two — with both source citations.
- The memo must be honest about gaps. A register that shows
  full coverage on day one is implausible.
- Use the EU AI Act Art. 6(3) analysis from Exercise 01 if
  it applies; cite the result.

## Rubric

| Criterion | Weight |
|---|---|
| Classification call — defensible, articulated | 15% |
| Register — covers at least three regimes; ≤ 25 rows | 20% |
| Merge discipline — no row replicates an obligation across regimes | 20% |
| Source citations — specific Article / sub-function / section | 15% |
| Gap honesty — top three gaps named | 15% |
| First kept-promise — concrete, deliverable, tied to a specific obligation | 15% |

## Where to submit

`solutions/modules/mod-102-regulatory-landscape/exercise-02-multi-framework-obligations-map/SOLUTION.md`

Reference solution merges EU AI Act + NIST AI RMF + NYDFS
Part 500 / NAIC for the US insurance angle. The reasoning
notes section discusses why the UK route was rejected for
the reference (UK regulator AI posture in 2026 is more
guidance-and-supervisory than rule-and-obligation).

## Reading before you start

- [Chapter 2 — EU AI Act: risk tiers and Annex III](../02-eu-ai-act-risk-tiers.md).
- [Chapter 3 — Article 9 and the NIST crosswalk](../03-article-9-and-nist-crosswalk.md).
- [Chapter 4 — Sector-specific regulation](../04-sector-specific-regulation.md).
- [Chapter 6 — Multi-regime obligations mapping](../06-multi-regime-obligations-mapping.md) — the register discipline the exercise runs on.
- One of: NYDFS Part 500 AI amendments + NAIC Model
  Bulletin on AI / UK FCA AI guidance / CA insurance AI
  rules — depending on the sector regime you pick.
