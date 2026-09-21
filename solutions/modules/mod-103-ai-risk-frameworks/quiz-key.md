# Module 103 — Quiz Answer Key

Answers and explanations for the [Module 103 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-103-ai-risk-frameworks/quiz.md).

---

## Section A — Framework vs program (§1)

**Q1. b.** Frameworks specify functions; programs need
artifacts, owners, cadences, and responses. The other
options are not wrong in spirit but miss the operational
gap §1 names.

**Q2. a.** MEASURE is the most demonstrable function. (b)
is the opposite of true; (c) is true of every function;
(d) is false.

**Q3.** Any answer naming the taxonomy as the *risk
vocabulary* the framework's *activity vocabulary* needs.
Example: "the framework tells you what activities to
perform; the taxonomy tells you what risks the activities
are treating, so the same risk is recognised across all
four functions."

---

## Section B — AI risk taxonomy (§2)

**Q4. c.** Exhaustive in three or more levels of depth is
**not** a property of a good taxonomy — the lecture notes
explicitly warn against three-level taxonomies (§2.5).

**Q5. False.** Risks should belong to one top-level
category. Risks that seem to fit multiple are typically
two related risks owned in different categories (§2.5).

**Q6.** Any answer from §2.5: borrowing OWASP as top-level
(distorts toward security), borrowing NIST sub-functions
as risks (confuses activities with risks), three-level
taxonomies (not used in practice), multi-category risks
(loses tracking).

---

## Section C — MAP in practice (§3)

**Q7. c.** Risk-treatment plan belongs to MANAGE.
Inventory, classification, and impact assessment are MAP
artifacts.

**Q8. c.** On any material system change. Annual review
also occurs but is not the *trigger*.

**Q9.** Any answer naming a §3.3 principle: specificity
("the model under-rates application from X" not "the
model could be biased"), separation from MANAGE, the
two-to-four-failure-modes-per-category discipline, or the
explicit rating exercise.

---

## Section D — MEASURE in practice (§4)

**Q10. b. Drift in input feature distribution.** It is a
true leading indicator. The others are lagging or mixed.

**Q11. c.** Defining the threshold after seeing data
invites motivated thresholds. The other answers are not
the reason.

**Q12. False.** A dashboard with no review cadence and no
audience is "wallpaper" per §4.5; remove it rather than
treat it as a record.

**Q13.** Any of the three from §4.4: staleness (eval set
is older than current production), contamination (eval
set used in training), coverage (eval set
under-represents populations production over-represents).

---

## Section E — MANAGE in practice (§5)

**Q14. b.** A structured library of treatments the
program knows how to apply. (a) is too broad; (c) is too
narrow; (d) is vendor-driven, not catalog-driven.

**Q15. c.** Programs that claim zero residual risk for
meaningful risks are not credible. The frameworks (a, d)
do imply residual-risk thinking but the *operational*
reason is credibility.

**Q16.** Any answer capturing §5.5: a program that uses
abundant controls without residual-risk discipline will
treat every risk down to "Low / accepted" and produce
implausible coverage — the *governance theatre* mode from
mod-101 §6.

**Q17. d. Independent third-party validation.** Not
required by the lecture notes. Required exception fields
are (a), (b), and (c) plus cadence of review.

---

## Section F — GOVERN continuously (§6)

**Q18. b.** The single source of truth for material
risks. Not every risk lives there (a); not just a
regulatory deliverable (c); not just for the board (d).

**Q19. d.** A comprehensive dashboard of every program
metric. The board report has a small handful of
indicators, not a dashboard (§6.3).

**Q20.** Any answer naming a §6.5 concrete pattern (e.g.,
MEASURE indicators consistently crossing thresholds in
one category triggering a policy update on required
controls for that category) **and** the failure-to-close
indicator (e.g., twelve months with no GOVERN changes
triggered by lower functions means the loop is not
closing).

---

Maintained by [Girish Nair](https://github.com/garynair)
