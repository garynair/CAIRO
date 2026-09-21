# Exercise 05 — Build vs Buy vs Partner — Reference Solution

## 1. Solution overview

The recommendation is **partner** for Halverston.
Reasoning: Halverston's multi-LOB structure and the
public-markets latency requirement make pure buy
infeasible; the engineering investment and timeline
of pure build are not justified by Halverston's
scale. The partner pattern: **build the policy and
orchestration layer in-house**; **buy the identity /
attestation infrastructure and the audit ledger**.
Vendor capture is addressed by multi-vendor strategy
on the bought components.

---

## 2. Artifact 1 — Decision matrix

| Dimension | Build | Buy (single vendor) | Partner |
|---|---|---|---|
| Time-to-deploy | 18–24 months | 6–9 months | 9–12 months |
| Engineering investment (5-year) | $20–30M total ($4–6M initial + $3M/yr operating × 5) | $7.5–12.5M licensing × 5; $1M integration | $4M built + $0.8–1.5M × 5 licensing + $1M integration |
| Annual operating cost | $3M (8–12 FTE) | $1.5–2.5M licensing + $0.8M (2–3 FTE) | $0.8–1.5M licensing + $1.5M (4–6 FTE) |
| Vendor dependency | None | High — single vendor | Selective — multiple vendors for bought components |
| Customisation for public-markets latency | Maximum — built to spec | Limited — vendor product may not meet PM latency | Selective — PM-critical components built in-house |
| Multi-LOB fit | Maximum — each LOB's needs accommodated | Vendor product fits some LOBs better than others | Selective — orchestration layer built to support all LOBs |
| Regulatory defensibility | Self-attested; complete control | Vendor-attested + vendor audit reports + Halverston wrapper | Mixed; bought components carry vendor attestations, built components self-attested |
| Standards evolution responsibility | Halverston tracks W3C, NIST, OAuth — full burden | Vendor handles | Bought components: vendor; built components: Halverston |
| Recruiting / talent posture | Hard — cryptographic expertise needed in-house | Easy — operations and integration roles | Medium — some cryptographic expertise; more orchestration / policy roles |

---

## 3. Artifact 2 — Recommendation memo

> **MEMO**
> **TO:** CTO and CISO, Halverston Capital
> **FROM:** Chief AI Risk Officer
> **DATE:** [date]
> **SUBJECT:** Trust architecture program — build vs. buy
> vs. partner recommendation
> **PAGES:** 2

I recommend **partner** for Halverston's trust
architecture program. Specifically: **build the
policy and orchestration layer in-house**, **buy the
identity / attestation infrastructure and the audit
ledger from commercial vendors**, and **adopt a
multi-vendor strategy** for the bought components
to address vendor capture. The reasoning below
covers the four dimensions that determined the
choice and is honest about what the choice gives up.

### Why partner over build or buy

**Public-markets latency** is determining. Halverston's
systematic-strategy agents in Public Markets have
trust-decision latency requirements in the
microseconds-to-low-milliseconds range — orders of
magnitude tighter than the agentic-customer-service
patterns commercial vendors are designed for. A pure
*buy* would require either accepting trust-gate
latency that the public-markets agents cannot
tolerate, or operating those agents outside the
trust architecture (which defeats the program).
Building the orchestration and policy layer in-house
lets us tune the public-markets path specifically.

**Multi-LOB structure** is also determining. The
three lines of business have materially different
trust-architecture needs: public markets requires
extreme latency; private credit requires
sophisticated capability vocabulary for
underwriting decisions; wealth advisory requires
customer-facing identity flows. No single commercial
product fits all three. Buying separately for each
LOB would produce inconsistent posture across
Halverston. Building the orchestration layer once
and adapting it to each LOB preserves consistency
where it matters.

**Engineering scale** rules out pure build. Halverston
has a substantial engineering organisation but does
not have the cryptographic-engineering specialist
team required to build identity / attestation
infrastructure (signed credentials, key management,
revocation lists, JWKS rotation) from scratch and
maintain it at production quality. Buying these
components from vendors who specialise in them is
operationally honest.

**Time-to-deploy** is a soft determinant. The 9–12
month partner timeline is acceptable for our roadmap.
The 18–24 month build timeline would defer the
program's first material risk reduction by over a
year — material to the AI Risk Council and the
Board.

### What this gives up

The partner choice is not free. Specifically:

- **Integration complexity.** Wiring commercial
  identity / attestation infrastructure into our
  built orchestration layer is non-trivial. The
  estimated 4–6 FTE ongoing for the program is
  substantially in this seam. If we underestimate
  the integration work, the timeline slips.
- **Partial vendor dependency.** Identity / attestation
  vendors become critical infrastructure for
  Halverston. Vendor outage = orchestration outage.
  This is a real risk and is addressed in §3.4
  below.
- **Some standards drift exposure.** The bought
  components track standards on the vendor's
  schedule, not Halverston's. We may face short
  windows of incompatibility during major standards
  updates.

I am asking the council to accept these costs as the
price of (a) public-markets-latency capability,
(b) multi-LOB consistency, and (c) avoiding the
two-year build-from-scratch alternative.

### CAIRO-program-specific contribution

The CAIRO function specifically contributes to this
choice:

1. **Regulatory defensibility.** Built orchestration
   gives Halverston direct control of the policy
   logic that authorises operations. Bought
   components carry vendor attestations Halverston
   can present at audit. The combination is
   stronger than either alone.
2. **Audit / evidence requirements.** Bought
   audit-ledger components must produce signed
   evidence in the formats Halverston's CAIRO program
   has standardised (mod-108 will treat in detail).
   Vendor selection criteria include export-format
   compatibility.
3. **AI-program constraints.** The orchestration
   policy logic must integrate with the AI risk
   register, the bias monitoring (mod-105), the
   MRM model lifecycle (mod-104). Built-in-house
   makes these integrations tractable; bought
   would force us to fit our program into the
   vendor's policy model.
4. **Long-term posture.** Building the orchestration
   layer makes Halverston a credible
   trust-architecture practitioner — useful for
   recruiting, for the next round of regulator
   engagement, and for advising the firm on AI
   investment decisions across the portfolio.

### Vendor capture analysis

The bought components carry vendor capture risk.
Halverston's mitigations:

- **Standards-based interfaces** for both bought
  components: identity / attestation must speak
  W3C VC + JWT + OAuth; audit ledger must export
  in standards-compatible formats (JSON Lines + JWS
  signatures + a documented schema). This makes
  vendor substitution technically possible.
- **Multi-vendor strategy** — Halverston will
  contract with two identity / attestation vendors
  for redundancy. The orchestration layer is
  built to use either vendor without reconfiguration.
  Audit ledger is single-vendor at start (acceptable
  for cost reasons) but with a documented migration
  path.
- **Annual vendor concentration review** by the CAIRO
  function as part of the obligations register
  cycle (per mod-102 §6.1).
- **Documented architecture independence** — the
  program documentation explicitly states what
  each vendor provides and what would need to be
  replaced if the vendor were unavailable. The
  document is owned by the CAIRO function and
  reviewed annually.

### Acknowledged uncertainties

Three substantial uncertainties the decision does
not fully resolve:

1. **Standards evolution.** W3C VC 2.0 is current;
   later versions may impose breaking changes.
   *Management plan:* Halverston tracks standards
   working groups and budgets for an annual
   compatibility refresh in the orchestration layer.
2. **Vendor consolidation.** The trust-architecture
   vendor market is young; consolidation (M&A,
   product discontinuation) is plausible within 5
   years. *Management plan:* the multi-vendor
   strategy provides resilience; an annual
   vendor-risk review is performed by the CAIRO
   function with input from Vendor Risk.
3. **Public-markets agent capability evolution.**
   The current public-markets agents do not need
   the full agentic-tool-calling pattern; they
   are decisioning systems whose trust
   requirements are simpler. If public-markets
   evolves toward more tool-calling agentic
   patterns over 5 years, the in-house
   orchestration layer must extend. *Management
   plan:* the orchestration layer is built with
   tool-calling-pattern support as a first-class
   case; latency optimisations are configurable
   per agent class.

— end memo —

---

## 4. Reasoning notes

- **Why partner and not just buy with a vendor
  selected for public-markets latency.** No
  current commercial vendor offers microsecond-
  range trust-gate latency suitable for systematic
  trading. The closest is roll-your-own
  service-mesh patterns, which are commercial in
  parts but not as a complete trust architecture.
  Even if such a vendor existed, vendor-locking
  the entire trust architecture to one product
  for one LOB's latency requirement would impose
  unacceptable constraints on the other LOBs.
- **Why I separated the identity / attestation
  layer from the audit ledger as both candidates
  for buying.** They are the components where
  building offers the least differential value.
  Standards exist (W3C VC for identity;
  RFC 9162 + JOSE for transparency ledgers); the
  engineering work is well-understood; the
  failure modes are well-mapped. The CAIRO function
  doesn't add specific value by Halverston-building
  these vs. integrating commercial offerings that
  speak the same standards.
- **Why the orchestration layer is the one to
  build.** This is where Halverston's specific
  context matters most. Policy decisions, multi-
  LOB customisation, the integration with the AI
  risk register and the MRM lifecycle — these are
  Halverston-specific and benefit from in-house
  control. Commercial orchestration products
  exist but they impose their own policy models;
  Halverston's policy model is determined by its
  program design.
- **Why I'm honest about the integration risk.**
  The 4–6 FTE estimate for ongoing work is real,
  and most of it is the integration seam. Programs
  that underestimate this discover the cost when
  the integration shows seams during incidents.
  Surfacing it in the memo gives the CTO and CISO
  a chance to push back if they think the estimate
  is wrong; my view is the estimate is on the low
  side and will need to be revisited in 12
  months.
- **The hardest call.** Whether to recommend
  starting with single-vendor for identity /
  attestation and adding the second vendor in
  year 2, vs. starting with two vendors. Two
  vendors at start is the safer posture but
  doubles the integration work upfront. The
  reference recommends starting with two — the
  cost is real but defers a second integration
  cycle that would be expensive to insert later.
- **What would change my recommendation.** If
  Halverston decided to exit public markets
  (rumoured but not confirmed as of memo date),
  the latency constraint goes away and a pure
  *buy* becomes more attractive. The reference
  assumes no such decision; the memo's
  recommendation would be revisited if it
  occurred.
- **What this analysis deliberately under-
  specifies.** The specific vendor identities for
  the bought components. The CAIRO function's role
  is the decision framework and the requirements;
  vendor selection is engineering and security
  led, with CAIRO input on requirements fit and
  vendor risk.

---

Maintained by [Girish Nair](https://github.com/garynair)
