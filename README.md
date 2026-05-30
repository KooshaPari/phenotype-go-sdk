# phenotype-go-sdk

Phenotype-org Go SDK — consolidates Go Kit/SDK packages from the KooshaPari org.

## Packages

| Path | Source | Description |
|------|--------|-------------|
| \packages/platformkit\ | [PlatformKit](https://github.com/KooshaPari/PlatformKit) | Go devenv and devhex tooling |
| \packages/devhex\ | [DevHex](https://github.com/KooshaPari/DevHex) | Hexagonal Go library for dev environment abstractions |
| \packages/mcpkit\ | [McpKit](https://github.com/KooshaPari/McpKit) | MCP framework SDK (Go workspace) |

Use `go work sync` from the repo root to build across packages.

## Workspace notes

- `go.work` includes `packages/devhex` and `packages/platformkit/go/devenv`.
- `packages/platformkit/go/devhex` duplicates `packages/devhex` (same module path) and is excluded from the workspace.
- `packages/mcpkit/go/go.work` references missing `pheno-mcp-*` modules — Go MCP packages deferred until restored.
