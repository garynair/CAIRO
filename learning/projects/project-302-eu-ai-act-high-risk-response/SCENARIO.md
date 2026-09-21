# Capstone 302 — Scenario

## Kerridge Healthcare and the Retinal-Imaging SaMD

You are the CAIRO at **Kerridge Healthcare**, the
medical-devices arm of Kerridge Industries
(continuity from mod-101 Ex-05, mod-103 Ex-05).

### The system

**KH-AI-027** — adult diabetic-retinopathy
screening SaMD. CNN-based image classifier that
analyses fundus images and produces a
referable / non-referable classification plus
a heatmap overlay highlighting attention
regions.

The system is intended for use in primary-care
diabetes screening — non-ophthalmologists run
the screening; the AI's output prompts
referral to an ophthalmologist for confirmed
referable cases.

### Regulatory state

The system is **pre-submission** simultaneously
to three regulators:

1. **FDA** — De Novo classification request
   pending.
2. **EU MDR** — Class IIa pursuit; CE marking
   required for EU market.
3. **EU AI Act** — **high-risk under Art. 6(1)**
   (safety component of a regulated medical
   device + third-party conformity assessment
   required for the underlying medical device).

This capstone focuses on **the EU AI Act
conformity work**. The FDA and EU MDR work is
proceeding in parallel under the regulatory
affairs team; you are responsible for the EU
AI Act layer.

### The 60-day timeline

A **Notified Body** has been engaged for both
the EU MDR conformity (Class IIa requires
third-party assessment) and the EU AI Act
conformity (high-risk systems via Annex VII
require third-party assessment for the
biometric subset; for Annex VI internal-control
route, Notified Body engagement is voluntary
but recommended for Kerridge's first
high-risk AI system).

The Notified Body **engagement meeting** is in
60 days. By that meeting, Kerridge needs the
EU AI Act conformity package substantively
ready.

### What you have

- **Clinical validation in progress.** Multi-
  site study at 14 European hospitals; 8,400
  patients across the validation cohort;
  diverse populations including age 70+ and
  multiple ethnic groups.
- **Engineering team.** Lead by the algorithm
  team that built the model.
- **Regulatory affairs team.** Senior team
  with prior FDA + EU MDR experience but
  limited EU AI Act experience.
- **Clinical advisors.** Two senior
  ophthalmologists on the advisory board.
- **External legal counsel.** Specialist EU AI
  Act counsel engaged on retainer.

### What you don't have

- **A completed EU AI Act conformity package.**
  This is what the next 60 days produce.
- **Operational post-market monitoring
  infrastructure.** Required by Art. 72; needs
  to exist before launch.
- **Article 73 incident reporting procedure.**
  Required to be in place before placing on
  the market; needs authoring.
- **Submission of the system to the EU AI
  Office database** per Art. 49. Pending the
  conformity package.

### Your authority

- You **own the EU AI Act conformity work**.
- You **collaborate with regulatory affairs**
  on the FDA + EU MDR work — they own those
  regulatory streams; you support where the
  EU AI Act overlaps.
- You **engage external legal counsel** on
  ambiguous EU AI Act interpretation
  questions.
- You **brief the Kerridge Healthcare CEO and
  the Kerridge Industries board** on EU AI
  Act conformity status at each major
  milestone.

### The stakes

Kerridge Healthcare's strategic posture
positions this product as the company's
flagship AI/ML SaMD. EU launch is targeted
for Q3 next year. A failed EU AI Act
conformity would delay launch by 6-12 months
minimum; a poorly-structured EU AI Act
conformity could produce a Notified Body
finding that requires re-architecting the
system.

The work matters.

### The discipline this capstone teaches

EU AI Act conformity is the most procedural
piece of work a CAIRO can be asked to deliver.
The artifacts have specific required content
(Annex IV is explicit); the timeline is
externally imposed; the Notified Body has
specific expectations.

The discipline: produce regulator-presentable
artifacts that survive Notified Body scrutiny
without becoming so dense that the firm's
own team cannot operate against them.

---

Maintained by [Girish Nair](https://github.com/garynair)
