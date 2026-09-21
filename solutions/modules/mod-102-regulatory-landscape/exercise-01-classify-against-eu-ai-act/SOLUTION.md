# Exercise 01 — Classify Five Systems Against EU AI Act — Reference Solution

## 1. Solution overview

Three of the five systems are high-risk; one is limited-risk;
one is minimal-risk. Two of the high-risk classifications
turn on subtle facts. The Art. 6(3) exemption is considered
for one system and ultimately rejected.

## 2. Classification table

| System | Tier | Article(s) | Annex III area | Art. 6(3) applies? | Key fact |
|---|---|---|---|---|---|
| A — Resume screening | **High-risk** | Art. 6(2) via Annex III(4)(a) | Recruitment / advertising / filtering of applications | **No** — see reasoning §A | 90% follow-through means it is *de facto* the selection step |
| B — Bank chat agent | **Limited-risk** | Art. 50(1) | — | n/a | No adverse decisioning; transparency obligation only |
| C — Worker-attention monitor | **High-risk** | Art. 6(2) via Annex III(4)(b) | Monitoring / evaluation of workers; used in disciplinary processes | **No** — disciplinary use defeats exemption | Disciplinary use is the determinative fact |
| D — Engine predictive maintenance | **High-risk** | Art. 6(1) — safety component of regulated aviation product | — | n/a | Aircraft components are regulated under EASA / Part 21 |
| E — ED triage support | **High-risk** | Art. 6(2) via Annex III(5)(a) | Access to essential private / public services — health | **No** — see reasoning §E | Influences clinical decision-making at intake |

## 3. Reasoning per system

### §A — Resume-screening assistant

Annex III(4)(a) covers AI systems used for *"recruitment or
selection of natural persons, in particular to place
targeted job advertisements, to analyse and filter job
applications, and to evaluate candidates."* This system
analyses and filters; that puts it inside Annex III(4)(a).

**Art. 6(3) exemption analysis.** The system description
positions the AI as "an assistant to recruiter judgment" —
which sounds like the exemption condition *"detect
decision-making patterns or deviations from prior
decision-making patterns... not meant to replace or
influence the previously completed human assessment."* But
the 90% follow-through rate on top recommendations is
determinative: the recruiter is, in practice, following the
AI. The exemption requires that the AI not *influence* the
human assessment. 90% follow-through is influence. The
exemption fails.

**What would change the tier.** If the system surfaced
multiple candidates as a *long list* (not a ranked
shortlist) and the recruiter independently evaluated each, a
defensible Art. 6(3) argument could be made. The current
ranked top-K design forecloses it.

### §B — Customer-service chat agent

This system makes no adverse decisions. It does not
underwrite credit, approve transactions, or determine
account eligibility. It surfaces information; the bank's
existing decision systems remain authoritative.

That places it outside Annex III. Art. 50(1)'s transparency
obligation applies because the system interacts directly
with natural persons; the system already discloses itself
at session start, satisfying Art. 50(1) on its face.

**What would change the tier.** Adding any decision capability
— credit pre-qualification, dispute auto-resolution, account
restriction — would re-evaluate the system against Annex
III(5)(b) (essential private services, financial). At that
point the analysis becomes substantive.

### §C — Worker-attention monitor

Annex III(4)(b) covers AI used to *"make decisions affecting
terms of work-related relationships, the promotion or
termination of work-related contractual relationships, or
to allocate tasks based on individual behaviour."* The
system is used in disciplinary processes — that fits
*"decisions affecting terms of work-related relationships."*

**Art. 6(3) analysis.** If the system were limited to in-cab
fatigue alerts with no follow-up consequences, Art. 6(3) on
*preparatory task* might apply. The disciplinary-process use
is determinative against the exemption.

**What would change the tier.** Removing the disciplinary-
process tie. The lecture notes' §1 discussion of how
sector-based and rights-based lineages intersect applies
here: even with the EU AI Act tier change, EU works-council
consultation rules would still apply.

### §D — Engine predictive maintenance

This system is a safety component of an aircraft. Aircraft
components are regulated under EU sectoral law (EASA Part
21, Part M, etc.) and are subject to third-party conformity
assessment. That puts the system inside Art. 6(1).

**Note.** Art. 6(1) high-risk classification is
*automatic* — no Annex III analysis needed. The Act's
treatment of safety-of-machinery / aviation / medical-device
products is layered on top of existing sectoral law.

**What would change the tier.** Nothing within the current
regulatory regime. EASA could in theory carve out
predictive-maintenance recommendations from "safety
components," but as of 2026 they have not.

### §E — ED triage support

Annex III(5)(a) covers AI systems used for *"evaluation and
classification of emergency calls by natural persons or to
dispatch, or to establish priority in the dispatching of,
emergency first response services."* That covers ED triage
intake.

**Art. 6(3) analysis.** The system "suggests" an ESI level
that triage nurses retain authority over. That sounds like
Art. 6(3)'s "preparatory task" exemption. But the system's
output is the **first signal** in the triage workflow —
nurses see the AI's suggestion before forming their own
judgement. This influences the assessment, not just
prepares for it. The exemption fails.

**What would change the tier.** Restructuring the workflow
so that the nurse independently forms an ESI judgment first
and *then* sees the AI's suggestion as a check (a
"deviation-from-prior-decision" detector). The Art. 6(3)
exemption explicitly contemplates this design. But it is a
meaningful workflow change, not a paperwork fix.

## 4. Reasoning notes

- **The hardest classification is System A.** Art. 6(3)
  exemption arguments are seductive — they let the operator
  avoid the high-risk obligations. Most operators will try
  to fit their system into Art. 6(3). The 90% follow-through
  metric in the description is the discipline: empirically,
  the recruiter is following the AI. Self-described
  *assistant* language does not survive empirical follow-
  through.
- **System D is the *most automatic*** — Art. 6(1) is the
  cleanest classification path in the Act. Most CAIROs will
  jump to Annex III analysis and miss Art. 6(1). When the
  product is already under sectoral conformity assessment,
  Art. 6(1) is checked first.
- **System E is the *most morally fraught*** — the nurse
  retains authority, the system was built specifically to
  support clinical judgement, and yet the analysis is high-
  risk. The Act is doing its job here: high-risk
  classification is not a moral judgement of the system; it
  is a procedural finding that triggers obligations.
- **A note on Art. 50 (limited-risk).** Many CAIROs read
  Art. 50 as a residual category. It is not — it is
  specifically about transparency to affected persons.
  System B is limited-risk because Art. 50(1) substantively
  applies and the system already satisfies it.

---

Maintained by [Girish Nair](https://github.com/garynair)
