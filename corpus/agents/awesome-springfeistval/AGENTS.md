# Repository Guidelines

## Project Shape

This repository combines an awesome-list style Spring Festival project catalog with a deployable React/Vite AI assistant in `cny-ai-web/`.

## Commands

- `cd cny-ai-web && npm run dev` starts the assistant app.
- `cd cny-ai-web && npm run lint` runs ESLint.
- `cd cny-ai-web && npm test` runs the TypeScript smoke check.
- `cd cny-ai-web && npm run build` creates the Vercel build artifact.

## Environment

- `VITE_GLM_API_KEY` is required by the AI assistant.

## Editing Rules

- Keep the root README curated as an awesome list; app implementation changes belong under `cny-ai-web/`.
- Avoid committing real GLM or other model provider keys.
