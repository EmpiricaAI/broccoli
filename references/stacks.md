# Reference stacks

Concrete tool choices for the Phase 1 dimensions. **You do not need this file to
run a sweep** — Phase 1 lists the dimensions, and the pattern hunt needs no tooling
at all. Come here when you're wiring a stack for the first time.

Two worked stacks. Others port by dimension, not by tool name.

## Python

| Dimension | Tool | Install / run |
|---|---|---|
| Lint + silent-failure | ruff | `pip install ruff` → `ruff check` (silent: `--select S110,S112,BLE001`) |
| Types | pyright | `pip install pyright` → `pyright` |
| Tests | pytest | `pip install pytest` → `pytest -q` |
| Dep CVEs | pip-audit | `pip install pip-audit` → `pip-audit` |
| Dead code | vulture | `pip install vulture` → `vulture src/ --min-confidence 80` |
| Complexity | radon | `pip install radon` → `radon cc src/ --min C` |
| SAST | semgrep | `pip install semgrep` → `semgrep --config auto` |
| Secrets | trufflehog | `trufflehog git file://.` |
| Test freshness | mutmut | `pip install mutmut` → `mutmut run` |

## Rust

| Dimension | Tool | Install / run |
|---|---|---|
| Lint | clippy | `rustup component add clippy` → `cargo clippy -- -D warnings` |
| Format | rustfmt | `cargo fmt --check` |
| Types / build | rustc | `cargo check` |
| Tests | cargo test / nextest | `cargo test` (or `cargo install cargo-nextest` → `cargo nextest run`) |
| Dep CVEs + licenses | cargo-audit, cargo-deny | `cargo install cargo-audit cargo-deny` → `cargo audit`, `cargo deny check` |
| Unused deps / dead code | cargo-machete, rustc `dead_code` | `cargo install cargo-machete` → `cargo machete` (`dead_code` is on by default) |
| Silent failures | clippy | `-W clippy::unwrap_used -W clippy::let_underscore_must_use` + hunt discarded Results: `let _ = fallible()`, `.ok()`, `.unwrap_or_default()` |
| Unsafe audit | cargo-geiger | `cargo install cargo-geiger` → `cargo geiger` |
| Test freshness | cargo-mutants | `cargo install cargo-mutants` → `cargo mutants` |

## Adding a stack

PR one table with the same dimension column, so a reader can diff their stack
against a known one. Leave a dimension out rather than inventing a tool for it —
**an empty cell is information; a plausible-but-unused tool is not.**
