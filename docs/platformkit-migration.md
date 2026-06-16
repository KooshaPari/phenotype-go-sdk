# PlatformKit migration

`KooshaPari/PlatformKit` (archived) is absorbed into this repo and [nanovms](https://github.com/KooshaPari/nanovms).

| PlatformKit path | Successor |
|------------------|-----------|
| `go/devhex/` | `packages/devhex/` (this repo) |
| `go/devenv/` | `nanovms/` sandbox adapters (evolved; SHAs diverged) |
| Docs / CHARTER | This `docs/` tree |

## Verification

- `packages/devhex/pkg/domain/registry.go` — byte-identical to PlatformKit source
- `packages/platformkit/` — consolidated platform tooling
- `packages/mcpkit/` — MCP Go bindings from org consolidation

PlatformKit repo remains archived until devenv parity is confirmed in nanovms.
