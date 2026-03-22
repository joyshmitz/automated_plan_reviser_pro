# Changelog

All notable changes to Automated Plan Reviser Pro (apr) are documented here.

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) adapted for agent consumption.
Versioning: [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
Repository: <https://github.com/Dicklesworthstone/automated_plan_reviser_pro>

---

## [Unreleased]

Changes on `main` after the v1.2.2 tag. No GitHub Release yet.

### Added

- TOON output format for robot mode (`apr robot run --format toon`) encoding via `toon_rust`/`tru` ([28c9e9c](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/28c9e9ce016c237fd3aa7d86ee4ff0baad2c901c))
- `--stats` flag on robot output to show JSON vs TOON byte savings ([3c4d4da](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/3c4d4daadd4ec41bb2bcc0199593c3c0bf785454))
- ACFS lesson registry sync via `notify-acfs` GitHub Actions workflow ([d96394c](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/d96394c6d9812287405613d77692299454b3a0c1))
- TOON integration research documentation ([342a758](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/342a758df2ff40d27f9df4f68501d86fd351ceb7))
- GitHub social preview image ([1037198](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/1037198e11655c699c21fd354ff18571da390034))

### Changed

- License updated to MIT with OpenAI/Anthropic Rider ([d967c42](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/d967c428c8e7a525ae8f7ca2840cf0af62290f6f), [7a2b218](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/7a2b218f8ff4a6910f57ceac8e332ff7eb7e2e0a))

### Fixed

- Robot error handling test uses `capture_streams` for correct stream separation ([a1d1e6d](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/a1d1e6d0c2958c995a05b03fbdbe8f6fe9568fb5))
- Preserved `REAL_HOME` and `TOON_SH_PATH` in isolated test environments ([c6b57ba](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c6b57ba6c4016b44ac7d7b521da666b76e7215f2))
- CI: remove blank lines in `test_continuation.sh` backslash continuations ([df02f1f](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/df02f1fc03f2e7f4d6114c71f9fc14a3a9052755))
- CI: resolve ShellCheck warnings in CI and pre-commit hook ([c3dbb66](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c3dbb66c91f965f37c7e323b864c6a8d11f28e1b))
- CI: skip checksum job on main pushes to avoid race condition ([c59beef](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c59beeff69c7ba0ac1f9c7cf10be6226125d1d5e))
- Aligned robot error codes and ignored runtime artifacts in tests ([be1586d](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/be1586d68e906651f3f81fab6ce4ebea0afa3b4f))

---

## [v1.2.2] - 2026-01-15

**Tag**: [`v1.2.2`](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/17d4fe4f717093f75242f431f9705e391dc66a45) -- **GitHub Release**: [APR v1.2.2](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/releases/tag/v1.2.2)

Patch release fixing ShellCheck SC2181 warnings and the file picker TUI.

### Fixed

- Resolve ShellCheck SC2181 warnings across the codebase ([17d4fe4](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/17d4fe4f717093f75242f431f9705e391dc66a45))

---

## [v1.2.1] - 2026-01-15

**Tag**: [`v1.2.1`](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/39428f9d91ef1c84cee56b9028f95bad64d7ad26) -- Tag only (no GitHub Release published).

File picker improvements and Oracle Extended Thinking enhancements.

### Added

- `thinking_time` config support for Oracle Extended Thinking ([86c3153](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/86c3153e97df49e2513d9968ccdb8c3e3225a0b2))
- Oracle stability threshold patching for GPT Pro Extended Thinking ([1450b44](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/1450b44d822150847b2d2c6ac33875db18887867))
- `impl_every_n` config: automatic periodic implementation inclusion every N rounds ([8937eac](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/8937eacab0b0f30d62c00422f68fb09b5315bb88))
- Oracle remote setup documentation for headless/SSH environments ([2ddb3b7](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/2ddb3b7303d4be2845aa2760b5989eacd3e10fa0))
- Oracle stability patching documentation ([291f49f](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/291f49f7f949a0e9132b81667b7cec78e3b39194))

### Changed

- CI: automatic checksum sync workflow to prevent installer SHA256 failures ([69d2baf](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/69d2baf2c69c5c7bb20ba988d32ddd698afb6c41), [41cbcd3](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/41cbcd322d98fef3d7f0257af1b982e0a718d56c))

### Fixed

- TUI file picker now shows folder structure instead of flat list ([c94968b](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c94968b7c346683a0c0c4273c3cf244039102b6f))
- Oracle patching validation and edge case handling ([1284790](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/128479020b8359fd5839d761c49dcc66cb65aa78))
- Use inline pasting instead of file uploads for GPT Pro compatibility ([dee5912](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/dee5912f3852a28d9af8dcb8da9d53851207490e))
- `--notify` flag conditional on Oracle version support ([e47d067](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/e47d067514ad32253b9ef94251b656df6494206c))
- Oracle `--notify` detection across all modes ([7ac0272](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/7ac02724523119390507e8e6ecfc957c661c8396))
- Dashboard cleanup and ESC key handling ([2090b53](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/2090b5393d1074598be0dba01041e8cb0db979ba))
- Locking and background concurrency race conditions ([65619a2](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/65619a2a22fa85fffe77a66d1b64074f2de826e6))
- Update path resolution and input validation ([49249e8](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/49249e8ca6b5fdc04728280212f2bf3ca7927133))
- Installer checksum (`apr.sha256`) sync to match current script ([fb23f92](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/fb23f92d869b775485df9931e0435bee58aff0d1))

### Testing

- Regression tests for diff ordering and lock file bugs ([98dd7d2](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/98dd7d26aee4ea6b415ec33864017c0c8d7862c8))
- Unit tests for dashboard helper functions ([af992b0](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/af992b0a3fca646e201dd7b4ba7ab04d3a53c3b3))
- Unit tests for formatting helper functions ([2405690](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/24056909f4edc075ca8e5430efa7bcaa9b00a8c7))
- Dedicated JSON output tests for `apr stats` ([ccbf567](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/ccbf5675055eda0debfc86c4b7b891c63e5ff065))
- Mock Oracle `--render` support and `setup_test_metrics` helper ([a77661c](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/a77661c697b608b27eacca21cd6f9e76b7e9af3d))
- Expanded integration test coverage for analytics features ([4ddddda](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/4dddddaeb6ca8d930bc69a2946d66913fa688cc0))
- Route all mock Oracle output to stderr for clean stdout in tests ([cb7cc47](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/cb7cc47551a2d85c581834d01a5f39a20ba2640d))

---

## [v1.2.0] - 2026-01-12

**Tag**: [`v1.2.0`](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/88f496d1f7407055edca01c98bfd0716fdbb3077) -- **GitHub Release**: [APR v1.2.0](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/releases/tag/v1.2.0)

Major feature release adding convergence analytics, interactive dashboard, backfill, robot subcommands, and a comprehensive BATS test suite. This release encompasses all development from the initial commit through the v1.2.0 tag.

### Core Architecture (Initial Release)

The foundation shipped in the initial commit ([c8bda80](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c8bda805e52246e2ea4df16d4fa30da8762c76ca)) and was rapidly hardened in the same day:

- Pure-Bash CLI for iterative specification refinement via GPT Pro Extended Reasoning
- YAML-based workflow configuration (`apr setup` wizard)
- Document bundling: automatic combination of README, spec, and implementation files
- Round management with `.apr/rounds/` history and tmux session handling
- Background execution with desktop notifications
- `apr run`, `apr status`, `apr attach`, `apr setup` commands
- Gum-powered TUI with graceful ANSI fallback
- Curl-pipe-bash installer with SHA256 verification

### Added

#### Robot Mode (Agent Automation API)
- `apr robot run <N>` -- JSON API for coding agents to drive revision rounds ([e1471a4](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/e1471a4b3490d9b8ec9fe8750d4fd62d20c117e0))
- `apr robot status`, `apr robot show`, `apr robot diff`, `apr robot history` subcommands ([ed35eab](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/ed35eab3110207401846e1c6e05c841778e369dc))
- Structured JSON output with semantic exit codes for all robot commands ([a0828ea](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/a0828eac1987eb4dd1986df0b1dc5f8a0dbbfe3b))

#### Convergence Analytics
- `apr stats` -- convergence detection with weighted signal analysis: output size trend (35%), change velocity (35%), similarity trend (30%) ([e72a194](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/e72a194e49c8a4c297f268bdcbac3ddbf0804f36))
- Inter-round change analysis functions measuring character, word, line, and heading deltas ([7b35a69](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/7b35a696148748d3bbc4f9cad18a4ee644d17c4b))
- Document metrics collection integrated into the `run_round` flow ([887b59e](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/887b59e4ba77cce1256ee8f27ee188c2c2374ff7), [b0ba3a9](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/b0ba3a9c6028e0945037b1043eaccef101286e91))
- Complete metrics storage layer with XDG-compliant paths ([abe1dee](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/abe1dee2650cbb316ec998ba18783dbd409380e3))
- Remaining-rounds estimation based on convergence trajectory (score >= 0.75 indicates stability)

#### Interactive Dashboard
- `apr dashboard` -- gum-powered interactive round browser with view/diff/navigate ([22850f0](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/22850f03175d79e8fdb777f75f60109d7feaf50e))
- Help key alias and terminal size check for dashboard UX ([b88fe30](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/b88fe30f7a120d277784f44481fc0950f32923de))
- Function docstrings, null handling, and arithmetic fixes in dashboard ([212e065](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/212e06551549d7899053c7ae7ca935dc449f299b))

#### Backfill Command
- `apr backfill` -- generate metrics from existing rounds retroactively, with `--force` to regenerate ([1fba93b](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/1fba93b82c55370200e28236d7bd3d93d68c7f91), [31ad561](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/31ad56116871dd5786990d1ccc1b618ceac87f3d))
- Integrated into main command dispatch and help text ([3cdc4ea](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/3cdc4ea0acace5c88b93577550b36c8b95c69a3e), [27e882e](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/27e882e02b00834b9b91ef6760f9d7575c50b8a2))

#### Analysis Commands
- `apr show <N>` -- view round output with pager support ([f3f3e62](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/f3f3e62ea88ed0c17a715231adce021bdf4a721d))
- `apr diff <N> [M]` -- compare rounds using delta/diff ([da8f545](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/da8f545370f61983ef68c1ce8b62a2d4774b9082))
- `apr integrate <N>` -- generate Claude Code integration prompt (clipboard-ready) ([da8f545](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/da8f545370f61983ef68c1ce8b62a2d4774b9082))

#### Operational
- Self-update command (`apr update`) ([2c4a411](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/2c4a411cb46e59726d77be1aeace36c4de9c52c7))
- `NO_COLOR` environment variable support ([2c4a411](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/2c4a411cb46e59726d77be1aeace36c4de9c52c7))
- GitHub Actions CI workflows ([2c4a411](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/2c4a411cb46e59726d77be1aeace36c4de9c52c7))
- Verbose mode (`--verbose`/`-v`) for debugging ([da8f545](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/da8f545370f61983ef68c1ce8b62a2d4774b9082))
- Pre-flight validation of Oracle, workflow config, and document files ([da8f545](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/da8f545370f61983ef68c1ce8b62a2d4774b9082))
- Auto-retry with exponential backoff (10s, 30s, 90s) via `APR_MAX_RETRIES` and `APR_INITIAL_BACKOFF` ([da8f545](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/da8f545370f61983ef68c1ce8b62a2d4774b9082))
- File-based session locking with 2-hour stale timeout and atomic fallback acquisition ([66a45d3](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/66a45d3cf6aeecff8183ffb6624e113151cc7d51))
- Automatic Node.js installation for Oracle dependency ([632e87b](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/632e87bd0d53cdc975e9d71d406a8231bb925d5b))

### Fixed

- Stream separation enforced per AGENTS.md (stdout for data, stderr for diagnostics) ([e180626](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/e1806266f78e0d09e73434ce7b69b338ca03c672))
- YAML parsing robustness with proper unquoting and comment handling ([38cf2b4](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/38cf2b439aabc5186d67718a5f0117fba69b27bd))
- Oracle detection and validation robustness ([408c0b9](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/408c0b926460dc45960cc88dca08ea920c108256))
- Robot history rounds sorted numerically, round number validation ([a528229](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/a528229eaf8ddeae61c5c04d85c0315e19201976))
- ORACLE_CMD array conversion to prevent word-splitting issues ([a22e741](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/a22e7414ffc123fc1b3db1b8a96c92ecce39287e), [775c3e2](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/775c3e2cdcffe76fc9d654d6180efade6560c275), [c6e2b4b](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/c6e2b4be9bdb205e2ba9afcfef9aa0a5bbacc418))
- Duplicate validation checks removed, CI/CD improved ([4dc1834](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/4dc18346ba00f73de478f34cd279d41b891c1184))
- Nine bugs found and fixed during code review ([fc720d1](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/fc720d16d5dc1bc166f0ff2f36047a6faa5ac119), [afb9bf6](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/afb9bf60cb69248fbd81bbfcb46706c4429b62a7), [b849541](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/b849541fa8c6dd97ac8ac3cbe5693e188c0763f0), [626ae4d](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/626ae4dc9772e8d0409ebb074b96741ea4693e5c))
- CI failures resolved for v1.2.0 release ([788e5de](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/788e5de3b5d9c701e2853034788128f08ffa44e2))

### Testing

- Comprehensive BATS-based test framework with 180+ tests ([dbd14d8](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/dbd14d8540abc658a8ad3e2e63bdc1cbaa3495f5))
- Test suites for setup wizard, analytics, preflight, and robot mode ([fafb5b6](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/fafb5b69eababa3325b4c49b1e0580511002528b))
- E2E tests and enhanced `apr stats` coverage ([fbd8cb1](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/fbd8cb1d8004d14ad34dd4a502df80007c7392c3))
- Comprehensive analytics test suite ([e6c5cb4](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/e6c5cb49e7b192ebea591eb396bbd452c44fe9af))
- Preflight and validation test coverage ([ec30667](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commit/ec306673fa85c95f3d97b5689fe2a83c4290dcc3))
- Semantic exit code verification and stream separation validation

---

## Compare Links

- [Unreleased](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/compare/v1.2.2...main)
- [v1.2.2](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/compare/v1.2.1...v1.2.2)
- [v1.2.1](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/compare/v1.2.0...v1.2.1)
- [v1.2.0](https://github.com/Dicklesworthstone/automated_plan_reviser_pro/commits/v1.2.0)
