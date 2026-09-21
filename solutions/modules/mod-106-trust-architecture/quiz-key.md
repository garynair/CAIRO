# Module 106 — Quiz Answer Key

Answers and explanations for the [Module 106 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-106-trust-architecture/quiz.md).

---

## Section A — What trust means (§1)

**Q1. b.** Trust as a runtime authorisation question.
mod-106 specifically addresses Sense B (per §1.1);
Sense A is the subject of mod-101 through mod-105.

**Q2. d.** "Intent — does this agent genuinely want
to do good" is not one of the three composable
questions. The three are identity, capability,
context (§1.2). Intent is a meaningless question to
ask of an agent in runtime authorisation terms.

**Q3. False.** §1.3 — security and trust architecture
interact heavily but are distinct disciplines.

**Q4.** Any answer naming the *positive vs after-
the-fact* distinction. Example: "trust architecture
decides what is allowed to happen; the audit ledger
records what happened — they are complementary
artifacts."

---

## Section B — Zero-trust adapted (§2)

**Q5. b.** "Access is granted on a per-session basis"
maps to the "each agent operation is independently
authorised" adaptation in §2.1.

**Q6. b.** Agent identity is not static (per §2.2 —
identity is composite). The other options (a),
(c), (d) are areas 800-207 was specifically designed
for.

**Q7.** Any answer naming the unusually-large blast
radius for AI agents due to tool-calling chains,
cascading reasoning, and irretrievable actions.
Example: "AI agents have unusually large blast
radius because operations can chain through multiple
services, the agent's decision step can cascade
errors, and many actions cannot be retracted by
removing access."

---

## Section C — Identity and capability scoping (§3)

**Q8. d.** Model accuracy score on the latest eval
is **not** part of composite identity; it is a
property of the model but not an identity attribute.
The composite identity per §3.1 is: model identity,
configuration identity, principal, delegation chain,
session, origin.

**Q9. d.** Vendor-neutral is **not** a required
property. The required properties per §3.2 are
bounded, verifiable, and short-lived.

**Q10.** Any answer naming the revocation problem
and one pattern from §3.4. Example: "the revocation
problem is stopping the trust architecture from
honouring an agent's existing capability assertions
when something goes wrong; short-lived tokens
address this implicitly because expiration removes
need for active revocation."

---

## Section D — Trust scoring (§4)

**Q11. c.** Adaptive to new threats is named as a
strength of *heuristic* scoring, not deterministic
(§4.1 vs §4.2).

**Q12. b. Identity.** §4.4's starting axes are
Identity, Risk, Reliability, Autonomy.

**Q13.** Any §4.3-grounded answer. Example: "as a
flag-for-review signal alongside deterministic
authorisation — heuristic scoring catches patterns
deterministic scoring cannot, but does not authorise."

**Q14. False.** §4.4 argues for multiple orthogonal
axes; a single combined score hides the trade-off
structure.

---

## Section E — Trust gates (§5)

**Q15. c. Agent-side.** §5.1 — lowest latency
because it's in-process, but trusts the agent
process and can be bypassed.

**Q16. d. Re-train the model** is not a trust gate
responsibility. The five are authenticate, verify
capability, evaluate context, decide, log (§5.2).

**Q17.** Any §5.4 trade-off — latency, availability
dependency, operational complexity, developer
friction, false positives. Example: "trust gates
add latency on the user-experience critical path,
which for interactive agents requires careful
latency-budget design."

**Q18. False.** §5.5 — step-up is the right pattern
when binary allow / deny is too coarse, specifically
for high-blast-radius operations where legitimate
use is also expected.

---

## Section F — Build, buy, or partner (§6)

**Q19. d. The architecture choice itself** is **not**
a CAIRO contribution. The CAIRO contributes
requirements, risk assessment, program-level
position, and long-term maintenance posture; the
architecture choice belongs to engineering
executives (§6.5).

**Q20.** Any §6.4 answer. Example: "vendor capture
is the risk that the program's architecture becomes
structurally dependent on a specific vendor in ways
not visible at decision time; one mitigation is
standards-based interfaces (W3C VC, OAuth, OIDC) so
substitution is technically possible."

---

Maintained by [Girish Nair](https://github.com/garynair)
