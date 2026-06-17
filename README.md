# wisdom-first

> Bring humanity's best thinking to your AI — the right frameworks and books *first*, then the work.

**[中文版 README →](README.zh-CN.md)**

`wisdom-first` is an [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) for Claude Code and other AI agents. Before your assistant improvises an answer to a question that deserves real thought, it reaches for the best thinking humanity has already done on that *kind* of problem: it names two or three complementary frameworks, recommends the best books, distills them, and only then solves your problem **through** those lenses.

*A skill that upgrades how an AI thinks, not just what it knows.*

## Install

Using the open [`skills`](https://github.com/vercel-labs/skills) CLI — no install needed, just `npx`:

```bash
npx skills add seacen/wisdom-first

# target a specific agent
npx skills add seacen/wisdom-first -a claude-code

# inspect before installing
npx skills add seacen/wisdom-first --list
```

Then start a fresh agent session — it picks up `SKILL.md` automatically. The `skills` CLI auto-detects Claude Code, Cursor, Codex, OpenCode, and many more.

<details><summary>Manual install (clone & symlink)</summary>

```bash
git clone https://github.com/seacen/wisdom-first.git
ln -s "$PWD/wisdom-first" ~/.claude/skills/wisdom-first
```

</details>

## What it does

When you ask for advice, or take on a substantive task that rewards real thinking — strategy, a speech, high-stakes writing, a negotiation, a conflict, a hard decision, a design — `wisdom-first`:

1. **Surfaces two or three complementary frameworks + the best books** for *your specific need*;
2. **Distills** their essence and recommends them for deeper reading;
3. **Solves your problem by weaving those lenses together**, so the answer visibly comes from the wisdom, not from improvisation.

It triggers on its own for advisory / long-horizon work, or call it explicitly with `/wisdom-first`.

## What makes it interesting

The skill contains **no lookup table of "topic → book."** Hard-coding titles would make it brittle and impossible to generalize. Instead, its core ([`references/the-taste.md`](references/the-taste.md)) is **pure, general *taste*** — a handful of domain-blind judgments about what makes one body of thought better than another for a given need:

- diagnose the **live need** (and notice when the real block is nerve and state, not content);
- match the **scope** of the wisdom to the scope of the problem;
- prefer the work that **defines its field**, gives a **method you can practice**, comes **from the source**, and installs a **durable model**;
- offer two or three complementary works and **weave** them, rather than name-drop one.

From those judgments alone, the right canonical works fall out of the model's own knowledge — across domains the skill was never told about.

### The author's shelf (optional taste layer)

A few excellent books sit too quietly in a model's "prior" to be reached by even perfect general taste. [`references/authors-shelf.md`](references/authors-shelf.md) lets the author hand-seed a few personal favorites as a **tie-break only** — never overriding fit, never adding a domain. It's a way to pass a point of view about what's good along to whoever installs the skill. Fork it and make it your own shelf.

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
SKILL.md                      # trigger + the 3-step sequence + output shape
references/
├── the-taste.md              # the core: 8 pure, domain-blind selection judgments
├── authors-shelf.md          # optional personal-taste tie-break layer
└── applying-via-workflow.md  # escalating the "solve" step to a multi-agent Workflow
evals/
└── evals.json                # acceptance scenarios
```

## License

[MIT](LICENSE) © 2026 Seacen Zhao

## Acknowledgements

- Authored as an [Anthropic Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills).
- Installable through the open [`skills` CLI](https://github.com/vercel-labs/skills) by Vercel Labs.
