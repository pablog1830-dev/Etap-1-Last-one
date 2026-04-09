# CODEX Parameters — 2A v1.1

## Repository
- repo: `pablog1830-dev/Etap-1-Last-one`
- base branch: `e1-a1-freeze-baseline`
- working branch: `codex/2a-v1.1-implementation`
- default branch: `main`

## Start point
Always start from the **baseline branch**, not from the existing exploratory Codex branch and not from open PR #1.

Do **not** continue work from:
- `codex/verify-branch-and-file-existence`
- PR #1

Those changes belong to an exploratory Etap-1 refactor line, not to the 2A execution line.

## Files of truth
Primary mirrors to update together:
- `src/ITER_04A_SCALP_4A_MANIPULATION_PHASE_CORRECTION_FULL.pine`
- `src/audit/FULL_COPY__ITER_04A_SCALP_4A_MANIPULATION_PHASE_CORRECTION_FULL.pine`
- `src/tradingview/TV_LIVE__ITER_04A_SCALP_4A_MANIPULATION_PHASE_CORRECTION_FULL.pine`

Supporting spec file:
- `docs/specs/2A_v1.1_EXECUTION_SPEC.md`

This parameter file:
- `codex/CODEX_PARAMS_2A.md`

## Codex mission
Implement **2A v1.1** as a narrow execution layer for crypto scalping on top of the existing VSA/Fib core.

## Hard constraints
- Preserve logical integrity of existing:
  - `VSA CORE`
  - `FIB CONTEXT — LOCATION / TARGETS`
  - base signal logic
  - base geometry and zones
- Do not build full Prediction / ML / FVG / Regime / Survival architecture
- Decision must be computed exactly **once per closed 1m bar**
- No look-ahead
- No unstable intrabar transitions
- Keep mirror parity across the three Pine files

## Mandatory sections to implement
1. `2A CONSTANTS / ENUMS`
2. `2A INPUT SPLIT`
3. `DATA_INTEGRITY_MINI`
4. `QUALITY DECOMPOSITION`
5. `SETUP_QUALITY`
6. `BASIC_LIQUIDITY_STATE`
7. `ENTRY_MODE_RESOLVER`
8. `FINAL_DECISION_GATE`
9. `WAIT_RECLAIM_FLOW`
10. `POST_ENTRY_MINI_STATE`
11. `STATE / REASON`
12. `UI / LOG FIELDS`

## Commit policy
Use focused commits only.
Recommended sequence:
1. `2A: add constants enums and input split`
2. `2A: add data_integrity_mini`
3. `2A: add quality decomposition and setup_quality`
4. `2A: add basic_liquidity_state and entry_mode_resolver`
5. `2A: add final_decision_gate and wait_reclaim_flow`
6. `2A: add post_entry_mini_state`
7. `2A: add state reason enums and 2A logs`
8. `2A: sync audit and tradingview mirrors`

## Pull request policy
When ready, open a PR:
- head: `codex/2a-v1.1-implementation`
- base: `e1-a1-freeze-baseline`

PR title template:
- `Implement 2A v1.1 narrow execution layer on baseline`

PR body must include:
- scope
- what remained untouched
- modules added
- acceptance checks performed
- known gaps, if any

## Acceptance checklist for Codex
Before opening PR, verify:
- compile path preserved
- no undeclared identifier
- no look-ahead
- one final decision per closed `1m` bar
- `WAIT_RECLAIM` only with `basicLiquidityState = reclaim_needed`
- `aggressive` only with `penalties_total = 0`
- BTC / ETH profiles are separated
- spot / linear are separated
- logs include required 2A fields
- all three mirrors are synchronized

## Manual repo settings recommended outside Codex
These settings should be configured in GitHub UI:
- protect `e1-a1-freeze-baseline`
- require PR before merge
- require at least 1 review before merge
- require conversation resolution before merge
- require linear history
- optionally require code owner review

## Suggested Codex prompt header
Use this as the start of the Codex task:

```text
Work only in repository pablog1830-dev/Etap-1-Last-one.
Use base branch e1-a1-freeze-baseline and working branch codex/2a-v1.1-implementation.
Treat docs/specs/2A_v1.1_EXECUTION_SPEC.md and codex/CODEX_PARAMS_2A.md as binding instructions.
Update the three Pine mirrors together.
Do not continue or reuse the exploratory branch codex/verify-branch-and-file-existence as the implementation base.
Do not broaden scope into full Survival/Regime/FVG/Prediction/ML architecture.
Implement only the narrow 2A v1.1 executor.
```
