# Chapter 1 — From Framework to Program

## Why this chapter exists

The NIST AI Risk Management Framework is complete on paper.
Every working CAIRO discovers, usually around month three of
the role, that *complete on paper* and *complete as a
program* are not the same thing. The gap is the most common
cause of AI risk programs that look right on a slide and
fail at the first regulatory review.

This module is organised around the gap. Chapter 1 names
it. Chapters 2–7 close it, function by function. Chapter 8
puts the loop under a signed risk-appetite statement.

## Frameworks specify functions; programs need artifacts

NIST AI RMF (NIST AI 100-1, 2023) tells you that GOVERN,
MAP, MEASURE, and MANAGE must be present. It does not tell
you what evidence each function must produce, in what form,
on what cadence, owned by whom, reviewed by whom, retained
for how long. Those questions are program questions, not
framework questions.

A useful mental conversion:

| Framework asks | Program answers |
|---|---|
| Is the function performed? | What artifact proves it? |
| Who is accountable? | Whose calendar does the artifact appear on? |
| How is it measured? | What dashboard shows the measure? |
| What happens on a finding? | What ticket gets opened where? |
| How often does it run? | What line of the operating rhythm calendar? |

Programs that skip the conversion produce policies that
exist *and* incidents that surprise everyone equally. The
first regulator to ask *"show me the risk-management
system"* — not *"is there one"* — will discover the gap in
the room.

ISO/IEC 23894:2023 (AI Risk Management Guidance) and
ISO/IEC 42001:2023 (AI Management System) push in the same
direction — 42001 in particular is a *management system*
standard, meaning it wants named artifacts, controlled
documents, defined records, and audit evidence. If your
program can pass an ISO 42001 certification audit, it has
already made the framework-to-program conversion. If it
cannot, that is a diagnostic.

## The measure-first failure mode

Of the four NIST functions, MEASURE is the most
demonstrable. Dashboards are visible; eval scores are
shareable; trending lines are board-friendly. New programs
gravitate toward MEASURE because it produces immediate
visible output — a graph in a slide, a number to point at.

This is exactly backwards. MEASURE is **the third function
in sequence**:

- Without **MAP**, you have not classified the system, so
  you do not know what to measure. MEASURE produces
  metrics for the wrong things.
- Without **GOVERN**, no one has decided what acceptable
  looks like. MEASURE produces metrics no one acts on.
- Without **MANAGE**, threshold breaches have no
  treatment path. MEASURE produces alarms with no
  responders.

The dashboards exist; the program is hollow. Auditors read
this pattern quickly — many green tiles, no traceable
decision cascade behind any of them.

A well-sequenced program does GOVERN and MAP first, then
MEASURE on the items MAP surfaced, then MANAGE on what
MEASURE flags. The sequence makes the loop close.
Chapter 7 develops what *closing the loop* means as an
observable behaviour.

## Frameworks are language; taxonomies are vocabulary

NIST AI RMF gives you four functions. A program also needs
a **taxonomy** — a structured vocabulary for the *risks
themselves*, independent of which function is currently
handling them.

Without a taxonomy, the same risk shows up as *"fairness
issue"* in a MAP impact assessment, *"bias score
deviation"* in a MEASURE dashboard, and *"model retraining
ticket"* in a MANAGE workflow — and the program does not
know they are the same risk. When the pattern later
surfaces on the front page of a newspaper, the program
cannot show it saw the pattern coming, because the pattern
was spread across three vocabularies.

Chapter 2 builds the taxonomy. Everything after that is
taxonomy-shaped.

## Three organising rules for the rest of the module

Restate for use as a compass:

1. **Every function must have named artifacts.** If you
   cannot point to what a function produces, the function
   is not running.
2. **Sequence matters.** GOVERN and MAP set the scope;
   MEASURE and MANAGE run against that scope; GOVERN
   updates the scope from what they learn.
3. **The taxonomy is the index.** Every artifact refers to
   risk categories from the same taxonomy. Cross-function
   traceability lives there.

If any chapter drifts from these, come back and check the
chapter against them.

## What this chapter does not do

This chapter does not tell you how to *run* MAP, MEASURE,
MANAGE, or GOVERN — Chapters 3 through 7 do that. It also
does not tell you which of the four functions you should
staff up first — that is an operating-model question
answered in mod-101 Chapter 6. What it does is set the
frame for reading the rest of the module: everything below
is a program conversion of a framework activity, and if the
conversion produces no artifact, no owner, and no cadence,
it has not happened.

## Summary

- Frameworks say *what* functions must exist. Programs say
  *what artifacts* prove each function is running, who
  owns them, and on what cadence.
- The most common failure is *measure-first*: producing
  dashboards without MAP context, GOVERN thresholds, or
  MANAGE responses. The dashboards exist; the program is
  hollow.
- A framework gives you a language; a taxonomy gives you a
  vocabulary for the risks themselves. Without the
  taxonomy, the same risk appears under three names and
  the program never sees it whole.
- Read the rest of the module against three rules: named
  artifacts, sequenced execution, taxonomy-anchored
  traceability.
