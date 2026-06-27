# Agent Instruction Best Practice Framework

This framework turns the local corpus into a practical review system for `AGENTS.md`, `CLAUDE.md`, and future agent instruction files.

## What The Corpus Shows

The archived files repeat a few high-value sections:

- Project overview or project state
- Commands
- Architecture or project structure
- Environment handling
- Before-editing checks
- Validation
- Deployment notes
- Common pitfalls or hazards

Those sections are useful because they answer the questions an agent must resolve before editing:

- What kind of project is this?
- What files and commands are safe to touch?
- How do I verify the smallest meaningful change?
- What should never be printed, committed, reverted, or deployed?

## Recommended File Roles

Use `AGENTS.md` as the cross-agent project contract:

- repository purpose and current status
- setup, dev, build, lint, test, and deploy commands
- architecture map and ownership boundaries
- safety rules for secrets, git state, generated files, migrations, and deployments
- verification expectations
- links to deeper docs instead of long copied material

Use `CLAUDE.md` when the content is Claude Code specific:

- Claude slash commands
- Claude-only MCP tool names
- Claude memory workflow notes
- local Claude session conventions
- temporary learnings that are not ready to become cross-agent rules

Use a Codex skill when the instruction is a reusable workflow:

- release checklist
- project triage
- deployment workflow
- browser QA flow
- security review flow
- migration or cleanup process

## Recommended AGENTS.md Shape

```md
# Repository Guidelines

## Project State

State whether this is an active product, library, reference repo, archive, generated demo, or experiment.

## Structure

Name the important directories and the boundaries between them.

## Commands

- `...`: install or sync dependencies
- `...`: local development
- `...`: lint, test, typecheck, or build
- `...`: deploy or preview, if applicable

## Environment

List variable names and template files only. Never include values.

## Working Rules

- Check git state before editing.
- Do not revert unrelated user changes.
- Keep generated files and migrations synchronized when relevant.
- Prefer existing patterns over new abstractions.

## Verification

Name the smallest meaningful checks for docs, backend, frontend, database, and deployment changes.

## Known Hazards

Record footguns, fragile migrations, provider limits, generated code boundaries, and private data rules.
```

## Review Rubric

Score each file from 0 to 2 for each dimension.

| Dimension | 0 | 1 | 2 |
| --- | --- | --- | --- |
| Scope | No clear project status | Mentions purpose only | Clearly states status and boundaries |
| Commands | Missing or invented | Some commands, unclear use | Real commands with purpose |
| Verification | Missing | Generic | Narrow checks by change type |
| Safety | Missing | Generic secret warning | Concrete rules for secrets, git state, destructive actions |
| Architecture | Missing | Directory list only | Explains important boundaries |
| Maintenance | No update rule | Manual notes | Explains when to update instructions |
| Tool Fit | One tool assumed everywhere | Mentions multiple tools | Splits cross-agent, Claude-specific, and skill content |

Interpretation:

- 0-5: risky or mostly decorative.
- 6-9: usable but likely to miss important context.
- 10-14: strong enough for routine agent work.

## Improvement Loop

After a real agent session, update the instruction layer when one of these happens:

- The agent had to rediscover a command from package scripts or README.
- The agent almost touched secrets, generated files, migrations, or unrelated user changes.
- The agent used the wrong verification command.
- The agent misunderstood whether the project was active, archived, or reference-only.
- A checklist was repeated across multiple projects and should become a template or skill.

Keep edits short. A good instruction file reduces repeated discovery work without becoming a second README.

