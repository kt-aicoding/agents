# 活跃产品 AGENTS.md 模板

适用于仍在开发、部署或频繁维护的产品型仓库。

```md
# <Project> Working Guide

## Project State

This is an active product. Treat local user changes as intentional unless proven otherwise.

## Structure

- `src/`: application source.
- `docs/`: product and maintenance docs.
- `scripts/`: local automation.

## Before Editing

- Read `README.md`.
- Inspect local scripts and package manager lockfiles.
- Run `git status --short`.
- Do not read or print `.env*` values.
- Do not revert unrelated user changes.

## Commands

- `...`: install or sync dependencies.
- `...`: start local development.
- `...`: run lint/test/typecheck.
- `...`: build or preview.

## Environment

Record variable names, secret-manager names, and template paths only. Do not include values.

## Deployment

Name the platform and deployment command only if it is real and current.

## Verification

Use the narrowest meaningful check. For UI changes, verify desktop and mobile rendering. For API changes, verify the changed endpoint or integration path.

## Known Hazards

- List generated files, fragile migrations, external service limits, or private data boundaries.
```
