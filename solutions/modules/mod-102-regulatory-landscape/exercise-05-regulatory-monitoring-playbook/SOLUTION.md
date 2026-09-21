# Exercise 05 — 90-Day Regulatory Monitoring Playbook — Reference Solution

## 1. Solution overview

This reference playbook is for a US bank with EU exposure
(roughly the Trillium profile from Exercise 04, with the
addition of EU operations). It deliberately stays inside
three pages, names every source owner, and explicitly
declares what it is *not* monitoring. Total time budget per
cycle: roughly 6 hours of named-role labor per week, with a
quarterly review at 1 full day.

---

## 2. The playbook

> **Regulatory Monitoring Playbook v1.0**
> *AI Governance Function — Trillium-Bancorp-class US bank
> with EU operations*

### §1 — Scope of monitoring

**In scope.**

- US federal banking regulators (OCC, FRB, FDIC) and
  consumer-financial regulators (CFPB) — for AI-relevant
  guidance, enforcement, and examiner letters.
- New York state regulator (NYDFS) — for Part 500 AI
  amendments and related guidance.
- EU Commission (AI Office) and the European Data
  Protection Board — for EU AI Act implementing acts and
  delegated acts.
- National competent authorities in the EU member states
  where Trillium has operations — for enforcement and
  guidance specific to those member states.

**Out of scope.**

- US state laws outside of New York, California, and
  Colorado (covered at the obligations-register level,
  not actively monitored). Other states added on
  evidence of regulatory activity that affects
  Trillium-class banks.
- Non-AI-specific changes to regulations already in scope
  (those go to the relevant function — CISO, GC,
  Compliance — not to this monitoring function).
- Academic AI policy literature. Read selectively, not
  monitored.

**Trigger thresholds for surfacing change.**

A change is surfaced if it is any of: a final or draft rule
adopted by a regulator in scope; an enforcement action
against a peer institution; a regulator letter to a peer
that has become public; a substantive change to a Tier-1
framework (NIST AI RMF, EU AI Act, ISO 42001).

A change is **not** surfaced if it is: an internal
regulator workshop notice; an academic article; a vendor
white paper; a peer institution's blog post about their
own program.

### §2 — Source list

**Weekly cadence (Mondays).**

| Source | URL / feed | Owner |
|---|---|---|
| OCC bulletins + interpretations | occ.gov / bulletins | AI Risk Lead |
| FRB SR letters | federalreserve.gov / supervisionreg / srletters | AI Risk Lead |
| FDIC FILs | fdic.gov / news / financial-institution-letters | AI Risk Lead |
| CFPB enforcement and guidance | consumerfinance.gov | AI Risk Lead |
| NYDFS guidance | dfs.ny.gov | AI Risk Lead |

Time budget per week: 90 minutes.

**Monthly cadence (first Tuesday of month).**

| Source | URL / feed | Owner |
|---|---|---|
| EU AI Office news + delegated acts | digital-strategy.ec.europa.eu | EU Counsel + Regulatory Engagement Lead |
| EDPB opinions | edpb.europa.eu | EU Counsel |
| Member-state DPA enforcement (FR CNIL, IE DPC, DE BfDI) | per-DPA feeds | EU Counsel |
| NIST AI RMF updates + Playbook revisions | nist.gov / itl / ai-risk-management-framework | Policy Lead |
| ISO 42001 amendments | iso.org via subscription | Policy Lead |

Time budget per month: 4 hours.

**Quarterly cadence (first week of quarter).**

| Source | URL / feed | Owner |
|---|---|---|
| Tier-1 framework review (NIST + ISO + EU AI Act + sector) | per source | CAIRO + Policy Lead + AI Risk Lead |
| Peer-institution enforcement scan | regulator publications + industry sources | AI Risk Lead |
| Internal obligations-register refresh | internal | CAIRO + Policy Lead |
| US state patchwork — full survey | state-by-state | Policy Lead |

Time budget per quarter: 1 full day for CAIRO, 2 days each
for Policy Lead and AI Risk Lead.

### §3 — Operating cadence

**Weekly (Monday 10:00–11:30).**

AI Risk Lead reads the weekly sources, produces a
two-paragraph note to the AI governance Slack channel:
"new this week" (with linked sources) and "watch list"
(items not yet surfacing but trending). CAIRO reads on
Monday afternoon; flags any item for Tuesday discussion.

**Monthly (first Tuesday).**

EU Counsel + Policy Lead produce a one-page monthly
digest covering EU and framework changes. Distributed
to the AI Risk Council ahead of the monthly Council
meeting; discussed in the regulatory-update section.

**Quarterly (first week).**

Full review. Quarterly memo to the Board Risk Committee
covering: substantive changes in scope-relevant
regulation; obligations-register updates; peer
enforcement actions of note; the watch list. Three pages
maximum.

### §4 — Triggers and escalation

| Trigger | Escalation path | Timeline |
|---|---|---|
| New obligation requiring obligations-register update | Policy Lead → CAIRO; register updated; reported in next monthly digest | 5 business days |
| Regulatory enforcement action against a peer institution in our regulator scope | AI Risk Lead → CAIRO + CRO; brief written analysis ("does this apply to us"); decision on whether to brief CEO | 3 business days |
| Regulator question pattern (a regulator starts asking about a topic across the industry) | AI Risk Lead → CAIRO; written analysis; decision on whether to brief Board Risk Committee | 5 business days |
| Regulator-cited Notified Body / auditor pattern (a Notified Body becomes a regulator preference) | Policy Lead → CAIRO + Vendor Risk; impact assessment | 10 business days |
| EU AI Act implementing act adopted that materially affects our classification or obligations | EU Counsel → CAIRO; full review; obligations-register impact analysis | 10 business days |
| Tier-1 framework revision (NIST AI RMF revision, ISO 42001 amendment) | Policy Lead → CAIRO; program-level impact analysis | 20 business days |

All escalations are written. Verbal escalations are
followed by written within 24 hours.

### §5 — Indicator dashboard

Monthly indicators reported to the AI Risk Council:

1. **Number of obligations added to the register in the
   period.** Counts new obligations identified through
   monitoring; expected non-zero in any quarter where
   regulation is active.
2. **Number of register rows where the cited source has
   been superseded.** Counts where our register cites old
   regulator text; should trend to zero.
3. **Time from regulatory event to register update.**
   Median in business days. Target: ≤ 10 days for material
   changes.
4. **Number of peer enforcement actions reviewed.** Counts
   reviews completed; expected non-zero in any quarter.
5. **Watch-list aging.** Items on the watch list for > 60
   days are reviewed for closure or escalation; reported
   as a list.

### §6 — Anti-patterns the playbook deliberately avoids

The playbook is *designed against*:

- **Subscribing to every regulator's RSS feed and reading
  everything.** We subscribe to artifact-types we have
  defined as in scope; everything else is filtered out
  before it reaches the team.
- **Reading academic AI policy literature in real time.**
  Academic literature is read quarterly, selectively, by
  the Policy Lead. It does not enter the weekly cadence.
- **Treating every state's AI-curious activity as a
  monitoring obligation.** US state patchwork is reviewed
  quarterly. States with sustained regulatory activity
  affecting Trillium-class banks are promoted to monthly.
- **Producing monitoring artifacts no one reads.**
  Indicators are reported to the AI Risk Council, not
  written to a shared drive. If the Council does not
  engage, the indicator gets re-designed.
- **Monitoring as a separate program from the obligations
  register.** Monitoring exists to *update the
  register*. Findings that do not change the register
  are reviewed for whether the register is incomplete or
  the finding is not material.

---

## 3. Reasoning notes

- **Why I capped at three pages.** A four-page monitoring
  playbook will not survive a CAIRO transition. Most CAIROs
  inheriting a long playbook re-write it; most CAIROs
  inheriting a three-page playbook keep it.
- **Why I split sources by cadence, not by regulator.**
  The unit of work is reading. The unit of cost is
  attention. Splitting by cadence means the AI Risk Lead
  reads one set of sources on Mondays; the EU Counsel
  reads a different set monthly. Splitting by regulator
  would create cross-cutting cadences for the same
  reader.
- **Why the indicator list is small.** Five indicators
  with named denominators. More indicators produce a
  dashboard no one reads. The indicators chosen are
  *leading* (register-update lag, watch-list aging)
  rather than *lagging* (number of enforcement actions
  we received), because the lagging metrics are what we
  are trying to avoid producing.
- **Where this playbook is most likely to fail.** The
  EU Counsel monthly cadence. EU Counsel is a single
  point of failure for EU monitoring. The playbook does
  not currently name a back-up. A v1.1 should name a
  back-up reader for the EU sources during EU Counsel
  PTO and at quarter-end periods of high regulatory
  activity (Council and Commission tend to issue
  guidance at the calendar pivots).
- **What I would do differently in a larger organization.**
  Add a *peer-watching cell* — a small standing function
  that monitors specifically what peer institutions are
  doing in their AI programs. Public statements by peer
  CAIROs, peer Board AI reports (when published), peer
  enforcement responses (when leaked or published).
  Trillium-class banks do not justify this; a Fortune-50
  bank does.

---

Maintained by [Girish Nair](https://github.com/garynair)
