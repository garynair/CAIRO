# Exercise 05 — CAIRO × Compliance Officer Boundary — Reference Solution

## 1. Solution overview

The resolution is **single-intake with split
authorship**: all regulatory inbound and outbound
on AI matters flows through the CCO's existing
intake for consistency, but AI-substantive content
is authored by the CAIRO function. The CCO chairs
joint review meetings; the CAIRO function maintains
the AI-specific machinery (controls, evidence,
the AI risk taxonomy) operationally below the
regulator-facing layer. This is the same
split-authorship pattern as mod-104 Ex-04 (MRM)
and mod-107 Ex-03 (CISO), specialised for this
boundary.

---

## 2. The resolution memo

> **MEMO**
> **TO:** CEO; CC: CRO, CCO, AI Risk Council
> **FROM:** Chief AI Risk Officer (with CCO concurrence)
> **SUBJECT:** AI regulatory engagement — boundary
> resolution
> **DATE:** [date]
> **PAGES:** 2

**Resolution.** Sentinel will operate a **single
regulatory intake** through the CCO's existing
process for all AI-related regulator inbound and
outbound, with **split authorship**: the CCO's
team manages the intake, formats, approvals, and
outbound channels; the CAIRO function authors the
AI-substantive content. Joint reviews are chaired
by the CCO. The CAIRO function continues to operate
the AI-specific operational machinery (controls,
evidence, risk taxonomy, AI Risk Council
processes) below the regulator-facing layer.
This pattern is the precedent for future
AI-specific regulatory engagement.

### The CCO's position (steel-manned)

The CCO has been Sentinel's accountable function
for regulatory matters for twelve years. The CEO
and Board have confidence in the CCO's
representation of Sentinel to regulators across
all subject matters. Regulators expect a
*consistent voice* from a single firm; spreading
inbound and outbound across multiple functions
(CCO, CAIRO function, CISO, MRM) creates real risk
that Sentinel says one thing to one regulator and
something else to another. The CCO's existing
process has institutional knowledge — formatting
expectations, regulator-specific preferences,
escalation paths — that took years to develop and
would be expensive to recreate. Folding AI
regulatory engagement into the CCO's process
preserves these advantages and serves Sentinel's
interest in consistency. Where AI-specific
expertise is needed, the CCO's process can pull
in the CAIRO function as content contributor.

This position is correct on several points:

- Consistency matters; multiple voices to a
  regulator do produce inconsistency.
- The CCO's institutional knowledge and process
  maturity are real assets.
- A regulator-facing process should not be
  duplicated across functions.

### The CAIRO's position (steel-manned)

AI-related regulatory engagement is *not*
equivalent to classical compliance engagement.
The EU AI Act introduces obligations no other
regulation has addressed (Article 9 RMS, Article
73 serious incidents, post-market monitoring as
a separable artifact). NYDFS Part 500 AI
amendments require AI-specific governance evidence
the CCO's organisation does not currently
produce. CFPB AI-related inquiries are
substantively about how the model behaves and how
its outputs are explained — questions that require
AI-specific expertise to answer credibly.

If the CCO's process answers an AI-related
inquiry without AI-specific expertise, the answer
risks being *substantively wrong* — and a
substantively wrong answer to a regulator is
worse than the inconsistency the CCO is trying to
avoid. Specifically: regulator examinations probe
for inconsistency *and* substance; a substantively
weak answer signals a program that does not
understand its own obligations.

Beyond regulator-facing, the CAIRO function's
operational machinery (controls, evidence cadence,
risk taxonomy, the AI Risk Council process) needs
to remain operationally coherent below the
regulator interface. Subordinating it to the
CCO's process would either dilute the operational
discipline or impose CCO-process constraints on
operational work that doesn't need them.

### Why the resolution holds

The CCO's consistency concern is correct: Sentinel
must speak with one voice to regulators. The CAIRO's
substance concern is also correct: the voice must
say substantively correct things about AI.

The split-authorship resolution preserves both.
The CCO's process owns the *interface* — intake,
formatting, approvals, outbound channels, the
calendar of regulator commitments. The CAIRO
function owns the *substance* — the content of
AI-specific responses, the AI program's evidence
base, the AI risk register that informs answers.

Where this looks like the mod-104 MRM and
mod-107 CISO boundaries: the structural pattern
is identical. Three different functions (CCO,
CISO, MRM) all interact with the AI program at
different layers; the CAIRO function partners with
each without encroaching on any.

### Operational mechanics

- **Inbound:** All AI-related regulator inbound
  (letters, examinations, inquiries) flows
  through the CCO's intake. The CCO's intake
  team distinguishes AI-substantive content from
  general compliance content and routes
  accordingly. AI-substantive routing notifies
  the CAIRO function within 24 hours of intake.
- **Authorship:** The CAIRO function authors the
  AI-substantive sections of responses. The
  CCO's team integrates with the rest of the
  response (formatting, cover letter, supporting
  documentation). Both functions sign off on the
  final response.
- **Outbound:** Through the CCO's existing
  outbound channels (regulator-specific portals,
  contact lists, etc.). The CCO is the named
  point of contact for the regulator; the CAIRO
  function is reachable via the CCO.
- **Joint review:** A joint regulatory-response
  review meeting is chaired by the CCO,
  attended by the CAIRO function, GC, CISO,
  and MRM Lead as needed. The CCO sets the
  agenda; the CAIRO function contributes
  AI-substantive review.
- **Operational machinery:** Continues to
  operate under the CAIRO function — AI Risk
  Council, AI Review Board, evidence cadences,
  control catalogue. The CCO is briefed
  quarterly on the operational machinery; the
  CCO is not a member of the AI Risk Council
  but is a permanent invited observer.

### Precedent

Future AI-specific regulatory matters will
follow the single-intake split-authorship
pattern. The pattern applies to EU AI Act, NYDFS
Part 500 AI matters, CFPB AI-related inquiries,
and any AI-specific elements of state insurance
or sector regulators that arise. The pattern is
documented in the program charter and the CCO's
intake procedures.

### Acknowledged loss

The CCO gives up sole authorship of AI-related
regulatory content; the CCO must accept content
authored by the CAIRO function as the basis for the
regulator response. This is a real loss — the CCO
has twelve years of representing Sentinel
unilaterally on regulatory matters. The CAIRO
function gives up the option of regulator-direct
engagement on AI matters; routine inbound and
outbound flows through the CCO's process. This is
also a real loss — the CAIRO function must
coordinate calendar with the CCO's process rather
than respond directly.

Both losses are real; both are accepted as the
price of the structural correctness of the
split.

— end memo —

---

## 3. Boundary diagram

```
                  CCO scope                       CAIRO function scope
              ┌──────────────────┐             ┌──────────────────────┐
              │ Enterprise       │             │ AI risk register     │
              │   compliance     │             │ AI risk taxonomy     │
              │   program        │             │ AI Risk Council      │
              │ Compliance risk  │             │ AI Review Board      │
              │   register       │             │ AI policy hierarchy  │
              │ Regulator        │             │ AI control catalog   │
              │   intake +       │             │ AI evidence cadence  │
              │   outbound       │             │                      │
              │ Investigation +  │             │ AI-substantive       │
              │   discipline     │             │   content authoring  │
              │ Training         │             │ AI-specific risk     │
              │ Compliance       │             │   identification     │
              │   culture        │             │                      │
              └──────────────────┘             └──────────────────────┘
                       │                              │
                       └──────── Intersection ────────┘
                            (single intake +
                             split authorship)

Scenario routing:

1. EU AI Act authority letter received
   → CCO intake; routes to CAIRO function within 24h
   → CAIRO authors substantive content; CCO formats
   → CCO outbound via established channels
   → Joint review chaired by CCO; CAIRO + GC + CISO + MRM
   → CCO signs cover; CAIRO signs substantive sections

2. Routine state insurance regulator examination
   → CCO intake (no specific AI question)
   → CCO's existing process applies
   → CAIRO function informed; consulted if AI question
     emerges
   → CCO completes per existing process

3. CFPB inquiry on adverse-action AI explanation
   → CCO intake; routes to CAIRO within 24h
   → CAIRO authors substantive content on explanation
     standard, the specific decision logic, the
     mod-105 Ex-03 transparency standard
   → CCO + CAIRO joint review with GC
   → CCO signs cover; both sign substantive content

4. NYDFS Part 500 AI examination scheduled
   → CCO leads scheduling; CAIRO function pre-briefs
     CCO on AI-specific topics likely to surface
   → Joint pre-examination working session
   → On-site: CCO leads; CAIRO function attends and
     speaks to AI-substantive questions
   → Post-examination response authored split

5. Inconsistency discovered between responses
     across regulators
   → CCO + CAIRO joint review immediately
   → If substantive (AI subject matter), CAIRO
     authoritative; if procedural (formatting,
     timing), CCO authoritative
   → Reconciliation across affected regulators
```

---

## 4. Reasoning notes

- **Why the split-authorship pattern again.** Per
  the mod-104 Ex-04 and mod-107 Ex-03
  references — the structural pattern is
  reusable. Programs that have already
  established the pattern with MRM and CISO
  benefit from the precedent when negotiating
  the boundary with CCO. The pattern's
  durability across three boundary types is
  evidence that it's the right structure.
- **Why I named the consistency-vs-substance
  trade-off so explicitly.** Both concerns are
  real; the resolution preserves both. Hiding
  either concern would weaken the resolution.
- **Why the CCO becomes the named point of
  contact for the regulator.** Regulators want
  a single name; institutional memory matters.
  The CAIRO function is reachable through the CCO,
  not parallel to the CCO.
- **Why the CAIRO function still attends
  AI-specific examinations on-site.** Some
  regulator questions surface during
  examinations that require AI-specific expertise
  to answer credibly. The CCO leads; the CAIRO
  function answers AI-substantive questions
  directly when they arise.
- **What this resolution under-specifies.** The
  specific calendar of joint review meetings
  (weekly during active matters; monthly
  otherwise); the specific format of AI-
  substantive content within responses; the
  specific escalation path when a deadline
  forces faster turnaround than the joint review
  supports. Operational details downstream of
  the resolution.
- **What would change my recommendation.** If
  the CCO had recently been replaced and the
  twelve-year track record didn't apply, the
  CCO's process maturity wouldn't be as strong
  an asset, and a more CAIRO-led arrangement
  might be defensible. The reference assumes the
  CCO's tenure as stated.

---

Maintained by [Girish Nair](https://github.com/garynair)
