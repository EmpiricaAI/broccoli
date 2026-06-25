# Integrations

`/eat-the-broccoli` names the *dimensions* (lint, types, deps, dead-code,
silent-failure, contract guards) and the *pattern hunt* — both work with
whatever tools you already have, and by-design verdicts can be recorded in a
plain [`.broccoli-accept`](SKILL.md) file. **No dependency required.**

These are reference implementations that wire the whole thing up for you. You
don't need them to use the skill — they're the "easy mode."

## Empirica (Python)

[Empirica](https://github.com/EmpiricaAI/empirica) bundles the deterministic
half into two commands, and records by-design verdicts so they *compound across
runs and across a team* instead of living in a flat file you maintain by hand:

- `empirica compliance-report` — lint + types + tests + complexity, mapped to a
  regulatory crosswalk (EU AI Act / GDPR / ISO 42001).
- `empirica security-audit` — dependency CVEs cross-referenced against the CISA
  KEV catalog for rotate-priority.
- by-design verdicts stored as decisions in its knowledge graph — a confirmed
  "intentional" never gets re-litigated, and the pattern catalog compounds.

Install: `pip install empirica`.

## Codex / Rust (ecodex)

A Codex-based Rust harness (ecodex) wires the same dimensions natively — clippy,
`cargo fmt --check`, `cargo check`, `cargo test`/`nextest`, `cargo audit` +
`cargo deny`, `cargo machete`, `cargo geiger`, and the discarded-`Result` hunt
(`-W clippy::unwrap_used`, `-W clippy::let_underscore_must_use`). The pattern
hunt ports verbatim — and it contributed the "decision downgraded across a
boundary" family back, from its own firewall work.

## Wiring your own

Any tracker works. The only thing that matters is the loop:

> **find → check intent → record the verdict *with its reason*.**

A `.broccoli-accept` file is the zero-dependency version. A knowledge graph (like
Empirica's) is the version that compounds across a team and never forgets. Pick
whichever fits — the skill doesn't care.
