# Module 112 — Lecture Notes

About 95 minutes of reading. This is the closing
module; the voice is more personal and the
patterns more pattern-language than the
prior modules.

---

## §1. The operating-model choice, revisited

mod-101 §5 introduced three operating-model
patterns: centralised, federated, hub-and-spoke.
Every CAIRO function eventually settles into one
of these (or a hybrid). The structural choice
shapes everything that follows — which is why
mod-101 placed it early.

This module revisits the choice from the
perspective of a CAIRO who has now seen what each
choice produces in practice across mod-102
through mod-111.

### 1.1 What the choice determines

The operating model determines:

- **Who decides** what controls apply where. The
  hub decides in centralised; the business unit
  in federated; both in hub-and-spoke.
- **Where the evidence lives.** Centralised
  produces consolidated evidence; federated
  produces distributed evidence; hub-and-spoke
  centralises some, distributes some.
- **How the CAIRO function scales.** Centralised
  scales with headcount in the hub; federated
  scales by adding business-unit functions;
  hub-and-spoke scales selectively.
- **Where the program is brittle.** Centralised
  has hub key-person risk; federated has
  consistency risk; hub-and-spoke has
  coordination overhead.
- **How regulators see the program.** Centralised
  presents a clear single interface; federated
  presents per-business-unit interfaces;
  hub-and-spoke presents both layers.

### 1.2 The choice is contextual

There is no universally correct model. The right
choice depends on:

- **Organisation size and complexity.** Small,
  single-business orgs do better centralised;
  large, multi-LOB orgs do better federated or
  hub-and-spoke.
- **Regulatory landscape.** Single-regulator
  contexts favour centralised; multi-regulator
  contexts favour distributed approaches.
- **Existing risk-function architecture.** If
  enterprise risk is centralised, AI risk often
  follows; if federated, vice versa.
- **Maturity of AI deployment.** Programs in the
  early stages benefit from centralised
  decision-making; mature programs can sustain
  distributed.

### 1.3 The choice carries forward

What you have seen across the track:

- The CAIRO × MRM split (mod-104) operates more
  cleanly in hub-and-spoke because both
  functions have natural counterparts.
- The CAIRO × CISO boundary (mod-107) operates
  more cleanly in centralised, where the
  boundary discussion happens once at the
  enterprise level.
- The CAIRO × Compliance boundary (mod-109)
  operates more cleanly when the operating
  models match (both centralised, or both
  federated).
- The evidence infrastructure (mod-108) is
  more efficient when centralised regardless of
  the broader CAIRO operating model.

The structural insight: **the operating model
should be chosen to optimise for the boundaries
the CAIRO function will spend the most time
operating**.

### 1.4 What if you inherited the model

Most CAIROs inherit an operating model rather than
choosing one. If the inherited model fits the
organisation, the right posture is *operate
within it*. If the inherited model doesn't fit,
the right posture is *operate within it for now
and propose change deliberately when the program
is mature enough to absorb the transition*.

Changing the operating model is one of the most
expensive things a CAIRO can do; doing it in year
1 or year 2 is rarely the right move regardless
of how obvious the case seems.

---

## §2. Year 1 — the foundation arc

Year 1 is about laying foundation. The work is
unglamorous, frequently invisible from outside
the function, and forms the basis for
everything that follows. CAIROs who try to skip
year 1 — by jumping to visible deliverables —
produce programs that look impressive briefly
and collapse under the first material
challenge.

### 2.1 What year 1 should accomplish

Six things, in roughly this order:

1. **Build the governance machinery.** AI Risk
   Council, AI Review Board, charter.
2. **Establish the program's authority.**
   Through the appetite statement and the
   policy hierarchy.
3. **Stand up the operational discipline.** The
   inventory, the impact assessments, the
   monitoring infrastructure, the trust
   architecture, the evidence layer.
4. **Engage the boundaries.** CAIRO × MRM,
   CAIRO × CISO, CAIRO × Compliance discussions
   conducted formally, resolutions documented.
5. **Hire the team.** The first 4-8 roles that
   will carry year 2.
6. **Brief and engage the board.** Quarterly
   reports operating; board adoption of the
   appetite statement.

### 2.2 What year 1 should not try to do

Equally important — things that year 1 will be
tempted to attempt but should defer:

- **Solve every gap.** Year 1 will surface
  numerous gaps. Picking which ones to address
  and which to document for year 2 is the
  discipline.
- **Build comprehensive automation.** Per mod-109
  §4.3, automation before practice maturity is
  the trap. Year 1 builds the practice; year 2
  considers automation.
- **Run too many tabletops.** Per mod-110 §6.5.
  One substantive tabletop in year 1 is enough;
  more is performance.
- **Author every standard at once.** The
  program standards take time to draft well.
  Year 1 produces the load-bearing ones
  (policy hierarchy, transparency standard,
  defense-in-depth standard) and defers
  others.
- **Win every boundary discussion.** Some
  boundary discussions are not yet ripe in
  year 1; documenting positions and
  re-engaging in year 2 is acceptable.

### 2.3 The mid-year-1 inflection point

Around month 6-8 of year 1, most CAIROs hit an
inflection point: the foundation work is
substantial, the visible deliverables are
limited, and pressure increases for visible
results.

The temptation is to pivot to visible
deliverables. The discipline is to continue the
foundation work and to *communicate the
foundation-laying as the deliverable*. The
quarterly board report's "material changes"
section can show foundation progress: "AI Risk
Council operating monthly; impact assessments
completed on X Tier 1 systems; trust
architecture partner contract executed."

CAIROs who pivot prematurely at month 6-8 produce
year-2 programs that have visible apparatus but
weak foundation.

### 2.4 The end-of-year-1 self-assessment

The annual self-assessment from mod-111 §6 is
particularly important at the end of year 1.
The honest read is rarely "the program is
mature"; it is usually "the foundation is laid
and the program is ready to consolidate". This
is the right read for a year-1 self-assessment.

---

## §3. Year 2 — the consolidation arc

Year 2 is about consolidating the foundation
and beginning to operate the program as
designed rather than building it. The work
shifts from authoring to operating.

### 3.1 What year 2 should accomplish

Six things:

1. **Operate the controls at cadence.** The
   continuous-evidence cadence from mod-109 §3
   becomes real.
2. **Close the year-1 gaps.** Most of the gaps
   the year-1 self-assessment surfaced.
3. **Mature the program.** Move from NIST
   maturity Level 1-2 to Level 2-3.
4. **Integrate cross-LOB or cross-function.**
   Patterns that worked in one LOB or function
   extend to others.
5. **Build the second tier of the team.** The
   roles that support the year-1 hires.
6. **Handle the first material incident
   credibly.** Most programs face one in year 2;
   handling it well establishes the program's
   reputation.

### 3.2 The consolidation discipline

Year 2 is where the CAIRO function moves from
"building" to "operating". The discipline:

- **Resist the temptation to start new
  initiatives.** Year 1's foundation needs to
  consolidate before year 2 can sustain new
  workstreams.
- **Honor the standards.** Year 1's standards
  become real. Pressure to relax them under
  business pressure surfaces; resisting that
  pressure is the year-2 work.
- **Use the evidence.** The evidence layer from
  mod-108 starts producing useful patterns in
  year 2. Reviewing it monthly across the
  AI Risk Council surfaces signals.
- **Refine, don't rebuild.** Year 1's structures
  will be imperfect. Year 2 refines them;
  rebuilding is year-3 work at the earliest.

### 3.3 The year-2 trap

A specific failure mode: the program in year 2
discovers that some year-1 choices were wrong
and tries to fix them comprehensively. The
result is that year 2 looks like year 1 again
— building rather than operating.

The discipline: name year-1 errors specifically,
fix the most material ones, document the
others as year-3 work. Trying to fix everything
in year 2 means the program never matures.

### 3.4 The first material incident

Programs that face their first material
incident in year 2 are well-positioned to
respond — the structure is in place, the team
knows each other, the relationships with the
CISO and CCO are established. The discipline:
treat the incident as the test the year-1
foundation was preparing for. The post-incident
review (per mod-110 §6) becomes a substantive
program artifact.

### 3.5 The end-of-year-2 self-assessment

The year-2 self-assessment is the most
important one. By end of year 2, the program
should be honestly *operating*. The
self-assessment should show:

- Mature controls (NIST Level 3 on most
  functions).
- Closed gaps from year 1.
- Substantive incident response track record (the
  first material incident handled).
- Cross-LOB or cross-function integration.

If the year-2 self-assessment cannot show
these, the program is stalling at year-2 levels.

---

## §4. Year 3 — the maturity arc

Year 3 is when the program transitions from
*operating* to *operating well*. The work
shifts from doing the right things to doing the
right things efficiently and at scale.

### 4.1 What year 3 should accomplish

Five things:

1. **Operate efficiently.** The cost per unit
   of risk-managed AI decreases meaningfully.
2. **Scale the practice.** New AI systems
   adopt the program's discipline within
   weeks rather than months.
3. **Establish industry voice.** The CAIRO and
   the program have something to contribute to
   the industry conversation.
4. **Build leadership succession.** The CAIRO is
   no longer the single load-bearing executive.
5. **Pursue strategic ambition.** The CAIRO
   contributes to organisational strategy
   beyond defensive risk management.

### 4.2 The shift in CAIRO time

In year 3, the CAIRO should spend materially less
time on operational decisions and materially
more on:

- Strategic contribution.
- Board and executive relationship-building.
- Talent development (their own team and
  cross-functional partners).
- External engagement (regulators, industry,
  peer institutions).

The shift requires deputies who can carry the
operational load. mod-111 Ex-05 reference
solution named "deputy AI Risk Lead" as a year-2
recruiting priority for exactly this reason.

### 4.3 Warning signs of stalling

Programs that don't reach year-3 maturity show
specific symptoms in year 3:

- The CAIRO is still personally handling many
  operational decisions.
- New AI systems require months to enter the
  program's discipline.
- The program is still building foundational
  artifacts (standards, controls) that should
  have been complete in year 2.
- Board reporting still has the "look at what
  we built" quality of year 1 rather than
  "look at what we operate" of year 2-3.

A CAIRO who recognises these symptoms in year 3
should treat them as signal that the program's
maturation has stalled and engage the AI Risk
Council and Board on what is needed.

### 4.4 The CAIRO at year 3

A CAIRO in their third year in role looks
materially different from a CAIRO in their first
year:

- More authoritative in cross-functional
  conversations.
- More selective about what reaches them
  personally vs. their deputies.
- More strategic in board engagements.
- More credibly able to disagree with peers
  (per mod-105 §6.5 and mod-111 §5.3).

The personal shift accompanies the program
shift. CAIROs who don't shift personally as the
program matures become bottlenecks.

### 4.5 The year-3 self-assessment

Mature; specific findings about what the
program does well and the next-frontier
questions (year-4 work). The peer-CAIRO honesty
test (mod-111 §6.3) becomes easier in year 3 —
the program has enough operating history to
support honest assessment.

---

## §5. The CAIRO's calendar and decision rhythm

The CAIRO's calendar shapes the function. CAIROs
whose calendars are driven by everyone else's
priorities don't have time for the work this
track has been about. The discipline is
operating the calendar deliberately.

### 5.1 The recurring rhythm

A working CAIRO calendar has:

| Cadence | Activity |
|---|---|
| Daily | Standup with AI Risk Lead; review of any incident or escalation |
| Weekly | 1:1 with each direct report; review of AI Review Board agenda; weekly bias-monitoring summary review |
| Bi-weekly | AI Review Board (chair); business-unit head 1:1 rotation |
| Monthly | AI Risk Council (chair); 1:1 with CRO, CCO, CISO, MRM Lead; CAIRO-of-other-institution peer call |
| Quarterly | Board Risk Committee meeting; AI Risk Council strategic review; CAIRO of the AI program quarterly self-review |
| Annually | Annual self-assessment; annual board adoption review; annual external benchmarking |

The calendar is *crowded* — at the CAIRO level it
needs to be. But it is also *deliberate*. The
CAIRO who clears the calendar reactively for
whatever crisis arrives won't do the structural
work.

### 5.2 Time protection

A working CAIRO protects time for:

- **Strategic thinking.** Half a day per week
  blocked, undisturbed.
- **Direct report development.** Weekly 1:1s
  treated as inviolable.
- **Stakeholder relationship-building.**
  Outside-the-fire-drill conversations with the
  CRO, CCO, CISO, MRM Lead.
- **External engagement.** Regulator, peer
  CAIRO, industry-body meetings.

CAIROs whose calendars are entirely incident
response, meeting back-to-back, and
deliverable-driven don't have time for the
relationship and strategic work that makes
year-3 maturity possible.

### 5.3 Delegation

A specific year-1-and-2 discipline: delegating
work that the CAIRO doesn't need to personally
do. The temptation is to do everything because
the team is small and the work is
consequential.

The discipline:

- **The AI Risk Lead** handles operational
  incident response.
- **The Policy Lead** owns standard authorship.
- **The Evidence Lead** owns the evidence
  layer.
- **The Regulatory Engagement Lead** owns
  routine regulator interface.

The CAIRO handles strategic decisions, executive
relationships, board engagement, and the few
operational decisions that genuinely need the
CAIRO's personal involvement.

### 5.4 The crisis discipline

When an incident or crisis arrives, the CAIRO is
pulled into operations. This is appropriate;
material incidents are CAIRO-level events. The
discipline is *getting back to the recurring
rhythm afterward*. CAIROs who let crises
permanently dominate the calendar drift into
purely reactive operation.

The reset pattern: after the immediate crisis
phase, schedule a "calendar reset" half-day
within 2 weeks to restore the protected time
blocks.

---

## §6. Talent, budget, and succession

The CAIRO function is one of the more difficult
to staff and budget for. The roles are new; the
required combination of skills is unusual; the
budget has to justify itself to a board that
doesn't yet see the program's value.

### 6.1 The talent profile

Roles in the CAIRO function require:

- **Technical depth.** Enough to engage
  substantively with engineering, MRM, CISO.
- **Risk discipline.** Familiarity with risk-
  management frameworks and practice.
- **Governance literacy.** Comfort with board,
  committee, and regulator dynamics.
- **Communication clarity.** The ability to
  write a 3-page report that a board can act
  on.

This combination is rare. CAIRO functions
typically build it through hiring across
backgrounds rather than finding it in a single
candidate.

### 6.2 The hiring sequence

A typical year-1 / year-2 hiring sequence:

| Hire | Year | Role | Background |
|---|---|---|---|
| CAIRO | 0 | Chief AI Risk Officer | Senior risk or program-lead with AI exposure |
| 1 | Y1 | AI Risk Lead | Risk professional; will carry day-to-day |
| 2 | Y1 | Policy Lead | Compliance background; policy authorship |
| 3 | Y1 | Evidence Lead | Engineering or audit background; evidence infrastructure |
| 4 | Y1 | Regulatory Engagement Lead | Legal or compliance background |
| 5 | Y2 | Deputy AI Risk Lead | Successor track for AI Risk Lead |
| 6 | Y2 | Algorithm Validation Lead | MRM-adjacent; partners with MRM |
| 7 | Y2 | Trust Architecture Lead | Engineering; cross-CISO partnership |
| 8 | Y2-3 | Communications / Board Lead | Specialty for board engagement |

Each role's specific shape varies by organisation;
the sequence is the pattern.

### 6.3 Budget posture

The CAIRO budget has to be defended. The discipline:

- **Tie investment to risk reduction.** Not "we
  need X to operate"; "this investment reduces
  risk Y by mechanism Z".
- **Phase the budget.** Year 1 is
  foundation-heavy; year 2 is consolidation
  with continued growth; year 3 is operational
  with selective investment.
- **Show the cost of not investing.** Per
  mod-111 Ex-04 — what's the exposure if
  this investment doesn't happen.

Boards respect CAIROs who treat budget as a
strategic conversation, not as a request for
resources.

### 6.4 Succession

Most boards and CEOs treat the CAIRO role as
person-specific in year 1: this CAIRO. In year 2,
they begin asking "what happens if?" In year 3,
the question becomes formal succession
planning.

A working CAIRO addresses succession:

- **Deputy CAIRO or equivalent** identified by
  year 2.
- **Cross-functional readiness** — direct
  reports who could step up.
- **External pipeline** — relationships with
  potential successors at peer institutions.
- **Documented operating model** — the
  function's discipline documented sufficiently
  that a successor can operate it.

The hardest part of succession is the CAIRO's own
posture. The temptation is to be irreplaceable.
The discipline is to be replaceable. CAIROs whose
function depends entirely on them produce
programs that don't survive their departure.

### 6.5 The CAIRO's own development

Finally: the CAIRO is themselves a person needing
development. CAIRO roles are isolating; the peer
group is small; the work is high-stakes.

Practices that work:

- **Peer CAIRO network.** Monthly conversation
  with peers at non-competing institutions.
- **Executive coaching.** Specifically for the
  CAIRO role, not generic coaching.
- **Board chair relationship.** The Audit
  Committee or Board Risk Committee chair is
  often an undervalued mentor and ally.
- **Reading.** AI safety, governance,
  regulatory developments continuously.

The CAIRO who treats their own development as
optional becomes the brittle keystone of an
otherwise mature program.

---

## Closing note

This is the last lecture in the foundational
track. The discipline of the CAIRO role, across
these 12 modules, is the discipline of operating
a substantive function in the absence of
external rules that fully specify what good
looks like.

You will be wrong some of the time. You will
make decisions you later wish you had made
differently. The track is not a recipe; it is
the structural background that lets you make
those decisions deliberately and defend them
when they are challenged.

Build the program. Operate the program. Survive
the program. And when you no longer need to,
hand it to a successor as ready as you wish you
had been when you started.

---

## References

Full reading list in [`resources.md`](./resources.md).
Three to start with:

1. **Carlyle / Lakhani — Boards and AI
   Oversight (HBR)** for the board-perspective
   on year 1-3 maturation.
2. **NIST AI RMF maturity model** as the
   year-by-year reference.
3. **The previous 11 mod-*-resources.md files
   collectively** — this module's reading is
   the prior modules' practice.
