# Module 107 — Quiz

Twenty questions. Answer key in the paired solutions repo.

---

## Section A — Threat landscape (§1)

**Q1.** Which of the following is **not** named in §1.1
as a category with documented production incidents?

  a. Prompt injection
  b. Data exfiltration through model output
  c. Membership inference attacks
  d. Tool-call exploitation in agentic systems

**Q2.** Which category does §1.2 name as remaining
mostly theoretical?

  a. Adversarial inputs to classification models
  b. Reward hacking in production
  c. Training-data poisoning
  d. Supply-chain compromise

**Q3.** True or false: A program that organises its
defences around every theoretical threat will produce
broad and deep defences.

**Q4.** Short answer: in one sentence, describe the
*misallocation pattern* (§1.3).

---

## Section B — Attack taxonomies (§2)

**Q5.** Which taxonomy is described as the **bridging
framework** for cross-LLM-and-classical-ML attack
treatment?

  a. MITRE ATLAS
  b. OWASP LLM Top 10
  c. NIST AI 100-2 E2023
  d. NIST AI RMF Playbook

**Q6.** Which taxonomy is described as best for
**executive communication of LLM-specific
priorities**?

  a. MITRE ATLAS
  b. OWASP LLM Top 10
  c. NIST AI 100-2 E2023
  d. NIST AI 600-1

**Q7.** Short answer: in one sentence, describe the
composition pattern §2.4 recommends.

---

## Section C — Defense-in-depth (§3)

**Q8.** Which is **not** one of the nine layers named
in §3.1?

  a. Principal layer
  b. Input layer
  c. Model layer
  d. Marketing layer

**Q9.** Which three layers are named in §3.2 as the
**most common blind spots**?

  a. Principal, model, infrastructure
  b. Tool, output, response
  c. Data, observability, model
  d. Input, output, infrastructure

**Q10.** True or false: Two layers using the same
filtering technique are two separate controls for
defense-in-depth purposes.

**Q11.** Short answer: in one sentence, describe the
*bypass test* (§3.4 third principle).

---

## Section D — Red-teaming (§4)

**Q12.** Which of the following is **not** named in
§4.1 as a program-level function red-teaming serves?

  a. Discover unknown failure modes
  b. Stress-test the controls
  c. Produce evidence
  d. Replace ongoing monitoring

**Q13.** What red-teaming cadence is recommended in
§4.4 for **Tier 1 Critical** systems?

  a. Trigger-based only
  b. Before deployment + annually + on material change
  c. Before deployment + quarterly + on material change
  d. Once at deployment

**Q14.** Which independence pattern is recommended in
§4.5 as the strongest for Tier 1 systems?

  a. Internal red team within the AI program with
     structural safeguards
  b. External red team or internal team in a separate
     organisational branch
  c. Development team self-evaluation
  d. Vendor-provided red team

**Q15.** Short answer: in one sentence, name one
element from §4.3 that a working red-team program
specifies.

---

## Section E — The CAIRO × CISO boundary (§5)

**Q16.** Per §5.5, where should AI-specific security
**engineering** sit?

  a. In the CAIRO function
  b. In the CISO's organisation
  c. In a parallel AI security function
  d. Outsourced to a vendor

**Q17.** Which of these is a **collision pattern**
per §5.4?

  a. Joint red-teaming expectations
  b. Cross-referenced incident classification
  c. Separate AI security incident channels
  d. Shared vendor-risk machinery

**Q18.** Short answer: in two sentences, describe how
the CAIRO × CISO boundary structurally mirrors the
CAIRO × MRM boundary (mod-104 §5).

---

## Section F — AI incident classification (§6)

**Q19.** A prompt injection causing an agent to
disclose another customer's account information is
classified as:

  a. Security incident
  b. AI-program incident
  c. Joint
  d. Neither

**Q20.** Short answer: in two sentences, describe one
EU AI Act Art. 73 timeline and explain why the
classification must be pre-computed before the
incident.
