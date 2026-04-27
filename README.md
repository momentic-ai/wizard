# @momentic/wizard

![](https://img.shields.io/badge/Node.js-20%2B-brightgreen?style=flat-square)
[![npm]](https://www.npmjs.com/package/@momentic/wizard)

[npm]: https://img.shields.io/npm/v/@momentic/wizard.svg?style=flat-square

The official onboarding wizard for [Momentic](https://momentic.ai). It walks you
through picking your testing platforms (web / iOS / Android), installing the
matching Momentic CLI(s), configuring an API key, and scaffolding your first
end-to-end test — all in a single command.

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

- `momentic-wizard login` — sign in via WorkOS in your browser and save an API
  key to `~/.momentic/auth.json`.
- `momentic-wizard logout` — remove the saved credentials.

## Options

```
momentic-wizard [options]

Options:
  --cwd <path>              Working directory to run the wizard in (default: cwd)
  --server <url>            Override Momentic API server URL (advanced)
  --platforms <platforms>   Comma-separated list of platforms (web, ios, android)
  --debug                   Enable verbose logging
  -h, --help                Display help
  -V, --version             Display version
```

The wizard is always interactive.
