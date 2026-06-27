# Agents

Practical `AGENTS.md` and `CLAUDE.md` patterns collected from a multi-project AI coding workspace.

This repository is a knowledge base for writing useful project instructions for Codex, Claude Code, and other coding agents. It contains both:

- actual archived instruction files from real projects
- distilled practices, migration notes, and reusable patterns

## Contents

| Path | Purpose |
| --- | --- |
| `corpus/agents/` | Archived `AGENTS.md` files, preserving source paths. |
| `corpus/claude/` | Archived `CLAUDE.md` files, preserving source paths. |
| `manifests/files.json` | Structured manifest of all archived files. |
| `manifests/files.csv` | Spreadsheet-friendly manifest. |
| `docs/practices.md` | Practical patterns learned from the corpus. |
| `docs/migration-guide.md` | How to migrate persistent Claude instructions into `AGENTS.md`. |
| `docs/patterns/` | Reusable guide templates. |
| `docs/source-workspace-agents-index.md` | Source workspace inventory and migration candidates. |

## Snapshot

- Archived `AGENTS.md`: 105
- Archived `CLAUDE.md`: 49
- Source workspace: `/Users/kevinten/projects`
- Temporary `.claude/worktrees` snapshots are excluded.

## Key Principles

1. Keep global rules short and stable.
2. Keep project-specific commands inside the nearest project `AGENTS.md`.
3. Preserve `CLAUDE.md` for historical or Claude-specific context, but migrate durable cross-agent instructions into `AGENTS.md`.
4. Do not centralize commands that only apply to one repository.
5. Never include secrets, `.env` values, tokens, cookies, or private credentials.

## Recommended Agent Lookup Order

1. Read the root or workspace `AGENTS.md`.
2. Read the nearest project or package `AGENTS.md`.
3. If no `AGENTS.md` exists, read `CLAUDE.md`.
4. Then read `README.md` and local scripts before editing.

## Corpus Notes

The corpus intentionally includes thin guides. In many reference/archive repositories, a short `AGENTS.md` is the correct form because the main instruction is to preserve history and avoid inventing fake build/test workflows.

The corpus also includes richer active-product guides with:

- project state
- before-editing checks
- useful commands
- environment handling
- deployment notes
- validation expectations

## Maintenance

Regenerate the corpus from a source workspace only after reviewing for secrets.

```bash
gitleaks detect --source . --no-banner
```
