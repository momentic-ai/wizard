# @momentic/wizard

![](https://img.shields.io/badge/Node.js-20%2B-brightgreen?style=flat-square)
[![npm]](https://www.npmjs.com/package/@momentic/wizard)

[npm]: https://img.shields.io/npm/v/@momentic/wizard.svg?style=flat-square

The official onboarding wizard for [Momentic](https://momentic.ai). It walks you
through picking your testing platforms (web / iOS / Android), installing the
matching Momentic CLI(s), configuring an API key, and scaffolding your first
end-to-end test, all in a single command.

**Learn more in the [official documentation](https://momentic.ai/docs)**.

## Get Started

Run the wizard inside your project directory:

```bash
npx @momentic/wizard@latest
```

The wizard will:

1. Detect your package manager (npm, pnpm, yarn, bun).
2. Ask which platforms you want to test: **web**, **iOS**, **Android**
   (multi-select).
3. Prompt you to sign in with your Momentic account in the browser, or skip.
4. Install the matching CLI(s):
   [`momentic`](https://www.npmjs.com/package/momentic) for web,
   [`momentic-mobile`](https://www.npmjs.com/package/momentic-mobile) for iOS /
   Android.
5. Create a `momentic.config.yaml` file.
6. For iOS / Android, print a checklist of local prerequisites (Xcode/idb for
   iOS; Java, `ANDROID_HOME`, adb for Android) and link to the relevant
   quickstart.
7. Print the next commands to run, tailored per platform.

## Subcommands

- `momentic-wizard login`: sign in via your browser and save an API key to
  `~/.momentic/auth.json`.
- `momentic-wizard logout`: remove the saved credentials.

## Options

Flags are documented by the CLI itself (defaults, env vars, and choices
included), so run:

```bash
npx @momentic/wizard@latest --help
```

The flags that matter most for CI and coding agents — `-y` / `--yes`,
`--api-key`, `--platform`, and `--editor-tools` — are covered in
[Non-interactive mode](#non-interactive-mode-ci--coding-agents) below.

## Non-interactive mode (CI & coding agents)

The wizard normally prompts for the platform, sign-in, project name, and which
coding agents to wire up. When there is no TTY (CI, or a coding agent like
Claude Code / Cursor shelling out), or when you pass `-y` / `--yes`, it runs
**non-interactively** and never prompts:

- **Auth** comes from `--api-key` / `MOMENTIC_API_KEY` (validated against the
  server), falling back to `~/.momentic/auth.json`. If neither is present it
  exits with a clear message instead of opening a browser or hanging.
- **Platform** uses `--platform` (defaults to `web`).
- **Project name** uses the directory / `package.json` name.
- **Coding agents** default to the ones detected in your environment plus
  Momentic skills; override with `--editor-tools` (`all`, `none`, or a list such
  as `claude-code,cursor,skills`).

```bash
MOMENTIC_API_KEY=mk_... npx @momentic/wizard@latest --yes
```
