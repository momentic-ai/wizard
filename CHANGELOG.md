# @momentic/wizard

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
