---
name: vault-health
description: Use when preparing for a session, after a large batch of wiki or code edits, or when diagnosing unexplained build or content errors. Skip for single-file changes.
---

# Vault Health

Run from the project root. **Stop at the first failure — report what to fix before continuing.**

## Checks (in order)

Adapt these to your project's toolchain:

| # | Command | Pass condition |
|---|---------|----------------|
| 1 | `<your-type-check-command>` (e.g. `pnpm check`, `tsc --noEmit`) | No type errors or linter violations |
| 2 | `<your-wiki-lint-command>` (e.g. `sea lint`) | Zero errors (warnings non-blocking) |
| 3 | `<your-taxonomy-sync-check>` (e.g. `python3 .claude/scripts/check_taxonomy_sync.py --check`) | Exits 0 |
| 4 | `<your-health-summary-command>` (e.g. `sea health`) | Print summary metrics only |

## Output

One status table:

| Check | Status | Notes |
|-------|--------|-------|
| Type check | ✓/✗ | error detail if failed |
| Wiki lint | ✓/✗ | counts if non-zero |
| Taxonomy | ✓/✗ | drifted tags if any |
| Vault snapshot | info | files, default-summaries, unresolved links |

All clean → one-line summary. Any failure → list what to fix before proceeding.
