# @momentic/wizard

## 0.6.1

### Patch Changes

- 0d18573: Improve onboarding reliability: the sample test run and coding-agent setup now resolve their commands more robustly across package managers and platforms, and surface clearer, more actionable error messages when a tool is missing or a step fails.

## 0.6.0

### Minor Changes

- 320bda0: The v4 locator, assertion, and visual-assertion agents are now the recommended default. New projects use them automatically, and existing projects that don't pin those agents in `ai.agentConfig` will pick them up as well. v4 is faster and more reliable than v3.

## 0.5.2

### Patch Changes

- 5cd9248: Skip the sample test run during onboarding when the browser isn't installed, and continue setup instead of stopping
- 74aa15c: Show a clear, actionable message instead of an unexpected crash when sign-in credentials can't be saved due to file permissions

## 0.5.1

### Patch Changes

- cc1d1a1: Show clear messages for missing, moved, or conflicting module files instead of unexpected errors.

## 0.5.0

### Minor Changes

- 3e4e0ee: When run in a directory that already has a Momentic project, the wizard no longer scaffolds tests or changes your config. It now offers to install the Momentic skills, MCP server, and browsers, and prompts you to upgrade when your project is on an older format or your installed Momentic version is behind the latest release.

## 0.4.1

### Patch Changes

- f94d62a: Fixed the onboarding wizard defaulting to npm inside pnpm/yarn monorepos. It now detects the project's package manager even when run from a nested package, and retries npm installs with --legacy-peer-deps when a pre-existing peer-dependency conflict would otherwise block installing the CLI.

## 0.4.0

### Minor Changes

- c3b63ac: The setup wizard now configures editor validation for your project: it detects your installed editors and adds Momentic's JSON Schema associations to the matching settings file (.vscode/settings.json for VS Code, Cursor, and Windsurf, or .zed/settings.json for Zed), so test and module YAML files get autocomplete and inline validation as you write.

### Patch Changes

- ab2f970: Use a cleaner npx command when running CLI commands in npm-based projects
- f7bd477: Fix the setup wizard reporting that Momentic skills were installed when they weren't, so the skills are now reliably installed and available to your coding agents right after setup.

## 0.3.0

### Minor Changes

- e21de6f: The wizard now runs non-interactively in CI and from coding agents (Claude Code, Cursor) instead of hanging on prompts. Without a TTY, or with `-y`/`--yes`, it authenticates from `MOMENTIC_API_KEY`/`--api-key` (falling back to saved credentials) rather than opening a browser sign-in, defaults the platform to web (override with `--platform`), names the project after the directory, and wires Momentic into your coding agents (configurable via `--editor-tools all|none|<list>`). With no credentials it exits with a clear, actionable message instead of stalling.

### Patch Changes

- 5e347e7: Show clearer next steps when run in an already-configured project, display the full sample test output, and run the sample web test in headless mode.

## 0.2.2

### Patch Changes

- 8dbce07: Speed up the first run of the sample test scaffolded during onboarding so it reuses cached element targeting instead of resolving every step with AI

## 0.2.1

### Patch Changes

- e6ca1a7: Reframe the wizard's welcome and sign-in copy when no Momentic credentials exist on the machine yet. First-time runners now see "Create your Momentic account (or sign in if you have one)" instead of language that assumes they already have an account.
- 947ec9b: Internal improvements to the wizard startup flow.

## 0.2.0

### Minor Changes

- 9080050: Scaffold new projects in the simplified v2 file format. `momentic init`, `momentic-mobile init`, and `@momentic/wizard` now create configs with `fileFormat: v2` and emit v2 sample tests. When the wizard finds an existing `momentic.config.yaml`, it stops and points you at `momentic upgrade` / `momentic-mobile upgrade` so the existing project can be brought to the latest format on its own.

## 0.1.13

### Patch Changes

- c9d2aea: Fix wizard crash when installing the Momentic CLI on Windows.

## 0.1.12

### Patch Changes

- 1b6ccf9: Identify authenticated CLI users to product analytics for better support and self-serve activation diagnostics.

## 0.1.11

### Patch Changes

- da10cb2: Fix wizard install errors when run via npx with non-npm package managers.
- 4f2eb35: Improve schema validation performance and error messages

## 0.1.10

### Patch Changes

- c1e6c6f: `momentic-mobile run` now prints the list of scheduled tests before the run starts. Wizard falls back to plain-text logging when stdout is not a TTY.
- 9fce4f9: Capture wizard setup failures with Sentry, a persistent log file at `~/.momentic/logs/`, and richer error messages — including a pre-flight check that points you at the right install command when the chosen package manager isn't on PATH.

## 0.1.9

### Patch Changes

- 0e97050: Surface package manager output when installing the Momentic CLI, so install errors (registry, auth, peer-dep, engine, etc.) are visible instead of hidden behind a generic failure message.

## 0.1.8

### Patch Changes

- 11e7140: Fix "(intermediate value).env is not a function" crash on startup that could occur in some package manager layouts.

## 0.1.7

### Patch Changes

- c358018: Improve reliability of usage telemetry.

## 0.1.6

### Patch Changes

- 4cf851c: Reduce CLI bundle size for faster installs.
- c8b83c5: Improve sign-in telemetry.

## 0.1.5

### Patch Changes

- 9f6c060: End-of-wizard "Next steps" now spells out the two ways to build your next test: open the local editor or prompt your AI editor via the Momentic MCP server.
- 4f9519e: The setup wizard now adds the sample environment(s) the scaffolded test depends on, even when a `momentic.config.yaml` already exists, so the very first run no longer fails with a missing-environment error. Mobile projects also get a sample environment so it's clear how to configure variables. Failures during the sample test, the editor-skills install, and the CLI install now show the full underlying output instead of being truncated to the last few lines. CLI command help, log messages, and READMEs now refer to the "Momentic dashboard" instead of "Momentic Cloud".

## 0.1.4

### Patch Changes

- c284376: Align init and upgrade configs with wizard defaults: add useMemory, failure recovery v2.0, and mobile upgrade command

## 0.1.3

### Patch Changes

- 1fb746c: Add telemetry for the wizard setup flow.
- fd1da59: Generated `momentic.config.yaml` files no longer set an unused default failure-recovery agent version.

## 0.1.2

### Patch Changes

- f3e2678: Surface dashboard URL for failed test runs with --upload-results
- 779165e: Append confetti query param when opening run URL after a successful sample test

## 0.1.1

### Patch Changes

- 878630f: Simplified wizard scaffold tests for faster execution

## 0.1.0

### Minor Changes

- 5d5fe4a: Wizard now picks a single platform (web, iOS, or Android) instead of a
  multiselect, opens the dashboard run URL in your browser as soon as the
  sample test passes, and offers to wire Momentic MCP + skills into Cursor
  or Claude Code via opt-in prompts. iOS / Android prerequisite checks now
  show actionable inline install commands with docs links. Existing
  `momentic.config.yaml` and an already-listed `momentic` /
  `momentic-mobile` dependency are detected and left alone instead of
  clobbered. Subprocess output from dependency installs and sample test
  runs no longer flickers the spinner.
