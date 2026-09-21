# Deliverable 05 — Trust Architecture Build/Buy Decision

**Target days:** 46–60 of the 90-day arc.
**Length:** ≤ 3 pages.
**Module integration:** mod-106 Ex-05 pattern.

---

## What this deliverable is

The CAIRO's recommendation to the CTO and Head of
Security on Northrise's trust architecture
posture for the Agent Platform — build, buy, or
partner.

This is the most architecture-laden
deliverable in the capstone. The decision
affects engineering for years.

## What it should contain

Per mod-106 Ex-05 reference solution
structure:

1. **Decision matrix.** Compare build, buy,
   and partner on at least 9 dimensions.
2. **Recommendation memo.** To CTO + Head of
   Security:
   - Recommendation in first sentence.
   - Reasoning organised around determining
     dimensions.
   - What's given up.
   - CAIRO-program-specific contribution.
   - Vendor capture analysis (if buy or
     partner).
   - Acknowledged uncertainties.

## Northrise-specific considerations

- **Customer-deployed agents.** The trust
  architecture for the Agent Platform must
  work *at customer edge*, not just at
  Northrise hub. This materially affects the
  build vs. buy calculus.
- **Engineering capacity.** Northrise's 120-
  person engineering org has substantial
  capability but isn't specialised on
  cryptographic engineering.
- **Series D pressure.** The trust
  architecture decision will be reviewed by
  enterprise customers and investors. Both
  audiences favour standards-conformant
  solutions over proprietary ones.
- **Time pressure.** Northrise needs trust
  architecture operational within ~6 months.
  Build timelines extend beyond this.

## Discipline applied

- **Vendor capture analysis** required per
  mod-106 §6.4.
- **Customer-edge consideration** explicit.
  This is a Northrise-specific dimension that
  the foundational module's reference
  doesn't address.
- **Acknowledged uncertainties** substantive.

## Rubric

| Criterion | Weight |
|---|---|
| Matrix — 9 dimensions, specific values | 25% |
| Recommendation clear, defensible | 15% |
| Customer-edge consideration explicit | 20% |
| Vendor capture analysis substantive | 15% |
| Reasoning addresses Northrise-specific factors | 15% |
| Acknowledged uncertainties | 5% |
| Length discipline — ≤ 3 pages | 5% |

## Where to find help

- mod-106 Ex-05 reference solution
  (Halverston build/buy/partner).
- mod-106 §6 (full framework).
- Deliverable 01 (charter — establishes the
  authority you're using to make this
  recommendation).

---

Maintained by [Girish Nair](https://github.com/garynair)
