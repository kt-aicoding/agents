# Repository Guidelines

## Project Shape

IKUN-UI is a Vue 3 component library and docs site. Development playground files live in `dev/`, package build logic is in `scripts/`, and documentation lives in `docs/`.

## Commands

- `pnpm dev` starts the Vite playground.
- `pnpm docs:dev` starts the docs site.
- `pnpm test:run` runs Vitest.
- `pnpm build` builds package, theme, and generated exports.

## Editing Rules

- Keep package, theme, and generated component exports in sync.
- Do not commit `node_modules/`, `dist/`, VitePress cache, or coverage output.
- Prefer pnpm because this repository uses a workspace lockfile.
