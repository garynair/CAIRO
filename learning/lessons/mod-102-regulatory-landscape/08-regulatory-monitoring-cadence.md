# Chapter 8 — The Regulatory Monitoring Cadence

## Why this chapter exists

The obligations register from Chapter 6 is only useful if
it stays current. Regulations change. Implementing acts get
adopted. Guidance is republished. Enforcement patterns
reveal what supervisors care about. A register that looks
right on day one and is not maintained becomes actively
misleading by month six.

The temptation for a new CAIRO is to *"track everything."*
Subscribe to every regulator's RSS feed, read every
enforcement press release, follow every legal-blog post.
This does not scale. Within two quarters the monitoring
function is either drowning the CAIRO's team in low-signal
noise or has quietly been abandoned.

The discipline is a **90-day cadence**: a defined,
time-bounded rhythm that catches meaningful change
without consuming the team. This chapter walks the shape
of that cadence. Exercise 05 has you author one.

## What the monitoring function must do

Three outputs, and only three:

1. **Detect regulatory change** early enough that the
   obligations register can be updated before it becomes
   wrong.
2. **Surface enforcement patterns** early enough that the
   program can be adjusted before the pattern reaches
   your firm.
3. **Feed the quarterly inventory-of-obligations report**
   with a summary of what changed and what did not.

Everything else that looks like monitoring — reading blog
posts about AI policy, tracking every state legislator's
bill introduction — is either input to those three or
overhead the function does not need.

## The 90-day cadence

A defensible default cadence for a mid-to-large enterprise
with EU and US exposure. Adjust for scale and sector.

### Weekly (10 to 30 minutes)

Only for **actively-in-flight regulatory proceedings**.
Examples that would trigger weekly monitoring:

- An EU AI Act delegated act during its consultation
  window.
- A pending state-level AI bill in a state you operate in,
  approaching floor vote.
- A live supervisory examination.

If nothing is actively in flight, the weekly cadence goes
to zero. This is normal and correct.

Owner: designated **first-line liaison** with the CAIRO
function (typically a senior compliance analyst or a
sector-specialist counsel).

### Monthly (2 to 4 hours)

Two categories:

- **Enforcement actions** in the sectors and
  jurisdictions you operate in. New consent orders, new
  fines, new supervisory letters made public. The signal
  is *what supervisors have been willing to act on
  recently*.
- **Formal guidance** issued by supervisors and
  standards bodies — new SR letters, new FDA guidance,
  new NAIC bulletins, new NIST publications.

Output: a one-page monthly digest, distributed to the
CAIRO's leadership team and the risk committee's staff
support. Digest names what was surfaced and whether any
register row was touched.

Owner: **AI risk function analyst** (second line).

### Quarterly (4 to 8 hours)

The full sweep:

- Every regulation cited in the obligations register.
  Is the cited text still in force? Has it been amended
  or superseded?
- Every major framework the program is anchored on
  (NIST AI RMF, ISO 42001, EU AI Act). Has any been
  updated?
- The overall pattern of regulatory movement in the
  sectors and jurisdictions the program covers. What
  themes are supervisors emphasising this quarter?

Output: the **quarterly inventory-of-obligations report**
— the artifact the board risk committee should expect to
receive (Chapter 6). Includes: obligations added,
obligations removed or superseded, obligations status
change, monitoring highlights.

Owner: **CAIRO**, drafted by AI risk function.

## The source list

The set of sources the function monitors, organised by
cadence. Every source has a named owner and a defined
signal that triggers escalation. The following is a
default starting set; adjust to your sector and
jurisdictions.

### Weekly sources (only when active proceeding)

- Regulator-specific pages for the active proceeding
  (e.g., EU Commission *"Have your say"* portal filtered
  to the specific act; state legislature bill status
  page).

### Monthly sources

- OCC / FRB / FDIC / CFPB enforcement action lists.
- NYDFS supervisory actions and industry letters.
- SEC AI-related enforcement (increasingly relevant for
  investment advisers using AI).
- FDA warning letters and untitled letters relevant to
  SaMD or drug-clinical AI.
- State insurance department bulletins in states you
  operate in.
- EU AI Office announcements and implementing act
  progress.
- NIST publication feed filtered to AI, ML, and risk.

### Quarterly sources

- The obligations register itself (sweep every row).
- NAIC and NAAG (National Association of Attorneys
  General) publications.
- OECD AI Policy Observatory updates.
- Framework updates: NIST AI RMF, ISO 42001, ISO 23894,
  ISO 38507.
- Sector-specific standards bodies (IEEE, HL7 for
  health, ISO/TC 22 for automotive).

Every source row in your playbook includes: name, URL or
feed, cadence, owner, escalation trigger. Orphan sources
— sources with no named owner — either get an owner or
get removed. There is no third option.

## Escalation triggers

The monitoring function must escalate on a defined set of
signals, not on the reader's gut. Defensible defaults:

- **New obligation surfaced** — a new rule, guidance, or
  interpretation that requires updating an existing
  register row or adding a new one. Escalation to CAIRO
  within 5 business days.
- **Peer-institution enforcement action** — a supervisor
  fine or consent order against a peer institution
  covering behaviour comparable to yours. Escalation to
  CAIRO and CRO within 5 business days.
- **Regulator question pattern** — the same question or
  theme appearing in three or more publicly-available
  supervisory letters or speeches within a month.
  Escalation to CAIRO within 10 business days with a
  pattern brief.
- **Regulator-cited specific vendor or auditor** — a
  supervisor names a specific vendor or auditor in a
  finding or guidance. Escalation to CAIRO and CISO within
  5 business days if you use the named party.

Every escalation has a **timeline in business days**,
not *"promptly"*. Promptly is not a timeline.

## Leading indicators

The monitoring function must be measurable. Vanity metrics
— *"number of regulations tracked"* — do not indicate
whether the function is working. Leading indicators that
do:

- **Register freshness** — number of register rows whose
  cited source has not been re-verified in more than one
  quarter.
- **Time-to-update** — median business days from a
  regulatory event to the register row being updated.
- **Detection lag on peer enforcement** — median business
  days from a peer institution's public enforcement
  action to it being surfaced in the monthly digest.
- **Register drift** — number of register rows whose
  cited source has been superseded since the last
  quarterly sweep.
- **Escalation quality** — proportion of escalations
  that produced a register change (a healthy signal is
  most of them do; a low proportion suggests the
  triggers are too loose).

Pick three to five. Report them monthly. Judge the
function's effectiveness on the leading indicators, not
on the volume of items read.

## Anti-patterns

The patterns the playbook is deliberately designed
against. Naming them in the playbook keeps the function
from drifting into them.

- **Everything-feed subscription.** Subscribing to every
  regulator's press release and reading everything.
  Guaranteed drowning. Replace with topic-filtered
  category subscriptions.
- **Reader-of-record without owner.** Sources that get
  read but never turn into an obligations-register change
  or a digest entry. Either give the source an
  escalation-worthy purpose or drop it.
- **Vendor as monitoring function.** Outsourcing all
  monitoring to a vendor's regulatory-alerts product.
  The vendor becomes an invisible fifth line
  (mod-101 Chapter 8 anti-pattern). Vendor alerts are a
  supplement; the CAIRO's monitoring is not replaceable by
  a subscription.
- **Monitoring the letter, not the theme.** Reading each
  new rule in isolation and never asking *"what is the
  supervisor trying to solve for."* The theme is what
  survives across specific rules and is what you can
  design against.

## Time budget

A monitoring function that consumes more than one FTE at a
mid-sized enterprise is broken. Defensible defaults:

- Weekly cadence (when active): 0.25 to 1 hour per week
  per active proceeding.
- Monthly cadence: 4 to 8 hours per month for the
  analyst.
- Quarterly cadence: 8 to 16 hours per quarter across the
  team, including the report write-up.

That is roughly 0.15 to 0.3 FTE at typical enterprise
scale. If the function is consuming 1+ FTE, either the
company is genuinely much larger and has an EU +
multiple-US-state + healthcare + financial-services
exposure profile, or the function is over-scoped and needs
pruning.

## Summary

- The obligations register is only useful if it stays
  current. The monitoring function keeps it current.
- Three outputs only: detect change, surface enforcement
  patterns, feed the quarterly report.
- 90-day cadence: weekly (only when something is active),
  monthly (enforcement + guidance), quarterly (full
  sweep).
- Every source has a named owner and a defined escalation
  trigger. Orphan sources get an owner or get dropped.
- Leading indicators — register freshness, time-to-update
  — measure the function's effectiveness. Report three to
  five monthly.
- Anti-patterns: everything-feed subscription,
  reader-without-owner, vendor-as-monitoring,
  letter-not-theme.
- Budget the function at 0.15 to 0.3 FTE at mid-enterprise
  scale. More than that and it is over-scoped.
