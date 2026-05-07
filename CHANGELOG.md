# @momentic/wizard

## 0.1.7

### Patch Changes

- c358018: Upgrade PostHog telemetry SDK to v5 (native fetch, no axios).

## 0.1.6

### Patch Changes

- 4cf851c: Migrate workspace packages from `main` to `exports` and enable tree-shaking in tsup bundles. Adds `sideEffects: false` to internal packages so esbuild can drop dead code from CLI builds.
- c8b83c5: Distinguish reused-credentials sign-ins from full device-code sign-ins in the wizard's auth telemetry.

## 0.1.5

### Patch Changes

- 9f6c060: End-of-wizard "Next steps" now spells out the two ways to build your next test: open the local editor or prompt your AI editor via the Momentic MCP server.
- 4f9519e: The setup wizard now adds the sample environment(s) the scaffolded test depends on, even when a `momentic.config.yaml` already exists, so the very first run no longer fails with a missing-environment error. Mobile projects also get a sample environment so it's clear how to configure variables. Failures during the sample test, the editor-skills install, and the CLI install now show the full underlying output instead of being truncated to the last few lines. CLI command help, log messages, and READMEs now refer to the "Momentic dashboard" instead of "Momentic Cloud".

## 0.1.4

### Patch Changes

- c284376: Align init and upgrade configs with wizard defaults: add useMemory, failure recovery v2.0, and mobile upgrade command

## 0.1.3

### Patch Changes

- 1fb746c: Add PostHog telemetry for wizard setup flow
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
