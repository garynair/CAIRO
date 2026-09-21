# Module 108 — Quiz Answer Key

Answers and explanations for the [Module 108 quiz](https://github.com/garynair/CAIRO/blob/main/learning/lessons/mod-108-audit-ledgers-and-evidence/quiz.md).

---

## Section A — What evidence is for (§1)

**Q1. d. Customer-experience integration** is not
one of the three. The three are provenance,
completeness, tamper resistance.

**Q2. True.** §1.2 — the working test for evidence
is whether a hostile replacement could lie about
history undetectably.

**Q3.** Any answer naming evidence as records-of-
what-happened vs. justification as records-of-why.
Example: "evidence records what happened; it does
not justify why — justification lives in policy
documents, decision memos, and incident reports
that evidence references but does not replace."

---

## Section B — Tamper-evident ledger pattern (§2)

**Q4. b. About 30 hashes.** Merkle inclusion proof
is log₂(n); log₂(10⁹) ≈ 30.

**Q5. b. Append-only with public commitments +
witness signatures + external monitors.** §2.3
names these as the CT structural properties that
transfer to AI audit.

**Q6. False.** §2.4 — the Merkle pattern
guarantees inclusion, not authenticity. A
compromised emitter can write false records that
the ledger faithfully preserves.

**Q7.** Any §2.4 limitation. Example:
"confidentiality — anyone with ledger access sees
what's in it; the Merkle pattern provides
integrity, not confidentiality."

---

## Section C — Event vocabulary (§3)

**Q8. b. Every operation that has program-relevant
consequences.** §3.1.

**Q9. d. Employee email contents** is not in the
§3.2 list of evidence-relevant categories. Email is
operational; only enters evidence if a specific
event references it.

**Q10. False.** §3.3 — large artifacts live in
object storage and are referenced by hash from
events; events should be small.

**Q11.** Any §3.4 consequence. Example: "without a
registry, new systems emit events using novel
field names that the analysis layer doesn't
recognise, producing vocabulary drift and analysis
gaps that surface only at audit time."

---

## Section D — Evidence packages (§4)

**Q12. d. The model's training weights** is **not**
a typical evidence package element. Packages
include cover, scope, evidence records, inclusion
proofs, consistency proof, supporting artifacts,
chain of custody, signature.

**Q13. b. Regulator quarterly attestations.** §4.4
— these are recurring and benefit from pre-built
templates. One-off requests (a, c, d) are
typically ad hoc.

**Q14.** Any §4.5 verification protocol step.
Example: "verify each evidence record's inclusion
proof against the ledger's published
commitments."

---

## Section E — Retention, sealing, chain of custody (§5)

**Q15. b. 6 months.** EU AI Act Art. 12 minimum
retention. Longer may apply per other EU law.

**Q16. False.** §5.1 — keeping more than needed is
itself a risk (privacy, breach exposure).
Retention is calibrated to obligations, not
maximised.

**Q17. d. The retail price of the evidence** is
not a chain-of-custody record element. The four
are: emitting system, signing key, intermediate
handling, recipients and timestamps.

**Q18.** Any §5.4 answer. Example: "email is not
a controlled channel — once evidence is
transmitted via email, chain of custody breaks
because Halverston / Tessera does not control the
mail-transport infrastructure that handles it."

---

## Section F — Build, buy, or partner (§6)

**Q19. b. Migration risk.** §6.4 names this as
most insidious for audit-ledger buying because
evidence has long retention requirements and
moving sealed evidence with preserved integrity
properties is a multi-quarter project.

**Q20.** Any §6.5 contribution. Example: "the
requirements — what evidence the infrastructure
must produce, what audiences it must serve, what
regulatory obligations it must satisfy; this is
what the CAIRO contributes to the engineering /
security-led decision."

---

Maintained by [Girish Nair](https://github.com/garynair)
