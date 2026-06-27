# Repository Working Guide

This directory contains many independent projects, knowledge bases, experiments, and product prototypes. Prefer local project instructions over this file when they exist.

## General Rules

- Follow the nearest `AGENTS.md` first. If a project has no `AGENTS.md`, use `CLAUDE.md` as migrated project context, then `README.md`.
- Keep project-specific rules local. Do not turn one project's commands, naming rules, or architecture choices into global behavior.
- Default to Simplified Chinese for user-facing explanations and Chinese knowledge-base documents. Follow the existing language of the codebase for code, comments, UI copy, and docs.
- Protect secrets aggressively. Never print, copy, commit, or migrate tokens, `.env` values, credentials, private keys, or account cookies.
- Before editing, inspect the relevant files and existing scripts. Prefer the project's package manager and commands over generic commands.
- Avoid broad cleanup, formatting, dependency upgrades, or generated-file churn unless directly required by the task.

## Workspace Inventory Materials

- Start broad project triage from `PROJECTS_INVENTORY.md`, then use `PROJECTS_WORK_ORDERS.md` as the single-project execution entry.
- Use `PROJECTS_OPTIMIZATION_QUEUE.md` for priority scoring when choosing the next project to optimize.
- Use `PROJECTS_DOMAIN_REGISTRY.md` when touching domains, deployment URLs, DNS, or README website links.
- Use `PROJECTS_STATUS_MATRIX.md` to classify a project as product/web, tooling/infra, code library, or knowledge/archive before changing it.
- Use `PROJECTS_BATCH_PLAN.md` for batch-level cleanup and acceptance criteria.
- Use `PROJECTS_READINESS_AUDIT.md` to see missing README sections, scripts, environment templates, and deployment notes before optimizing a project.
- Use `PROJECTS_P0_TRIAGE.md` before touching high-noise repositories; it lists exact local files to classify or clean.
- Refresh all workspace reports with `python3 tools/project_workspace_inventory.py` after each batch of project updates.

## Common Project Shapes

- Frontend and product sites are usually React/Next.js/Vite/Tailwind with Vercel and sometimes Supabase. Verify with the project's own `package.json` scripts.
- AI and MCP projects are often Python with `uv`, `pyproject.toml`, or `requirements.txt`; TypeScript MCP projects usually use Node 18+ or Node 22+.
- Monorepos may use `pnpm` workspaces. Do not replace `pnpm` with `npm` when a lockfile or workspace config says otherwise.
- Some repositories are content-only knowledge bases. For those, do not invent build/test steps; validate by checking links, structure, naming, and document consistency.
- Mobile/app projects may use Expo, Flutter, Unity, or mini-program tooling. Use the local instructions before running heavyweight commands.

## Verification Preferences

- Use the narrowest meaningful verification: typecheck/lint/build/test for the touched package, not the whole projects directory.
- For Next/Vite/React UI work, start the dev server when needed and visually verify responsive layouts before calling the work done.
- For Python MCP or agent projects, prefer `uv run ...` or the documented venv flow when present; otherwise use the local `requirements.txt`/`pyproject.toml`.
- For documentation-only edits, verify headings, paths, links, and examples rather than running unrelated code checks.

## Codex Usage

- Use Codex subagents for bounded read-only review, planning, research, frontend, MCP, deployment, or documentation passes when they reduce main-context noise.
- Use official OpenAI developer documentation when working with OpenAI APIs, ChatGPT Apps SDK, Codex behavior, or model/tooling details.
- Keep long-running work resumable: record important decisions, commands run, remaining risks, and validation status in the final handoff.
