# Deliverable 05 — Trust Architecture Build/Buy/Partner — Reference Solution

## 1. Solution overview

Recommendation: **partner** — buy the identity /
attestation infrastructure and the audit ledger
primitives from a commercial vendor; build the
policy and orchestration layer in-house;
*explicitly architect for the customer-edge
deployment pattern* that Northrise's Agent
Platform requires. Vendor capture addressed
via standards-conformant interfaces;
customer-edge consideration drives the build
vs. buy boundary differently than financial-
services references.

---

## 2. The decision matrix

| Dimension | Build | Buy | Partner |
|---|---|---|---|
| Time-to-deploy | 18-24 months | 4-6 months | 8-12 months |
| 5-year total cost | $8-12M | $4-6M (license) | $5-7M (split) |
| Annual operating cost (steady-state) | $1.5M | $0.8-1.2M | $1.2M |
| Vendor dependency | None | High | Medium |
| Customisation for customer-edge pattern | Maximum | Limited — vendor's pattern may not fit | Selective — orchestration custom; primitives standard |
| Customer trust signal (enterprise customers favor standards-conformant) | Self-attested | Vendor brand | Standards-conformant primitives + Northrise-controlled orchestration |
| Standards conformance | Self-enforced | Vendor-enforced | Both layers conformant |
| Engineering capacity required | High specialised | Low | Medium |
| Migration risk | None | High | Medium |

## 3. Recommendation memo

> **TO:** CTO and Head of Security.
> **FROM:** Chief AI Risk Officer.
> **SUBJECT:** Trust architecture posture for
> Agent Platform.

**Recommendation: partner.** Specifically:
**buy** identity / attestation infrastructure
and audit-ledger primitives from a commercial
vendor; **build** the policy and orchestration
layer in-house with explicit accommodation for
customer-edge deployment.

### Why partner

**Customer-edge deployment** is determining.
The Agent Platform runs at customer
infrastructure with customer configuration.
Trust architecture must work *across the
Northrise-customer boundary*, not just at
Northrise hub. This is a different shape from
the reference patterns from mod-106. Commercial
vendors' patterns assume the trust authority is
the deploying organisation; Northrise's pattern
requires Northrise's trust authority to interact
with customer authorities (which Northrise
doesn't operate) and with customer
configurations (which Northrise doesn't
control).

The hybrid resolves this:

- **Standards-conformant primitives (buy).**
  Identity / attestation per W3C VC + OAuth +
  JWT (per mod-106 §3 patterns). Audit ledger
  per RFC 9162. These are well-bounded
  components where vendor expertise adds
  value.
- **Custom orchestration (build).** The
  orchestration that integrates with customer
  authorities, surfaces customer-side controls
  as Northrise capabilities, and presents the
  Northrise-controlled portion as a unified
  trust architecture is Northrise-specific.

**Time-to-deploy.** 8-12 months is tight but
achievable for the partner path. Build alone
would exceed Northrise's window before Series D.

**Enterprise customer signal.** Top-20
enterprise customers are increasingly
diligencing trust architecture. The
*recognition* of standards-conformant
primitives (RFC 9162; W3C VC) carries customer
weight; the *control* of orchestration carries
investor weight on Series D. Partner delivers
both.

### What is given up

- **Engineering specialisation requirements.**
  Northrise's engineering team takes on
  meaningful cryptographic engineering work
  for the orchestration layer.
- **Vendor dependency on primitives.** Vendor
  outage or pivot would affect Northrise.
  Multi-vendor strategy on primitives mitigates
  but doesn't eliminate.
- **Coordination cost.** Multiple components
  from multiple sources require integration
  discipline.

### CAIRO function contribution

The CAIRO's contribution to this decision:

- The requirements that drive the partner
  pattern (the customer-edge consideration).
- The vendor risk assessment of the primitives
  vendor.
- The program-level position that integrates
  this architectural choice with the broader
  AI program.
- The long-term maintenance posture and
  succession-readiness of the choice.

The architecture choice itself is engineering-led
with the above CAIRO inputs.

### Vendor capture analysis

The bought primitives carry vendor capture
risk. Mitigations:

- **Standards-based interfaces** required:
  primitives must speak W3C VC + RFC 9162 +
  RFC 3161 so substitution is technically
  feasible.
- **Multi-vendor strategy** at the primitives
  layer — Northrise contracts with two
  identity / attestation vendors for
  redundancy after year 1.
- **Annual vendor concentration review** by the
  CAIRO function.

### Acknowledged uncertainties

1. **Customer adoption of Northrise's
   trust architecture controls.** Customers
   may not configure trust controls actively.
   Mitigation: customer-facing guidance + customer
   success monitoring.
2. **Foundation-model vendor cooperation on
   identity-attestation patterns.** Some
   foundation-model providers don't support
   model-identity attestation patterns
   directly. Mitigation: engineering work to
   compensate where vendor support is absent.
3. **Standards evolution.** W3C VC and RFC
   9162 are stable but may evolve. Mitigation:
   standards-tracking work shared with the
   vendor.

— end memo —

---

## 4. Reasoning notes

- **Why partner over pure buy.** Buy would
  produce a vendor-shaped trust architecture
  that doesn't address customer-edge. Critical
  weakness for Northrise.
- **Why partner over pure build.** Northrise
  doesn't have the cryptographic engineering
  team to build identity / attestation from
  scratch and maintain it. Buying primitives
  is operationally honest.
- **What this decision deliberately doesn't
  do.** Name specific vendors. Vendor
  selection is engineering-led with input
  from CAIRO on requirements fit.
- **What would change my recommendation.** If
  Northrise's Agent Platform exits market and
  the only remaining products are
  Northrise-hosted (Analytics, Studio), the
  customer-edge consideration disappears and
  pure buy becomes more attractive.

---

Maintained by [Girish Nair](https://github.com/garynair)
