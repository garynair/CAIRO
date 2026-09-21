# Scenario — Tessera Bank, Q4 MRM Extension

## Tessera

Tessera Bank is a US regional bank, $25B AUM,
~3,800 employees. Federally-chartered under
the OCC. Lines of business: consumer banking,
small-business lending, commercial real estate,
wealth management. Traditional MRM function
established 2014 post-SR 11-7; mature
governance for credit scorecards, deposit-
attrition models, ALM/IRR models, AML
transaction monitoring, Basel-III capital
models.

## You

You are Chief AI Risk Officer at Tessera, recently
hired (you started ~6 months ago). You report
to the CEO with a dotted line to the CRO. Your
mandate is AI-specific governance, model risk
for AI/ML models, AI-related regulatory
engagement, and AI literacy across the
organization.

## Where AI/ML stands today

Roughly **42 AI/ML models** in production or
in late-stage development across Tessera, per
your inventory from month 2:

- 11 in consumer banking (next-best-offer,
  call-deflection, fraud-signals augmentation)
- 9 in small-business lending (cash-flow
  modeling, alternative-data credit)
- 7 in commercial real estate (CRE risk
  scoring, deal screening)
- 8 in wealth management (portfolio rebalancing
  signals, client-segmentation)
- 7 in shared functions (HR resume screening,
  marketing analytics, document classification)

Of these 42:

- 14 are managed under existing MRM (the credit
  and CRE scoring use cases that fit
  traditional MRM scope)
- 28 are **outside MRM** — managed by various
  business lines and shared-services teams with
  varying governance discipline

## The conversation

Two months ago you and the CRO sat down. You
walked her through the inventory. She agreed,
in principle, that all 42 should be under MRM
with appropriate proportionality. The
practical questions: scope language, tiering
(SR 11-7 applies to "models"; what's a
"model" for AI/ML — a fine-tuned vendor LLM is
ambiguous), validation methodology for AI
(traditional MRM validation methodology
doesn't fully translate), ongoing monitoring
(performance drift in ML doesn't look like
parameter drift in traditional models), and
sequencing (you can't validate 28 systems in
90 days).

The CRO is supportive but cautious. She does
not want MRM swamped with low-criticality
classifier work at the expense of the
high-criticality traditional models that
already consume bandwidth. She does want a
clear approach in place by the Q4 board
meeting and exam-ready posture for the OCC
February examination.

## Constraints

- 90-day arc.
- Q4 board review at day 75; the framework
  goes to the Risk Committee.
- OCC examination in February (day ~140
  from today; not in your 90-day arc but
  exam-readiness shapes choices).
- 28 models outside MRM cannot all be
  validated in 90 days. Sequencing and
  triage are part of the deliverable.
- CRO holds final authority on MRM scope
  decisions. You author and recommend; she
  approves.
- Audit (Internal Audit) is preparing to
  scope Q1 audit testing on AI governance.
  They will want to see this framework.
- Two of the 28 outside-MRM models are
  customer-facing in consumer banking and
  have produced complaints to the bank's
  consumer-relations function in the last
  quarter (no formal CFPB complaints yet,
  but the trend is real).

## Constraints you will discover

- The HR resume-screening model is a vendor
  LLM-based system. The vendor positions it
  as "not a model" — but it produces ranked
  candidates. Sourcing function uses the
  rankings. You will need to make a call.
- One of the 28 outside-MRM systems —
  Treasury operations' "smart cash position"
  forecasting tool — has been quietly
  driving real Treasury decisions for 8
  months without formal governance. CRO did
  not know.
- A wealth management portfolio-rebalancing
  signal was retrained 3 weeks ago without
  pre/post comparison. Performance has
  degraded since. The line-of-business team
  has not noticed.

## You have access to

- mod-104 (CAIRO × MRM split authorship pattern)
- mod-106 (SR 11-7 governance frame)
- mod-107 (security boundaries with CISO,
  applicable to AI vendor risk)
- mod-110 (incident response — useful for
  the wealth-management retrain issue)
- mod-111 (board reporting cadence — Q4
  board engagement)
- mod-112 (year 3 synthesis — applicable
  to multi-quarter planning)

## What the work is

You will produce six artifacts that
together define Tessera's AI-extended MRM
operating model, plus a synthesis memo to
the CEO/CRO/Audit at the close of the
90-day arc.

The six artifacts are designed to be
deliverables in their own right (board
papers, internal procedures, exam-ready
documentation) — not internal-CAIRO-only
planning artifacts.

---

Maintained by [Girish Nair](https://github.com/garynair)
