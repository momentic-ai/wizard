# @momentic/wizard

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
