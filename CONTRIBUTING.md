# Contributing to CoffeeQL for VS Code

Thank you for your interest in contributing to the CoffeeQL VS Code extension. This document explains what you can work on, how to set up the development environment, and what a pull request needs to include before it is ready for review.

---

## What This Repository Contains

This repository is the VS Code extension for CoffeeQL. It provides:

- **Syntax highlighting** — the TextMate grammar in `syntaxes/coffeeql.tmLanguage.json`
- **Snippets** — the snippet definitions in `snippets/coffeeql.json`
- **Hover documentation** — the TypeScript extension in `src/extension.ts`
- **Language configuration** — bracket matching, comment toggling in `language-configuration.json`

This repository does **not** contain the CoffeeQL execution engine, the parser, or the lexer. Those live in separate repositories under the `coffeeql` organization.

---

## What You Can Contribute To

### Syntax Highlighting (`syntaxes/coffeeql.tmLanguage.json`)

- Fix incorrect or missing token scopes
- Add highlighting for new CoffeeQL syntax as it ships in new versions
- Improve collection type detection (`[]` vs `{}` vs `ns:key{}`)
- Test against different VS Code color themes and fix contrast issues

### Snippets (`snippets/coffeeql.json`)

- Add new snippets for common CoffeeQL patterns
- Improve existing snippet tab stop order
- Add snippets for new chain operations when they ship (e.g. `.stream()` in v0.5.0)

### Hover Documentation (`src/extension.ts`)

- Fix incorrect or outdated documentation for any keyword
- Add documentation for keywords not yet covered
- Improve code examples in hover text
- Add links to the relevant coffeeql.dev documentation page

### Language Configuration (`language-configuration.json`)

- Fix bracket pair matching
- Improve comment toggling behavior

### README and Documentation

- Fix typos or outdated information
- Improve the quick start example
- Add screenshots showing syntax highlighting in action

---

## What Is Off-Limits

- Do not modify the CoffeeQL syntax or add new keywords — that is decided in the language spec repository (`coffeeql/coffeeql-spec`) and implemented in the lexer and parser
- Do not add runtime dependencies to the extension — it should remain lightweight and load instantly

---

## Development Setup

### Prerequisites

- [Node.js](https://nodejs.org) 18 or later
- [VS Code](https://code.visualstudio.com)
- npm

### Clone and Install

```bash
git clone https://github.com/coffeeql/coffeeql-vscode
cd coffeeql-vscode
npm install
```

### Compile

```bash
npm run compile
```

### Run in VS Code

Press `F5` in VS Code to open a new Extension Development Host window with the extension loaded. Open any `.cql` file to test your changes.

### Watch Mode

```bash
npm run watch
```

This recompiles automatically when you save changes to `src/extension.ts`.

---

## Testing Your Changes

Before submitting a PR, verify the following manually:

**Syntax highlighting:**
- Open `sample.cql` (or create your own) and confirm all token types are colored correctly
- Test with at least two different VS Code themes (e.g. Dark+ and One Dark Pro)

**Snippets:**
- Open a `.cql` file, type a snippet prefix, press Tab, and confirm the snippet expands correctly with all tab stops working

**Hover documentation:**
- Hover over at least five different keywords and confirm the correct documentation appears
- Confirm that hovering over a non-keyword identifier shows no hover

---

## Building the .vsix

```bash
npx vsce package
```

This produces `coffeeql-X.Y.Z.vsix`. Install it locally to test:

```
VS Code → Extensions → ... → Install from VSIX
```

---

## Pull Request Process

**Before opening a PR:**

1. Fork the repository and create a branch from `main`
2. Make your changes
3. Compile with `npm run compile` — fix any TypeScript errors
4. Test your changes manually as described above
5. Run `npm run lint` and fix any lint errors

**PR requirements:**

- Reference the issue number in the PR title: `fix #021 — add highlighting for VECTOR data type`
- Describe what changed and why in the PR description
- If you changed the grammar, include a before-and-after screenshot
- If you added a snippet, show the expanded output
- If you changed hover docs, show the updated hover text

**One issue per PR.** Do not bundle multiple unrelated changes.

---

## CLA

All contributors must sign the Contributor License Agreement before their first PR is merged. You will be prompted automatically when you open a PR.

---

## Questions

Join the CoffeeQL Discord for questions — the link is shared with all founding contributors. For public discussion, open a GitHub Discussion in this repository.
