# Chapter 3 — Article 9 and the NIST AI RMF Crosswalk

## Why this chapter exists

Article 9 is the heart of operational compliance for every
high-risk system under the EU AI Act. It is also the
article most CAIROs spend the most authoring time against
and the one most likely to be quoted back at you in a
regulator meeting. A CAIRO who cannot draft an Article 9
risk-management-system summary on demand will not survive
their first serious EU review.

The good news is that a NIST-anchored program already has
most of the raw material. NIST AI RMF and Article 9 are not
the same document, but the four functions of the NIST
framework map onto the four elements of Article 9 tightly
enough that a well-run NIST program can produce an
Article 9-compliant RMS with **extensions and re-framing**,
not a rewrite.

This chapter walks Article 9 element by element, shows the
NIST RMF crosswalk, and calls out the two places where the
crosswalk is *not* clean and Article 9 asks for more.

## What Article 9 requires

Article 9(1) says every high-risk system must have a **risk
management system** that is *"established, implemented,
documented, and maintained."* Four verbs, each load-bearing:

- **Established** — the RMS exists as a defined process
  before the system is placed on the market. Not
  reverse-engineered after deployment.
- **Implemented** — the process is actually run. A written
  RMS that is not executed is a documentation defect and,
  in the Act's framing, an implementation defect too.
- **Documented** — the outputs of the process are
  written down. The regulator will ask for the documents.
- **Maintained** — the RMS is a **continuous, iterative
  process** across the full lifecycle. Article 9(2)
  explicitly calls it that.

Article 9(2) enumerates what the RMS must contain:

(a) **Identification and analysis** of the known and
    reasonably foreseeable risks the system can pose to
    health, safety, or fundamental rights when used
    according to its intended purpose.

(b) **Estimation and evaluation** of the risks that may
    emerge when the system is used according to its
    intended purpose and under conditions of reasonably
    foreseeable misuse.

(c) **Evaluation of other risks** possibly arising, based
    on the analysis of data gathered from the post-market
    monitoring system (Art. 72).

(d) **Adoption of appropriate and targeted
    risk-management measures**, with explicit attention
    to **residual risk** after measures are applied.

Article 9(3) requires that risk-management measures give
due consideration to the effects of interaction with other
systems and to the deployment context. Article 9(5)
requires that the residual risks be **communicated to the
deployer** in the operating instructions (link to
Art. 13). Article 9(6) requires **testing** of the system
before it is placed on the market and, thereafter, at
appropriate points to confirm the RMS remains valid.

## The crosswalk (at a glance)

| Article 9 element | NIST AI RMF function | Illustrative sub-functions |
|---|---|---|
| Art. 9(2)(a) — Identification and analysis | MAP | MAP-1.1, MAP-2.x, MAP-3.x, MAP-5.1 |
| Art. 9(2)(b) — Estimation and evaluation | MEASURE | MEASURE-1.1, MEASURE-2.x, MEASURE-3.x |
| Art. 9(2)(c) — Post-market risk evaluation | MEASURE (feed) + GOVERN (loop) | MEASURE-4.x, GOVERN-4.3, GOVERN-5.x |
| Art. 9(2)(d) — Risk-management measures + residual risk | MANAGE | MANAGE-1.x, MANAGE-2.x, MANAGE-3.x |
| Continuous, iterative process | GOVERN | GOVERN-1.x, GOVERN-3.x |
| Art. 9(5) — Communication to deployers | GOVERN + MANAGE | GOVERN-6.x, MANAGE-4.x |
| Art. 9(6) — Testing before placement | MEASURE | MEASURE-2.3, MEASURE-2.5 |

The crosswalk is not one-for-one. NIST is a framework of
recommendations without pass/fail criteria; Article 9 is a
statutory obligation with the possibility of a market
surveillance authority reading the file. But the mapping
is tight enough that a program built on NIST can produce an
Article 9-compliant RMS by extending its existing artifacts
rather than authoring from scratch.

## Article 9(2)(a) — Identification and analysis (MAP)

What Article 9 wants: a **named list of risks** the system
could reasonably pose, tied to intended use, with the
analysis method visible.

What NIST MAP gives you: the *context* work — MAP-1.1
(intended purposes documented), MAP-2.x (system
categorisation), MAP-3.x (capabilities and limitations
documented), MAP-5.1 (likelihood and magnitude of each
identified risk). If you have run MAP well, you already
have the underlying content.

What Article 9 adds:

- The risks must be framed in terms of **health, safety, or
  fundamental rights** — not just performance or business.
  A NIST-shaped risk register that lists *"model latency
  regression risk"* is not itself an Article 9 risk;
  translate to fundamental-rights or safety terms.
- The list must be **comprehensive of reasonably
  foreseeable** risks. Silence about a known failure mode
  is a defect. If the system has ever failed, the failure
  mode goes on the list along with the mitigation.

**Practical rule:** if your NIST-shaped MAP artifacts
identify a risk that is not on the Article 9 list, the
Article 9 list has a hole. If the Article 9 list references
a risk that MAP does not, the RMS is not properly derived.

## Article 9(2)(b) — Estimation and evaluation (MEASURE)

What Article 9 wants: for each identified risk, a **method
of estimating and evaluating** it, applied both under
intended use and under **reasonably foreseeable misuse**.

What NIST MEASURE gives you: MEASURE-1.1 (metrics and
methods for measuring AI risks), MEASURE-2.x (performance
and assurance criteria), MEASURE-3.x (trustworthy
characteristics measured).

What Article 9 adds:

- **Reasonably foreseeable misuse.** NIST addresses this in
  MAP and MEASURE but does not centre it. Article 9(2)(b)
  puts misuse alongside intended use as a first-class
  evaluation lens. A red-team result showing the system
  can be jailbroken into recommending contraindicated drug
  doses is an Article 9(2)(b) exhibit even if the vendor
  never intended pharmaceutical use.
- The method must be **named**, not asserted. Writing
  *"we evaluate model performance"* is not sufficient.
  Writing *"we compute equal-opportunity difference across
  self-reported gender and race at pre-deployment, at
  every retrain, and quarterly in production"* is
  sufficient.

## Article 9(2)(c) — Post-market risk evaluation

What Article 9 wants: risks that emerge from **operational
data** collected during post-market monitoring must feed
back into the RMS.

What NIST GOVERN and MEASURE give you: GOVERN-5.x
(governance mechanisms updated with third-party feedback
and monitored performance), MEASURE-4.x (measurements
inform how the AI system is monitored and adapted).

What Article 9 adds:

- The **explicit loop from Art. 72 post-market monitoring
  into Art. 9**. Post-market monitoring is not a separate
  activity — its outputs are inputs to the RMS. If your
  post-market monitoring dashboards never feed into a
  change to the RMS or the risk-management measures, the
  loop is broken.

Article 72 is treated in operational depth in mod-110
(Incident Response); the RMS-loop framing lives here.

## Article 9(2)(d) — Risk-management measures + residual risk (MANAGE)

What Article 9 wants: for each risk, a **specific
mitigation**, and an **explicit statement** of the residual
risk that survives the mitigation.

What NIST MANAGE gives you: MANAGE-1.x (risk responses
developed), MANAGE-2.x (mechanisms in place to sustain the
system), MANAGE-3.x (third-party AI risks monitored).

What Article 9 adds:

- **Residual risk must be named.** Writing *"all residual
  risk has been mitigated to acceptable levels"* is
  defensible for a trivial system and indefensible for a
  serious one. If the system deals with health, safety, or
  fundamental rights, residual risk exists — the question
  is how you have chosen to manage it.
- **Residual risk must be communicated to the deployer**
  in the operating instructions (Art. 9(5) linking to
  Art. 13). This is the connective tissue between the
  provider's RMS and the deployer's operating decisions.

## The two places the crosswalk breaks

The NIST → Article 9 mapping is close but not clean in
two places worth naming explicitly:

1. **Named separable artifact.** Article 9 requires the
   RMS as a *documented, maintained* artifact — a thing
   the regulator can ask you to produce. NIST does not
   name any specific document. A NIST-shaped program can
   have every function running and still not have a
   summary document to hand over. If you take one
   deliverable from this chapter, take that summary
   document. Exercise 03 has you draft one.

2. **Reasonably foreseeable misuse as a first-class
   category.** NIST addresses misuse throughout but does
   not put it on the same footing as intended use. Article
   9(2)(b) does. Programs that evaluate only under intended
   use routinely find gaps on the first regulator read;
   surface reasonably foreseeable misuse in your
   evaluation plan explicitly.

## An operational template (skeleton, not solution)

An Article 9 RMS summary that would survive a first
regulator read has these six sections. Exercise 03 asks
you to draft one; use this skeleton as the outline, not the
answer.

```
### 1. System scope and classification
    - Intended purpose, deployment context, Annex III area
    - Art. 6(3) analysis if relevant

### 2. Article 9(2)(a) — Identification of risks
    - Named risks (health / safety / fundamental rights)
    - Method used to identify them
    - Link back to MAP artifacts

### 3. Article 9(2)(b) — Estimation and evaluation
    - Per-risk estimation method, named
    - Reasonably foreseeable misuse evaluated
    - Link back to MEASURE artifacts

### 4. Article 9(2)(c) — Post-market feedback
    - How Art. 72 monitoring data feeds back into the RMS
    - Trigger conditions for RMS review

### 5. Article 9(2)(d) — Measures and residual risk
    - Per-risk mitigation
    - Residual risk named, not asserted-away
    - Link back to MANAGE artifacts

### 6. Iterative governance + deployer communication
    - Cadence of RMS review
    - What Art. 13 operating instructions say to deployers
      about residual risk
```

## Summary

- Article 9 requires a continuous, iterative,
  **documented** risk-management system for every
  high-risk EU AI Act system.
- The four Article 9(2) elements map cleanly enough onto
  MAP, MEASURE, MEASURE + GOVERN, and MANAGE that a NIST
  program can produce an Article 9 RMS through extension.
- The crosswalk breaks in two places: NIST does not name
  a separable RMS artifact, and NIST does not put misuse
  on equal footing with intended use. Cover both gaps
  explicitly.
- Residual risk must be named, not asserted-away, and
  communicated to deployers via the operating
  instructions.
- Exercise 03 has you draft a one-page Article 9 RMS
  summary. Use the skeleton above as the outline.
