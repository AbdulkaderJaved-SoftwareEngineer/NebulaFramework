# NebulaFramework
🌌 Nebula: An enterprise-grade, TypeScript-first Playwright automation framework. Features a robust Page Object Model (POM) architecture, integrated CLI for rapid scaffolding, automated logging with Chalk, and a high-level wrapper API for reliable web interactions and assertions. Built for scale, designed for speed.

🚀 Quick Start

Installation

Prepare your environment by installing dependencies and the Playwright browser binaries:

# Install core dependencies
npm install

# Install Playwright browsers and system dependencies
npx playwright install --with-deps

# Build the project
npm run build


🛠 CLI Reference

Nebula comes with a built-in CLI tool (nebula) to manage your workspace and scaffold components instantly.

Command

Alias

Description

nebula create-page <name>

cp

Scaffolds a Page Object in pages/ and a Test Spec in tests/.

nebula remove <name>

rm

Deletes the specified Page Object and Test folder.

nebula scan

s

Checks the integrity of the project architecture.

nebula status

-

Displays a health report of core framework modules.

nebula clean

-

Danger: Resets the workspace by emptying pages and tests.

🎮 Core API: Global Actions

The Actions class provides a wrapper around Playwright interactions, adding automatic logging and standardized timeouts.

Navigation & Interaction

goto(url: string): Navigates to a URL and waits for networkidle.

click(selector: string | Locator): Performs a click with automatic logging.

doubleClick(selector: string): Performs a mouse double-click.

hoverAndClick(hoverSelector, clickSelector): Hovers over one element and clicks another.

clickInsideFrame(frameSelector, elementSelector): Interacts with elements inside an IFrame.

Inputs & Keyboard

type(selector, text, delay?): Fills an input field with optional delay.

clearAndType(selector, text): Resets a field before entering new data.

selectOption(selector, option): Selects dropdown values by label, value, or index.

pressKey(key: string): Simulates keyboard presses (e.g., 'Enter', 'Tab').

Advanced & Utilities

dragAndDrop(source, target): Drags an element to a target location.

waitForNewTab(action): Handles events that open new browser tabs.

waitForState(selector, state): Waits for elements to be visible, hidden, or attached.

takeScreenshot(name: string): Saves a full-page screenshot to the reporting directory.

✅ Core API: Global Assertions

The Assert class provides a readable, logged alternative to standard Playwright expectations.

State Assertions

toBeVisible(selector): Asserts element is visible (10s timeout).

toBeHidden(selector): Asserts element is not present or hidden.

toBeEnabled(selector) / toBeDisabled(selector): Checks element interactivity state.

toBeEditable(selector): Verifies if an input field is editable.

toBeChecked(selector): Checks the state of checkboxes or radio buttons.

Content Assertions

toHaveText(selector, text): Matches inner text exactly or via RegExp.

toContainText(selector, text): Checks if the element contains a substring.

toHaveValue(selector, value): Verifies the current value of form inputs.

toHaveAttribute(selector, attr, value): Checks for specific HTML attributes (e.g., src, href).

Page & API Assertions

toHaveURL(url): Verifies the current browser URL.

toHaveTitle(title): Verifies the page title.

toHaveCount(selector, count): Asserts the number of elements found.

toBeOK(response): Asserts that an API response status is between 200-299.

🏛 Architecture

Nebula follows a strict directory structure to ensure maintainability:

├── actions/         # Global interaction wrappers
├── assertions/      # Global assertion wrappers
├── bin/             # CLI binary logic
├── pages/           # Page Object classes (Scaffolded by CLI)
├── tests/           # Test specifications (Scaffolded by CLI)
├── utility/         # Helper functions and loggers
└── playwright.config.ts


👥 Authors

Designed and Developed by Mustufa Qureshi and Abdul Kader Qureshi.

License: MIT
