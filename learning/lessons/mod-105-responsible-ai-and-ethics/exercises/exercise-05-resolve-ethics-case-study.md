# Exercise 05 — Resolve a Hard Ethics Case

**Estimated time**: 3 hours
**Deliverable**: A decision memo (≤ 3 pages)

---

## Why this exercise exists

§6 of the lecture notes named the hardest CAIRO ethics
work: holding a position under pressure, naming
disagreement honestly, surviving the moment when the
business wants the program to soften. This exercise puts
you into that moment and asks you to produce the
specific artifact: the decision memo.

## The case

You are the CAIRO at **Halverston Capital** (continuity
from mod-103 Exercise 01). The Wealth Advisory division
has been piloting an LLM-based **financial-advice
generation assistant** for the firm's advisors. The
assistant produces draft client communications,
suggested portfolio rebalancing rationales, and
client-meeting summaries.

The pilot results are strong: advisors using the
assistant produce more written advice for clients,
clients report higher satisfaction with the depth of
explanations they receive, and the firm's advisor-
productivity metric is up materially. The Wealth
Advisory division wants to deploy the assistant to all
2,400 advisors next quarter.

Three concerns surfaced during the program's AI Review
Board review:

### Concern 1 — Adviser-of-record framing

The assistant produces high-quality, well-written client
communications. Advisors are *signing* these
communications as their own advice. But: in some cases,
advisors are signing communications that include
investment rationales the advisor did not independently
form. The communication says, in effect, "I recommend X
because of Y, Z, W" — and the advisor agreed with X
but did not arrive at Y, Z, W independently.

The Wealth Advisory division says this is normal —
advisors have always used templates and research
material, and "as long as the advisor agrees with the
conclusion, the reasoning is theirs to sign for."
The Compliance team agrees with this read.

The concern: the assistant's output is *materially more
persuasive* than the previous templates. Clients reading
these communications form deeper trust based on the
quality of the reasoning. The advisor's name and
relationship are doing more work — making the advisor's
adoption of the LLM's framing more significant — than
under the previous template regime.

### Concern 2 — Disclosure to clients

Clients are not told the communications they receive
were drafted with AI assistance. The Wealth Advisory
division argues this is correct: clients are receiving
advice from their advisor, who personally reviewed and
adopted it; the AI is a *tool*, like a research
database; no disclosure is required and disclosure would
be confusing.

The CFTC, FINRA, and SEC have not specifically required
disclosure of AI use in this context. California's AI
Transparency Act (mod-102 §5) might require it for
California-resident clients but the application is
unclear.

The concern: clients may not be receiving the
relationship they think they are. The advisor's
attention per-client may have materially declined even
if the per-client output increased.

### Concern 3 — Differential adoption

Pilot data shows that some advisors (typically newer,
lower-AUM-per-client) are using the assistant for
~80% of their client communications. Others (typically
senior, high-AUM) use it for ~10%. The high-quality
output is therefore disproportionately reaching the
clients of newer, lower-AUM advisors — meaning some
clients are receiving advisor-signed communications
where most of the substantive content came from the AI.

The Wealth Advisory division says this is the system
working — newer advisors are getting leverage. The
concern: those clients' interests may be served
differently than the firm's senior advisors' clients,
in ways that touch on Halverston's fiduciary obligations.

## Your assignment

The CEO has asked you for a decision memo (≤ 3 pages)
addressing the three concerns and your recommendation
to the AI Risk Council. The memo will be discussed at
next week's Council meeting.

The memo must:

1. **Take a position on each of the three concerns.**
   For each, state the position in the first paragraph
   of that concern's section.

2. **Address the steel-manned counter-argument** on at
   least two of the three concerns. The Wealth
   Advisory division's positions are not unreasonable;
   the memo must show why your position prevails even
   given the steel-manned alternative.

3. **Recommend a deployment posture.** Approve as
   proposed? Approve with conditions? Pause? Decline?
   The recommendation must be specific.

4. **Name the disagreement honestly** where it exists.
   Per §6.5 of the lecture notes, the CAIRO ethics
   function sometimes names a disagreement rather
   than resolves it. Identify which (if any) of the
   three concerns falls into this category.

5. **Identify the precedent** the decision sets. Future
   Halverston AI deployments with similar patterns
   will be guided by this precedent; name what that
   precedent is.

6. **Acknowledge what your recommendation costs the
   business**, if anything. Recommendations with no
   acknowledged cost are read as costless ethics —
   which means the position has not been tested.

## Constraints

- **Three pages, hard limit.**
- The memo must address all three concerns. Punting
  any of them is not within the exercise.
- The recommendation must not be "study further."
  Study-further is the rhetorical move that lets the
  business deploy while the ethics work is ongoing.
- At least one of the three concerns must be addressed
  by *naming a disagreement* rather than resolving it.
  All three resolved with confident answers is
  implausible for a case at this depth.
- The memo's voice must be the CAIRO's, not an ethics
  professor's. Decisions, not lectures.

## Rubric

| Criterion | Weight |
|---|---|
| Position on each concern — stated up front | 15% |
| Steel-manning — substantive, on at least two of three | 20% |
| Deployment recommendation — specific, defensible | 15% |
| Naming-disagreement discipline — at least one of three | 15% |
| Precedent identification — specific | 15% |
| Acknowledged cost — substantive | 10% |
| Length discipline — ≤ 3 pages | 5% |
| Voice — CAIRO speaking, not principle-listing | 5% |

## Where to submit

`solutions/modules/mod-105-responsible-ai-and-ethics/exercise-05-resolve-ethics-case-study/SOLUTION.md`

Reference solution recommends *approve with conditions*:
the assistant is deployed but only with a disclosure
mechanism, with advisor-attestation discipline on the
adoption of AI-drafted reasoning, and with monitoring
of the differential-adoption pattern. The third concern
(differential adoption) is named as a *partially-
resolved disagreement* — the position taken is
documented, but the underlying question of fiduciary
obligations as advisor leverage shifts is named as
unresolved.

## Reading before you start

- Lecture notes §6 (operationalizing ethics) — all of
  it, especially §6.3 (under business pressure) and
  §6.5 (naming a disagreement).
- mod-101 §6 (failure modes — governance theatre).
- mod-102 §4 (financial-services regulation; SEC /
  FINRA / CFTC posture on AI).
