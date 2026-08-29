# Dotscope — Documentation

Dotscope is a structural code-analysis engine ("the physics engine for AI coding
agents"): a Rust compiler that maps explicit dependencies and temporal (Git-history)
coupling of a codebase and exposes that map to AI coding agents via MCP. It operates
entirely locally. See the root `README.md` for the full product overview.

## Directory map

| Path | Contents |
| ---- | -------- |
| `crates/` | Rust workspace crates (the structural compiler) |
| `dotscope/` | Python package / distribution layer |
| `tests/`, `titan_testing/` | Test suites |
| `assets/` | Static assets |
| `docs/` | This documentation tree |

## How to run

From the root `README.md` and `pyproject.toml` (name `dotscope`, version 1.7.1,
MIT, requires Python >= 3.10): install with `pip install dotscope` (zero-dependency
setup per README). The Python package depends on tree-sitter language grammars
(JS/TS/Go/Solidity/Java/Rust). MCP integration is documented in
[MCP setup](mcp-setup.md) and [MCP integration](mcp-integration.md).

## Document index

- [Architecture](architecture.md)
- [How it works](how-it-works.md)
- [Scope file format](scope-file.md)
- [MCP setup](mcp-setup.md) / [MCP integration](mcp-integration.md)
- [CLI reference](cli-reference.md)

Not documented in repo — needs owner input: a contributor/development setup guide
beyond the install one-liner.
