# Exercise 03 — SR 11-7 Inventory Entry for an LLM — Reference Solution

## 1. Solution overview

The inventory entry below populates every field in
Sentinel's classical MRM template for Model B (the LLM
chat agent). Four classical fields needed adaptation; the
template misses five fields that materially matter for
LLM governance. The recommendation is an "LLM Supplement"
section that classical models leave blank.

---

## 2. Artifact 1 — Inventory entry

> **Model ID:** SMB-M-0294
> **Model name:** Customer-service LLM chat agent
> **Model type:** *Large language model, vendor-hosted
> (classical "Model type" field adapted — see audit §1)*
> **Model owner (role):** Head of Customer Experience,
> Retail Banking division.
> **Model purpose:** Provide self-service customer
> support for account-related inquiries; influence
> dispute initiation; reduce call-centre volume on
> low-complexity questions.
> **Inputs (named):** Customer message text; account-
> context payload pulled from Sentinel's authenticated
> account-services API (balance, recent transactions,
> dispute eligibility); session identifier.
> **Outputs (named):** Generated natural-language
> response; structured action signals (intent
> classification, escalate-to-human flag, dispute-initiation-
> intent flag).
> **Methodology summary:** Vendor X foundation model
> (current version: X-Pro-2026.02) accessed via API.
> Sentinel-authored system prompt + 23-shot in-context
> guidance defines the assistant persona, scope, and
> safety constraints. Sentinel-side output filter pass
> for PII and explicit constraints. Post-processing
> classifies user intent and emits action signals.
> **Implementation environment:** Sentinel customer-facing
> chat interface (web + mobile). Vendor API called from
> Sentinel-side backend; no customer data sent to vendor
> outside the message text and session ID. Rate-limited
> to ~50 requests / second peak.
> **Development date:** Pilot deployed [date]; current
> form (post the recent vendor model swap) in production
> since [date].
> **Last validation:** [pre-pilot validation date] —
> conducted by MRM with CAIRO function contributing AI-
> specific patterns. Outcome: pass with conditions.
> Conditions covered (i) bias-stratified monitoring
> deployment, (ii) prompt-template versioning discipline.
> **Tier:** Tier 2 (per Exercise 01 reference).
> **Material limitations:** Generated outputs are not
> deterministic; identical inputs may produce different
> outputs across sessions. The vendor's foundation model
> may change with 30-day notice (re-validation trigger).
> Output filter cannot guarantee zero PII leakage; bias
> in language patterns is detectable in monitoring but
> not at-generation.
> **Performance metrics:** Customer-satisfaction-survey
> response rate (lagging); session-resolution rate
> (lagging); fraction of sessions escalated to human
> (mixed); model-confidence-score distribution shift
> (leading; not yet operational). Detailed metric list:
> see Measurement Plan SMB-M-0294-MP.
> **Material changes since last validation:** Vendor
> foundation-model swap [date — two months ago]. Triggered
> targeted re-validation; pending close.
> **Vendor (if any):** Vendor X (LLM provider). Contract
> in force through [date]. SLA includes 30-day notice
> on foundation-model swaps; vendor has met SLA on the
> most recent swap.

---

## 3. Artifact 2 — Completeness audit

### Fields adapted from the classical template

1. **Model type.** Classical template offered "statistical
   / econometric / mixed". LLM does not fit cleanly.
   Adapted to "Large language model, vendor-hosted". The
   adapted value carries meaning *Vendor-hosted* should
   be elsewhere; see missing fields below.
2. **Methodology summary.** Classical methodology summary
   assumes the model methodology is the firm's choice.
   For an LLM, the *vendor's methodology* (training
   approach, alignment technique, scale) is unknown.
   Adapted to describe Sentinel-side configuration
   (prompt + filter + post-processing) rather than the
   vendor's model methodology. The classical-model
   reader expects more detail than is honestly available.
3. **Inputs (named).** Classical models have well-defined
   feature inputs. LLMs receive open-ended text.
   Adapted to describe *what Sentinel passes to the
   vendor* rather than what the model uses internally.
4. **Performance metrics.** Classical metrics
   (accuracy, AUC, KS-statistic) do not map. Adapted
   to LLM-relevant metrics (resolution rate, escalation
   rate, drift signals).

### Fields the classical template misses

Five LLM-relevant fields that have no home in the
classical inventory:

1. **Prompt template version.** What system prompt
   version is currently in production. Without this,
   "the model" is under-specified — two different
   prompts produce two different systems on the same
   foundation model. *Why it matters:* prompt changes
   are material model changes (§3.4 of the lecture
   notes); the inventory must track them.
2. **Vendor model-version pinning policy.** Whether
   Sentinel has contractually pinned the foundation
   model version or accepts vendor swaps. The vendor-
   swap exposure (the actual recent event) lives here.
   *Why it matters:* foundation-model swap is a
   material change requiring re-validation;
   the inventory must track whether the firm is exposed
   to it.
3. **Output filter configuration.** What Sentinel-side
   output filtering is in place (PII detection, content
   policy, persona constraint). *Why it matters:* the
   filter is part of the production behaviour; without
   it documented, an audit cannot verify the controls.
4. **Evaluation set provenance.** For each evaluation
   metric, which evaluation set (production-sampled,
   synthetic, vendor-supplied) is used to compute it,
   and its refresh cadence. *Why it matters:* per §4.4
   of mod-103, eval-set discipline is the foundation of
   trustworthy metrics.
5. **Deployment-time guardrails.** Rate limits,
   session-isolation controls, authentication checks,
   PII-flow constraints. *Why it matters:* LLM systems
   have rich attack surfaces; the inventory must track
   what guardrails are in place to enable security
   validation.

### Recommendation to the MRM Lead

Add an **"LLM Supplement" section** to the MRM model
inventory template, consisting of the five fields above.
Classical models leave the section blank; LLM-class
models populate it. The supplement preserves backward
compatibility with the existing template (no field
renamed, no field removed) while making LLM-specific
governance machinery available where it matters.

Proposed supplement field set:

| Field | Required for |
|---|---|
| Prompt template version + history | All LLM systems |
| Foundation-model version + pinning policy | All vendor-hosted LLM systems |
| Output filter configuration | All LLM systems with output to external or sensitive surfaces |
| Evaluation set provenance | All LLM systems with metric reporting |
| Deployment-time guardrails | All LLM systems |

Tier 1 LLM-class systems would have all five fields
populated; Tier 2 would have all five but at less depth;
Tier 3 LLM-class systems (rare) would have at minimum
the prompt-template-version field.

---

## 4. Reasoning notes

- **Why the "LLM Supplement" approach rather than a
  parallel template.** Parallel templates fragment the
  inventory and force decision-points ("which template
  do I use") that are themselves a failure surface.
  A supplement section that classical models leave
  blank is operationally cleaner.
- **Why "prompt template version" is the first
  supplement field.** Of the five, it is the one most
  often forgotten in real-world LLM inventories. A
  program that tracks prompt versions has effectively
  defeated half of the LLM-specific drift risk.
- **What the inventory entry deliberately under-
  specifies.** The vendor-side methodology. Sentinel
  does not have access to Vendor X's training process
  or alignment technique. Pretending otherwise in the
  inventory would be dishonest. The reference handles
  this by adapting the Methodology field and naming
  the limitation in Material Limitations.
- **The implicit governance test.** If an examiner
  reads this inventory entry, can they identify
  every material decision point in Model B's
  behaviour and trace each to a documented control?
  For Model B specifically, the answer is *almost
  yes* — the LLM Supplement closes the remaining
  gap. A classical-only entry would leave the
  examiner with the right questions and no answers.
- **What a Tier 1 LLM inventory entry would look
  like.** All of Model B's fields, plus: a more
  detailed prompt-template change-history; a vendor
  evaluation-attestation reference; a third-party
  validation attestation; a more specific eval-set
  provenance description. The principle of "LLM
  Supplement varies by tier" should be in the MRM
  policy update.

---

Maintained by [Girish Nair](https://github.com/garynair)
