# Chapter 7 — Engagement Contracts: Above and Below

## Why this chapter exists

The CAIRO sits between two very different audiences.

- **Above:** the CEO, the board, and typically the risk
  committee of the board. They want decisions, not
  process; they care about materiality and defensibility.
- **Below:** the Head of AI Governance (level 60, the
  role trained by
  `head-of-ai-governance-learning`)
  and their team, plus embedded governance staff across
  the business. They want clarity on what the CAIRO is
  going to escalate, decide, and delegate.

Both relationships fail predictably when they run on
implicit understandings. This chapter is about writing
them down as **engagement contracts** — explicit,
signed, revisited artifacts that define what each party
owes the other.

An engagement contract is not a job description. A job
description says what someone *does*; an engagement
contract says how two roles *work together*, what each
delivers to the other on what cadence, what escalates
between them, and how disagreement is resolved.

## The two contracts

The CAIRO has two primary engagement contracts:

1. **Downward: CAIRO ↔ Head of AI Governance.** The
   working-level operating handshake between the
   executive and the person actually running the
   governance function day-to-day.
2. **Upward: CAIRO ↔ CEO and Board.** The strategic
   handshake between the CAIRO and the accountable
   principals for enterprise risk and strategy.

Secondary engagement contracts (with peer executives)
are Chapter 5's boundary memos, which are a different
artifact — those settle *what each of us owns*. Engagement
contracts settle *how we work together on the things we
overlap on*.

## The downward contract: CAIRO ↔ Head of AI Governance

The Head of AI Governance runs the governance function.
The CAIRO sponsors it. The line between "run" and
"sponsor" is where this contract lives.

### What the CAIRO delivers to the Head of AI Governance

- **Air cover.** When the head has to say "no" to a
  senior executive at a peer BU, the CAIRO backs the call
  publicly. When the head is wrong, the CAIRO reverses
  publicly and privately explains — never reverses
  without explanation.
- **Executive-layer access.** The head does not have to
  wait for the CAIRO to be free to escalate a fast-moving
  incident to the CEO or GC; the CAIRO establishes
  standing access with a defined SLA.
- **Budget and headcount authority.** Confirmed at
  annual planning; not renegotiated per case.
- **Strategic priorities.** The CAIRO sets the top three
  priorities for the year, in writing, before Q1
  planning; the head plans against them.
- **Regulatory and board narrative.** The CAIRO owns the
  outward story of the program. The head does not have
  to invent it under pressure.

### What the Head of AI Governance delivers to the CAIRO

- **A working program.** All GOVERN artifacts (policy
  hierarchy, RACI, review board, escalation paths)
  operational and current.
- **The risk register.** Weekly or bi-weekly rollup;
  monthly aging analysis; quarterly material-change
  summary.
- **Escalations, correctly scoped.** Cases where the CAIRO
  needs to decide, distinguished clearly from cases
  where the CAIRO just needs to be informed. False
  escalations waste executive attention; missed
  escalations produce surprise.
- **Regulator and audit interface prep.** The CAIRO signs
  the response; the head does the work.
- **Board-report inputs.** Structured, pre-committee
  drafts, on the cadence the board sets (Chapter 111 of
  the track drills into this).
- **Program metrics.** A defined dashboard of program
  health metrics, updated on a defined cadence — with
  the metrics themselves agreed with the CAIRO annually
  so they do not shift under pressure.

### The escalation ladder

A three-tier escalation ladder the head uses to
categorize cases going up:

| Tier | Meaning | CAIRO response SLA |
|---|---|---|
| **Informational** | You should be aware; no decision needed | Weekly digest |
| **Decision needed, non-urgent** | Requires CAIRO decision; not time-critical | 3 business days |
| **Immediate** | Time-critical decision or serious incident | Same business day; standing access channel |

The head decides tier; the CAIRO can re-tier down but not
up (down-tiering is fine because the CAIRO can absorb
what the head thought was important; up-tiering by the
CAIRO signals that the head under-classified, which is a
performance conversation not a mid-case correction).

### The written artifact

The contract is one page. Sections:

1. **Purpose.** One sentence — the working relationship
   this contract governs.
2. **What the CAIRO delivers.** Bullet list, above.
3. **What the Head delivers.** Bullet list, above.
4. **Cadence.** Weekly 1:1, monthly deep dive,
   quarterly business review, annual planning. Who
   drives each, what the artifact is.
5. **Escalation ladder.** The table above, filled in
   with actual channels (Slack, phone, standing hold).
6. **Change control.** How the contract is revised
   (jointly, at least annually, in writing).

Two signatures. Filed alongside the peer boundary memos
(Chapter 5).

## The upward contract: CAIRO ↔ CEO and Board

The upward contract is more constrained: the CEO and
board decide what they want. The CAIRO's job is to make
what they *should* want cheap and clear enough that they
choose it. The contract negotiates this framing.

### What the CAIRO owes the CEO and board

- **Quarterly AI risk report.** Written; three to five
  pages max. Not the raw risk register. Not a
  compliance status update. A CAIRO's *judgment* about
  where the enterprise is, what has changed, and what
  decisions are pending. Chapter 111 owns the report
  format.
- **Material-incident briefing.** Same-day for a
  material incident, per the CAIRO's definition of
  material — pre-agreed with the CEO and board.
- **Annual risk-appetite statement.** Draft
  authored by the CAIRO, adopted (or amended) by the
  board. Every material AI decision then traces back
  to it.
- **Regulator-facing posture.** The CAIRO owns the
  narrative on how the enterprise is engaging with AI
  regulators. Board can override; CAIRO owns until
  overridden.
- **A defensible "no" list.** Explicit list of AI uses
  the enterprise has chosen *not* to pursue and why.
  This is a governance artifact and a board disclosure
  artifact simultaneously.

### What the CAIRO needs from the CEO and board

- **A materiality definition.** What size of AI risk
  is a same-day briefing versus a next-quarter
  report? Cannot be discovered mid-incident.
- **Standing access.** A defined channel to the audit
  or risk committee chair for emergency escalation
  without needing to be scheduled onto an agenda.
- **Backing on peer disputes.** When a boundary
  dispute reaches the CEO (Chapter 5, level 3), a
  decision — not deferral. Deferral trains the peer
  network that the CAIRO can be worn down.
- **Explicit tolerance for judgment calls.** The CAIRO
  will be wrong sometimes. The contract needs to say,
  in writing, that being wrong on a judgment call is
  not by itself a firing offense — only failing to
  make the call, or making it without evidence, is.
- **Adopted risk appetite.** Without it, the CAIRO
  operates on inference. Chapter 111 covers the
  drafting process; this contract holds the board
  accountable for adopting *something*.

### The four boards, roughly

Different boards want different things. A rough
taxonomy:

| Board flavor | What they want from the CAIRO | What they don't want |
|---|---|---|
| Regulated-industry board (banking, insurance, health) | Compliance status *and* forward risk view; supervisory-exam readiness | Excuses; surprises |
| Public-tech-company board | Strategic narrative, disclosure counsel, competitive positioning | Program mechanics; framework theater |
| Founder-led scale-up board | Speed protection, incident-safety plan, defensible growth | Bureaucracy that slows the business |
| Public-sector board / oversight body | Statutory adherence, transparency, precedent-setting decisions | Undocumented judgment |

The engagement contract adjusts to which one you have.
Same underlying obligations; different framing.

### The written artifact

The upward contract is not always literally signed by
the board — some boards will not sign such a document.
It can be embodied as:

- A **CAIRO charter** approved by the board or risk
  committee (Exercise 02 shape).
- A **board interaction protocol** approved by the
  chair.
- A **quarterly rhythm document** the risk committee
  adopts.

Whichever form, it needs to be *written and referenced*.
A CAIRO relying on verbal understandings with the board
is one board-composition change away from having no
contract at all.

## The two contracts, joined

The CAIRO's job, viewed as a translation function:

- Downward: turns board decisions and appetite into
  program direction.
- Upward: turns program state and material judgments
  into decisions the board can make.

The engagement contracts are what let the translation
run at the right resolution. Too much detail going up
becomes program mechanics the board cannot act on. Too
much abstraction going down becomes strategic intent
the head cannot execute against.

Both contracts should be reviewed *jointly* at least
annually — the CAIRO looks at what the board has actually
been able to act on and what the head has actually been
able to execute, and the contracts get adjusted to close
the gaps.

## A worked example

A concrete case that exercises both contracts at once.

**Scenario.** A production LLM-based customer-support
agent starts producing responses that recommend a
competitor's product in specific edge cases. The head
of AI governance's team detects it in the weekly
evaluation review.

- **The head's call.** This is a program-material
  finding but not (yet) a serious incident. Under the
  escalation ladder: **Decision needed, non-urgent**
  — the CAIRO decides whether to disclose to the CEO
  now or after mitigation is scoped.
- **The CAIRO's call, per downward contract.** Reads the
  head's brief within the 3-business-day SLA. Decides:
  disclose to the CEO now (per upward contract's
  materiality definition, this crosses the "board
  should know at next report" threshold, and the CEO
  gets a heads-up before the report). Backs the head's
  scoping of "not a serious incident."
- **The CAIRO's call, per upward contract.** Sends a
  same-day informational note to the CEO. Adds a
  paragraph to the draft quarterly board report.
  Considers whether the "no" list needs updating (does
  the enterprise want to preclude AI-driven competitor
  recommendations by policy going forward?).
- **What could have gone wrong without the
  contracts.** Without the downward contract, the head
  might have not escalated at all (assuming the CAIRO
  wanted to see only serious incidents), or escalated
  as an emergency (overloading the executive channel).
  Without the upward contract, the CAIRO might have
  surprised the CEO in the quarterly report with a
  three-month-old incident, or briefed them same-day
  when a written note next week would have been
  proportionate.

The right resolution is the boring one because both
contracts are working.

## Summary

- Two engagement contracts: downward with the Head of
  AI Governance, upward with the CEO and board.
- Downward contract defines what the CAIRO delivers
  (air cover, access, budget, priorities) and what the
  head delivers (working program, register, correctly-
  scoped escalations); enforced by a three-tier
  escalation ladder.
- Upward contract defines what the CAIRO owes the board
  (quarterly report, material-incident briefing, risk-
  appetite draft, "no" list) and what the CAIRO needs
  back (materiality definition, standing access, peer-
  dispute backing, judgment-call tolerance).
- Both contracts are written artifacts, jointly
  reviewed annually. Verbal understandings survive one
  board-composition change or one executive turnover
  before they collapse.
- The CAIRO is a translation function. The contracts set
  the resolution of the translation — enough detail
  going up to enable decision, enough direction going
  down to enable execution.
