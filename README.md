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
     A friendly, abstract character eating a forkful of broccoli. Facial
     expression = mild, dignified suffering — "I know, I know, it's good for
     me." Clean flat-design vector, warm palette, a little funny. ~1024px. -->

## What's in it

- **Two dials:** depth (`quick` / `standard` / `deep`) × scope (`changed` / `module` / `repo`).
- **Deterministic tooling**, tool-agnostic — wire in your stack's linter / typechecker / scanner (Python & Rust reference stacks included). The pattern hunt needs no tooling at all.
- **The pattern hunt** — ~20 structural failure classes across 4 families
  (state & timing · failure visibility · boundaries & contracts · environment &
  control flow), each with a *"is this by design?"* disambiguator so you catch
  real issues without crying wolf on intentional ones.
- **A `.broccoli-accept` file** — record confirmed by-design findings so the next sweep skips them.

## Install

Drop `SKILL.md` into your Claude Code skills directory:

```
~/.claude/plugins/local/<your-plugin>/skills/eat-the-broccoli/SKILL.md
```

Then say `/eat-the-broccoli` (or "eat the broccoli").

## Contributing

The pattern catalog is meant to **grow across languages and harnesses**. Hit a
failure class that isn't in the table? Open a PR with a row —
`Name | ✅ by design if … | ❌ broken if …`. Real war stories make the best rows.

## Integrations

Works with any tools plus a plain `.broccoli-accept` file — no dependency. For
reference setups that bundle the tooling and make the by-design verdicts
*compound across a team*, see [INTEGRATIONS.md](INTEGRATIONS.md).

## License

MIT — it's a public good. Eat your vegetables. 🥦
