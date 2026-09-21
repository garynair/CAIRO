# Deliverable 02 — Scope and Root-Cause Analysis

**Target:** Days 2-15. **Length:** 6-10 pages
+ technical appendix.

## What this deliverable is

The substantive investigation document. Scope
analysis (which customers, what data, what
time window) and root-cause analysis (what
went wrong technically and systemically).
Goes to General Counsel for privilege-
protected handling; informs all subsequent
deliverables.

## What it should contain

### Scope analysis

1. **Affected customer set.** Which of the
   180 customers are affected (or
   potentially affected). Methodology for
   the determination. Statistical
   confidence where applicable.
2. **Affected data.** What data may have
   been disclosed. PHI? PII? Financial?
   Privileged?
3. **Time window.** When did the
   vulnerability open. When did it close
   (if closed). What query traffic during
   the window may have triggered
   inappropriate disclosure.
4. **Actual disclosure events.** Where
   logs support a determination, specific
   events where customer A's data was
   surfaced in response to customer B's
   query.

### Root-cause analysis

Per mod-110 systemic-cause discipline. The
proximate technical cause AND the systemic
causes.

5. **Proximate technical cause.** The
   specific bug. How it manifested. Why
   testing did not catch it.
6. **Systemic causes.** Per mod-110.
   What development, review, deployment,
   monitoring, and incident-detection
   patterns allowed this bug to:
   (a) be introduced;
   (b) survive code review;
   (c) deploy to production;
   (d) operate for 6 weeks without
       detection;
   (e) be detected by a customer red-team
       rather than Northrise itself.

### What we don't know

7. **Known unknowns.** Specifically what
   investigation work is in flight.
8. **Confidence levels.** Where the scope
   analysis is high-confidence vs. where
   it depends on log retention or
   estimation.

## Constraints

- Document is privileged (General Counsel
  involvement). Drafting discipline
  reflects that.
- Honest about what is not known. Premature
  closure on scope produces post-incident
  surprises.
- Root-cause must be deep. Single-line
  technical causes ("the deploy was buggy")
  fail mod-110 systemic-cause discipline.
- Trade-off: speed vs. depth. Day 15
  document is preliminary; refinement
  continues into the post-mortem
  (Deliverable 06).

## Rubric

| Criterion | Weight |
|---|---|
| Scope methodology sound | 20% |
| Affected-customer determination | 15% |
| Affected-data classification | 15% |
| Systemic causes substantive (per mod-110) | 25% |
| What we don't know named | 15% |
| Privilege-aware drafting | 10% |

## Where to find help

- mod-110 §3-4 (systemic-cause discipline).
- mod-107 §5 (security investigation
  methodology).
- mod-108 §3 (breach scope analysis).
- mod-104 patterns (joint CAIRO-CTO
  investigation discipline).
