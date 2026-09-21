# Exercise 02 — Design a Red-Team Exercise

**Estimated time**: 4 hours
**Deliverable**: A red-team exercise design + scoring
rubric (≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank**. The agentic
customer-service agent (Exercise 01 + the mod-106
context) is approaching production deployment. Per
the AI Risk Council's policy, every Tier 1 system
must be red-teamed before deployment. The CISO has
asked you to **author the red-team exercise design**
that the security engineering team will execute.

The red team will be a **mixed team** — two
external security researchers contracted for this
exercise plus three internal security engineers from
the CISO's organisation, none of whom worked on the
agent's development. The exercise will run for **one
business week**.

## Your assignment

Produce a red-team exercise design with the
following structure.

### Section 1 — Scope and goals (≤ ½ page)

State:

- **Scope** — what is in scope (the agent + its
  trust architecture + downstream tools); what is
  out of scope (Tessera's classical security
  perimeter; the vendor LLM's internal weights;
  customer device compromise).
- **Goals** — three specific outcomes the exercise
  is trying to demonstrate. Examples: (a) whether
  the trust gates from mod-106 Ex-04 fail closed
  under adversarial pressure; (b) whether the
  capability scoping prevents tool-call
  exploitation; (c) whether the output filters
  prevent PII leakage.

### Section 2 — Threat scenarios (≤ 1 page)

For each of **4–6 specific threat scenarios** the
red team will execute, specify:

- **Scenario name**.
- **Aligned ATLAS techniques** (cite IDs).
- **Specific actions** the red team will take.
- **Expected defence layer(s) being tested** (per
  mod-107 §3.1).
- **Success criteria for the red team** (what
  constitutes a finding).
- **Success criteria for the defenders** (what
  would mean the defence held).

### Section 3 — Rules of engagement (≤ ½ page)

What the red team can and cannot do:

- Authentication and access boundaries (e.g., red
  team operates as authenticated customers, not as
  internal employees with elevated privilege).
- Data handling (e.g., if a vulnerability would
  produce real PII, document the exploit but do
  not retain the PII).
- Coordination with operations (e.g., daily check-in
  with the AI Risk Lead; immediate notification on
  any actual customer-impacting find).
- Out-of-scope actions (e.g., no DDoS attempts; no
  social engineering of Tessera employees).
- Time-box — start, end, and any restricted hours.

### Section 4 — Scoring rubric (≤ ½ page)

How findings will be graded. Include dimensions for:

- **Severity** — what is the impact if exploited.
- **Exploitability** — how hard is the attack to
  execute.
- **Reproducibility** — can the finding be
  reproduced reliably.
- **Detection** — was the attack detected by
  Tessera's monitoring during the exercise.

Provide a specific numeric or categorical scale for
each dimension and a way to combine them into an
overall priority.

### Section 5 — Reporting and disposition (≤ ½ page)

Specify:

- **What the red team produces** — findings report
  format, evidence retention.
- **Who receives findings** — initial briefing
  recipients, full report distribution.
- **Triage process** — how findings are converted
  into remediation tickets.
- **Re-test policy** — when and how findings are
  re-tested after remediation.
- **Evidence for audit** — what artifacts get
  retained for the audit + regulator file.

## Constraints

- The exercise must include **at least one trust-
  gate stress test** — testing whether the mod-106
  trust architecture holds.
- The exercise must include **at least one
  capability-scope test** — testing whether the
  agent's signed capability scope prevents an
  attempted out-of-scope tool call.
- Rules of engagement must explicitly **prohibit
  actual customer harm**. PII observations are
  documented; exploitation that would harm real
  customers is not permitted.
- The scoring rubric must address **detection** —
  whether Tessera's monitoring would have caught
  the attack in production is part of the finding,
  not separate from it.
- Reporting must include both an **immediate
  briefing** (within 24 hours of exercise end) and
  a **full report** (within 10 business days).

## Rubric

| Criterion | Weight |
|---|---|
| Scope and goals — three specific goals, defensible | 10% |
| Threat scenarios — 4–6, ATLAS-aligned, layer-specific | 30% |
| Rules of engagement — comprehensive, customer-protective | 15% |
| Scoring rubric — four dimensions specified | 20% |
| Reporting and disposition — both immediate and full | 15% |
| Length discipline — ≤ 3 pages | 5% |
| Trust-gate stress test included | 5% |

## Where to submit

`solutions/modules/mod-107-ai-security/exercise-02-design-red-team-exercise/SOLUTION.md`

Reference solution has 5 threat scenarios; the trust-
gate stress test specifically attempts to bypass
Gate 2's revocation check.

## Reading before you start

- Lecture notes §4 (red-teaming).
- Exercise 01 reference solution (for the threat
  context).
- MITRE ATLAS technique catalog (for scenario
  construction).
