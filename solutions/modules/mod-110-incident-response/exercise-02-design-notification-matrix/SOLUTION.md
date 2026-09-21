# Exercise 02 — Design a Notification Matrix — Reference Solution

## 1. Solution overview

A notification matrix for **Tessera Bank**
covering all 9 sub-categories from the mod-107
Ex-04 taxonomy across ~22 notification
obligations. The matrix names specific authorities,
timelines, and approval chains. Three edge cases
addressed: multi-jurisdiction customers,
vendor-side incidents, regulator-discovery during
examination.

---

## 2. Scope and use

**Scope:** AI-program (Cat 2) and joint (Cat 3)
incidents per mod-107 Ex-04. Security-only (Cat 1)
incidents are covered by the CISO's existing
incident-response notification matrix; this matrix
applies AI-specific overlays where they intersect.

**Maintenance:** Authored by the CAIRO function;
reviewed quarterly by CAIRO + CCO + GC + CISO.
Material changes require joint approval.

**Use:** When an incident is classified, the
response team consults the matrix for the
sub-category and triggers the applicable
notifications. The matrix lives in the audit
ledger; consultation is itself an event.

---

## 3. The matrix

### Sub-category 2.a — Bias / fairness incident

| # | Trigger | Recipient | Timeline | Led by | Format | Approvals |
|---|---|---|---|---|---|---|
| 1 | EU-resident customer affected with discriminatory pattern | EU AI Act NCA (per Tessera's EU operations) | 2 days from determination | CAIRO | Per EU AI Act Annex IX | CAIRO + GC + CCO |
| 2 | US customer affected; CFPB-regulated outcome (credit, etc.) | CFPB | "Without undue delay" — typically 5 business days | CCO | CFPB-portal narrative | CCO + CAIRO + GC |
| 3 | NY-resident customer affected | NYDFS | 72 hours per §500.17 if cybersecurity dimension | CCO + CAIRO | NYDFS portal | CCO + CAIRO + GC |
| 4 | Material AI-program risk impact | AI Risk Council | Auto-convene per mod-107 Ex-04 thresholds | AI Risk Lead | Incident brief | AI Risk Lead |
| 5 | Material customer / regulatory event | Board Risk Committee | Next regular meeting; convene early if catastrophic | CAIRO + CRO | Board pack section | CRO + CAIRO |
| 6 | Affected customer | Customer | Per Reg B / ECOA + customer-protection policies | CCO + CAIRO | Adverse-action notice pattern | CCO + CAIRO |

### Sub-category 2.b — Transparency / explainability failure

| # | Trigger | Recipient | Timeline | Led by | Format | Approvals |
|---|---|---|---|---|---|---|
| 7 | Affected customer who received a determination | Customer | Per Reg B (adverse action) — 30 days | CCO | Reg B notice | CCO |
| 8 | If pattern affects EU residents | EU AI Act NCA | 2 days for serious patterns | CAIRO | Per Annex IX | CAIRO + GC |
| 9 | Material risk to AI program | AI Risk Council | Next meeting; convene early if material | AI Risk Lead | Incident brief | AI Risk Lead |

### Sub-category 2.c — Capability scope violation

| # | Trigger | Recipient | Timeline | Led by | Format | Approvals |
|---|---|---|---|---|---|---|
| 10 | Material scope violation | AI Risk Council | Auto-convene | AI Risk Lead | Brief | AI Risk Lead |
| 11 | Customer-affecting violation | Customer | Per applicable customer-protection regulation | CCO + CAIRO | Per matter | CCO |
| 12 | Material to the program | Board Risk Committee | Next meeting | CAIRO | Board pack | CRO + CAIRO |

### Sub-category 2.d — Model behaviour change (unauthorised)

| # | Trigger | Recipient | Timeline | Led by | Format | Approvals |
|---|---|---|---|---|---|---|
| 13 | Vendor LLM swap discovered | Vendor (formal complaint) | Per contract terms | Vendor Risk + CAIRO | Per contract | Vendor Risk Lead + CAIRO + GC |
| 14 | Material impact on customers | Customer | Per applicable regulation | CCO + CAIRO | Per matter | CCO + CAIRO |
| 15 | EU AI Act high-risk system | EU AI Act NCA | 15 days for "other serious" if no fundamental rights; 2 days if fundamental rights affected | CAIRO | Per Annex IX | CAIRO + GC |
| 16 | SR 11-7 model event | OCC | Per SR 11-7 model event policy (typically next examination cycle; immediate if material) | MRM + CAIRO | Per SR 11-7 standard | MRM Lead + CAIRO |

### Sub-category 3.a — Adversarial exploitation

| # | Trigger | Recipient | Timeline | Led by | Format | Approvals |
|---|---|---|---|---|---|---|
| 17 | Cybersecurity event | NYDFS | 72 hours per §500.17 | CISO + CAIRO | NYDFS portal | CISO + CAIRO + GC |
| 18 | Personal data breach | DPA (per affected jurisdiction) | 72 hours per GDPR Art. 33 (and equivalent state laws) | CISO + Privacy + CAIRO | Per regulator | CISO + Privacy + CAIRO + GC |
| 19 | EU AI Act high-risk system + fundamental rights | EU AI Act NCA | 2 days | CAIRO | Annex IX | CAIRO + GC |
| 20 | Material customer impact | Customer | Per applicable regulation | CCO + Privacy + CAIRO | Per matter | CCO + Privacy |

### Sub-categories 3.b, 3.c, 3.d (cross-context leak, training-data integrity, identity / capability spoofing)

(Compressed for length — each follows similar pattern to 3.a with the relevant variations.)

### No-notification-required cases

- *Sub-category 2.b minor explainability failure not affecting any individual decision.* No external notification; internal-only via AI Risk Council. The discipline of *not over-notifying* matters — over-notification erodes regulator credibility.
- *Sub-category 2.d model behaviour change within documented envelope.* No external notification; internal-only.

---

## 4. Edge cases

**Multi-jurisdiction.** Customer affected is both
EU-resident AND US-resident. Both notification
regimes apply; treat each independently. The
matrix entries for each apply concurrently. Joint
working group convened if the regulatory windows
conflict materially.

**Vendor-side incident.** The vendor's incident
affects Tessera's AI program. Tessera's
notifications apply to *Tessera's customers and
regulators*; Tessera does not notify on the
vendor's behalf. The vendor's notification of the
incident *to Tessera* is itself a notification
Tessera should require contractually. If the
vendor's incident produces customer-affecting
behaviour at Tessera, Tessera's notifications
trigger normally.

**Regulator-discovery during examination.** A
regulator discovers an incident during their
examination before Tessera had independently
detected it. The discovery is itself the
detection event for Tessera. Tessera notifies
within the standard windows from the moment of
the regulator's notification *to Tessera*.
Pretending Tessera detected earlier than the
regulator's notification is the failure mode to
avoid.

---

## 5. Maintenance

- **Quarterly review** — CAIRO function + CCO +
  GC + CISO review the matrix for currency
  against the regulatory landscape.
- **Trigger events:** New jurisdiction
  (Tessera expands operations); new regulation;
  new sub-category in the taxonomy.
- **Material changes** require joint
  CAIRO + CCO + GC + CISO approval.
- **Version control:** Each matrix version is
  signed and added to the audit ledger.
  Historical versions are preserved for the
  duration of the underlying retention
  obligations.

---

## 6. Reasoning notes

- **Why I included no-notification cases
  explicitly.** Programs that don't name what's
  *not* notifiable tend to over-notify under
  pressure, which erodes regulator credibility.
  Naming the no-notification cases makes the
  matrix complete.
- **Why I named approvals per cell.** Without
  named approvals, the response team
  spends incident time figuring out who can
  sign. With named approvals, the approval is
  pre-determined by the matrix.
- **Why I separated DPA notification (Art. 33)
  from data-subject notification (Art. 34).**
  Different timelines, different recipients,
  different content. Treating them as one
  obligation hides the differences.
- **What this matrix doesn't address.** Litigation-
  hold or litigation-discovery notification —
  those are GC-led and follow a separate
  matrix.

---

Maintained by [Girish Nair](https://github.com/garynair)
