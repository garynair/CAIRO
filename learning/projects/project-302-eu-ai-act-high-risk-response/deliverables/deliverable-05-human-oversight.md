# Deliverable 05 — Article 14 Human Oversight Design

**Target:** Days 26-32. **Length:** ≤ 3 pages.
**Modules:** mod-102 §2.3 (Art. 14); mod-105
(transparency + contestability); mod-106 §3
(capability scoping at the trust-architecture
level).

## What this deliverable is

The human oversight design for KH-AI-027. Art.
14 requires that high-risk AI systems be
"effectively overseen by natural persons" during
the period in which the system is in use. The
oversight design specifies *how* this happens
for KH-AI-027 — who oversees, with what
information, with what authority, at what
points.

## What it should contain

1. **The oversight model.** The three Art. 14
   modes (human-in-the-loop, human-on-the-loop,
   human-in-command) per EU HLEG framing.
   Which mode applies to KH-AI-027 and why.
2. **Who oversees.** The named clinical role
   that operates the system. For KH-AI-027:
   the primary-care clinician operating the
   screening; the ophthalmologist receiving
   referrals; the clinical quality officer
   at site level.
3. **Information provided to the human
   operator.** What the screening clinician
   sees (referable / non-referable
   classification; heatmap; confidence
   indicator; system version); what the
   receiving ophthalmologist sees; what the
   clinical quality officer sees.
4. **Authority and constraints.** Per Art.
   14(4) — the human operator's authority to
   override; the conditions under which
   override is documented; the conditions
   under which override patterns are
   reviewed.
5. **Asymmetric escalation design** (per
   mod-105 Ex-03 reference) — KH-AI-027 can
   prompt referral; cannot prevent referral
   the clinician would otherwise have
   initiated.
6. **Workflow integration.** How the
   oversight design integrates with primary-
   care screening workflows; how
   site-level training operationalizes the
   oversight.
7. **Limits of oversight.** Honest naming of
   what the human oversight cannot reasonably
   catch — the workflow-capture failure mode
   from mod-105 §4.5.

## Constraints

- The oversight design must address Art. 14(4)
  specifically — the (a) through (e)
  obligations.
- The asymmetric-escalation pattern is
  required — KH-AI-027 cannot recommend
  *against* referral; only *for*. This is the
  clinical-safety-driven design.
- "Limits of oversight" section must be
  substantive — Art. 14 is sometimes treated
  as a checkbox; effective oversight requires
  acknowledging what humans cannot reasonably
  do.

## Rubric

| Criterion | Weight |
|---|---|
| Art. 14 mode named and defended | 15% |
| Named overseers — specific roles | 20% |
| Information provided per role | 20% |
| Asymmetric escalation design | 15% |
| Workflow integration substantive | 15% |
| Limits of oversight named | 10% |
| Length discipline ≤ 3 pages | 5% |

## Where to find help

- mod-102 §2.3 (Art. 14 in depth).
- mod-105 Ex-03 reference (asymmetric
  escalation for Aldwych ED triage).
- mod-105 §4-5 (transparency + contestability).
- EU AI Act Art. 14 (read directly).
