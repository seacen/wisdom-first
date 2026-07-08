<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo/logo-wordmark-dark.svg">
  <img src="assets/logo/logo-wordmark.svg" alt="wisdom-first" width="420">
</picture>

<br>

**It widens how you think, <em>first</em> — then it solves the problem in front of you.**

**🌐 Language:** **English (this page)** · [**中文**](README.zh-CN.md)

[![version](https://img.shields.io/badge/version-3.0.0-EFE8D8?style=flat-square&labelColor=1B2C40)](https://github.com/seacen/wisdom-first/releases/tag/v3.0.0)
[![license](https://img.shields.io/badge/license-MIT-EFE8D8?style=flat-square&labelColor=1B2C40)](LICENSE)
[![format](https://img.shields.io/badge/format-Agent%20Skill-EFE8D8?style=flat-square&labelColor=1B2C40)](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)
[![install](https://img.shields.io/badge/install-skills%20CLI-EFE8D8?style=flat-square&labelColor=1B2C40)](https://github.com/vercel-labs/skills)

</div>

---

`wisdom-first` is an [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) — a portable capability that any AI agent can load. Before your assistant improvises an answer to a question that deserves real thought, it reaches for the best thinking humanity has already done on that *kind* of problem: it names two or three complementary frameworks, recommends the best books, distills them, and only then solves your problem **through** those lenses.

## Why this matters: it widens *your* thinking, not just the AI's

The easy path with AI is to hand over your judgment and take the answer on faith. You get output — but you're left *knowing what without knowing why*, a little more dependent each time.

`wisdom-first` does the opposite. It names the actual frameworks, distills the moves that matter most, and points you back to the source books — so every answer doubles as a lesson, not just a verdict for today. The AI does the retrieval and the synthesis; **you keep the wisdom.**

That's the whole bet — an AI that makes you wiser, not one that makes you dependent.

## Install

Using the open [`skills`](https://github.com/vercel-labs/skills) CLI — no install needed, just `npx`:

```bash
npx skills add seacen/wisdom-first
```

Then start a fresh agent session — it picks up `SKILL.md` automatically. The `skills` CLI auto-detects whichever agent you're using and installs to the right place.

## What it does

When you ask for advice, or take on a substantive task that rewards real thinking — strategy, a speech, high-stakes writing, a negotiation, a conflict, a hard decision, a design — `wisdom-first`:

1. **Surfaces two or three complementary frameworks + the best books** for *your specific need*;
2. **Distills** their essence and recommends them for deeper reading;
3. **Solves your problem by weaving those lenses together**, so the answer visibly comes from the wisdom, not from improvisation.

It triggers on its own for advisory / long-horizon work, or call it explicitly with `/wisdom-first`.

## How it picks — with no lookup table

The skill contains **no lookup table of "topic → book."** Hard-coding titles would make it brittle and impossible to generalize. Instead, its core ([`references/the-taste.md`](skills/wisdom-first/references/the-taste.md)) is **pure, general *taste*** — a handful of domain-blind judgments about what makes one body of thought better than another for a given need:

- diagnose the **live need** (and notice when the real block is nerve and state, not content);
- match the **scope** of the wisdom to the scope of the problem;
- prefer the work that **defines its field**, gives a **method you can practice**, comes **from the source**, and installs a **durable model**;
- offer two or three complementary works and **weave** them, rather than name-drop one.

From those judgments alone, the right canonical works fall out of the model's own knowledge — across domains the skill was never told about.

### The author's shelf (optional taste layer)

A few excellent books sit too quietly in a model's "prior" to be reached by even perfect general taste. [`references/authors-shelf.md`](skills/wisdom-first/references/authors-shelf.md) lets the author hand-seed a few personal favorites as a **tie-break only** — never overriding fit, never adding a domain. It's a way to pass a point of view about what's good along to whoever installs the skill. Fork it and make it your own shelf.

## Examples

The skill was never given a "topic → book" list — these picks fall out of its general taste. A few of the kinds of works it surfaces on its own:

| When you're working on… | It tends to reach for… |
| --- | --- |
| A presentation, and you're nervous about it | a delivery-and-presence classic (the author's shelf seeds *As We Speak*), alongside a "make it memorable" framework |
| A conflict with your partner, friend, or colleague | *Nonviolent Communication* (Marshall Rosenberg) |
| A report or email your boss must grasp fast | *The Pyramid Principle* (Barbara Minto) + MECE |
| Company strategy, spread too thin across products | *Playing to Win* (Lafley & Martin) and the strategy-as-choices cascade |
| Feeling stuck and adrift in work and life | *The 7 Habits of Highly Effective People* (Stephen Covey) |
| A negotiation where you fear it'll blow up | *Getting to Yes* (Fisher & Ury) and BATNA |

…then it distills the few moves that matter and weaves them into your actual answer.

## How it was built

`wisdom-first` was developed and validated with multi-agent evaluation workflows: each candidate version ran *with-skill vs. baseline* across a battery of real scenarios (speaking, strategy, a life rut, interpersonal conflict, business writing, negotiation, habit-building, a zero-downtime technical migration), each scenario 3× for stability, graded on whether it recalled the right canonical work, sized the wisdom to the problem, and *actually applied* the frameworks instead of name-dropping them. Rules that **sounded** wise but hurt the data (e.g. "always prefer the work that re-frames the problem") were caught and reverted. The taste you see is what survived the evidence.

## Layout

```
skills/wisdom-first/
├── SKILL.md                  # trigger + the 3-step sequence + output shape
└── references/
    ├── the-taste.md          # the core: 8 pure, domain-blind selection judgments
    ├── authors-shelf.md      # optional personal-taste tie-break layer
    └── applying-via-workflow.md  # escalating the "solve" step to a multi-agent Workflow
.claude-plugin/plugin.json     # Claude Code plugin manifest
brand.md                       # brand definition — mark, color, type, voice
assets/logo/                   # logo assets (SVG + PNG) + usage spec
evals/
└── evals.json                # acceptance scenarios
```

## License

[MIT](LICENSE) © 2026 Seacen Zhao

## Acknowledgements

- Built as an [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) — the open format for extending AI agents.
- Installable through the open [`skills` CLI](https://github.com/vercel-labs/skills) by Vercel Labs.
