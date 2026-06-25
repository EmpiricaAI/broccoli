# Eat the Broccoli 🥦

> The quality sweep you know you should run and skip anyway.

A tiered, language-agnostic quality-and-pattern audit for any codebase. It pairs
the deterministic tooling you already have (lint, types, tests, dependency CVEs,
dead-code, silent-failure scanners) with a **learned-pattern hunt** — a
checklist of the *hard* failure classes that pass every test and still ship
broken: races, stale caches, silent fallbacks, null-masking, deploy-staleness.

It's a [Claude Code](https://claude.com/claude-code) skill, but the checklist is
useful to anyone.

![Claude eating broccoli with the expression of someone who knows it's good for them](assets/claude-broccoli.png)

<!-- ART DIRECTION for assets/claude-broccoli.png:
     Claude (friendly, abstract) eating a forkful of broccoli. Facial
     expression = mild, dignified suffering — "I know, I know, it's good for
     me." Clean, warm, a little funny. PNG, ~800px wide. -->

## What's in it

- **Two dials:** depth (`quick` / `standard` / `deep`) × scope (`changed` / `module` / `repo`).
- **Deterministic tooling**, tool-agnostic — wire in your stack's linter / typechecker / scanner.
- **The pattern hunt** — ~20 structural failure classes across 4 families
  (state & timing · failure visibility · boundaries & contracts · environment &
  control flow), each with a *"is this by design?"* disambiguator so you catch
  real issues without crying wolf on intentional ones.

## Install

Drop `SKILL.md` into your Claude Code skills directory:

```
~/.claude/plugins/local/<your-plugin>/skills/eat-the-broccoli/SKILL.md
```

Then say `/eat-the-broccoli` (or "eat the broccoli").

## Without the deterministic services

The skill names the *dimensions* (lint, types, deps, dead-code, silent-failure,
contract guards); you supply your stack's tools. The pattern hunt needs no
tooling at all — it's a structured way of looking.

## With Empirica (optional)

If you run [Empirica](https://github.com/EmpiricaAI/empirica), the
`[empirica]`-marked lines bundle the tooling into single commands **and** record
which findings are "by design" (`decision-log`) so the next sweep doesn't
re-litigate them — the judgments compound instead of evaporating. Without it,
record by-design verdicts yourself (an inline annotation or a `.broccoli-accept`
allow-list).

## License

MIT — it's a public good. Eat your vegetables.
