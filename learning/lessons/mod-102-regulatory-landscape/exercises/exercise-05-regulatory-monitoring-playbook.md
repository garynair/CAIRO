# Exercise 05 — 90-Day Regulatory Monitoring Playbook

**Estimated time**: 3 hours
**Deliverable**: A playbook specification (≤ 3 pages)

---

## The scenario

You are the CAIRO at any organization of your choice (use one
of the fictional companies from earlier exercises, or
imagine your real employer's profile if you have one).
[Chapter 8 — Regulatory monitoring cadence](../08-regulatory-monitoring-cadence.md)
names the three outputs a monitoring function must
produce:

1. Detect regulatory change early enough that the
   obligations register can be updated before it becomes
   wrong.
2. Surface enforcement patterns early enough that the
   program can adjust before the pattern reaches your
   firm.
3. Feed the quarterly inventory-of-obligations report.

This exercise builds the **monitoring** function — item 2.
The deliverable is a *playbook specification* that another
CAIRO, dropped into your seat, could pick up and run.

## Your assignment

Produce a playbook specification with the following
sections.

### §1 — Scope of monitoring

What is in scope:

- Which regulators? (Be specific.)
- Which categories of artifact are we watching for? (Final
  rules, draft rules, enforcement actions, guidance,
  examiner letters, technical bulletins, etc.)
- Which sectors / jurisdictions?
- Which thresholds make a change worth surfacing? (Not
  every regulator's RSS feed deserves your attention.)

### §2 — Source list

A concrete list of the sources you will monitor, organized
by cadence. Examples:

- **Weekly**: …
- **Monthly**: …
- **Quarterly**: …

Each source row includes: source name, URL or feed, owner
(role), cadence, and what kind of signal triggers
escalation.

### §3 — Operating cadence

The week-by-week / month-by-month rhythm:

- Who reads what, when.
- Where the read-outs go (Slack channel, internal note,
  email digest).
- The format of the read-out.
- Time budget per cycle.

### §4 — Triggers and escalation

What signals require escalation, to whom, and within what
window. At minimum:

- Trigger that surfaces a new obligation requiring
  inventory-register update.
- Trigger that surfaces a regulatory action against a peer
  (a competing-bank fine, for instance).
- Trigger that surfaces a regulator question pattern (the
  regulator is starting to ask about X).
- Trigger that surfaces a regulator-cited specific vendor
  (a Notified Body or auditor pattern).

### §5 — Indicator dashboard

Three to five **leading indicators** the playbook will
produce monthly. These are not vanity metrics; they should
be the metrics by which you would judge the monitoring
function's effectiveness. Examples might include:

- Number of obligations added to the register in the period.
- Number of register rows where the cited source has been
  superseded.
- Time from regulatory event to register update.

### §6 — Anti-patterns the playbook deliberately avoids

A short section naming patterns the playbook is *designed
against*. Example: "we do not subscribe to every regulator
press release and read everything; we subscribe to specific
*kinds* of artifact filtered by topic." The discipline is
honesty about what you are *not* doing.

## Constraints

- **Three pages, hard limit.** A monitoring playbook longer
  than three pages will not survive a CAIRO transition.
- Every source must have a named **owner** and **cadence**.
  Orphan sources clog the function.
- Time budget per cycle is **explicit**. A playbook that
  requires 40 hours / week of monitoring labor is broken.
- Triggers must include **escalation timelines** ("within 5
  business days", not "promptly").
- Indicators must be **observable**. "Better regulatory
  posture" is not an indicator.

## Rubric

| Criterion | Weight |
|---|---|
| Scope clarity — in / out / why | 15% |
| Source list — concrete, owned, time-bounded | 25% |
| Operating cadence — explicit, executable | 15% |
| Triggers — substantive, with escalation timelines | 15% |
| Indicators — observable, leading rather than lagging | 15% |
| Anti-patterns — substantive, not platitudes | 10% |
| Length discipline — three pages max | 5% |

## Where to submit

`solutions/modules/mod-102-regulatory-landscape/exercise-05-regulatory-monitoring-playbook/SOLUTION.md`

Reference solution is for a US bank with EU exposure. As
elsewhere, defensible playbooks for different profiles will
diverge; score yourself on rubric, not match.

## Reading before you start

- [Chapter 8 — Regulatory monitoring cadence](../08-regulatory-monitoring-cadence.md) — the shape the playbook implements.
- [Chapter 6 — Multi-regime obligations mapping](../06-multi-regime-obligations-mapping.md) — the register the monitoring function keeps current.
- One of: an existing internal regulatory-monitoring
  playbook you have access to, or the open-source EU
  Commission *Have your say* portal's notification
  structure (for an example of the artifact granularity
  you should monitor at).
