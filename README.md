# Louise Beale Presentation Evaluator

A one-shot [Claude](https://claude.ai) / [Claude Code](https://docs.claude.com/en/docs/claude-code) **skill** that scores a presentation, keynote, or talk against a delivery-quality rubric distilled from Louise Beale's TEDx talk **["How to speak powerfully in the age of AI"](https://youtu.be/va-T1gX9iNk)** (TEDxNorthampton, 2026).

Point it at a near-final deck, script, or rehearsal transcript and it returns a structured scorecard — strengths, impact-ranked gaps, a cut list, and a rehearsal checklist — in a single pass. The goal is simple: **find the weak spots before your audience does.**

---

## The framework

Beale's thesis is that AI can hand you the facts in seconds, but it can't feel a room shift, carry emotion, or be authentic — so in the AI age the *human* layer of speaking matters more, not less. Her method has two parts.

### A SMILE — the preparation checklist
| | Dimension | The question it answers |
|---|---|---|
| **A** | Audience | Who is this *for*? Does it say what *they* want to hear? |
| **S** | Start | Does the opening hook in the first ~30 seconds? |
| **M** | Messages | Few and tight, or many and diluted? |
| **I** | Intent | Is there **one** takeaway you can state in a sentence? |
| **L** | Language | Plain, spoken, "explain-it-to-a-friend" language? |
| **E** | Examples | Are claims made concrete with vivid, human stories? |

Plus her hardest question: **what to leave *out*.**

### The 3 Ps
- **Prepare** — the A-SMILE work above.
- **Practice** — rehearse *out loud* to kill phrasing that looks fine on paper but clunks when spoken.
- **Perform** — three micro-tips: **pause** (a beat before you start), **emphasis** (write the lines that must land to be emphasized), and **smile** (warmth projects confidence).

---

## What the skill produces

A scorecard across nine dimensions (out of 45) — Audience, Start, Messages, Intent, Language, Examples, Cut, Practice, and an overall "AI-age human edge" check — each with a score, evidence quoted from your own material, the gap, and a same-day fix. It also emits a **rehearsal-only checklist** for the things a document physically can't grade: live pausing, vocal emphasis, body language, and on-stage warmth — the part Beale says AI can't do for you.

## Install

**Claude Code:** copy the [`presentation-evaluator/`](presentation-evaluator/) folder into your skills directory, or import the packaged [`dist/presentation-evaluator.skill`](dist/presentation-evaluator.skill).

Then invoke naturally:

> "Evaluate my keynote deck — where will I fall short?"

## Attribution & disclaimer

The **framework** is Louise Beale's, presented publicly in her TEDx talk linked above — full credit to her. This repository is an **independent, unofficial** interpretation that turns that framework into an evaluation rubric. It is **not affiliated with, reviewed by, or endorsed by** Louise Beale, TED, or TEDxNorthampton. Watch the original talk — it's worth your 17 minutes.

The skill paraphrases her method; it does **not** reproduce the talk's transcript.

## License

[MIT](LICENSE) — © 2026 Lance Winder / SilverWulf's Computer Service. Built with the [Lazy Admin School of Thought](https://silverwulf.com).
