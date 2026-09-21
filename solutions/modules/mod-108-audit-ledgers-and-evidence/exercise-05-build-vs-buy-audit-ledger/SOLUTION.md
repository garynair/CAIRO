# Exercise 05 — Build / Buy / Partner Decision — Reference Solution

## 1. Solution overview

The recommendation is **partner** for **Halverston**:
buy the cryptographic ledger primitives from a vendor;
build the event-emission and evidence-package
assembly layers in-house. Migration risk is the
determining factor — addressed via standards-conformant
vendor requirements (from Exercise 03) and a
documented migration playbook.

---

## 2. Artifact 1 — Decision matrix

| Dimension | Build | Buy | Partner |
|---|---|---|---|
| Time-to-deploy | 12–18 months | 4–6 months | 6–9 months |
| 5-year total cost | $10.5M ($3M initial + $1.5M × 5 maintenance) | $4–7.5M ($0.8–1.5M × 5) + $0.3M | $7M ($0.8M × 5 + $1M build + $0.5M × 5 maintenance) |
| Annual operating cost | $1.5M | $0.8–1.5M | $1.3M |
| Vendor dependency | None | High — single vendor for the entire layer | Selective — vendor for ledger primitives only |
| Migration risk | None (already in-house) | High — sealed evidence integrity must be preserved across migration; multi-quarter project | Medium — only the ledger primitives need migration; event emission and packaging are Halverston-controlled |
| Standards conformance | Self-enforced (RFC 9162 + RFC 3161) | Vendor-enforced; verify in selection | Vendor-enforced for ledger primitives; Halverston-enforced for emission and packaging |
| Customisation for Halverston event vocabulary | Maximum | Limited — vendor's schema | Selective — emission layer Halverston-controlled; ledger accepts conforming records |
| Regulator defensibility | Strong — self-attested; complete control | Strong — vendor attestations are recognised | Strong — combination |
| Engineering / talent posture | Hard — 3–4 specialised cryptographic engineers required | Easy — integration roles | Medium — cryptographic engineering for emission and packaging; vendor handles ledger crypto |

---

## 3. Artifact 2 — Recommendation memo

> **MEMO**
> **TO:** CTO, CISO, CRO
> **FROM:** Chief AI Risk Officer
> **SUBJECT:** Audit-ledger build / buy / partner
> recommendation
> **DATE:** [date]
> **PAGES:** 2

I recommend **partner** for Halverston's audit-
ledger infrastructure. Specifically: **buy the
cryptographic ledger primitives** (the Merkle
tree, hash chain, sealing, witness coordination,
public-commitment publication) from a vendor;
**build the event-emission and evidence-package
assembly layers** in-house. Migration risk is
addressed via standards-conformant vendor
requirements per the structural design (Exercise
03) and via a documented migration playbook.

### Why partner over build or buy

**Migration risk** is the determining factor. Pure
buy puts Halverston in the worst position: the
entire layer depends on the vendor, and the
migration cost — measured in multi-quarter
projects to move sealed evidence with preserved
integrity — is materially higher than for most
infrastructure. Pure build avoids vendor
dependency but at substantial engineering cost and
ongoing burden (3–4 specialised cryptographic
engineers).

The partner pattern locates the vendor dependency
in **the smallest part of the layer where vendor
expertise adds most value** (the cryptographic
primitives) while keeping Halverston-specific
work (event emission and packaging) in-house. If
Halverston ever needs to migrate, the work is
limited to re-importing the ledger primitives into
a new conformant implementation; the event
emission and packaging layers do not change.

**Multi-LOB structure** reinforces the partner
recommendation. Halverston's three LOBs have
different event volumes (public-markets agents
emit far more events than wealth-advisory
assistants) and different regulator expectations
(SEC vs SR-11-7-flavored vs FINRA). A Halverston-
built emission layer can accommodate this
variation natively; a vendor-bought emission
layer would impose vendor-imposed assumptions
(typically based on the vendor's modal customer).

**Retention duration** also reinforces. Halverston's
7+ year retention obligations mean that the
audit-ledger lives a long time. Halverston-controlled
event emission and packaging insulates Halverston
from vendor pivots over a multi-year horizon —
the vendor may change its product strategy,
ownership, or pricing within the retention
window. The ledger primitives' specification is
stable (the standards do not move quickly); the
emission and packaging layers are where vendor
turbulence would matter most.

### What is given up

The partner choice is not free:

- **Integration complexity.** Wiring the event
  emission and evidence-packaging assembly with
  a commercial ledger is non-trivial. The
  estimated 1–2 FTE ongoing on integration is
  real.
- **Bounded vendor dependency.** Even with the
  Halverston-built emission and packaging, the
  ledger primitives become critical
  infrastructure. Vendor outage = inability to
  seal events = significant operational concern.
- **Specialised cryptographic engineering still
  required.** The partner pattern reduces but
  does not eliminate the need for cryptographic
  expertise; the emission layer's signing
  discipline and the verification protocol
  require ongoing specialised attention.

I am asking the council to accept these costs as
the price of (a) preserved migration optionality,
(b) multi-LOB customisation, and (c) insulation
from vendor pivots over the 7+ year retention
horizon.

### CAIRO-program-specific contribution

Per §6.5 of mod-108 of the curriculum, the CAIRO
function contributes:

1. **Requirements.** The structural design from
   Exercise 03 + the event vocabulary from
   Exercise 01 specify what the vendor must
   support and what Halverston builds. Both are
   the CAIRO's contribution.
2. **Risk assessment.** Migration risk is the most
   insidious risk per §6.4; the partner
   recommendation specifically addresses it.
   Vendor capture risk on the ledger primitives
   is bounded but real; the CAIRO function's
   vendor risk review applies.
3. **Program-level position.** The CAIRO will
   describe the architecture in the program
   charter as Halverston-controlled emission +
   vendor-provided ledger primitives + standards-
   conformant migration capability; this framing
   is presentable to regulators as a
   defensible posture.

### Migration risk mitigation

Per §6.4, three mitigations:

1. **Standards-based export.** The vendor must
   produce evidence in standards-conformant
   formats (RFC 9162 inclusion / consistency
   proofs; RFC 3161 timestamps; JOSE-format
   signatures). This makes migration
   technically feasible: another conformant
   implementation can re-verify the migrated
   evidence.
2. **Documented migration playbook.** A
   playbook exists from program day 1, even
   though no migration is planned. The playbook
   documents the export pathway, the import
   pathway, the integrity-preservation strategy,
   the estimated effort and timeline.
3. **Annual export verification.** Halverston
   produces a full ledger export annually and
   verifies it independently. This exercises the
   export pathway and surfaces problems
   (vendor pivot, export-format drift) before
   they matter.

### Acknowledged uncertainties

1. **Vendor consolidation.** The audit-ledger
   vendor market is young; consolidation within
   5 years is plausible. *Management plan:* the
   migration playbook + the annual export
   verification provide resilience.
2. **Standards evolution.** RFC 9162 v2 is
   current; later versions may impose breaking
   changes. *Management plan:* Halverston
   tracks the standards working group; the
   partner pattern means standards-tracking
   work is shared with the vendor.
3. **Halverston's own scale evolution.** If
   Halverston's event volume grows materially
   (e.g., further public-markets expansion), the
   chosen vendor's scaling capacity may be
   tested. *Management plan:* event volume is
   itself an indicator in the program's
   monitoring; vendor scaling capacity is
   tested annually.

— end memo —

---

## 4. Reasoning notes

- **Why partner specifically over single-vendor
  buy.** The buy option's migration risk is the
  critical concern. A pure buy concentrates the
  entire audit layer on one vendor, with
  Halverston's 7+ year retention obligations
  creating an extreme migration cost. Even a
  vendor as well-positioned as the strongest
  candidate carries this risk.
- **Why I did not recommend pure build.** Build
  has zero migration risk, but 12–18-month time-
  to-deploy is unacceptable for a program that
  needs to be operational now, and the
  ongoing cryptographic engineering burden is
  real. Build is the right choice for an
  organisation with idiosyncratic requirements
  not met by commercial offerings; Halverston's
  requirements are largely conformant to the
  standards-based commercial market.
- **Why I located the build/buy boundary at
  ledger primitives vs emission/packaging.** The
  ledger primitives are the most cryptographically
  intricate and the most well-standardised
  component. Halverston gains the most from
  vendor expertise here and pays the smallest
  customisation penalty. Conversely, emission
  and packaging are the most Halverston-specific.
  The boundary is *exactly* where the value
  exchange is most favourable.
- **Why annual export verification is critical.**
  Many programs assume export will work without
  testing. When migration becomes necessary
  (vendor failure, M&A, pricing change), the
  export pathway has often degraded silently.
  Annual testing surfaces this with margin to
  respond.
- **What this recommendation under-specifies.**
  The vendor selection itself. Three candidate
  vendors (named in the scenario) need evaluation
  against the Exercise 03 structural design and
  the Exercise 01 vocabulary requirements. The
  CAIRO contributes the requirements; the CTO and
  CISO conduct the selection.
- **What would change my recommendation.** If
  Halverston exited public markets (which
  produces most of the event volume), the
  vendor capacity concerns recede and a
  hyperscaler-managed buy option becomes more
  attractive. The recommendation should be
  revisited at any major portfolio change.

---

Maintained by [Girish Nair](https://github.com/garynair)
