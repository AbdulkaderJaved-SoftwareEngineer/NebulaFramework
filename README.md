# Nebula 🌌 — Web Automation Framework (TypeScript + Playwright)

A lightweight, layered Page Object Model (POM) automation framework designed to be reusable across any web application. Nebula prioritizes minimal setup for consumers and a clear separation of responsibilities so teams can onboard quickly.

Key goals
- Robust, language-agnostic test design for web automation ⚙️  
- Layered POM (pages, actions, assertions) for clear responsibilities 🧩  
- Minimal friction for users: run the provided CLI to configure environment without manual npm steps where possible 🚀

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
  - `/bin` — CLI scaffolding (`nebula` command)
- Zero-dependency CLI wrapper (requires Node) so users can run `nebula` without invoking npm directly
- Playwright artifacts (traces, screenshots) directed to `/reporting`

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
- bin/ (nebula CLI wrapper)

All Page classes use the `*Page.ts` suffix and contain locators only. Business logic belongs in `/actions`.

---

## Quick start (Windows) ⚡️

Prerequisite: Node.js installed (v16+ recommended).

1) Use the bundled CLI to set environment (no npm required):
```powershell
# From the repository root:
.\bin\nebula.cmd env qa
# or if bin is added to PATH:
nebula env staging
```

This writes a small state file (`.nebula_env.json`) and the framework's TypeScript helpers will pick the selected environment automatically.

2) Recommended: install framework dependencies for development & run tests (optional for users who want to run tests locally):
```powershell
npm install
# install Playwright browsers (required if you run tests)
npx playwright install
# run tests
npx playwright test
```

Note: The CLI itself only requires Node at runtime; dependency installation is required only if you intend to run or develop tests locally.

---

## Environment management 🌍
- Switch environments with the CLI: `nebula env <qa|staging|prod>`
- Config files live in `utility/env/*.json` and are consumed by `utility/config-helper.ts`

---

## Running tests & reporting 🧪
- Playwright config writes artifacts to `/reporting`
- Run tests:
  - `npx playwright test` (recommended during development)
- Generated HTML report lands inside `reporting/playwright-report` by default

---

## Contributing & extending 🤝
- Keep Page objects focused on selectors only
- Put flows and orchestration inside `/actions`
- Add reusable expects/wrappers to `/assertions`
- Add new env JSON files to `/utility/env` and update `config-helper` if needed
- Consider adding ESLint/Prettier and CI pipelines for consistent quality

---

## Making `nebula` globally available (optional)
Add the project's `bin` folder to your PATH (Windows System Environment Variables) to run `nebula` from anywhere:
- Add `D:\Desktop\Nebula\bin` (or your project path) to PATH
- Then run:
```powershell
nebula env qa
```

---

## License & contact 📬
- MIT — free to reuse and extend  
For questions or help extending the initializer, open an issue or contribute a PR.

Happy testing! 🚀
