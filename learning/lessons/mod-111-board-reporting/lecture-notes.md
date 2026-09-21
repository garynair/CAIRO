# Module 111 — Lecture Notes

About 90 minutes of reading. §2 (risk appetite
statement) is the most operationally
consequential section; §5 (the CAIRO at the board
table) is the most context-specific.

---

## §1. What boards actually need

The most common CAIRO board-reporting failure mode
is **over-reporting** — producing a 40-page
quarterly pack that nobody reads. The discipline
this module teaches starts with understanding what
boards actually need, which is much less than CAIROs
typically produce.

### 1.1 What boards do

Boards exercise oversight. They do not manage.
The distinction matters operationally:

- **Management** decides how to allocate
  resources, design processes, run operations.
- **Oversight** determines whether management is
  doing the above competently and accountably.

The CAIRO reports to the board's *oversight*
function. The board needs the information that
lets it exercise oversight — not the information
that would let it manage.

### 1.2 What boards need from the CAIRO

Four things, in order of importance:

1. **The risk posture.** What's the program's
   current view of AI risk across the
   organisation? What's changed since last
   quarter?
2. **Material exceptions.** What's not within risk
   appetite right now? What's the response?
3. **Material decisions pending.** What does the
   board need to decide or ratify? What's the
   recommendation?
4. **Material changes ahead.** What's
   foreseeable that the board should be aware
   of (regulatory, market, organisational)?

That's it. Four things. Programs that produce
quarterly reports with much more than this are
producing operational reports for management
consumption — using the board's calendar.

### 1.3 What boards don't need from the CAIRO

Equally important:

- **Operational metrics in detail.** Boards don't
  need to know that the trust-gate p99 latency was
  47ms. They need to know whether the trust
  architecture is operating per policy.
- **Process descriptions.** Boards don't need to
  understand the structural design of the audit
  ledger. They need to know whether evidence
  exists when called for.
- **Technology details.** Boards don't need to
  know the foundation model version. They need to
  know whether vendor governance is operating.
- **Educational content.** Boards don't need the
  CAIRO to teach them about AI generally. They
  need the specific decisions and trade-offs
  this organisation is making.

### 1.4 Why the over-reporting failure mode persists

Despite this, CAIRO board reports are routinely too
long. Three patterns:

- **Insurance against criticism.** The CAIRO
  defends against the implicit accusation that
  the board wasn't informed by producing
  comprehensive reports. The report is
  insurance, not communication.
- **Demonstration of effort.** A long report
  demonstrates that the CAIRO function is busy. A
  short report invites the question of whether
  the function is needed.
- **Misunderstanding of audience.** The CAIRO
  produces a report at the level of management
  consumption rather than oversight.

A CAIRO who can produce a 3-page quarterly board
report and defend its completeness has the
discipline this module teaches.

---

## §2. The AI risk appetite statement

The single most important document the CAIRO
produces for the board is the **AI risk appetite
statement**. It is the document the board adopts
that says, in board-readable language, *how much
AI risk this organisation is willing to take.*
Every other governance artifact downstream of the
board derives from this.

### 2.1 What a risk appetite statement is

A risk appetite statement:

- Names the categories of AI risk the
  organisation faces.
- For each, expresses the organisation's
  appetite — how much of this risk the
  organisation will take.
- Establishes the boundary between acceptable
  and unacceptable.
- Names the process for handling cases that
  approach or exceed the boundary.

The statement is **adopted by the board**, not
authored by the board. The CAIRO authors; the
board reviews and ratifies; the program operates
against the ratified statement.

### 2.2 What a risk appetite statement is not

Honest distinctions:

- **Not a risk tolerance.** Tolerance is what the
  organisation can withstand; appetite is what
  the organisation chooses to take. The two
  often differ.
- **Not a control catalogue.** Controls
  operationalize appetite; they are downstream.
- **Not a list of metrics.** Metrics measure
  whether the program is within appetite; they
  are downstream.
- **Not a policy.** Policies derive from the
  appetite; the appetite is the source.

### 2.3 The structure that works

A working AI risk appetite statement has these
elements:

1. **Preamble.** What AI risk means at this
   organisation; what this statement does.
2. **Risk categories.** Drawn from the program's
   AI risk taxonomy (mod-103 §2).
3. **For each category, the appetite.** Expressed
   in board-readable language with concrete
   boundaries.
4. **The escalation process.** What happens when a
   case approaches or exceeds the boundary.
5. **The review cadence.** When the board
   reconsiders the statement.

### 2.4 Expressing appetite in board-readable language

The hardest practical problem: appetite is
inherently fuzzy and the board needs to be able
to act on it. Three patterns that work:

**Pattern 1 — Risk-class language.** "We accept
material model-performance risk where the
business case justifies it and validation
demonstrates fitness for purpose. We do not
accept performance risk that materially affects
customers without explicit customer-experience
review."

**Pattern 2 — Boundary language.** "The
organisation will not deploy AI systems that
produce binding adverse decisions for which we
cannot provide affected-party explanations
meeting Reg B / GDPR Art. 22 standards."

**Pattern 3 — Threshold language.** "Bias risk
appetite: equalized-odds gap > 5 percentage
points across protected classes is outside
appetite for any Tier 1 system; sustained
crossing requires AI Risk Council remediation."

A working statement uses all three patterns —
risk-class framing for the overall category,
boundaries for the categorical limits, thresholds
for the operational triggers.

### 2.5 The hardest categories

Some risk categories are harder than others to
express appetite for:

- **Bias and fairness.** The mod-105 impossibility
  result (§3.2) means appetite cannot simultaneously
  cover all fairness conceptions. The statement
  must name which conceptions take priority.
- **Reputational risk.** Reputational risk is
  inherently subjective. The statement names the
  *kinds* of reputational risk the organisation
  will not accept (rather than thresholds).
- **Strategic risk.** Strategic appetite is
  inherently directional; the statement frames
  it as "we will / will not pursue X" rather
  than as bounded thresholds.

### 2.6 Drafting the appetite

A working drafting process:

1. CAIRO + AI Risk Council draft.
2. Pre-circulation to CRO, CFO, CCO, GC for
   substantive review.
3. Pre-circulation to Audit Committee chair and
   Board Risk Committee chair for read-out
   before the full board.
4. Board review and adoption (typically over 1-2
   board cycles).
5. Annual review by the board.

The pre-circulation steps matter. Boards do not
want to be the first audience for a substantive
new document; pre-circulation lets the document
arrive at the board having already been
sharpened by peer review.

---

## §3. Quarterly board reporting

The quarterly board report is the operational
artifact connecting the program to the board.
This is the document where the over-reporting
failure mode lives or dies.

### 3.1 The structure that works

A working quarterly board report is **3 to 5
pages** and includes:

1. **Risk posture summary** (½ page).
   Aggregate view of the program by risk
   category, with change-from-last-quarter
   indicators.
2. **Material changes** (½ page). What has
   changed in the trailing quarter that the
   board should know.
3. **Material exceptions** (1 page). Cases
   outside risk appetite, with the response
   and the timeline.
4. **Material decisions pending** (½ page).
   What the board needs to decide.
5. **Material changes ahead** (½ page).
   Regulatory, market, organisational changes
   the board should be aware of.
6. **Asks** (½ page). What the program needs
   from the board (ratifications, resource
   approvals, charter changes).

Anything else goes in appendices that the board
doesn't need to read unless it asks. Appendices
might include: detailed metrics, incident
register, vendor register, gap analyses. They
exist for reference, not for reading.

### 3.2 The "asks" discipline

The most underused section is "Asks." A working
CAIRO leaves the board meeting having received a
specific answer to a specific question.

A board report without asks signals one of two
things:

- The CAIRO believes the program needs nothing
  from the board (rarely true).
- The CAIRO has not asked clearly (commonly
  true).

The discipline: every quarterly report has at
least one ask. The ask might be small
(ratification of an updated risk appetite
threshold) or large (approval of a new
operating-model investment). The board needs to
practice being asked things; if the CAIRO never
asks, the board's reflex when an ask does come
is "why now?"

### 3.3 The honesty discipline

The single biggest failure of board reports is
softening the bad news. A report that
systematically presents the program as healthy
when it is struggling produces a board that
discovers reality from external sources — a
regulator, a peer institution, a media
incident. That discovery is much more damaging
than the originally bad news would have been.

The discipline: when the program is struggling,
say so specifically. Boards are professional
audiences; they expect bad news to surface and
they respect the executive who delivers it
honestly.

### 3.4 The cadence and the off-cycle update

Quarterly is the standard cadence for board
reporting. But material incidents (per mod-110)
and material decisions in flight may require
**off-cycle updates**:

- **Board Risk Committee chair briefings.**
  Brief the chair when something material is
  happening; let the chair decide whether to
  convene early.
- **Executive session updates.** Updates to a
  smaller body (Audit Committee or Risk
  Committee) without going to the full board.
- **Pre-meeting briefings.** Brief the chair
  before the meeting on items that will be
  discussed; surprises at the meeting are
  unwelcome.

A CAIRO who never briefs off-cycle is either not
encountering material events or is hiding them.

---

## §4. Materiality

The hardest practical question in board reporting:
*does this matter to the board?* Programs without
a materiality framework either flood the board
with non-material items or hide material items
the board should know.

### 4.1 What materiality means

Materiality is the threshold at which something
is *important enough* to require board
attention. It is a judgment, not a calculation,
but it can be structured to make the judgment
defensible.

The classical materiality test (from financial
accounting): something is material if a
reasonable user of the information would make a
different decision if they knew it. Applied to
AI board reporting: something is material if the
board would have a different view of the
program's risk posture, or take different
oversight action, if it knew.

### 4.2 The materiality dimensions

For AI matters, materiality has multiple
dimensions:

- **Financial.** Would this affect the
  organisation's financial results
  materially?
- **Regulatory.** Would this trigger regulatory
  action, fines, or enforcement?
- **Reputational.** Would this affect the
  organisation's public reputation if it
  surfaced?
- **Operational.** Would this affect core
  operations (downtime, customer service,
  internal processes)?
- **Strategic.** Would this affect the
  organisation's strategic direction or
  long-term posture?

A matter that crosses any of these dimensions
at sufficient magnitude is material.

### 4.3 The threshold framework

A working materiality framework has, for each
dimension, a threshold above which matters are
considered material. The framework should be
*calibrated* to the organisation's size and
context — what's material at a $1B firm is
different from what's material at a $100B firm.

A simple framework structure:

| Dimension | Threshold | Examples |
|---|---|---|
| Financial | > 1% of annual revenue or > $X | An AI incident producing $X+ in customer remediation; an AI-related regulatory fine |
| Regulatory | Any regulator-initiated action; EU AI Act Art. 73 incident | OCC examination finding; CFPB inquiry |
| Reputational | Public exposure or potential exposure | Media coverage of an AI incident; customer-facing incident affecting > Y customers |
| Operational | Multi-system outage; customer-affecting incident > Z duration | Trust gate outage; vendor LLM outage |
| Strategic | Material change in AI program direction | Decision to enter / exit a major AI use case; major vendor change |

The framework is **calibrated** to the specific
organisation — these are pattern thresholds, not
the answer.

### 4.4 The materiality decision

For each potential matter, the CAIRO function
applies the framework. Three outcomes:

- **Clearly material.** Reaches the board pack
  for the next regular meeting (or off-cycle if
  warranted).
- **Clearly non-material.** Operates internally
  to the CAIRO function; appears in appendices if
  relevant.
- **Boundary case.** The CAIRO function consults
  with CRO and Board Risk Committee chair on
  whether to escalate.

The boundary-case discipline is the most
important. Pretending material items are not is
the failure mode that produces post-hoc board
embarrassment. The boundary-case consultation
prevents this without flooding the board.

### 4.5 The escalation of boundary cases

A working boundary-case escalation:

- Within 5 business days of recognising the
  matter as boundary, brief the CRO.
- Within 10 business days, brief the Board Risk
  Committee chair.
- Disposition: include in next regular board
  pack; raise off-cycle; or stand down.

The disposition is captured in the program's
evidence ledger; the boundary-case audit trail
matters when the matter later proves to have been
material.

---

## §5. The CAIRO at the board table

Whether the CAIRO sits at the board table depends
on the organisation. In many firms, the CAIRO
attends Board Risk Committee meetings as a
permanent invitee but is not a member; in some
firms, the CAIRO presents formally at quarterly
meetings; in a few firms, the CAIRO has a direct
relationship with the full Board.

The CAIRO needs to operate effectively at whatever
level of board interaction the role has.

### 5.1 The CAIRO's role at the table

When the CAIRO is present:

- **Present the report.** The report should be
  pre-read; the CAIRO's presentation is
  highlights and emphasis, not full read-out.
- **Answer questions specifically.** Board
  questions deserve specific answers; "I'll get
  back to you" is acceptable for facts
  unknown but not for substantive matters.
- **Surface emerging issues.** The CAIRO is in the
  room as a substantive contributor; if the
  discussion is missing an angle the CAIRO can
  contribute, the CAIRO should.
- **Make asks.** The asks section of the report
  is presented and the board is given the
  opportunity to act.

### 5.2 The honesty discipline at the table

Boards are sophisticated. The CAIRO's credibility
depends on being honest about what is known,
what is uncertain, and what is unknown. Three
patterns to avoid:

- **Overclaiming.** "Our trust architecture is
  fully effective against prompt injection."
  Almost certainly false; the board will discount
  the rest of the CAIRO's input.
- **Hedging.** "It's hard to say; depends on
  several factors." The board needs a position;
  hedging is a non-answer.
- **Education-as-answer.** The board asks a
  specific question; the CAIRO answers with a
  textbook overview of the topic. The board
  walks away with no answer to its question.

The discipline: give specific answers when you
have them; honestly say "I don't know — I will
report back by [date]" when you don't.

### 5.3 The disagreement discipline

When the CAIRO disagrees with another executive or
with a board member's framing, the CAIRO must
say so. mod-105 §6.5 (naming a disagreement)
applies here directly. Three patterns:

- **The respectful direct.** "I see this
  differently. My view is X because Y. I think
  the position you've outlined would lead to Z."
- **The bounded.** "I agree on most points but
  disagree specifically on [point]. The
  alternative would be [position]."
- **The provisional.** "I want to think through
  this before committing. My initial view is X,
  but I'll come back to you by [date] with a
  considered position."

Boards respect the discipline. They lose
confidence in CAIROs who never disagree (signals
weak substantive position) and in CAIROs who
disagree on everything (signals weak
collaborative posture).

### 5.4 Confidentiality

Board discussions are confidential. The CAIRO's
ability to operate substantively at the board
table depends on never being the source of
leaks. Even within the CAIRO function, board
substance is shared only on need-to-know;
verbal-only briefings to the AI Risk Council
about board decisions are typical practice.

The discipline holds even when the CAIRO is asked
informally what the board thinks. The answer is
"I'm not at liberty to discuss board
deliberations." Programs where the CAIRO is loose
with board confidentiality lose access quickly.

---

## §6. Annual self-assessment

Once a year, the CAIRO function conducts a
self-assessment of the program. This is the
program's chance to honestly survey what's
working and what isn't, free of incident
pressure and free of audit calendar.

### 6.1 The self-assessment vs. the audit

The self-assessment is *not* an internal audit.
Internal audit is third-line (mod-101 §3); it is
independent of the CAIRO function. The
self-assessment is the CAIRO function's own
honest review of itself.

The two complement each other: the
self-assessment surfaces issues the audit may
miss because audit is constrained by its
methodology; the audit surfaces issues the
self-assessment may not surface because the
self-assessment can be self-serving.

### 6.2 What the self-assessment covers

A working self-assessment covers:

1. **Program maturity** against a defined
   maturity model (NIST AI RMF maturity, ISO
   42001 readiness, sector benchmarks).
2. **Operating effectiveness.** Are the
   controls operating; what does the evidence
   show.
3. **Coverage gaps.** What's not yet covered
   that should be.
4. **Investment posture.** Is the program
   investing in the right areas;
   under-investing in others.
5. **Leadership and talent.** Does the CAIRO
   function have the right capabilities; what
   gaps exist.
6. **Cultural integration.** Is the program
   integrated into the organisation's
   operations or operating in parallel.

For each, the self-assessment provides specific
evidence and specific recommendations.

### 6.3 The honesty test

The hardest part of the self-assessment is
honesty. A self-assessment that says everything
is working is rarely accurate; a self-assessment
that says nothing is working is rarely
accurate either. The right posture is:
specific findings, both positive and negative,
with evidence.

A test: would the CAIRO be comfortable showing the
self-assessment to a peer CAIRO at a similar
institution who would give an honest read? If
yes, the self-assessment is probably honest. If
the CAIRO would want to revise before showing,
the self-assessment isn't there yet.

### 6.4 The output

The self-assessment produces:

- A written document, signed by the CAIRO,
  submitted to the AI Risk Council and the
  Audit Committee.
- A specific action list — what the program will
  do differently in the year ahead.
- A specific resource request — what the CAIRO
  function needs to do the above.

The document becomes input to the board's
view of the program, separately from the
internal audit's view.

### 6.5 The annual cycle

A working annual cycle:

- Q4: Self-assessment authored.
- Q1: Self-assessment reviewed by AI Risk
  Council; recommendations integrated into the
  annual planning.
- Q1: Self-assessment presented to the Audit
  Committee.
- Q2-Q4: Actions tracked; status updates in
  quarterly reports.

The self-assessment closes the loop on the
program's GOVERN function (mod-103 §6) at the
annual level.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **COSO ERM — Applying ERM to AI (2024)** —
   the operationalizable risk appetite
   framework §2 builds on.
2. **AICPA AI Risk Reporting Guide** — board
   reporting structure.
3. **NIST AI RMF maturity model** — §6.1
   self-assessment anchor.
