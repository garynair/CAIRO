# Module 104 — Quiz Answer Key

Answers and explanations for the [Module 104 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-104-model-risk-management/quiz.md).

---

## Section A — What SR 11-7 actually says (§1)

**Q1. a.** Fundamental error and misuse. SR 11-7 §I
explicitly names both. Programs that address only
fundamental error miss half of what SR 11-7 is doing.

**Q2. d.** Independent third-party audit firm engagement
is **not** a pillar. The four pillars are (a), (b), (c),
plus a firm-wide MRM framework integrating them.

**Q3.** Any answer naming the *examiner-breadth* logic.
Example: "examiners read 'model' broadly under SR 11-7,
and any attempt to define a system out of scope is read
as evasion, drawing harder questions about the rest of
the program."

**Q4. b. Second line.** MRM is independent oversight,
separate from first-line model owners and from third-
line internal audit.

---

## Section B — Model tiering (§2)

**Q5. c. Always uses three tiers.** Tiering schemes can
have three, four, or more tiers; the count is not the
property that matters.

**Q6. b. Model size / inscrutability.** §2.3 mentions
this as a possible additional tiering input for ML.

**Q7. False.** §2.4 names "tiering everything as Tier 1
to be safe" as an anti-pattern that overwhelms MRM and
degrades the program silently.

---

## Section C — Independent validation (§3)

**Q8. b.** Evaluation of conceptual soundness is one of
the four elements in SR 11-7 §IV. The others are ongoing
monitoring, outcomes analysis, and benchmarking. (a),
(c), and (d) are not elements named in the source.

**Q9. c. Human evaluation by domain experts.** §3.2
identifies this for LLM outputs without ground truth.

**Q10.** Any answer naming the *after-failure bias* test.
Example: "if the model fails in production, can the
validation team be reasonably accused of bias toward the
model owner — if yes, independence is insufficient."

**Q11. b. Prompt template change.** §3.4 lists this as a
material change for LLM systems often missed because
classical-model triggers do not name it.

---

## Section D — The model lifecycle (§4)

**Q12. b.** Implementation review and retirement. §4.2
identifies these as the two stops most often skipped.

**Q13.** Any answer naming the *deployment-infrastructure
vs. model artifact* gap. Example: "ML systems often have
a deployment infrastructure — serving stack, prompt
template, post-processing — that is as load-bearing as
the model itself; implementation review covers this."

---

## Section E — CAIRO × MRM boundary (§5)

**Q14. c. Re-validation of MRM-validated models by the
CAIRO function** is named in §5.5 as a collision pattern.
(a), (b), and (d) are working patterns from §5.4.

**Q15. b.** Independent validation of models within MRM
scope is MRM's. (a), (c), and (d) are CAIRO function
ownership per §5.2.

**Q16.** Any §5.3 intersection topic with a working
operational pattern. Example: "ML model validation —
MRM does the validation, CAIRO contributes the validation
expectations for AI-specific risk categories (e.g.,
subgroup fairness as a required validation pattern)."

---

## Section F — MRM outside banking + comprehensive (§6 + cross)

**Q17. c. The four-pillar framework.** §6.1 identifies
this as the discipline that translates well across all
sectors.

**Q18. True.** §6.6 explicitly applies SR 11-7's misuse
framing to industrial AI deployments beyond the
validated envelope.

**Q19. d. Quarterly regardless of change.** SR 11-7 does
not mandate quarterly re-validation; periodic cadence
typically is annual for material models, and event-driven
otherwise. (a), (b), (c) are the named triggers in §3.4.

**Q20.** Any §5.6 pattern with its trade-off named.
Example: "both CAIRO and MRM report to CRO — easier
coordination but risk that organizational gravity pulls
AI work into being treated as 'another MRM team'."

---

Maintained by [Girish Nair](https://github.com/garynair)
