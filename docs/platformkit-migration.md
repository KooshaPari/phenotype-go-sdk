# PlatformKit migration record

**Source:** [KooshaPari/PlatformKit](https://github.com/KooshaPari/PlatformKit) (KEEP ARCHIVED)  
**Migration branch:** `archive/platformkit-migration` (2026-06-16)  
**Registry status:** `absorbed-pending-delete` (pending devenv consumer cutover in nanovms)

## Absorption map

| PlatformKit path | Target | Coverage |
|------------------|--------|----------|
| Root docs (`README`, `PRD`, `ADR`, `docs/adr/*`, `docs/research/*`, worklogs) | `packages/platformkit/` | **100%** (24/24 root files match) |
| `go/devhex/` (7 Go source files) | `packages/devhex/` | **100%** (SHA256-identical `registry.go` and siblings) |
| `go/devenv/` (31 files) | [nanovms/packages/devenv](https://github.com/KooshaPari/nanovms/tree/main/packages/devenv) | **100%** (copied on `archive/platformkit-devenv-migration`) |
| `tests/test_smoke.py` | `packages/platformkit/tests/` | **100%** |

## Merge considerations (do NOT delete PlatformKit yet)

1. **Module paths:** Consumers referencing `github.com/KooshaPari/PlatformKit/go/devhex` must repoint to
   `phenotype-go-sdk/packages/devhex` (or published module path once tagged).
2. **devenv CLI:** Lives in nanovms now; nanovms `go.work` / CI must wire `packages/devenv` before archive deletion.
3. **DevHex dependents:** Per `phenotype-registry/RATIONALIZATION_EXECUTION.md`, DevHex module path repoint is 🔶 pending.
4. **Duplicate husks:** PlatformKit root and `packages/platformkit` in this repo are intentionally parallel until
   the source repo is retired with redirect README.

## PlatformKit-only notes preserved here

- ADR-001 through ADR-005 under `packages/platformkit/docs/adr/` document architecture, storage, API, security decisions.
- SOTA research under `packages/platformkit/docs/research/` captures implementation patterns from PlatformKit era.
- `go/devenv/SPEC.md` defines sandbox adapter ports (linux/mac/windows/wasm) — canonical copy now in nanovms.

## Deprecation (when 100% boundary covered)

When all dependents repoint and nanovms CI validates devenv:

1. Add archive banner to PlatformKit README pointing here + nanovms devenv.
2. Set PlatformKit registry status to `retired`.
3. Delete repo only after `gh repo view` shows zero open dependents.
