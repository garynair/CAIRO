# Chapter 6 — Governance Operating Models

## Why this chapter exists

Once you have decided the CAIRO exists (Chapter 4) and where
it reports, you have to pick an **operating model**: *how*
the governance work actually gets done across the
organization. There are three patterns that recur.
Practitioners often argue as if one is universally
correct. None is. The right model depends on the
organization's size, regulatory shape, business-unit
diversity, and existing risk maturity.

This chapter walks the three patterns, gives you the two
strongest objections to each, and hands you the framing
you will use in Exercise 05 to recommend one to a board.

## Pattern 1 — Centralized

A single corporate AI governance team executes most of
the work: writes the policies, runs the review board,
owns the risk register, performs the impact assessments,
handles the regulatory engagement. Product teams interact
with governance through a defined intake — typically an
impact-assessment form and a review-board queue.

- **Strengths.** Consistency of interpretation. Easier
  hiring (specialized governance skills concentrated).
  Clearer regulator interface. Simpler for a first-time
  supervisory exam.
- **Weaknesses.** Slow. Becomes a bottleneck. Tends to
  alienate product teams who feel governance is
  something done *to* them.
- **Best for.** Small-to-medium orgs (up to a few
  hundred people in AI-adjacent roles), or orgs in
  heavily regulated single-industry contexts where
  consistency matters more than speed.

**Two strongest objections and their responses:**

- *"Centralized bottlenecks kill velocity."* True at
  scale. The response is to publish decision SLAs (e.g.
  three business days for standard reviews, ten for
  high-risk) and staff to hit them. If you cannot hit
  the SLAs, the model is wrong for your scale — you
  have outgrown centralized.
- *"Product teams won't own risk they didn't help
  design."* Real risk. The response is a defined
  first-line-of-defense residency: even in a centralized
  model, treatment ownership stays with the business
  unit; the central team documents and reviews but does
  not execute the fix.

## Pattern 2 — Federated

Governance work is distributed to business units, each of
which runs its own AI risk function under common
standards set centrally. The CAIRO sets the standards, owns
the enterprise risk register (rolled up from BU
registers), and runs the *review-of-the-reviewers*
function.

- **Strengths.** Scales to very large organizations.
  Domain expertise embedded near the work. Product teams
  feel ownership. Business-unit specificity respected
  (a healthcare BU's AI risks are meaningfully different
  from a fintech BU's).
- **Weaknesses.** Inconsistency of interpretation.
  Standards drift over time as each BU customizes.
  Hard to roll up a coherent enterprise view. Regulator
  interface fragmented — a supervisor talking to two
  BUs may get two different postures.
- **Best for.** Large, diversified organizations with
  distinct business units that have meaningfully
  different AI risk profiles (an industrial holding
  company with aerospace, healthcare, and financial
  services arms, for example).

**Two strongest objections and their responses:**

- *"Standards will drift and the enterprise view will
  fragment."* Real risk, empirically. The response is an
  annual central re-alignment: standards are re-issued,
  BUs must attest to interpretation, differences from
  the canonical interpretation are formally documented
  as *deviations* rather than left implicit.
- *"You are paying for four AI risk functions instead
  of one."* True; the model has real cost. The response
  is that the alternative — a single central function
  trying to understand four different regulatory
  regimes and four different technical stacks —
  produces its own hidden cost as it either grows to
  parity (paying for the same headcount) or fails to
  cover the diversity.

## Pattern 3 — Hub-and-spoke

A central team (the **hub**) owns the framework, the
standards, the enterprise risk register, and the regulator
interface. Embedded "AI risk partners" (**spokes**) live
inside business units. Spokes report *dotted-line* to the
hub, *solid-line* to the business. The partners are first
responders on their BU's AI work; the hub handles
escalation, policy work, and enterprise reporting.

- **Strengths.** Combines consistency of the hub with
  the embedded knowledge of federated. The most common
  mature pattern in large enterprises. Regulator
  interface remains coherent (hub owns it) while
  velocity stays reasonable (spokes handle the
  everyday cases).
- **Weaknesses.** The dotted-line/solid-line dynamic
  requires active management. Spokes can be captured by
  their BU (going native) or resented by the BU (seen
  as informants for the hub). Requires deliberate
  operating rhythm — quarterly hub-spoke meetings, joint
  performance reviews, rotational assignments.
- **Best for.** Mid-sized to large orgs that have
  outgrown centralized but cannot tolerate the
  consistency loss of fully federated.

**Two strongest objections and their responses:**

- *"The dotted-line relationship never works — the
  spoke always ends up serving the BU."* Common failure,
  well-documented in matrix organizations generally. The
  response is *joint performance evaluation*: the hub
  and BU sign off jointly on the spoke's annual review,
  and either side can veto. Also: rotational assignments
  (spokes rotate through the hub every three to five
  years) prevent going native.
- *"You are creating two chains of command; when they
  conflict, the CAIRO loses."* Real risk if the escalation
  path is undefined. The response is a written
  escalation path (Chapter 5's three-level pattern) and
  a standing agreement that hub-line policy disputes
  are resolved above the BU executive layer.

## The three, side by side

| Dimension | Centralized | Federated | Hub-and-spoke |
|---|---|---|---|
| Where policy is written | Center | Center, BUs interpret | Hub |
| Where reviews happen | Center | BUs, center audits | Spokes for standard, hub for escalation |
| Regulator interface | Center | BUs (fragmented) | Hub |
| Enterprise risk register | Center | Rolled up from BUs | Hub |
| Consistency | High | Low | Medium-high |
| Velocity | Low | High | Medium-high |
| Cost | Lowest at small scale | Highest at any scale | Medium |
| Best fit | Small-to-medium regulated org | Diversified large org | Most mid-large enterprises |

## The two-objection defense (Exercise 05 shape)

When you pick an operating model, defense against a
board or risk committee will look like:

1. **State the pick in the first sentence.** "We
   recommend hub-and-spoke, with the hub in the CRO's
   risk function and spokes embedded in each business
   unit."
2. **Name the two other options and dispose of each in
   one paragraph.** Not a strawman — a fair statement
   of why the other option would be reasonable, followed
   by why it is not right for *this* org.
3. **State the two strongest objections to your pick**
   and answer them substantively. The strongest
   objections are usually the ones above in each
   pattern's section — internalize them.

Exercise 05 will ask you to write this memo for Kerridge
Industries, a diversified $14B industrial holding
company. The exercise is graded on the *quality of the
defense*, not on which model you pick. Two of the three
patterns are defensible for Kerridge; only one is not.

## Practitioner illustrations (range, not template)

Public implementations that illustrate each pattern.
Each is a *defensible* choice in its own context.
Picking one because a respected company picked it is the
worst reason — they are solving a different problem.

- **[Anthropic Responsible Scaling Policy](https://www.anthropic.com/rsp)** —
  a frontier-AI research-org pattern; centralized,
  extremely explicit about capability tiers and
  associated controls. Useful to read for the
  *granularity* of risk-tier definitions, not as a
  template for a typical enterprise.
- **[Microsoft Responsible AI Standard v2](https://www.microsoft.com/en-us/ai/responsible-ai)** —
  hyperscaler-scale RAI program; effectively
  hub-and-spoke with a strong policy hub. Useful for the
  policy hierarchy structure and the impact-assessment
  template shape.
- **[Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/)** —
  security-overlay framing; pairs with a separate RAI
  governance function. Useful for showing the boundary
  between security and governance functions on a
  peer-role basis (Chapter 5).
- **[NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook)** —
  not an operating model but a menu of considerations
  per sub-function; useful for populating whichever
  model you pick with actual working practices.

## The failure trap: picking the model that fits the CAIRO, not the org

A very common trap: the newly-appointed CAIRO picks the
operating model that fits *their* previous experience.
The CAIRO who came from an insurance CRO function picks
centralized because it is what they ran before. The CAIRO
who came from a large tech company picks hub-and-spoke
because it is what worked at their previous employer.

The right question is not "what have I done before" but
"what does *this* organization need." Chapter 4 covered
readiness; the same discipline applies to operating
model. Write down the organization's shape (size, BU
diversity, regulatory count, existing risk maturity)
first, then pick the model that fits.

## Summary

- Three operating models: centralized (consistent,
  slow), federated (fast, drifts), hub-and-spoke
  (balanced, requires active matrix management).
- Best-fit heuristics: centralized for small-to-medium
  regulated orgs; federated for large diversified orgs
  with BUs that have meaningfully different AI risk
  profiles; hub-and-spoke as the mature default for
  most mid-to-large enterprises.
- Every recommendation must survive the two strongest
  objections; the objections above are what you defend
  against.
- Practitioner references show range; none is the
  answer.
- Pick the model that fits the organization, not the
  CAIRO's previous role. The trap is subtle but common.
