# Project instructions

- When a request is ambiguous or incomplete, ask one closed question at a time (yes/no or pick-one).
- Be direct and concise, and match the user's language level; no lecturing, no filler.
- Prefer actionable steps and checklists over essays, unless depth is needed.
- Write specs, `AGENTS.md` files and other records in the style of ASD-STE100.

## Environment

- OS: `Windows` 
- Shell: `Git Bash`

### Git

- Git remote: `https://github.com/Testing-IA-TrIT/testing-inteligente-practica.git`
- Default branch: `main`
- MANDATORY: Preserve work; no secrets; no destructive commands.
- Group related changes; keep commits small and focused.
- Conventional commit `{feat|refactor|fix|chore|docs|test}(scope): {description}`

## Specifications

- When you move a spec file, keep its ID and criterion codes.
- Update the references to the moved file. Check `.feature` headers, seed comments and triage links.

## System

### Back API

- Only `projects/back` connects to persistence.
- REST API: paths start with `/api`; a resource is a plural noun. JSON bodies, ISO 8601 dates, `Authorization: Bearer <token>`. Status codes: 200, 201, 204, 400, 401, 403, 404, 409, 413, 500. Every error has the body `{ "error": "<message>" }`; an input error adds `fields`. An error never shows a stack, SQL or a path.
- Check each input at the API boundary. Store passwords as salted hashes.

### Front Web

- Get front-end data through `projects/back` only.
- Use only native Web Components for the UI. Use the existing CSS framework for styles. Serve the single-page application with Vite.

## Tooling (Vite+)

- The root, `projects/back`, `projects/front` and `e2e/` use Vite+ (`vp`). The root `package.json` has `"type": "module"`.
- The root `vite.config.ts` holds the shared configuration: `lint` (Oxlint, typeAware, typeCheck), `fmt` (Oxfmt), `staged` and `test.projects`.
- Set a unique `test.name` and set `test.include` in the local Vite configs for `back` and `front`.
- Use the [root commands](PROYECTO.md#comprobaciones-y-pruebas). Use the Vite+ type check for all projects, including E2E. Do not add a separate `tsc` check.

## Tests

### Unit tests

- Write fast, independent tests for `logic`, `shared` and `core`. Test each business rule with fake `data`.
- Put TypeScript unit tests next to the code. Use `expect`, `test` and `vi` from `vite-plus/test`.

### E2E tests

- Use Playwright with TypeScript and the `chromium` project. Follow [the E2E file and code rules](.agents/skills/implement-test/references/e2e-rules.md#e1-files-and-codes).
- Before running E2E tests, check [when the database resets](PROYECTO.md#la-base-de-datos).
- Use the URLs from `e2e/core/env.ts`. The checks and seed run in `e2e/core/global-setup.ts`.
- Add data that a scenario needs at the start to `e2e/core/seed-data.ts`. Use unique values for data that the test creates. Make each test independent.

### Code complexity limits

No tool checks these limits. Review them manually.

| Limit | Code | Tests (all `e2e` files) |
| --- | --- | --- |
| Cyclomatic complexity of a function | 8 | 8 |
| Statements in a function | 16 | 64 |
| Nesting depth | 2 | 4 |
| Parameters of a function | 2 | 4 |
| Lines in a file | 128 | 256 |
| Entries in a folder | 16 | — |

---

> last updated: 2026-11-23
