# Repository Guidelines

## Project Shape

This repository is a fiction/worldbuilding project plus an Astro reading website in `website/`. Root Markdown files, `worldbuilding/`, and media assets are source material; `website/` is the deployable site.

## Commands

- `cd website && npm run dev` starts the Astro site.
- `cd website && npm run build` builds the production site.
- `cd website && npm run lint` runs the site build as a static smoke check.
- `cd website && npm test` runs the same CI-safe build check.

## Editing Rules

- Preserve story canon in `worldbuilding/`, `CHANGELOG.md`, and release-facing README copy.
- Keep large media assets out of incidental refactors.
- Do not edit `_private/` unless the task explicitly covers private strategy material.
