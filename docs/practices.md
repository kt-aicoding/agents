# Practical Patterns For AGENTS.md

This guide distills patterns from the archived corpus.

## 1. Use Layers

Agent instructions work best as layers:

- Workspace `AGENTS.md`: global safety, language, tool preference, and inventory entry points.
- Project `AGENTS.md`: local project state, commands, hazards, verification, and deployment notes.
- Package/subproject `AGENTS.md`: framework-specific caveats or package-local commands.
- `CLAUDE.md`: historical Claude-specific context or migration source.

## 2. Keep Root Rules Stable

Good root rules avoid project-specific assumptions. They cover:

- nearest-instruction lookup order
- secret handling
- preferred CLI/tooling behavior
- workspace inventory files
- verification expectations
- language preference

Root rules should not include one project's package manager, deploy target, or architecture.

## 3. Put Commands Near The Code

Project guides should record real commands from local scripts and README files:

```md
## Useful Commands

- `npm run dev`: start the local app.
- `npm run build`: production build.
- `npm run lint`: lint or syntax check.
```

Do not invent test/build commands for reference-only repositories.

## 4. Mark Project State Explicitly

Many repositories are experiments, references, archives, or generated demos. A useful guide states that directly:

```md
## Project State

This repository is a reference archive. Preserve existing notes and do not add new build automation unless the project becomes active again.
```

This prevents agents from over-engineering inactive projects.

## 5. Use A Before-Editing Checklist

Active products benefit from a short preflight:

- read `README.md`
- inspect `package.json` or build files
- check `git status --short`
- avoid reverting unrelated user changes
- identify env templates without reading secrets

## 6. Keep Verification Narrow

Use the smallest meaningful check:

- UI project: package-local lint/build/test plus browser verification when visual behavior changes.
- Python/uv project: `uv sync`, `uv run ...`, or documented test command.
- Go project: `go test ./...`.
- Maven project: `mvn test`.
- Docs-only project: headings, links, paths, and examples.

## 7. Handle Provider Operations Through CLI

For repeatable cloud and repo operations, prefer CLIs over always-on provider MCPs:

- GitHub: `gh`
- Vercel: `vercel`
- Supabase: `supabase`
- CloudBase: `tcb`
- Cloudflare: `wrangler`
- Netlify: `netlify`
- Fly: `flyctl`

Use MCP only when it adds clear agent-native value, such as documentation search or browser automation.

## 8. Thin Guides Are Valid

A short guide is good when it accurately says:

- this is reference material
- preserve history
- no active runtime is known
- do not add deployment automation until the project is reactivated

Thin guides are bad only when they hide active product commands or hazards.

## 9. Avoid Temporary Worktree Copies

Do not treat `.claude/worktrees/.../AGENTS.md` as canonical. They are snapshots created for a temporary working tree.

## 10. Migrate Durable Claude Notes

Move durable, cross-agent instructions from `CLAUDE.md` to `AGENTS.md` when:

- the project is still active
- Codex or other agents work there regularly
- the instructions are not Claude-specific

Keep Claude-specific command references in `CLAUDE.md`.

