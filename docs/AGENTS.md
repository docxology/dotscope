# AGENTS.md — Dotscope docs/

## Layout

Hand-maintained topic files: `architecture.md`, `how-it-works.md`, `scope-file.md`,
`mcp-setup.md`, `mcp-integration.md`, `cli-reference.md`. `README.md` is the index.
`manuscript/MANUSCRIPT_STATUS.md` records the manuscript posture.

## Key modules

- `crates/` — Rust implementation of the structural compiler (source of truth for behavior).
- `dotscope/` — Python package exposing the engine (pyproject name `dotscope`, v1.7.1).

## Conventions observed

- Root `AGENT_INSTRUCTIONS.md` declares strict repository rules ("physics engine"
  management of the codebase); read it before proposing structural changes.
- Root `CLAUDE.md` and `.claude/` carry agent configuration; `epic.yaml` and
  `intent.yaml` carry project intent.
- Docs are plain Markdown with relative links; keep new links verified against
  existing filenames.

## Maintenance

No generated docs. When CLI or scope-file behavior changes in `crates/`, update
`cli-reference.md` and `scope-file.md` in the same change.
