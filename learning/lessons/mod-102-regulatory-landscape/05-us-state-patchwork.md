# Chapter 5 — The US State Patchwork

## Why this chapter exists

The United States has no comprehensive federal AI statute.
In its absence, states have produced a patchwork of
AI-related laws. The patchwork is **incomplete** (most
states have no AI-specific law), **inconsistent** (states
that have laws disagree on specifics), and **growing**
(new bills appear every legislative session).

A CAIRO at a US-facing firm has to operate the patchwork
without letting it consume the program. The discipline is
narrower than it looks; the trap is to treat each new
state law as a separate compliance project.

## What the patchwork covers in 2026

The state-level landscape as of this writing. Verify each
against the current statute — states are moving faster
than any textbook can keep up with. Where the current
statute has been superseded, the statute wins.

| State | Instrument | What it does |
|---|---|---|
| California | AI Transparency Act (SB 942) | Notice and watermarking obligations for large generative AI providers |
| California | SB 243 (companion AI provisions) | Consumer-facing chatbot disclosure and companion-chatbot safety obligations |
| California | AB 2013 | Training-data disclosure for generative AI models |
| California | CCPA/CPRA + Automated Decisionmaking Technology regs | Access, opt-out, and disclosure rights around ADM |
| Colorado | Colorado AI Act (SB 24-205) | Comprehensive high-risk AI system regime (first US analogue to the EU AI Act) |
| Colorado | Div. of Insurance 3 CCR 702-10 | Insurance-sector algorithmic non-discrimination testing |
| New York | NYC Local Law 144 (city, not state) | Bias audit + notice for automated employment decision tools |
| New York | NYDFS Part 500 | Financial-services cybersecurity + AI-relevant governance |
| Illinois | AI Video Interview Act | Notice + consent for AI-analyzed video interviews |
| Illinois | HB 3773 (Illinois Human Rights Act AI amendments) | Employment discrimination liability for AI-driven decisions |
| Texas | HB 2060 (AI Advisory Council) | Informational — legislation to watch, not to comply with (yet) |
| Utah | Artificial Intelligence Policy Act (SB 149) | Notice and consumer-protection disclosures for regulated professions and generative AI |
| Tennessee | ELVIS Act | Right of publicity applied to AI-generated voice/likeness |

<!-- needs-research: continue tracking Texas, Virginia, Connecticut, Washington active AI bills that may have advanced since publication -->

Notable *federal* threads that intersect the state
patchwork:

- **Executive-branch guidance** shapes what state Attorneys
  General enforce. When the FTC signals interest in an
  AI-related practice, state AGs often follow.
- **OMB M-25-21** governs federal-agency AI use and CAIO
  designation — covered in Chapter 9.
- Federal statutes (ECOA, FCRA, ADA, Title VII, HIPAA) are
  jurisdictional overlays that apply nationwide regardless
  of the state patchwork.

## The three patterns across the patchwork

Stepping back, the state laws cluster around three shapes.
Learning the shape helps you predict what the next state
law will require without having to read it first.

### Pattern 1 — Notice and disclosure

The most common shape. The state requires that:

- Consumers be told when they are interacting with an AI
  system.
- Content generated or substantially modified by AI be
  labelled.
- Businesses disclose their AI use to regulators.

Compliance capability required: a *disclosure surface* —
the plumbing that puts a notice in front of a consumer at
the right point in the flow, in the required language.
Build this once, use it across every notice-and-disclosure
law.

### Pattern 2 — Testing and audit

The employment-focused laws (NYC LL 144, Illinois HB 3773),
the insurance regulations (Colorado Reg 10-1-1), and
increasingly the state comprehensive statutes (Colorado AI
Act) require **testing** for adverse outcomes on protected
classes and **documentation** of the testing regime.

Compliance capability required: a *bias testing
capability* — the ability to compute standard fairness
metrics on production systems on demand, with the results
reviewable by an independent auditor. Build this once, use
it across every testing-and-audit law.

### Pattern 3 — Comprehensive high-risk regime

Colorado's Consumer Protections for Artificial Intelligence
(SB 24-205), effective phased through 2026, is the first
comprehensive US state analogue to the EU AI Act. It
introduces a *"high-risk artificial intelligence system"*
category, obligates developers and deployers to use
reasonable care, requires risk-management programs and
impact assessments, and provides an Attorney-General
enforcement mechanism.

Compliance capability required: substantial. A firm that
has built to the EU AI Act (Chapters 2 and 3) has most of
the raw material, but the Colorado obligations are not the
same obligations — impact assessment content differs, the
"reasonable care" standard is a US tort-flavored construct
rather than a compliance construct, and the enforcement
authority is the state AG rather than a market surveillance
authority.

Other states have proposed similar comprehensive statutes;
watch adoption. Programs that get Colorado right will
absorb subsequent state adoptions with much lower
incremental effort.

## Federal preemption is contested

Two open questions that will shape the patchwork through
this decade:

1. **Federal preemption** — whether federal AI legislation,
   if it passes, will preempt state law is politically
   contested. The industry generally wants preemption; some
   states resist. A CAIRO cannot bet the program on
   preemption arriving.
2. **State-vs-state conflict** — different states have
   different notice requirements, different testing
   requirements, and different definitions of *"AI
   system."* The CAIRO does not resolve this; the courts
   will.

The program has to be designed to accommodate both the
current patchwork and the reasonable-worst-case future
patchwork without a rebuild.

## Operating across the patchwork

The discipline that keeps the patchwork from consuming the
program:

1. **Establish a baseline capability** for each of the
   three patterns above:
    - A disclosure surface that satisfies the
      most-stringent notice law you are subject to.
    - A bias-testing capability that satisfies the
      most-stringent audit law.
    - A high-risk risk-management program that satisfies
      the Colorado AI Act (as the current comprehensive
      leader) and the EU AI Act (as the international
      leader).
2. **Add per-state overlays** only for **substantive
   differences** — not for variations in phrasing. If
   California requires disclosure "at or before the point
   of interaction" and Utah requires it "clearly and
   conspicuously," treat that as one obligation, not two.
3. **Maintain a state-monitoring cadence** that catches
   material change without consuming the team (Chapter 8
   builds this).
4. **Do not organise the program by state.** A program
   structured as *"California team, Colorado team, NY
   team"* will lose to a program structured around the
   three underlying capabilities plus a monitoring
   function.

Exercise 05 builds the monitoring cadence.

## What the patchwork does not do

The state patchwork is largely silent on:

- **AI supply chain and dual-use risks** — no state has
  meaningful GPAI or foundation-model regulation
  comparable to EU AI Act Title V.
- **Cross-jurisdictional coordination** — states do not
  coordinate directly with EU authorities; each stands
  alone.
- **Enforcement uniformity** — some state AGs are highly
  active on AI, others are not. Enforcement risk is
  uneven.

These gaps are why the *federal* level and the *EU AI Act*
still do most of the load-bearing work in a serious US-EU
program. The state patchwork adds obligations at the
edges.

## Summary

- No comprehensive US federal AI statute (as of 2026).
  States have filled the gap with an inconsistent,
  growing patchwork.
- The patchwork sorts into three patterns: notice and
  disclosure, testing and audit, comprehensive high-risk
  regime.
- Colorado AI Act (SB 24-205) is the current
  comprehensive-regime leader; watch other states'
  adoption.
- Baseline for each pattern; per-state overlays only for
  substantive differences; do **not** organise the
  program state by state.
- Federal preemption is contested; do not bet the
  program on it.
- State patchwork is silent on GPAI, cross-jurisdictional
  coordination, and enforcement uniformity — the EU AI
  Act and federal statutes still carry most of the
  serious load.
