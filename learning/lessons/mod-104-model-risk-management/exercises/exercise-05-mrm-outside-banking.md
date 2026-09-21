# Exercise 05 — Apply MRM Outside Banking

**Estimated time**: 3 hours
**Deliverable**: An MRM-equivalent program design for a
non-bank context (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Cardinal Health Network**, an
800-hospital-bed regional healthcare system. Cardinal
has 14 AI/ML systems in production. A new state
healthcare regulator has asked, in writing, whether
Cardinal has a *model risk management* discipline
analogous to the one used in banking. Cardinal does not
— it has a clinical-safety review process and a
device-quality program but nothing that maps directly
to SR 11-7.

The CEO has asked you to design an **MRM-equivalent
program** for Cardinal. The CEO will present the design
in response to the regulator.

## Your assignment

Produce a 3-page program design that addresses, at
minimum:

### Section 1 — Translation (½ page)

A short statement of how SR 11-7's discipline translates
to Cardinal's context:

- What "model" means at Cardinal (use the local
  vocabulary — *device algorithm*, *clinical-decision-
  support tool*, etc. — per §6.2 of the lecture notes).
- Which SR 11-7 disciplines translate directly and which
  need adaptation (per §6.1 / §6.2).
- Which Cardinal functions are the analogs to MRM and
  to the AI program.

### Section 2 — The four pillars at Cardinal (1½ pages)

For each of SR 11-7's four pillars:

1. **Robust development, implementation, and use** —
   how does this work at Cardinal?
2. **Sound validation processes** — who validates
   (existing or new)?
3. **Strong governance, policies, controls** — what
   governance bodies, what policies, what controls?
4. **A firm-wide framework integrating the above** —
   what is the integrating artifact at Cardinal?

For each pillar, name the **existing Cardinal function**
that owns it (the new program should reuse where it can)
and the **gap** that needs to be filled by new work.

### Section 3 — Tiering (½ page)

A tiering scheme for Cardinal's 14 AI/ML systems. Use the
§2.2 starting scheme as a base, adapted for healthcare:

- Tier 1 Critical — criteria including FDA-cleared
  SaMD, EU MDR Class IIa or higher, anything affecting
  acute clinical decisions.
- Tier 2 Important — criteria.
- Tier 3 Standard — criteria.

You do not need to list all 14 systems; describe the
tiering criteria + name 2 example systems per tier.

### Section 4 — Independence and the clinical-authority
boundary (½ page)

The hardest section in healthcare. How does
*independence* work when:

- The clinical authority (Chief Medical Officer + Chief
  Quality Officer) is the natural validator on clinical
  grounds.
- The AI program is the natural validator on AI-program
  grounds.
- Neither is independent of the clinical-system
  development process.

Propose an arrangement. Honestly note where independence
is imperfect.

## Constraints

- **3 pages, hard limit.**
- The program must **reuse existing Cardinal functions**
  where possible. Building parallel machinery is more
  costly than adapting existing.
- The translation in §1 must explicitly **not** force
  banking vocabulary on Cardinal. *Model* may be used
  but the design must show awareness of the local
  language.
- The independence discussion in §4 must be **honest**
  about imperfection. A claim of perfect independence
  in a 800-bed hospital system is implausible.
- The design must **address the regulator** — what will
  the CEO say if the regulator asks "is this MRM?".

## Rubric

| Criterion | Weight |
|---|---|
| Translation — context-aware, vocabulary-respecting | 15% |
| Four pillars — each addressed with existing-owner + gap | 30% |
| Tiering — healthcare-adapted, criteria specific | 15% |
| Independence — honest, structurally addressed | 20% |
| Regulator framing — explicit response to "is this MRM?" | 10% |
| Length discipline — ≤ 3 pages | 10% |

## Where to submit

`solutions/modules/mod-104-model-risk-management/exercise-05-mrm-outside-banking/SOLUTION.md`

Reference solution uses Cardinal's existing Chief Quality
Officer's office as the MRM-equivalent home, with the
CAIRO function providing AI-specific overlays. The
clinical-authority independence problem is solved by
*structural workflow constraints* on the clinical-
decision-support systems, not by personnel independence.

## Reading before you start

- Lecture notes §6 (MRM beyond banking) and §6.3
  (healthcare adaptation).
- mod-101 Exercise 03 (Aldwych Health) and mod-102
  Exercise 03 (Aldwych Article 9 RMS) — for tone of
  healthcare-context governance.
- mod-103 Exercise 05 (Kerridge Healthcare retinal-
  imaging system) — for a healthcare-AI example shape.
