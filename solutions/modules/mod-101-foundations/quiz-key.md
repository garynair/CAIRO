# Module 101 — Quiz Answer Key

Answers and short explanations for the [Module 101 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-101-foundations/quiz.md).

---

## Section A — Vocabulary (§1)

**Q1. b.** Governance is about *who decides and how you know
it worked*; compliance is about *external rules you must
satisfy*. Answer (a) confuses governance with ethics. Answer
(c) makes governance and ethics co-extensive, which they are
not. Answer (d) is a common mistake by new CAIROs and is the
direct cause of the "compliance-only stance" failure mode
(§6).

**Q2. True.** Model risk management is a category within
governance. SR 11-7 lives inside the broader governance
function in any well-structured organization.

**Q3.** Any two of: capability shift (post-2022 generative
systems removed the bounded blast radius), regulatory wave
(EU AI Act, NYDFS, NIST AI RMF, ISO 42001), incident base
(public record of cross-functional AI failures).

---

## Section B — NIST AI RMF (§2)

**Q4. d. GOVERN.** Per the lecture notes, GOVERN operates
continuously across MAP, MEASURE, and MANAGE.

**Q5. b.** AI system inventory with use-case
classifications. The other artifacts belong to MEASURE
(dashboard), MANAGE (risk treatment plan), or GOVERN
(board report).

**Q6.** Any answer that captures the *operating system vs.
application* distinction. Example: "NIST AI RMF tells you
what functions need to exist but not what good looks like
inside each function — a program can implement all four
functions and still produce dashboards that no one acts on."

---

## Section C — Three Lines of Defense (§3)

**Q7. b.** The AI risk function that authors the policy
hierarchy is second-line. (a) is first-line, (c) is
third-line, (d) is first-line.

**Q8. c.** AI risk function reporting to the CTO breaks 3LOD
because the CTO is accountable for the AI shipping work that
the risk function oversees. (a), (b), and (d) all preserve
independence.

**Q9.** Any answer naming an arrangement where independence
exists on paper but not in practice. Examples: "AI risk
function reports through the engineering executive whose work
they oversee, even if titled as independent." Or: "The
second-line lead's performance review is signed by the
first-line VP whose work they oversee."

---

## Section D — The CAIRO role (§4)

**Q10. b.** Ownership of model selection decisions is
explicitly *not* CAIRO scope. That is a first-line decision.

**Q11. c.** CAIRO → CTO. The lecture notes also identify CAIRO →
CIO and CAIRO → General Counsel as non-viable; (a), (b), and
(d) are the three viable lines.

**Q12. False.** The lecture notes are explicit that the role
is right for an org only when at least two of five readiness
conditions are met.

**Q13.**
- CISO → **b** (AI-specific threat models + AI incident
  classification)
- CDO (Data) → **c** (training-data provenance + downstream
  use restrictions)
- General Counsel → **a** (regulatory engagement strategy +
  filings)

**Q14.** The likely failure mode is **The Tech Evangelist**.
A retitled senior researcher cannot credibly oversee the
function they came from (the second-line independence test
fails immediately), and tends to merge first- and
second-line accountabilities.

---

## Section E — Operating models (§5)

**Q15. c.** Hub-and-spoke is described as the most common
mature pattern for mid-to-large orgs.

**Q16. b.** Inconsistency across business units is the
primary weakness of fully federated.

**Q17.** Any defensible answer naming an org type where
consistency dominates speed. Examples: "small-to-medium
orgs where a single CAIRO function can credibly cover all the
work"; "heavily regulated single-industry orgs where
consistent regulator interface matters more than business-
unit speed."

---

## Section F — Failure modes (§6)

**Q18. b. Control sprawl.** Symptom: governance team's main
work becomes processing exceptions.

**Q19. c. Regulatory whiplash.** Symptom: policy hierarchy
maps directly to regulators rather than to risks.

**Q20.** Answers should distinguish:

- *Compliance-only stance* — the program scopes itself to
  what regulators have asked about. Surprised by every
  un-asked risk.
- *Governance theatre* — the program builds elaborate
  apparatus that does not change behavior. Surprised by
  failures that occur despite the apparatus.

Both fail to change outcomes; they fail for different
reasons. Compliance-only is *too narrow*; theatre is *too
ceremonial*. The same program can suffer both
simultaneously.

---

Maintained by [Girish Nair](https://github.com/garynair)
