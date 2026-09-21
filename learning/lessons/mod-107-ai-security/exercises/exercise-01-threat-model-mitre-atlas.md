# Exercise 01 — Threat-Model an AI System Using MITRE ATLAS

**Estimated time**: 3 hours
**Deliverable**: An ATLAS-aligned threat model
(≤ 3 pages)

---

## The scenario

You are the CAIRO at **Tessera Bank**. Use the agentic
customer-service agent from mod-106 (the agent with
account-read, message-send, dispute-initiation, funds-
transfer, appointment-scheduling, and profile-update
capabilities). The CISO has asked you to contribute the
**program-level threat model** that the security
engineering team will use to design defences.

The CISO's specific ask: a threat model that uses
**MITRE ATLAS** as the primary vocabulary, supplemented
by **OWASP LLM Top 10** and **NIST AI 100-2 E2023** where
they add precision the ATLAS treatment misses. The goal
is *program-level* coverage — not engineering depth.

## Your assignment

Produce a threat model with the following structure.

### Section 1 — System summary (≤ ½ page)

Brief restatement of the agent's surface — purpose,
inputs, outputs, downstream tools/resources,
principal layer. Reference Exercises 01–04 from
mod-106 for the trust architecture context.

### Section 2 — ATLAS-aligned threat enumeration (≤ 1½ pages)

Walk through MITRE ATLAS tactics. For **each** of:

- **ML model access** (which techniques apply)
- **Execution** (which techniques apply)
- **Defense evasion** (which techniques apply)
- **Exfiltration** (which techniques apply)
- **Impact** (which techniques apply)

For each applicable tactic, name the **specific
techniques** that are credible threats to this agent.
Cite the ATLAS technique IDs (e.g., AML.T0010 for
ML supply-chain compromise). For each technique, note:

- A one-line description of how the technique would
  manifest against this specific agent.
- Likelihood: High / Medium / Low.
- Blast radius: High / Medium / Low.

Aim for 8–15 specific techniques total across the
tactics. More than 20 is over-enumeration; fewer
than 6 is under-coverage.

### Section 3 — OWASP supplements (≤ ¼ page)

For each OWASP LLM Top 10 category that applies and
is not adequately covered by the ATLAS treatment,
note the gap and the OWASP framing. Common
supplements: excessive agency (LLM06), unbounded
consumption (LLM10).

### Section 4 — NIST AI 100-2 cross-reference (≤ ¼ page)

For the **2–3 highest-priority** threats from §2,
cross-reference NIST AI 100-2 E2023's attack-goal
framing (availability / integrity / confidentiality
/ abuse) and its adversary-knowledge framing (white-box
/ grey-box / black-box). The cross-reference grounds
the program in framework vocabulary regulators expect.

### Section 5 — Priority ranking (≤ ½ page)

Rank the threats from §2 by **(likelihood × blast
radius)**. Identify the top **3** as program-level
priorities — these are the threats the CISO is
expected to invest in defending against. Provide
one-paragraph defence of each ranking.

## Constraints

- Cite **specific** ATLAS technique IDs, not just
  tactic names.
- Do not enumerate every conceivable threat. The
  §1.3 misallocation pattern is the failure mode.
  Programs that list 50 threats invariably defend
  none of them well.
- The priority ranking must be **defensible**.
  Programs that claim every threat is high priority
  produce defences that are broad and shallow.
- Stay at **program level**. Specific control
  recommendations belong to the CISO's engineering
  team; this threat model specifies *what to
  protect against*, not *how*.
- Include at least one threat that involves the
  **trust architecture from mod-106** — the
  agent's capability scope and identity boundary
  are themselves part of the threat surface.

## Rubric

| Criterion | Weight |
|---|---|
| ATLAS technique citations — specific, accurate | 25% |
| Coverage — 8–15 techniques, with restraint | 15% |
| Per-threat manifestation — agent-specific, not generic | 20% |
| OWASP supplements — meaningful, not redundant | 10% |
| NIST 100-2 cross-reference — substantive | 10% |
| Priority ranking — defensible top 3 | 15% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`solutions/modules/mod-107-ai-security/exercise-01-threat-model-mitre-atlas/SOLUTION.md`

Reference solution lists 11 techniques across 5
tactics. Top 3 priorities: prompt injection (with
agent-tool-invocation pathway), data exfiltration
via output, ML supply-chain compromise of the
vendor LLM.

## Reading before you start

- Lecture notes §1 (threat landscape) and §2
  (taxonomies).
- mod-106 (trust architecture) — Exercises 01–04
  reference solutions for the agent context.
- MITRE ATLAS website — at least skim the tactics
  list and pick 5–8 techniques per tactic you'll
  treat.
