# CLAUDE.md To AGENTS.md Migration Guide

Use this when a project has useful `CLAUDE.md` instructions but no sibling `AGENTS.md`.

## What To Migrate

Move durable rules into `AGENTS.md`:

- project structure
- build/test/dev commands
- package manager
- deployment target
- environment variable policy
- validation expectations
- known hazards
- project state: active, maintenance, reference, archive

Keep in `CLAUDE.md`:

- Claude-specific slash commands
- Claude-only MCP tool names
- conversation history
- temporary planning notes
- personal scratch instructions

## Suggested Process

1. Read `CLAUDE.md`, `README.md`, and project scripts.
2. Extract only stable instructions.
3. Create concise `AGENTS.md`.
4. Keep `CLAUDE.md` if it still contains Claude-specific material.
5. Run the narrowest project verification command after changing docs only if the project expects it.

## Minimal AGENTS.md Template

```md
# Repository Guidelines

## Project Shape

Describe whether this is an active product, platform, reference, or archive.

## Commands

- `...`: local development
- `...`: build/test/lint

## Editing Rules

- Keep project-specific conventions local.
- Do not print or commit secrets.
- Preserve unrelated user changes.

## Verification

Describe the smallest meaningful check.
```

## Migration Triage

Prioritize active projects and repositories that agents touch often. Do not migrate every historical `CLAUDE.md` automatically.

