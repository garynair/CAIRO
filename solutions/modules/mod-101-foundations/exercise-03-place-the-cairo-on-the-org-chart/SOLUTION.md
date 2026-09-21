# Exercise 03 — Place the CAIRO on the Org Chart — Reference Solution

## 1. Recommendation

For **Aldwych Health** (the fictional UK healthcare system in
the exercise): the Chief AI Risk Officer **reports solid-line to
the Chief Risk Officer**, with **dotted-line accountability
to the Chief Medical Officer for clinical-decision-support
oversight**. This places the function in 3LOD's second line,
consolidates AI risk under existing enterprise-risk
machinery, and preserves the Chief Medical Officer's
clinical authority over patient care.

## 2. Org chart

```
CEO
├── Chief Medical Officer
│   └── (clinical authority; ··· dotted line: CAIRO for CDS oversight)
├── Chief Operating Officer
├── Chief Information Officer
│   └── Information Security (no separate CISO at Aldwych)
├── Chief Technology Officer
│   └── Data Platform + AI/ML Capability (first-line ML engineering)
├── Chief Quality Officer
│   └── Patient Safety + Clinical Safety Officer (DCB 0129/0160 owner)
├── Chief Risk Officer
│   └── Chief AI Risk Officer
│       ├── AI Policy & Standards Lead
│       ├── AI Risk Lead (model risk + assurance interface)
│       └── AI Regulatory Engagement Lead (MHRA / CQC / ICO / EU AI Act)
├── General Counsel
└── Chief Financial Officer

Board Audit Committee — Internal Audit (3LOD) reports here
```

The CAIRO's three direct reports are illustrative; mature
programs at Aldwych's scale typically operate with 4–7
direct reports.

## 3. Memo to the board

> **TO:** Board, Aldwych Health
> **FROM:** [external advisor]
> **SUBJECT:** Reporting line for the Chief AI Risk Officer
> **PAGE:** 1 of 1

The Chief AI Risk Officer should report to the Chief Risk
Officer, with a dotted-line accountability to the Chief
Medical Officer for clinical-decision-support oversight. I
recommend this structure because it is the only one that
preserves three things the Board has asked for in the same
breath: AI-risk consolidation, clinical authority over
patient care, and an independent second-line that can
challenge engineering and operations on equal footing.

**Why CRO, and not the alternatives.** Reporting to the CEO
would give the function visibility but no organizational
home for routine work; the CEO does not have the bandwidth
to be the day-to-day arbiter of AI risk decisions, and the
role would become CEO-anchored in the wrong way (the CEO
would be both the escalation path *and* the operational
sponsor). Reporting to the CTO is structurally unworkable:
the CTO is accountable for the AI capability we are asking
the CAIRO to govern. Reporting to the COO would embed the
function operationally but is harder to defend to regulators
who will look for risk-side ownership; the CQC's emerging AI
guidance specifically expects an enterprise-risk owner.

**3LOD independence.** Under this structure, model owners
(under the CTO) are first line. The CAIRO (under the CRO) is
second line. Internal Audit, reporting to the Board Audit
Committee, is third line. The CRO is the right home for
second-line consolidation because Aldwych's existing
enterprise-risk reporting machinery already serves that
purpose for non-AI risks.

**The Chief Medical Officer boundary.** Clinical authority
stays with the CMO. The CAIRO does not approve clinical
decisions. The CAIRO does approve *deployment* of any AI
system that produces clinical-decision-support outputs, and
the CMO co-signs that deployment approval through the dotted
line. In practice: the CMO can block deployment on clinical
grounds; the CAIRO can block deployment on risk grounds;
neither can override the other; ties go to the CEO. This
boundary was the part of the design I spent the most time on
— Aldwych's recent triage incident showed that clinical
authority alone did not detect the bias quickly enough, and
pure risk authority would have lacked clinical context.

**The CIO boundary.** The CIO runs clinical IT operations,
including the EHR and the infrastructure that hosts AI
systems. The CAIRO does not approve infrastructure choices;
the CIO does not approve which AI systems are deployed on
that infrastructure. Boundary kept by a deployment-checklist
artifact co-owned with the AI Review Board.

**Most likely failure mode of this structure.** The dotted
line to the CMO will be hard to operationalize. CMOs in
NHS-aligned systems are extremely time-poor; a co-sign
process can degrade into a CMO rubber-stamp, which would
re-create the recent triage failure. We will detect this by
tracking three indicators monthly: CMO time spent on AI
deployment reviews, fraction of CMO co-signs preceded by a
substantive question, and time-to-decommission for any AI
system the AI Review Board flags as a clinical-bias
candidate. If any indicator falls below threshold for two
consecutive quarters, the dotted line is restructured into a
named Clinical AI Officer reporting solid-line to the CMO and
dotted-line to the CAIRO.

I recommend the Board approve this structure with the
12-month review built in as a condition.

— end memo —

## 4. Reasoning notes

- **Why not "report to CEO."** Aldwych is a 12,000-person
  org with a working CEO calendar. CEO direct-report works
  best in orgs where AI risk dominates the executive agenda
  (large frontier-AI orgs) or in orgs much smaller than
  Aldwych. For Aldwych, the CEO-direct option is symbolic
  rather than operational.
- **Why the dotted-line to the CMO matters more than usual.**
  The recent triage incident is the determining context. In
  healthcare, clinical authority is a non-negotiable
  feature of the operating model; in finance it would be
  the General Counsel; in industrial it might be the COO.
  The dotted line is *jurisdiction-specific* design.
- **What would change my recommendation.** If Aldwych had a
  Chief Clinical Information Officer (CCIO), I would propose
  the dotted line through the CCIO instead of the CMO
  directly; the CCIO is closer to clinical-system
  operations. Aldwych does not.
- **Where this differs from a financial-services analogue.**
  At Northfield Mutual (Exercise 02), the equivalent
  dotted-line did not exist. There is no clinical-style
  authority figure to consult for an underwriting model. The
  Fair-Lending boundary at Northfield is the closest
  analogue and was kept in the AI Review Board membership
  rather than as a dotted line. Different industry, different
  shape.

---

Maintained by [Girish Nair](https://github.com/garynair)
