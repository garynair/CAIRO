# Chapter 6 — Multi-Regime Obligations Mapping

## Why this chapter exists

Every real AI product is subject to more than one
regulatory regime at once. The mistake is to build a
separate compliance workstream for each — one for the EU
AI Act, one for SR 11-7, one for CCPA, one for NAIC. That
structure produces:

- **Double-counting** — the same underlying obligation is
  worked twice under two different names.
- **Missing load-bearing obligations** — an obligation that
  belongs to more than one regime is assumed to be
  covered by the other workstream and is done by neither.
- **Programme sprawl** — headcount grows one workstream at
  a time until nobody can hold the whole map in their
  head.

The discipline is the opposite. **One product, one merged
obligations register.** The register lists each
underlying obligation once and tags every regime that
requires it. Each row has one owner. Each row has one
evidence artifact. Ownership does not follow the regulator;
it follows the obligation.

This chapter builds the register discipline. Exercise 02
makes you author one.

## The register format that works

One row per **(regulation, system, business unit)** triple.
The same underlying obligation appears in multiple rows if
it applies to multiple systems or business units — but the
same regulation on the same system on the same business
unit is *one row*, no matter how many articles cite it.

| Field | What it holds |
|---|---|
| ID | Stable identifier (e.g., O-034) |
| System | The AI system this obligation attaches to |
| Business unit | Who owns the system |
| Obligation (plain English) | What has to be true, in one sentence |
| Sources | All the citations that impose this obligation — Article, section, sub-function |
| Trigger condition | The fact about the system that triggers the obligation |
| Responsible role | The role accountable for producing evidence |
| Status | Not started / in progress / met / stale |
| Evidence required | The artifact that demonstrates the obligation is met |
| Last reviewed | When the row was last touched |

Two design choices to note:

- **Sources column is plural.** One row can cite EU AI Act
  Article 9(2)(d), NIST MANAGE-1.3, and NYDFS Part 500 §7
  simultaneously if all three impose the same underlying
  obligation. The plural sources column is what prevents
  double-counting.
- **Responsible role is singular.** If two roles could own
  it, pick one. Shared ownership without a lead is
  unowned.

## Filling the register — the four-lineage sweep

The reliable way to fill the register on a new product is
to sweep the product through each of the four lineages
from Chapter 1, in order, and add rows as you go.

1. **Rights-based sweep.** Who is affected by this
   system's decisions? What rights do the affected persons
   have — under GDPR Art. 22, ECOA, CCPA/CPRA, state
   privacy laws? Add rows.
2. **Sector-based sweep.** What sector does this product
   live in? What sector regulation applies? SR 11-7?
   NAIC? FDA? NYDFS Part 500? Add rows.
3. **Capability-based sweep.** Where does this product sit
   in the EU AI Act risk tiers? What Article 9 / 10 / 11 /
   43 / 50 / 72 / 73 obligations attach? If it uses a
   GPAI model, does Title V pull in? Add rows.
4. **Jurisdiction-based sweep.** Which jurisdictions'
   residents are affected? Which markets is the product
   placed on? What extraterritorial reach applies? Add
   rows.

After the sweep, **deduplicate** by underlying obligation.
If the rights sweep and the sector sweep both surfaced an
adverse-action-notice obligation, that is one row with two
sources — not two rows.

## Deduplication rules

Two rows collapse into one when *all* of the following are
true:

- They attach to the **same system**.
- They attach to the **same business unit**.
- The **underlying obligation is the same** — the same
  artifact, produced by the same role, would satisfy both
  citations.

Two rows do **not** collapse when:

- The citations require different evidence artifacts
  (e.g., EU AI Act Art. 11 Annex IV technical
  documentation versus SR 11-7 model development
  documentation — the content overlaps but the artifacts
  are different).
- The citations require different cadence or scope of
  evidence (annual bias audit under NYC LL 144 vs.
  Colorado life insurance quantitative testing — both
  fairness tests, different frequencies and metrics).

When in doubt, keep them separate and revisit at the next
review. Two rows that could have been one is a smaller
error than one row that hid a distinct obligation.

## The "who counts as provider vs deployer" question

Under the EU AI Act, obligations depend heavily on whether
you are a **provider** (the entity placing the system on
the market) or a **deployer** (the entity using it). The
same firm can be both simultaneously for different
systems, and the obligations register has to know the
difference row by row. A CAIRO who lets *"we're a deployer,
not a provider"* live at the program level rather than the
row level will end up with wrong obligations on the wrong
rows.

Two default rules to keep the register clean:

- **Any system built in-house is a provider role**, even if
  the deployer is also in-house. Log the obligations
  accordingly.
- **Any GPAI model integrated into a high-risk system**
  can move the integrator into provider-like territory
  under Art. 25. Flag such rows for legal review.

## The register is the source of truth — for the CAIRO

The obligations register is the primary artifact the CAIRO
owns for regulatory work. When the board asks *"what do
we owe regulators"*, the register is the answer. When the
regulator asks for a status update, a filtered view of the
register is the response.

Two consequences:

1. The register lives in a system of record that survives
   personnel changes. A spreadsheet on a personal drive
   fails on the first CAIRO transition. A dedicated GRC tool
   or a governed shared workspace with change history is
   the minimum.
2. The register is **auditable**. Every row change has a
   timestamp, an author, and a reason. Internal audit
   (third line) will ask for the change history when they
   test the register; if it does not exist, the register
   is not evidence.

## Common failure modes

- **Register by regulator.** Rows organised
  primarily by which regulator cares. This structure
  double-counts and hides the underlying obligation. Fix
  by re-keying to (regulation, system, business unit) and
  making sources plural.
- **Register without triggers.** Rows that assert an
  obligation without naming the fact about the system that
  triggers it. When the system changes, nobody knows
  whether the row still applies. Fix by adding the trigger
  condition column and reviewing at every material system
  change.
- **Register without owners.** Rows in *"AI Risk"* or
  *"Compliance"* generically. The obligation is unowned.
  Fix by naming a specific role.
- **Register without cadence.** Rows marked *"met"* with
  no review date. The obligation drifts into staleness
  quietly. Fix by requiring a *last reviewed* date and
  reviewing rows on a rolling schedule.

## Restraint is part of the discipline

Registers with 200 rows for a single product are almost
always over-decomposed. If a rows are near-identical
except for the citation, collapse them and expand the
sources column. If a row is trivial (the system logs
system events), it does not belong in the register — it
belongs in the operational runbook. Reserve the register
for obligations that the regulator will ask about.

Exercise 02 sets a range of **12 to 25 rows** for a
mid-complexity product. The lower bound guards against
under-decomposition; the upper bound guards against
overreach.

## Summary

- One product, one merged register. Rows are keyed to
  (regulation, system, business unit); sources are
  plural.
- Fill the register by sweeping the product through the
  four lineages; deduplicate on underlying obligation, not
  citation.
- Distinguish provider vs deployer role row by row —
  never at the program level.
- The register is the CAIRO's source of truth. It lives in
  a system of record with change history. Rows have
  owners, triggers, evidence, and review dates.
- Restraint matters. Registers with too many rows fail
  the same way registers with too few rows fail — they
  stop being usable.
