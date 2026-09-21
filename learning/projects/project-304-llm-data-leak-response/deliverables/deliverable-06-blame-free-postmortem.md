# Deliverable 06 — Blame-Free Post-Mortem

**Target:** Days 20-30. **Length:** 8-12
pages.

## What this deliverable is

The post-mortem in the NTSB blame-free
sense per mod-110. The substantive document
of record for what happened, why, what
Northrise learned, what changes. Goes to
all of Northrise's engineering organization;
to Board; to customers (a public-facing
abstracted version is part of the
deliverable).

## What it should contain

### Public-facing abstracted version

1. **What happened.** Plain language;
   honest about the incident.
2. **What was affected.** Customer-facing
   summary of scope per Deliverable 03
   notification cohorts.
3. **What caused it.** The substantive
   causes, abstracted to what customers
   need to understand without specific
   technical implementation details.
4. **What we changed.** Per Deliverable
   05.
5. **What we learned.** The systemic
   lessons.

### Internal full version

6. **Timeline.** Day-by-day, with
   decisions and reasoning.
7. **Causal chain.** Per mod-110. Multiple
   layers of cause. The proximate
   technical bug; the development-process
   cause; the deployment-process cause;
   the detection-process cause; the
   organisational-pattern cause.
8. **What went well.** Per mod-110 — the
   parts of the response that worked.
   Sentinel's CISO conversation. The
   speed of executive response. The
   General Counsel privilege handling.
9. **What didn't go well.** Honest. The
   three previous customer tickets
   triaged as model hallucination. The
   6-week detection gap. Any internal
   process failures during the response.
10. **The CEO conversation that didn't
    happen until Day -1.** The CTO knew
    Day -2; the question of whether the
    CEO should have known sooner is real.
11. **What we are doing differently.**
    Per Deliverable 05 controls; plus
    process and organisational changes
    not captured in technical controls.
12. **The pattern that recurs.** Per
    mod-110, post-mortems that name the
    pattern (not just the instance) are
    the durable ones. Northrise's
    tenant-isolation invariants are the
    pattern; how do we treat them
    differently going forward.

### Honesty discipline

13. **What we still don't know.** Per
    mod-110.
14. **What we anticipate may surface
    later.** Customer investigations are
    ongoing; future findings possible.

## Constraints

- Blame-free. Per mod-110. Individual-
  fault framing is out of bounds. Systemic
  framing throughout.
- Honest. Performative post-mortems fail
  the discipline.
- The two-version split (public abstracted
  + internal full) preserves customer
  communication while supporting internal
  learning.
- Privilege considerations apply to the
  internal version. The public version is
  unprotected.

## Rubric

| Criterion | Weight |
|---|---|
| Causal chain depth | 25% |
| Blame-free framing | 15% |
| What went well + what didn't | 15% |
| The CEO-timing question addressed | 10% |
| Pattern (not just instance) named | 15% |
| Public version usable as customer comm | 10% |
| Honesty about what we don't know | 10% |

## Where to find help

- mod-110 §3-7 (blame-free post-mortem
  discipline; NTSB pattern).
- mod-112 §6 (honesty discipline at
  closure of work).
- mod-107 §6 (CAIRO × CISO joint authorship
  of security post-mortems).
