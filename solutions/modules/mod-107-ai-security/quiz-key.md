# Module 107 — Quiz Answer Key

Answers and explanations for the [Module 107 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-107-ai-security/quiz.md).

---

## Section A — Threat landscape (§1)

**Q1. c.** Membership inference attacks are §1.2
("mostly theoretical"), not §1.1. The other options
are all named in §1.1 with documented incident bases.

**Q2. b.** Reward hacking in production is named in
§1.2 as remaining mostly theoretical.

**Q3. False.** §1.3 — broad-and-shallow is the
characteristic failure mode of programs that try to
defend everything.

**Q4.** Any answer noting that programs misallocate
when they spend effort on theoretical threats while
the seven documented categories continue producing
incidents. Example: "the misallocation pattern is
program effort on theoretical threats while the
seven documented categories — prompt injection,
exfiltration, adversarial inputs, poisoning, supply
chain, tool exploitation, denial of service —
continue producing incidents."

---

## Section B — Attack taxonomies (§2)

**Q5. c. NIST AI 100-2 E2023** — §2.3 names it as
the bridging framework.

**Q6. b. OWASP LLM Top 10** — §2.2 short-enough-to-
remember property.

**Q7.** Any answer naming the OWASP-for-priority +
ATLAS-for-vocabulary + NIST 100-2 for cross-classical-
LLM pattern. Example: "OWASP LLM Top 10 for LLM-
specific priority and executive communication; MITRE
ATLAS for threat-modelling vocabulary and incident
classification structure; NIST AI 100-2 E2023 for
cross-LLM-and-classical framing in regulator-facing
program documentation."

---

## Section C — Defense-in-depth (§3)

**Q8. d. Marketing layer** is not one of the nine.
The nine are principal, input, model, output, tool,
data, infrastructure, observability, response.

**Q9. b. Tool, output, response.** §3.2 names these
as the most common blind spots.

**Q10. False.** §3.4 — two layers using the same
technique are one control with two instances; two
layers using independent techniques are two
controls.

**Q11.** Any answer naming the test: a layer the
attacker can skip without consequence is not
providing protection. Example: "the bypass test asks
whether an attacker could skip a layer without
consequence — defense-in-depth means the attacker
must bypass *each* layer."

---

## Section D — Red-teaming (§4)

**Q12. d. Replace ongoing monitoring** — §4.2
explicitly distinguishes red-teaming from
monitoring; red-teaming surfaces failure modes;
monitoring detects production occurrences.

**Q13. c.** Before deployment + quarterly + on
material change for Tier 1 systems per §4.4.

**Q14. b. External red team or internal team in a
separate organisational branch.** §4.5 names this
as the strongest for Tier 1.

**Q15.** Any §4.3 element: scope, methodology,
independence, reporting, disposition, re-test,
evidence.

---

## Section E — The CAIRO × CISO boundary (§5)

**Q16. b. In the CISO's organisation.** §5.5 —
AI-specific security engineering sits with the CISO;
CAIRO's contribution is program design and oversight.

**Q17. c. Separate AI security incident channels** —
§5.4 collision pattern; produces duplication and loses
coherent posture.

**Q18.** Any answer noting the parallel discipline:
the CISO does the technical security work like MRM
does the technical model-risk work; the CAIRO sets
program-level requirements and addresses what the
CISO/MRM does not own (governance, AI-program
reporting, AI-specific regulator interfaces).

---

## Section F — AI incident classification (§6)

**Q19. c. Joint.** §6.4 — security (unauthorised
disclosure) and AI-program (agent behaviour
failure); CAIRO leads because EU AI Act Art. 73 may
apply.

**Q20.** Any answer noting an Art. 73 timeline
(immediate / 2 days / 15 days) and explaining that
real-time classification negotiation during the
incident consumes the notification window.
Example: "EU AI Act Art. 73 requires 2-day
notification for fundamental-rights incidents;
programs that negotiate classification during the
incident consume that 2-day window on internal
debate, so the taxonomy must be pre-computed for the
notification trigger to fire in time."

---

Maintained by [Girish Nair](https://github.com/garynair)
