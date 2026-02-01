# Nebula 🌌 — Web Automation Framework (TypeScript + Playwright)

A lightweight, layered Page Object Model (POM) automation framework designed to be reusable across any web application. Nebula prioritizes minimal setup for consumers and a clear separation of responsibilities so teams can onboard quickly.

Author: Abdul Kader Javed Qureshi — this framework is purely written by Abdul Kader Javed Qureshi. ✍️

Key goals
- Robust, application-agnostic test design for web automation ⚙️  
- Layered POM (pages, actions, assertions) for clear responsibilities 🧩  
- Minimal friction for users: run a single setup command and everything is handled automatically 🚀

---

## Features ✨
- TypeScript-first framework with Playwright integration
- Layered structure:
  - `/pages` — locator-only Page classes (class names end with `Page`)
  - `/actions` — reusable business logic & workflows
  - `/assertions` — custom validation helpers and expect wrappers
  - `/utility` — config helpers and shared utilities
  - `/utility/env` — environment JSON files (qa, staging, prod)
  - `/tests` — `.spec.ts` test files
  - `/reporting` — test results, logs, screenshots (git-ignored)
  - `/bin` — project initializer scaffolding
- Single-step setup: one script installs dependencies, Playwright browsers, and optional helpers

---

## Important — One command setup ✅
You do NOT need to run multiple npm commands. To prepare the project for first use, run only:

```powershell
npm run setup
```

What `npm run setup` does (examples — implemented in package.json):
- Installs project dependencies (production + dev)
- Installs Playwright browsers (`npx playwright install`)
- Runs any post-install scaffolding and OS-specific setup
- Prepares the reporting folder and sample artifacts

After `npm run setup` completes, the framework is ready for development and testing.

---

## Project structure 📁
Top-level layout (important folders):
- pages/
- actions/
- assertions/
- utility/
  - env/ (qa.json, staging.json, prod.json)
- tests/
- reporting/ (ignored in git)
- bin/ (project initializer scaffolding)

All Page classes use the `*Page.ts` suffix and contain locators only. Business logic belongs in `/actions`.

---

## Quick start (Windows) ⚡️

Prerequisite: Node.js installed (v16+ recommended).

1) Run the single setup command:
```powershell
# From the repository root:
npm run setup
```

2) (Optional) Run tests locally:
```powershell
# only if you want to run tests locally after setup
npx playwright test
```

---

## Environment management 🌍
- Environment config files live in `utility/env/*.json`.
- The framework reads the active environment via `utility/config-helper.ts`. Switch logic is implemented in the helper and can be driven by the initializer or CI.

---

## Running tests & reporting 🧪
- Playwright config writes artifacts to `/reporting`
- Generated HTML report lands inside `reporting/playwright-report` by default

---

## Contributing & extending 🤝
- Keep Page objects focused on selectors only
- Put flows and orchestration inside `/actions`
- Add reusable expects/wrappers to `/assertions`
- Add new env JSON files to `/utility/env` and update `config-helper` if needed
- Consider adding ESLint/Prettier and CI pipelines for consistent quality

---


## CLI Reference — Nebula CLI (bin/cli.ts) 🛠️

Nebula ships a CLI implemented at `bin/cli.ts` (built with commander, chalk, ora, fs-extra and inquirer). The CLI provides fast scaffolding and workspace utilities to manage a Nebula project.

Available commands
- scan (alias: s)  
  - Performs a deep integrity scan (pages, tests, Playwright config, package.json) and prints a health report.
  - Example: nebula scan

- create-page <Name> (alias: cp)  
  - Generates a locator-only Page class and an isolated test folder with a starter spec.
  - Creates: `pages/<Name>/<Name>.ts` and `tests/<Name>/<Name>.spec.ts` (uses project Actions & Assertions in the template).
  - Example: nebula create-page Login

- status  
  - Quick health check for required folders (pages, actions, assertions, utility, tests).
  - Example: nebula status

- remove <Name>  
  - Prompts for confirmation and removes a specific page and its isolated test folder.
  - Example: nebula remove Login

- clean  
  - Hard-reset helper that (after confirmation) empties workspace content under `pages`, `tests`, `reporting`, and `test-results` while preserving the folder structure.
  - Example: nebula clean

Notes
- The CLI prints a decorative banner (credit shown in the banner) — designed and developed by Mustufa Qureshi and Abdul Kader Javed Qureshi.
- The CLI templates reference `Actions` and `Assert` helper classes — keep those global helpers in `actions/` and `assertions/` to ensure generated tests are ready-to-run.
- The setup script (`npm run setup`) will wire required runtime pieces and install CLI dependencies so the CLI behaves as expected across environments.

-- end of CLI Reference --

Happy testing! 🚀
