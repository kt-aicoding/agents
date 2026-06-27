# Active Product AGENTS.md Pattern

```md
# <Project> Working Guide

## Project State

This is an active product. Treat local user changes as intentional unless proven otherwise.

## Before Editing

- Read `README.md`.
- Inspect local scripts and package manager lockfiles.
- Run `git status --short`.
- Do not read or print `.env*` values.

## Useful Commands

- `...`: start dev server
- `...`: build
- `...`: lint/test

## Environment

Record variable names and template paths only. Do not include values.

## Verification

Use the narrowest meaningful check. For UI changes, verify desktop and mobile rendering.
```

