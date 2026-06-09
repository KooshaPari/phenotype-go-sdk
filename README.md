## Work State

| Field | Value |
|---|---|
| Last commit | 2026-06-02 |
| Open issues | 0 |
| Open PRs | 0 |
| Focus | Go SDK scaffold (ADR-011) |

Progress: ████░░░░░░ 40%

# phenotype-go-sdk

Phenotype-org Go SDK — consolidates Go Kit/SDK packages from the KooshaPari org.

## Packages

| Path | Source | Description |
|------|--------|-------------|
| \packages/devhex\ | [DevHex](https://github.com/KooshaPari/DevHex) | Hexagonal Go library for dev environment abstractions (module `github.com/KooshaPari/devenv-abstraction`). The single canonical Go module in the workspace. |
| \packages/platformkit\ | [PlatformKit](https://github.com/KooshaPari/PlatformKit) | Docs/specs only. Its Go code (`go/devenv`, `go/devhex`) was a broken duplicate of `devhex` and was removed (see Workspace notes). |
| \packages/mcpkit\ | [McpKit](https://github.com/KooshaPari/McpKit) | MCP framework SDK (Go workspace) — deferred (see notes). |

Use `go work sync` from the repo root to build across packages.

## Workspace notes

- `go.work` includes only `packages/devhex` — it builds and tests clean and is
  the single source of the devenv/devhex modules.
- The two duplicate copies under `packages/platformkit/go/` were **removed**
  (2026-06-02, ADR-011 Go convergence): `platformkit/go/devhex` was a
  byte-divergent dup of `packages/devhex` claiming the same module path, and
  `platformkit/go/devenv` was an older lowercase-path copy that did not compile.
- `packages/mcpkit/go/go.work` references missing `pheno-mcp-*` modules — Go MCP
  packages deferred until restored.