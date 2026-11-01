# AGENTS.md — dotscope

Guidance for agents working in this repository.

## What this repository is

A static-analysis tool that maps Python code structure — modules, classes, functions, imports
and their dependencies — and exposes that map to editors and agents. Python 3.10 or newer on
the outside; the analysis engine itself is a Rust crate compiled into a native extension
through PyO3, so the parser and the traversal are Rust and only the surface is Python.

Version `1.7.1`. Published to PyPI.

## Layout

| Path | Role |
|---|---|
| `crates/` | The Rust workspace — `dotscope-core`, the actual analysis engine |
| `dotscope/` | The Python package: CLI, MCP server, and the PyO3 bindings |
| `src/` | Supporting Python sources |
| `tests/` | Pytest suite |
| `titan_testing/` | Larger integration/parity harness |
| `docs/` | Documentation, with its own `docs/AGENTS.md` |
| `virtual/` | Virtual environment material; not source |

## Commands

```bash
uv sync                                    # Python side
uv run maturin develop --release           # rebuild the Rust extension after touching crates/
uv run pytest                              # tests
uv run ruff check .                        # lint, configured in pyproject.toml
dotscope                                   # CLI entry, dotscope.cli:main
dotscope-mcp                               # MCP server entry, dotscope.mcp:main
```

Both console scripts are declared under `[project.scripts]` in `pyproject.toml`.

## Working here

- **A Rust change is invisible until the extension is rebuilt.** Editing `crates/` and running
  `pytest` without `maturin develop` tests the old binary. If a Rust edit appears to have had no
  effect, that is why.
- Keep Python and Rust behaviour in step; `titan_testing/` exists to catch parity drift.
- CI runs `python-publish.yml` only — it publishes, it does not gate on the test suite. A green
  workflow here does not mean the tests passed.
- Lint and pytest settings both live in `pyproject.toml`; read them rather than assuming
  defaults.

## Repository hygiene

This repository carries `CLAUDE.md`, `AGENT_INSTRUCTIONS.md` and a `.claude/` directory. Those
are vendor-specific agent configuration and conflict with the account's tooling-neutrality
rule, which expects guidance in `AGENTS.md` and `.agents/`. They are slated for migration into
`.agents/` and removal; **do not add more vendor-specific files, and do not extend those.** New
guidance belongs here.

`docs/AGENTS.md` documents the `docs/` folder only. This file is the repository-level entry
point; the two should not restate each other.
