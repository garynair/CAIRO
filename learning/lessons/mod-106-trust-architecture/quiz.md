# Module 106 — Quiz

Twenty questions. Answer key in the paired solutions repo.

---

## Section A — What trust means for AI systems (§1)

**Q1.** Which sense of "trust" is the subject of mod-106?

  a. Trust as a property of the system overall
  b. Trust as a runtime authorisation question
  c. Trust as a regulatory obligation
  d. Trust as a customer-perception attribute

**Q2.** Which of the following is **not** one of the
three composable questions trust architecture asks?

  a. Identity — is this agent who it claims to be?
  b. Capability — is this agent permitted to perform
     this operation?
  c. Context — do current conditions support performing
     this operation?
  d. Intent — does this agent genuinely want to do good?

**Q3.** True or false: Trust architecture and security
are the same discipline.

**Q4.** Short answer: in one sentence, distinguish
trust architecture from the audit ledger.

---

## Section B — Zero-trust adapted (§2)

**Q5.** Which NIST 800-207 tenet is most directly
adapted by "each agent operation is independently
authorised; prior operations do not extend authority"?

  a. All data sources are considered resources
  b. Access is granted on a per-session basis
  c. Access is determined by dynamic policy
  d. Authentication is dynamic and strictly enforced

**Q6.** Which of the following is named in §2.2 as a
place 800-207 was not designed for agentic AI?

  a. Workload identity
  b. Agent identity is not static; it is a composite
     of model + configuration + principal + session
  c. Network segmentation
  d. Certificate authority

**Q7.** Short answer: in one sentence, describe the
*blast-radius framing* for AI agents (§2.3).

---

## Section C — Identity and capability scoping (§3)

**Q8.** Which of these is **not** a typical attribute
of an AI agent's composite identity?

  a. Model identity (vendor + version)
  b. Configuration identity (system prompt + tools)
  c. Principal (on whose behalf)
  d. Model accuracy score on the latest eval

**Q9.** Which property is **not** required of capability
scopes per §3.2?

  a. Bounded
  b. Verifiable
  c. Short-lived
  d. Vendor-neutral

**Q10.** Short answer: in one sentence, describe the
revocation problem (§3.4) and one pattern that
addresses it.

---

## Section D — Trust scoring (§4)

**Q11.** Which property is **not** named as a strength
of deterministic scoring?

  a. Reproducible
  b. Auditable
  c. Adaptive to new threats
  d. Defendable

**Q12.** Which axis is named in §4.4 as one of the four
trust-scoring axes?

  a. Bias
  b. Identity
  c. Latency
  d. Throughput

**Q13.** Short answer: name one place where heuristic
scoring fits *adjacent to* deterministic authorisation.

**Q14.** True or false: A single combined trust score is
preferable to multiple orthogonal axes for transparency.

---

## Section E — Trust gates in the request path (§5)

**Q15.** Which gate placement pattern is described as
having the lowest latency but the weakest separation
from the agent?

  a. Reverse-proxy
  b. Resource-side
  c. Agent-side
  d. Gateway-mediated

**Q16.** Which is **not** one of the trust gate's
responsibilities per §5.2?

  a. Authenticate
  b. Verify capability
  c. Decide
  d. Re-train the model

**Q17.** Short answer: in one sentence, describe one
trade-off a trust gate imposes (§5.4).

**Q18.** True or false: Step-up authentication is the
right pattern for binary high-stakes / low-stakes
authorisation.

---

## Section F — Build, buy, or partner (§6)

**Q19.** Which is **not** named as a CAIRO contribution
to the build / buy / partner decision per §6.5?

  a. The requirements
  b. The risk assessment
  c. The program-level position
  d. The architecture choice itself

**Q20.** Short answer: in two sentences, describe the
*vendor capture* risk in trust architecture and one
mitigation.
