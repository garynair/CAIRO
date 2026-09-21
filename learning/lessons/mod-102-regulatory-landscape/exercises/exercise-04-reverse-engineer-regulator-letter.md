# Exercise 04 — Reverse-Engineer a Regulator Letter

**Estimated time**: 3 hours
**Deliverable**: A "what they actually want" memo + a
response plan (≤ 2 pages combined)

---

## Why this exercise exists

Regulators rarely ask the question they actually want
answered. The letter you receive is a *probe* — it tests how
your organization will respond, what your governance
maturity is, and whether you can be trusted to police
yourself in the next twelve months. Treating the letter as a
literal questionnaire is the most common error.

This exercise builds the skill of reading past the literal
text.

## The letter

You are the CAIRO at **Trillium Bancorp**, a mid-size US
regional bank. The bank is supervised by the OCC. Two months
ago Trillium publicized a generative-AI customer-service
agent that has been in pilot for six months. You received
the following letter ten days ago.

> **Office of the Comptroller of the Currency**
> Washington, DC
>
> Re: Information request — Trillium Bancorp AI deployments
>
> Dear Ms. [CAIRO],
>
> The OCC is conducting a review of artificial-intelligence
> and machine-learning deployments at supervised institutions.
> In connection with that review, please provide the
> following information within thirty days:
>
> 1. A list of all AI/ML models in production at Trillium,
>    including model purpose, intended users, and date of
>    initial deployment.
>
> 2. A copy of any model risk management policy or procedure
>    documents governing AI/ML at Trillium.
>
> 3. For your recently announced AI customer-service
>    capability, please provide: a description of the model,
>    the data on which it was trained, the controls in place
>    to prevent unauthorized disclosure of customer
>    information, and the procedures for human review of
>    customer-facing outputs.
>
> 4. Information about any incidents or near-incidents
>    involving the AI customer-service capability since its
>    initial deployment.
>
> Please send responses to the undersigned. We may follow up
> with additional requests after reviewing the materials.
>
> Sincerely,
> [name]
> Bank Examiner, Large Bank Supervision

## Your assignment

Produce two deliverables.

### Deliverable 1 — "What they actually want" memo (1 page)

Address the following:

1. **What is the OCC's actual question?** What is this letter
   probing? (It is not just the four enumerated items. What
   is the *underlying concern*?)
2. **Why now?** What about the timing — six-month pilot,
   recent publicity, this exam cycle — explains the letter
   arriving when it did?
3. **What posture does the OCC want to see?** What kind of
   responding institution gets through this review without
   follow-up?
4. **What posture must Trillium avoid?** What kind of
   response *guarantees* follow-up?

### Deliverable 2 — Response plan (1 page)

A response plan covering:

1. **Internal mobilization.** Who at Trillium produces what,
   on what cadence, in the 30 days. Name roles, not people.
2. **Scope decisions.** Are there models in production at
   Trillium that the letter could be read to require *but
   that Trillium's leadership had not yet considered AI/ML*?
   If so, how do you handle that scope question?
3. **Response framing.** What is the **lede sentence** of
   the response cover letter — the one sentence the
   examiner will read first and use to frame everything
   else? Write it.
4. **Things you will not say.** Name at least two true facts
   about Trillium's AI program that, if volunteered now,
   would make the rest of the response harder.
5. **What you will request from the OCC** — if anything.

## Constraints

- The "what they actually want" memo must go beyond restating
  the letter. If your memo reads like a paraphrase of the
  enumerated items, you are not doing the exercise.
- The response plan must respect SR 11-7 — Trillium's AI/ML
  models are *models* under SR 11-7 whether or not Trillium's
  MRM function has absorbed them.
- The "things you will not say" section is **not** a
  recommendation to lie. It is a recommendation to manage
  information disclosure surface deliberately. Items must be
  true facts that are nevertheless not load-bearing for the
  response.
- The lede sentence must be deliverable. If you cannot
  imagine sending it tomorrow, redraft.

## Rubric

| Criterion | Weight |
|---|---|
| Underlying-concern identification — substantive, beyond paraphrase | 25% |
| Timing analysis — pilot, publicity, exam cycle are explained | 10% |
| Posture analysis — both desired and forbidden postures named | 15% |
| Response plan — concrete internal mobilization | 15% |
| Scope discipline — un-classified-AI question addressed | 10% |
| Lede sentence — deliverable, sets frame correctly | 15% |
| "Things not to say" — substantive, not trivial | 10% |

## Where to submit

`solutions/modules/mod-102-regulatory-landscape/exercise-04-reverse-engineer-regulator-letter/SOLUTION.md`

The reference solution names the underlying concern as
*"is your MRM function actually covering your AI/ML
deployments, or have they slipped past it through the
front door of customer-service tooling"* — with explicit
reasoning. As elsewhere, defensible alternative reads
exist.

## Reading before you start

- [Chapter 7 — Reading a regulator letter](../07-reading-a-regulator-letter.md) — the four questions and the response-plan structure.
- [Chapter 4 — Sector-specific regulation](../04-sector-specific-regulation.md) — financial services subsection.
- OCC/FRB SR 11-7. The MRM framework is the lens through
  which OCC examiners read AI letters.
- CFPB Circular 2022-03 — for awareness, though OCC, not
  CFPB, is the supervisor here.
