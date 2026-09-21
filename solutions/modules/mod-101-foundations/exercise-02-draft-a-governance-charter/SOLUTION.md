# Exercise 02 — Draft a Governance Charter — Reference Solution

## 1. Solution overview

The charter below is for **Northfield Mutual** (the fictional
mid-market P&C insurer from the exercise). It anchors on
**NIST AI RMF** as the operating framework with **ISO 42001
§5 (Leadership)** as the structural reference. It compresses
the governance machinery to two bodies (an AI Risk Council
and an AI Review Board) and leaves out anything that does not
deliver decision rights or oversight. Three pages, no annexes.

---

## 2. The charter

> **Northfield Mutual — AI Governance Program Charter**
> *Adopted by the Executive Committee. Pending Board Risk
> Committee ratification.*

### 2.1 Mission

This program exists to ensure that every AI system Northfield
operates produces decisions Northfield can defend — to
regulators, to insureds, to employees, and to the Board.
Success is the absence of surprises: no AI-related
regulatory action, customer harm, or material reputational
event that the program failed to anticipate, and a documented
risk posture the Board can read and challenge each quarter.

### 2.2 Scope

In scope: any system — internal, vendor-provided, or hybrid —
that uses machine learning, generative AI, or rules derived
from statistical inference, *and* whose output affects (a) a
coverage, claims, pricing, fraud, or marketing decision; (b)
an employee performance, hiring, or termination decision; or
(c) a customer-facing communication. The four current
material systems — underwriting model, claims-triage vision
model, third-party LLM chat agent, fraud-detection anomaly
detector — are in scope from day one.

Out of scope: deterministic rules engines without statistical
inference; analytic dashboards used purely for human-led
decisions; office-productivity AI features used by employees
in their own workflow with no customer or employment impact.
Out-of-scope items will be reviewed quarterly to confirm they
remain out of scope; promotion in is the AI Risk Council's
call.

### 2.3 Authority

The Chief AI Risk Officer has:

- **Decision authority** to approve or block deployment of any
  in-scope AI system at Northfield.
- **Standard-setting authority** for all AI-specific policies,
  controls, and review processes.
- **Recommendation authority** on training-data sources,
  vendor selection, and model architecture; the first-line
  function (the model owner) holds the decision.

Disagreements between the CAIRO and the model owner that cannot
be resolved at the AI Review Board are escalated to the AI
Risk Council. Disagreements at the Council that cannot be
resolved go to the CEO. Disagreements involving material
enterprise risk go to the Board Risk Committee.

### 2.4 Structure and 3LOD posture

The CAIRO reports to the **Chief Risk Officer** with a
dotted line to the **CEO**. This places the function in the
second line of defense and consolidates AI risk under
existing enterprise-risk reporting machinery.

The CAIRO holds the second-line accountability for AI risk.
Model owners (in the lines of business) hold the first-line
accountability. Internal audit (third-line) tests the
program; internal audit reports to the Board Audit Committee
and is independent of the CAIRO.

Peer-role boundaries:

- **CRO:** owns the enterprise risk taxonomy; the CAIRO owns
  the AI-specific risk register and how AI risks roll up into
  the CRO's taxonomy.
- **MRM (under CRO):** owns validation methodology; the CAIRO
  defines which AI/ML systems require MRM validation tier-by-
  tier.
- **CISO (under CIO at Northfield):** owns AI-system security;
  the CAIRO owns AI-specific threat models (prompt injection,
  model exfiltration, training-data poisoning) and AI
  incident classification.
- **CDO:** owns data quality and lineage; the CAIRO owns
  training-data provenance constraints and downstream-use
  restrictions.
- **GC:** owns legal posture; the CAIRO owns regulator-facing
  AI program documentation.

### 2.5 Standards alignment

The program anchors on **NIST AI RMF 1.0** as its operating
framework. The four functions (GOVERN, MAP, MEASURE, MANAGE)
structure the work; the Playbook informs sub-category
implementation. The program will additionally align to
**ISO/IEC 42001:2023** with the intent of pursuing
certification within 24 months once core controls are
stable. The state insurance regulator and any future EU
exposure (Northfield's reinsurance carrier is EU-domiciled)
will be addressed through obligation overlays, not by
rebuilding the program around each.

### 2.6 Governance bodies

Two bodies, no more:

**AI Risk Council.** Chaired by the CRO; members are the
CAIRO, CDO, CISO, GC, CTO, and Chief Compliance Officer.
Meets monthly. Reviews the AI risk register, approves
material risk-treatment changes, ratifies the AI Review
Board's tier classifications, hears escalations. Has the
authority to instruct the first line.

**AI Review Board.** Chaired by the CAIRO; members are the
head of underwriting, head of claims, head of customer
experience, the MRM lead, and a senior Fair-Lending /
Compliance officer. Meets bi-weekly. Reviews each in-scope
AI deployment, classifies it by tier, requires named
controls, and approves or blocks production deployment.
Escalates to the Risk Council on tied votes or material
disagreement.

### 2.7 Risk-appetite posture pending Board action

Until the Board Risk Committee adopts a formal AI risk
appetite statement, the program operates under the
following posture: **no AI system may be deployed that takes
on risk the existing enterprise risk appetite does not
already absorb.** The CAIRO drafts a candidate appetite
statement within 60 days for Board consideration. Anything
materially novel (e.g. autonomous customer-facing
decisioning) is held pending Board action.

### 2.8 First-90-day deliverables

- AI system inventory (all in-scope systems, with tier
  classification).
- AI policy hierarchy (top-level policy + four standards:
  development, third-party, monitoring, incident response).
- AI Risk Council and AI Review Board operationalized.
- AI incident-response playbook, with regulator-notification
  triggers mapped to state insurance regulation and EU AI
  Act Art. 73 (for any EU-affecting paths).
- First quarterly AI risk report to the Board Risk Committee
  (draft form, for ratification of charter).

---

## 3. Reasoning notes

- **Why two governance bodies and not five.** Restraint is
  the design choice. Each additional body raises the
  cost-to-ship of any AI system at Northfield. Two
  bodies — one strategic (Council), one operational
  (Review Board) — is the minimum that preserves both
  enterprise oversight and per-deployment control.
- **Why anchor NIST + pursue ISO certification.** NIST is
  the operating system; ISO is the *external assurance*
  surface. Pursuing ISO 42001 certification within 24 months
  signals seriousness to the regulator without locking the
  program into a single jurisdiction's framework.
- **Why the risk-appetite posture is pre-stated.** The
  hardest moment for a new program is the period before the
  Board has formally adopted an AI risk appetite — every
  decision is implicitly setting one. Naming the posture
  ("no risk beyond existing enterprise appetite") gives the
  program a defensible default while the formal statement is
  drafted.
- **Where this charter is most likely to fail in practice.**
  The CAIRO-vs-MRM-lead boundary. MRM lives under the CRO and
  has decades of authority over financial models. ML models
  feel new and adjacent. Without explicit boundary work in
  the first 90 days, the MRM lead and the CAIRO will collide
  on validation tier-setting. Charter §2.4 names this; the
  90-day plan §2.8 should add a specific deliverable on it.

## 4. Failure-mode check (from lecture notes §6)

- *Governance theatre?* Two bodies with named decision
  rights; both can block deployment. Acceptable.
- *Control sprawl?* No control catalog defined yet; the
  90-day plan is bounded to a four-standard hierarchy. Risk
  is real but controlled.
- *Compliance-only stance?* The mission language ("absence
  of surprises") is explicit about un-asked risks. Pre-stated
  risk-appetite posture forces the program to think beyond
  the regulator's prompts.

---

Maintained by [Girish Nair](https://github.com/garynair)
