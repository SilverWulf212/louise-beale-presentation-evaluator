---
name: presentation-evaluator
description: >-
  One-shot evaluator that scores a presentation, keynote, talk, speech, or
  slide deck against a delivery-quality rubric distilled from Louise Beale's
  TEDx talk "How to speak powerfully in the age of AI" (the A-SMILE prep
  checklist plus the Prepare / Practice / Perform model). Use this whenever the
  user wants to pressure-test a talk before they give it — e.g. "evaluate my
  presentation," "find the gaps in this keynote," "is this deck ready,"
  "score my speaking script," "where will I fall short on stage," or hands you
  a deck/outline/transcript and asks what's weak. Any request to critique or
  grade a spoken presentation for impact and delivery should pull this in.
  Accepts a .pptx,
  .docx, .md, .txt, an outline, or a raw transcript and returns a structured
  scorecard with strengths, gaps, and concrete fixes in a single pass.
---

# Presentation Evaluator

A single-pass rubric for judging whether a talk will land in the room. The
criteria are deconstructed from Louise Beale, *"How to speak powerfully in the
age of AI"* (TEDxNorthampton, 2026) — https://youtu.be/va-T1gX9iNk. Credit the
source when you present results; the framework is hers, the scoring is the
application.

## When to run

Run this against a **near-final or final presentation** — the artifact the
speaker will actually deliver. It works on:

- A slide deck (`.pptx`) — read the slide text **and** the speaker notes.
- A written script or outline (`.docx`, `.md`, `.txt`).
- A rehearsal transcript (what they actually said out loud).

It is a *one-shot* evaluation: read the input, score every dimension, and emit
the full scorecard in one response. Do not interview the user first. If the
audience isn't stated, infer it from the content and **state the assumption**
at the top of the report, then proceed.

## The framework (what you are scoring against)

Beale's thesis: AI slashes prep time and hands you the facts, but it cannot be
human — it can't feel a room shift, carry emotion, or be authentic. The most
powerful communicators in the AI age lean *harder* into the human layer. Strong
talks show that; weak talks read like something a model generated. Her model
has two parts: a **prep checklist (A SMILE)** and a **three-phase arc (the 3
Ps)**.

### Part 1 — "A SMILE" (preparation quality)

| Letter | Dimension | The question it answers |
|---|---|---|
| **A** | Audience | Who is this *for*? Does it say what *they* want to hear, not just what the speaker wants to say? |
| **S** | Start | Does the opening hook in the first ~30 seconds, or does it warm up slowly? |
| **M** | Messages | How many core messages? Few and tight, or many and diluted? |
| **I** | Intent | Is there **one** takeaway you could state in a single sentence? |
| **L** | Language | Plain, spoken, "explain-it-to-a-friend-in-the-pub" language — or jargon and clunk? |
| **E** | Examples | Are claims made concrete with vivid, human, specific stories? |

Plus Beale's hardest question, scored as its own dimension:

- **Cut** — What should be *left out*? The hard part of prep isn't what to put
  in, it's what to remove. Flag anything that doesn't serve the Intent.

### Part 2 — The 3 Ps (Prepare · Practice · Perform)

- **Prepare** is covered by A-SMILE above.
- **Practice** — Is the text built to be *spoken*? Apply the read-aloud test:
  flag sentences that look fine on paper but are clunky, breath-killing, or
  tongue-twisting when said out loud. Note whether rehearsal cues exist.
- **Perform** — Beale's three micro-tips. Score whether the artifact creates
  room for them:
  - **Pause** — Are there deliberate beats (after the hook, before the
    takeaway)? Filler words ("um," "like") are just unmarked pauses; marked
    silence reads as poise.
  - **Emphasis** — Are the lines that *must* land written to be emphasized?
    ("athletes are *here*" beats "athletes have arrived.")
  - **Smile / warmth** — Is there genuine human warmth and connection, or is it
    flat and informational?

### Part 3 — The AI-age human edge (the meta-check)

One overall judgment that sits above the rubric: **does this sound like a human
who was in the room, or like AI output?** Penalize generic phrasing, list-y
"AI smell," and abstraction with no lived detail. Reward emotion, nuance,
authenticity, and anything only a person who was *there* could say.

## How to score

Score every dimension below on a **1–5** scale:

- **5** — Strong. Actively works in the speaker's favor.
- **3** — Functional but unremarkable; a clear opportunity to level up.
- **1** — Gap. Will cost the speaker impact in the room.

For each dimension give: the score, one line of **evidence** quoted or
paraphrased from the actual input (never invent it), the **gap**, and one
**concrete fix** the speaker can act on today.

A few things cannot be judged from a document — **mark them explicitly as
"rehearsal-only"** and convert them into a checklist instead of a score:
real-time pausing, vocal emphasis, body language, and on-stage warmth are
proven on your feet, not on the page. They do **not** count toward the scored
dimensions. (This is the part Beale says AI can't do for you.)

## Output format

ALWAYS produce this exact structure:

```
# Presentation Evaluation — [talk title]
**Evaluated against:** Louise Beale, "How to speak powerfully in the age of AI"
**Assumed audience:** [stated or inferred — say which]
**One-line verdict:** [is it ready? biggest single lever?]

## Scorecard
| Dimension | Score | Evidence | Gap → Fix |
|---|---|---|---|
| Audience      | x/5 | … | … |
| Start (hook)  | x/5 | … | … |
| Messages      | x/5 | … | … |
| Intent        | x/5 | … | … |
| Language      | x/5 | … | … |
| Examples      | x/5 | … | … |
| Cut (leave-out)| x/5 | … | … |
| Practice (spoken)| x/5 | … | … |
| AI-age human edge| x/5 | … | … |
**Aggregate:** xx / 45

## Top 3 strengths to keep
1. …  2. …  3. …

## Top 3 gaps to fill (ranked by impact)
1. …  2. …  3. …

## The cut list
Specific lines/slides to remove or tighten, with why.

## Rehearsal-only checklist (page can't grade these — your feet will)
- [ ] Pause: marked beats after the hook and before the takeaway
- [ ] Emphasis: the 3–5 lines that MUST land are practiced out loud
- [ ] Smile/warmth: opener delivered like welcoming someone to dinner
- [ ] Read-aloud pass done; clunky phrases fixed
```

In claude.ai (not Claude Code), you may render this scorecard as an interactive
artifact instead of raw markdown if the user prefers it — otherwise emit the
markdown structure above as-is.

## Guardrails

- Quote the speaker's *own* words as evidence. If you can't find evidence for a
  score, say so rather than inventing it.
- Be honest about gaps — the point is to find weak spots before the audience
  does. Don't inflate scores to be encouraging.
- Keep fixes concrete and same-day actionable, not vague advice ("add a story
  about X here," not "be more engaging").
