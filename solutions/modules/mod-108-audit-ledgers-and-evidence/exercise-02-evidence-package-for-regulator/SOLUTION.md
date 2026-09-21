# Exercise 02 — Evidence Package for Regulator — Reference Solution

## 1. Solution overview

A 4-page evidence package responding to the state
insurance regulator's inquiry on **Northfield's
claims-triage v2** over the trailing 6 months. The
package addresses (a) capability scope, (b)
demographic monitoring, (c) no disparate impact on
age 70+ — with **honest treatment of one month**
where a demographic threshold was crossed and the
AI Review Board responded with a documented site-
level pause.

---

## 2. The evidence package

> **NORTHFIELD MUTUAL — EVIDENCE PACKAGE**
> *Regulator inquiry response: AI-assisted claims-
> triage system v2*
> *Period covered: 2025-12-01 to 2026-05-31*
> *Package produced: 2026-06-15*
> *Package ID: NM-EP-2026-06-15-001*

### 1. Cover

In response to State Insurance Regulator letter
SIR-2026-04-22-NM (dated 2026-04-22), Northfield
Mutual provides the following evidence covering the
operation of its AI-assisted claims-triage system
v2 from 2025-12-01 to 2026-05-31. Point of contact:
[Chief AI Risk Officer name, contact details].

### 2. Scope

- *In scope:* System `NM-AI-019` (claims-triage v2);
  period 2025-12-01 through 2026-05-31; the three
  specific items in the regulator's request.
- *Out of scope:* Operations of other Northfield
  AI systems; operations outside the named period;
  attestations concerning v1 (decommissioned 2025).

### 3. Evidence for (a) — capability scope

**Reference policy:** Capability scope is defined in
Northfield AI Policy CAS-2025-09-15 §3, which
limits the triage system to producing
recommendations within ESI levels 1–5 and
restricts the system from generating ESI
de-escalations (per the asymmetric-escalation
design from mod-105 Ex-03 reference).

**Operations summary:**

| Quantity | Count |
|---|---|
| Total triage operations | 487,213 |
| Operations authorised within capability scope | 487,213 |
| Operations denied as out-of-scope | 0 |
| Operations producing recommendations | 487,213 |
| Recommendations that de-escalated ESI | 0 |

The zero count for ESI de-escalations is a
program-design constraint enforced at the
orchestrator level (per the v2 workflow design);
the audit ledger contains the corresponding
`tool.invoked` events showing the constraint
operating throughout the period.

**Statistical sample evidence references:**

A 50-operation random sample for regulator
inspection, with full inclusion proofs:

| Sample ID | Date | Operation | Ledger Event ID |
|---|---|---|---|
| S-001 | 2025-12-03 | triage_recommendation | 01HF...XX01 |
| S-002 | 2025-12-09 | triage_recommendation | 01HF...XX02 |
| ... | ... | ... | ... |
| S-050 | 2026-05-28 | triage_recommendation | 01HF...XX50 |

(Inclusion proofs appended as Annex A; representative.)

### 4. Evidence for (b) — demographic monitoring

**Reference policy:** AI Risk Council charter
update of 2025-05-15 §4 requires monthly
demographic-stratified monitoring of the v2 system
across age, sex, race/ethnicity (where data
available), and language of presentation.

**Monitoring evidence:**

| Month | Demographic monitoring run | AI Review Board reviewed | Threshold crossing detected | Response |
|---|---|---|---|---|
| 2025-12 | Yes (event 01HF...DM01) | Yes (minutes ref MIN-2025-12-15) | No | N/A |
| 2026-01 | Yes (event 01HF...DM02) | Yes (MIN-2026-01-19) | No | N/A |
| 2026-02 | Yes (event 01HF...DM03) | Yes (MIN-2026-02-16) | **Yes (age 80+ at Site H-04)** | **Site H-04 paused 2026-02-17 through 2026-02-28; root-cause review concluded calibration drift; re-validation completed; site resumed 2026-03-01** |
| 2026-03 | Yes (event 01HF...DM04) | Yes (MIN-2026-03-16) | No (post-resume) | N/A |
| 2026-04 | Yes (event 01HF...DM05) | Yes (MIN-2026-04-20) | No | N/A |
| 2026-05 | Yes (event 01HF...DM06) | Yes (MIN-2026-05-18) | No | N/A |

All 6 monthly monitoring runs and the AI Review
Board reviews are recorded in the ledger with
inclusion proofs (Annex B). The February threshold
crossing and the site-level pause are recorded
with full incident classification per Northfield's
taxonomy (mod-107 Ex-04); the pause response
emitted `incident.classification.assigned` event
01HF...IC01 with classification 2.a (bias /
fairness incident).

### 5. Evidence for (c) — no disparate impact on age 70+

**Reference metric:** The v2 system's bias metric
specification (per mod-105 Ex-02 pattern adapted
for insurance triage) uses equalized odds across
age strata, with sensitivity gap ≤ 3 percentage
points and specificity gap ≤ 5 percentage points
between any two age strata.

**Period summary for age 70+ subgroup:**

| Month | Age 70+ sensitivity | Reference sensitivity | Gap (pp) | Within threshold |
|---|---|---|---|---|
| 2025-12 | 0.94 | 0.95 | -1.0 | Yes |
| 2026-01 | 0.93 | 0.95 | -2.0 | Yes |
| 2026-02 | **0.89** | **0.96** | **-7.0** | **No (site H-04)** |
| 2026-03 | 0.93 | 0.94 | -1.0 | Yes |
| 2026-04 | 0.94 | 0.95 | -1.0 | Yes |
| 2026-05 | 0.94 | 0.95 | -1.0 | Yes |

The February crossing affected one site (H-04). The
package does *not* claim no threshold was crossed
during the period; the package shows the
threshold was crossed at one site, the response
was triggered per policy, the site was paused,
the root cause was identified (calibration drift
specific to that site's local case mix), and the
site resumed under verified threshold compliance.
This is the evidence the regulator's question (c)
warrants — *no sustained disparate-impact pattern
across the period* — not the stronger claim of *no
threshold crossing*.

For all 50 sample operations in §3, the per-
operation evidence records include age-stratum
classification suitable for the regulator's
independent disparate-impact analysis. Inclusion
proofs in Annex C.

### 6. Supporting artifacts

The following Northfield artifacts are referenced
in this evidence package and made available to the
regulator on request:

- System identity manifest for NM-AI-019,
  version 2.4.1 (which applied 2025-12-01
  through 2026-05-31).
- AI Policy CAS-2025-09-15 (capability scope).
- AI Risk Council Charter update 2025-05-15
  (demographic monitoring).
- AI Review Board minutes for the period
  (referenced individually in §4).
- The incident-classification documentation for
  the February pause (per the §2.7 EU AI Act
  Art. 73 evaluation — concluded reportable as a
  serious incident; reported to the EU AI Act
  authority for the EU-resident insureds
  affected on 2026-02-18).

### 7. Chain of custody and signature

This package was produced by Northfield's evidence
production service on 2026-06-15 at 14:32 UTC,
under request CAIRO-EP-Request-2026-06-12-001
(authorised by the CAIRO's office). Production used
audit-ledger snapshots sealed through 2026-05-31
inclusive.

The package is signed by Northfield's evidence
signing key (key ID `nm-evidence-2026-q2`); the
signature covers the entire package contents
including the three annexes. Witness
countersignatures (Northfield internal compliance
+ external attestation provider) are attached as
Annex D.

**Verification protocol** (for the regulator's
independent verification):

1. Verify the package signature using the public
   key at `https://identity.northfieldmutual.com/.well-known/jwks.json`,
   key ID `nm-evidence-2026-q2`.
2. Verify each annex's inclusion proofs against
   the published ledger commitments at
   `https://transparency.northfieldmutual.com/.well-known/sct-log/`.
3. Verify ledger consistency between the sealed
   2026-05-31 root and the current published root
   (consistency proof in Annex E).
4. Verify the RFC 3161 timestamps on the witness
   countersignatures (Annex D).

— end package —

---

## 3. Reasoning notes

- **Why I included the February threshold crossing
  honestly.** §1 — evidence is not justification.
  Hiding the crossing would be a fabricated record.
  The regulator's question (c) is whether
  *disparate impact patterns* affected age 70+
  insureds across the period. The February crossing
  is a discrete incident, addressed per policy,
  with documented response. That is the honest
  answer; it is also the answer that survives
  follow-up examination if the regulator's
  examiner asks the same question independently
  through the ledger.
- **Why I cited the EU AI Act Art. 73
  notification in §6.** This is the *positive*
  evidence that Northfield's program is operating:
  when a threshold was crossed and the
  classification taxonomy fired, the program
  reported per Art. 73. The notification itself
  is in the ledger; referencing it strengthens
  the package's posture.
- **Why I separated the per-site detail from the
  cross-site aggregate.** The state insurance
  regulator is interested in the program's
  performance across Northfield's footprint.
  Burying the site-level detail in the aggregate
  would hide the H-04 incident; surfacing only
  the site-level detail would distort the
  picture. The reference shows both.
- **Why the verification protocol references
  specific URLs.** §4.5 — the verification
  protocol must be executable. Without the JWKS
  URL and the transparency-log URL, the regulator
  cannot independently verify.
- **What this package deliberately under-
  specifies.** The detail of the annexes (the
  full 50-operation evidence records, the full
  cryptographic proofs, the witness signatures).
  These exist in the actual package; the exercise
  treats them as references.
- **What I would do differently in v2.** Include
  an *interpretation appendix* — a brief
  practitioner-level explanation of how to read
  the evidence records, helpful for examiners who
  do not work with Merkle proofs daily. The
  reference omits for length but a working
  program's evidence packages should include it.

---

Maintained by [Girish Nair](https://github.com/garynair)
