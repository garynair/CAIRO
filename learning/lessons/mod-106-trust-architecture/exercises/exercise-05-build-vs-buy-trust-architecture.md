# Exercise 05 — Build vs. Buy vs. Partner Decision

**Estimated time**: 3 hours
**Deliverable**: A decision matrix + a recommendation
memo (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Halverston Capital** (continuity
from mod-103 / mod-105). Halverston is operating a
growing portfolio of AI agents across its three lines
of business (public markets systematic strategies,
private credit AI underwriting, wealth advisory LLM
assistant — the Exercise 05 system from mod-105). The
existing trust posture is ad-hoc: each business unit
has its own identity story, no shared capability
registry, no consistent audit trail across agents.

Halverston's CTO and CISO are commissioning a
**trust architecture program** to consolidate. The
question they have asked you, as the CAIRO, is: should
the program **build, buy, or partner**?

Their initial assessment of the three options:

- **Build.** Estimated 18–24 months to first production,
  $4–6M in engineering investment, 8–12 FTE ongoing
  for maintenance. Architecture matches Halverston's
  multi-LOB needs exactly. No vendor dependency.
- **Buy** (single commercial product — they've shortlisted
  Cloudflare AI Gateway and IBM watsonx.governance). 6–9 months to
  first production, $1.5–2.5M annual licensing, 2–3
  FTE ongoing for integration. Architecture is
  battle-tested but may not perfectly fit Halverston's
  public-markets latency requirements.
- **Partner.** 9–12 months to first production, $0.8–1.5M
  annual for the bought components + $1.5–2M engineering
  for the built components, 4–6 FTE ongoing.
  Components-of-choice architecture.

## Your assignment

Produce two artifacts.

### Artifact 1 — Decision matrix (≤ 1 page)

A matrix comparing the three options on at least nine
dimensions. Use §6.2 of the lecture notes as the
starting structure, adapted for Halverston:

| Dimension | Build | Buy | Partner |
|---|---|---|---|
| Time-to-deploy |  |  |  |
| Engineering investment (5-year) |  |  |  |
| Annual operating cost |  |  |  |
| Vendor dependency |  |  |  |
| Customisation for public-markets latency |  |  |  |
| Multi-LOB fit |  |  |  |
| Regulatory defensibility |  |  |  |
| Standards evolution responsibility |  |  |  |
| Recruiting / talent posture |  |  |  |

For each cell, provide a specific value or
characterisation (not "good / bad").

### Artifact 2 — Recommendation memo (≤ 2 pages)

A memo to the CTO and CISO from the CAIRO containing:

1. **Recommendation** stated in the first sentence.
2. **Reasoning** organised around the dimensions
   that determined the choice (typically 3–4 most
   important dimensions).
3. **What the choice gives up.** §6.1 named the
   weaknesses of each option; the chosen option
   has weaknesses that the memo must name.
4. **CAIRO-program-specific concerns.** Per §6.5,
   what the CAIRO function specifically contributes:
   regulatory defensibility, audit / evidence
   requirements, AI-program constraints, long-
   term posture.
5. **Vendor capture analysis** (per §6.4, if buy
   or partner). What concentration risk does the
   choice carry, and what mitigations apply?
6. **Acknowledged uncertainties.** Things the
   decision cannot fully resolve and how they will
   be managed.

## Constraints

- The recommendation must be one of the three —
  not "study further" or "depends on Q4 budget".
- The reasoning must address Halverston's **multi-
  LOB structure**. A recommendation that ignores
  the three business units' different needs is
  not credible.
- The reasoning must address **public-markets
  latency** specifically. Public-markets agents
  have stricter latency requirements than wealth
  advisory; the recommendation must engage with
  this.
- The vendor capture analysis must name at least
  one **specific** mitigation if the recommendation
  involves buying or partnering with a specific
  vendor.
- The acknowledged uncertainties section must be
  substantive — at least three named uncertainties
  with their management plans.

## Rubric

| Criterion | Weight |
|---|---|
| Matrix — at least nine dimensions, specific values | 25% |
| Recommendation — clear, defensible | 15% |
| Reasoning — addresses multi-LOB + public-markets latency | 20% |
| What is given up — substantive | 10% |
| CAIRO contribution — substantive per §6.5 | 10% |
| Vendor capture analysis (if relevant) | 10% |
| Acknowledged uncertainties — at least three with plans | 10% |

## Where to submit

`solutions/modules/mod-106-trust-architecture/exercise-05-build-vs-buy-trust-architecture/SOLUTION.md`

Reference solution recommends **partner** for
Halverston. The reasoning: build the policy and
orchestration layer in-house (because of multi-LOB
customisation requirements and the public-markets
latency constraint), buy the identity /
attestation infrastructure and the audit ledger
(because the standards are mature, the security
expertise required is hard to recruit, and the
commercial offerings are credible). The vendor-
capture analysis names specific risks and proposes
multi-vendor strategy for the bought components.

## Reading before you start

- Lecture notes §6 (build, buy, or partner) — all of
  it.
- mod-101 §5 (operating models) — the same
  hub-and-spoke pattern logic applies.
- mod-104 §3.3 (independence and access) — the
  vendor independence considerations apply.
