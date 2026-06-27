# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A Claude Code agent architecture for indie game development. 48 specialized subagents
are organized into a 3-tier studio hierarchy (Directors > Leads > Specialists), with
37 slash-command workflows, 8 automated hooks, and 11 path-scoped coding rules.
This is a template — not a game itself. There is no source code to build or test until
the user creates a game project using the workflows below.

## Agent Architecture

Three tiers with model assignments reflecting decision weight:

- **Tier 1 — Directors (Opus)**: `creative-director`, `technical-director`, `producer`
  High-level vision, architecture, and coordination decisions.
- **Tier 2 — Department Leads (Sonnet)**: `game-designer`, `lead-programmer`, `art-director`,
  `audio-director`, `narrative-director`, `qa-lead`, `release-manager`, `localization-lead`
- **Tier 3 — Specialists (Sonnet/Haiku)**: 30+ agents for implementation, testing, content.

Agent definitions live in `.claude/agents/`. Delegation flows downward; conflicts escalate
upward. Cross-department coordination goes through `producer`. See
`.claude/docs/agent-coordination-map.md` for full delegation and escalation paths.

Engine-specialist agent sets exist for Godot, Unity, and Unreal — each with 3-4
sub-specialists. Use whichever set matches the configured engine.

## Technology Stack

- **Engine**: Unity 2021.3.11f1 (LTS)
- **Language**: C#
- **Version Control**: Git with trunk-based development
- **Build System**: Unity Build Pipeline
- **Asset Pipeline**: Unity Asset Import Pipeline + Addressables

## Automated Safety (Hooks)

Hooks in `.claude/settings.json` run automatically — no manual invocation needed:

| Hook | Trigger | Purpose |
|------|---------|---------|
| `session-start.sh` | Session open | Loads sprint context, recent git activity |
| `detect-gaps.sh` | Session open | Detects fresh projects, missing docs |
| `validate-commit.sh` | `git commit` (PreToolUse) | Checks hardcoded values, TODO format, JSON validity |
| `validate-push.sh` | `git push` (PreToolUse) | Warns on pushes to protected branches |
| `validate-assets.sh` | Write/Edit in `assets/` (PostToolUse) | Validates naming, JSON structure |
| `pre-compact.sh` | Context compression | Preserves session progress notes |
| `session-stop.sh` | Session close | Logs accomplishments |
| `log-agent.sh` | Subagent spawn | Audit trail of all agent invocations |

## Collaboration Protocol

**User-driven collaboration, not autonomous execution.**
Every task follows: **Question -> Options -> Decision -> Draft -> Approval**

- Agents MUST ask "May I write this to [filepath]?" before using Write/Edit tools
- Agents MUST show drafts or summaries before requesting approval
- Multi-file changes require explicit approval for the full changeset
- No commits without user instruction

See `docs/COLLABORATIVE-DESIGN-PRINCIPLE.md` for full protocol and examples.

## Key Workflows

| Starting point | Run this |
|---------------|----------|
| No idea what to build | `/start` or `/brainstorm` |
| Have a concept, need engine | `/setup-engine` |
| Have concept + engine, need design | `/map-systems` then `/design-system` |
| Have existing project | `/project-stage-detect` then `/gate-check` |
| Ready to implement | `/sprint-plan new` |

## Session Recovery

After compaction, crash, or `/clear`: read `production/session-state/active.md` first.
This file is the living checkpoint — it tracks current task, progress, decisions, and
files being worked on. The file is the memory, not the conversation.

## Project Structure

@.claude/docs/directory-structure.md

## Engine Version Reference

@docs/engine-reference/unity/VERSION.md

## Technical Preferences

@.claude/docs/technical-preferences.md

## Coordination Rules

@.claude/docs/coordination-rules.md

## Coding Standards

@.claude/docs/coding-standards.md

## Context Management

@.claude/docs/context-management.md
