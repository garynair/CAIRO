# Deliverable 05 — Controls Hardening Plan

**Target:** Days 10-25. **Length:** 5-7 pages.

## What this deliverable is

The forward-looking remediation plan. What
specifically Northrise will change about
GuardianGPT's architecture, development
process, deployment process, and operations
to prevent recurrence of this incident
class. Goes to engineering for execution;
CISO for security sign-off; CEO and Board
for governance commitment.

## What it should contain

1. **Architecture changes.** Specific
   changes to GuardianGPT's tenant-
   isolation architecture. Defense-in-
   depth approach: identity scoping at
   query, retrieval, and synthesis layers
   independently.
2. **Development-process changes.**
   Specific changes to code review,
   testing (tenant-isolation tests as a
   class), and CI gating. Tied to mod-110
   systemic-cause findings.
3. **Deployment-process changes.**
   Staging environment behavior; canary
   rollout discipline; rollback gates.
4. **Operational changes.** Active
   tenant-isolation monitoring;
   query-pattern anomaly detection;
   customer-facing self-service
   investigation tools.
5. **Detection-side improvements.** How
   the next incident of this class would
   be caught by Northrise rather than by
   a customer red team. Specific signals;
   specific monitoring.
6. **Vendor-model interaction.** What in
   this incident is attributable to the
   foundation-model layer vs. the
   Northrise integration layer. What
   foundation-model-side commitments
   matter going forward.
7. **Verification.** How Northrise will
   verify the controls are operating.
   Independent assurance (third-party
   penetration testing; SOC 2 control
   updates).
8. **Sequencing and timeline.** Specific
   dates per control. Some controls
   in-flight during the 30-day arc; some
   for Q1; some for Q2.
9. **Resourcing implications.** Engineering
   capacity; security capacity; product
   roadmap impact.

## Constraints

- Defense-in-depth, not single-point fix.
  Single-point fixes invite the next
  variant.
- Specific dates, not "we will improve."
- Honest about which controls require
  customer cooperation (e.g., customer-
  side audit-log access).
- Resourcing impact on product roadmap
  must be named; engineering team cannot
  absorb arbitrary new controls without
  trade-off.

## Rubric

| Criterion | Weight |
|---|---|
| Defense-in-depth architecture | 20% |
| Development-process changes substantive | 15% |
| Detection-side improvements specific | 15% |
| Vendor-model framing | 10% |
| Verification (independent assurance) | 15% |
| Timeline with specific dates | 15% |
| Resourcing impact named | 10% |

## Where to find help

- mod-107 (CAIRO × CISO security boundary).
- mod-110 §6-7 (systemic-cause
  corrective actions).
- mod-103 (risk taxonomy informs the
  control set).
