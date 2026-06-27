# AGENTS.md Index

- Generated: 2026-06-27
- Root: `/Users/kevinten/projects`
- Purpose: organize all project instructions used by Codex/agents without rewriting project-local rules.

## Summary

- Agents files found: 106
- Project/root guides: 54
- Nested package/subproject guides: 51
- Temporary worktree copies: 1
- Nonstandard lowercase `agents.md`: 0
- Rich guides: 41
- Medium guides: 6
- Thin guides: 59
- CLAUDE-only migration candidates: 34

## How To Use

1. Root rule: read `/Users/kevinten/projects/AGENTS.md` first for workspace-wide behavior.
2. Project rule: when inside a repo, prefer the nearest `AGENTS.md`.
3. Fallback rule: if a directory only has `CLAUDE.md`, use it as context and consider migrating key rules into `AGENTS.md`.
4. Do not edit generated worktree copies under `.claude/worktrees`; treat them as temporary snapshots.
5. Do not merge thin guides blindly. Many intentionally mark reference/archive repositories.

## Organization Policy

- Keep project-specific rules local. Do not centralize commands that only apply to one repo.
- Use root `AGENTS.md` only for workspace-wide safety, language, inventory, and verification defaults.
- Use project `AGENTS.md` for package manager, build/test commands, deployment notes, project status, and local hazards.
- For thin reference repos, a short `AGENTS.md` is acceptable if it clearly says the repo is reference/archive/low-signal.
- For active products, `AGENTS.md` should include structure, commands, environment handling, validation, and deployment notes.
- Do not print or migrate secrets from `.env*`.

## Duplicate Template Clusters

### Duplicate Cluster 1: 10 files

- Hash: `e3447d842518`
- Files:
  - `2077-daily/AGENTS.md`
  - `ai-chat-chrome/.claude/worktrees/agent-acd69f6d/hotel-compare/web/AGENTS.md`
  - `ai-chat-chrome/hotel-compare/web/AGENTS.md`
  - `ai-hackthon/agentverse/AGENTS.md`
  - `ai-home-care-platform/AGENTS.md`
  - `awesome-ai-ideas/site/AGENTS.md`
  - `bci-research/web/AGENTS.md`
  - `kevinten10.github.io/next-portfolio/AGENTS.md`
  - `minimind/website/AGENTS.md`
  - `openclawpool/AGENTS.md`

## Special Cases

Temporary worktree copies:
- `ai-chat-chrome/.claude/worktrees/agent-acd69f6d/hotel-compare/web/AGENTS.md`

- No lowercase `agents.md` files found.

## CLAUDE-only Migration Candidates

These directories have `CLAUDE.md` but no sibling `AGENTS.md`. Migrate only if the repo is still active or if Codex repeatedly works there.

- `Claude-Code-Game-Studios/CLAUDE.md`
- `OpenOctopus/CLAUDE.md`
- `TripMeta/CLAUDE.md`
- `ai-agent-crewai/CLAUDE.md`
- `ai-archi-analyzer/CLAUDE.md`
- `ai-codereview-web/CLAUDE.md`
- `ai-meeting-web/CLAUDE.md`
- `ai-rag-pipeline/CLAUDE.md`
- `bci-research/CLAUDE.md`
- `bin/CLAUDE.md`
- `books/CLAUDE.md`
- `brag/AI创意/一站式会议助手/CLAUDE.md`
- `brag/AI创意/摩托车社区/CLAUDE.md`
- `brag/CLAUDE.md`
- `brag/ai_claude_code/CLAUDE.md`
- `brag/ai_openclaw/CLAUDE.md`
- `capa.io/CLAUDE.md`
- `ikun/ikun-activity/CLAUDE.md`
- `kevinten10.github.io/CLAUDE.md`
- `kimi/CLAUDE.md`
- `mcp-avatar/CLAUDE.md`
- `mcp-image-gen/CLAUDE.md`
- `mcp-media-toolkit/CLAUDE.md`
- `mcp-presentation/CLAUDE.md`
- `mcp-social-publisher/CLAUDE.md`
- `mcp-subtitle/CLAUDE.md`
- `mcp-video-gen/CLAUDE.md`
- `mcp-voice-clone/CLAUDE.md`
- `promotion-agent/CLAUDE.md`
- `spa-agent/CLAUDE.md`
- `spatial-memory/CLAUDE.md`
- `yuanjie/ai-product-playbook/CLAUDE.md`
- `yuanjie-ar/CLAUDE.md`
- `yuanjie-ar-weapp/CLAUDE.md`

## Full Inventory

| Path | Type | Quality | Lines | Headings |
| --- | --- | --- | ---: | --- |
| `.github/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `2077-daily/AGENTS.md` | Project/root guide | Thin | 5 | # This is NOT the Next.js you know |
| `3d-agent/AGENTS.md` | Project/root guide | Rich | 28 | # 3D Agent Maintenance Guide<br>## Project State<br>## Before Editing |
| `Aditum/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `AGENTS.md` | Project/root guide | Rich | 44 | # Repository Working Guide<br>## General Rules<br>## Workspace Inventory Materials |
| `ai-agent-agentscope-codereview/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `ai-agent-agentscope-deepresearch/AGENTS.md` | Project/root guide | Rich | 51 | # Repository Guidelines<br>## Project Structure<br>## Commands |
| `ai-agent-agentscope/AGENTS.md` | Project/root guide | Rich | 23 | # Eino Agent Platform Working Guide<br>## Scope<br>## Validation |
| `ai-chat-chrome/.claude/worktrees/agent-acd69f6d/hotel-compare/web/AGENTS.md` | Temporary worktree copy | Thin | 5 | # This is NOT the Next.js you know |
| `ai-chat-chrome/AGENTS.md` | Project/root guide | Rich | 41 | # Repository Notes<br>## Structure<br>## Working Rules |
| `ai-chat-chrome/hotel-compare/web/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `ai-chat-cr-chrome/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `ai-coding-mcp/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `ai-dify-dsl/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `ai-hackthon/agentverse/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `ai-home-care-platform/AGENTS.md` | Project/root guide | Thin | 5 | # This is NOT the Next.js you know |
| `ai-ops-script/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `AI/AGENTS.md` | Project/root guide | Rich | 33 | # AI / Ring Working Guide<br>## Scope<br>## Validation |
| `Air/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `anycap/anycap/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # AnyCap |
| `argue-agent/AGENTS.md` | Project/root guide | Rich | 27 | # Argue Agent Maintenance Guide<br>## Project State<br>## Before Editing |
| `awesome-ai-ideas/AGENTS.md` | Project/root guide | Rich | 29 | # Awesome AI Ideas Working Guide<br>## Scope<br>## Validation |
| `awesome-ai-ideas/site/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `awesome-springfeistval/AGENTS.md` | Project/root guide | Rich | 21 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `bci-research/web/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `books/Compiling-the-Dao/AGENTS.md` | Nested package/subproject guide | Medium | 18 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `brag/ai_claude_code/.claude/commands/monitoring/AGENTS.md` | Nested package/subproject guide | Rich | 44 | # List Active Patterns<br>## 🎯 Key Principle<br>## MCP Tool Usage in Claude Code |
| `brag/ai_cli/AGENTS.md` | Nested package/subproject guide | Rich | 177 | # AI CLI Project - Agent Guidelines<br>## Project Overview<br>## Build/Test Commands |
| `brag/ai_codex/AGENTS.md` | Nested package/subproject guide | Thin | 3 | # Rules |
| `brag/ai_tools/AGENTS.md` | Nested package/subproject guide | Rich | 37 | # Repository Guidelines<br>## Project Structure & Module Organization<br>## Build, Test, and Development Commands |
| `brag/ai_tools/ai-tools/AGENTS.md` | Nested package/subproject guide | Rich | 40 | # Repository Guidelines<br>## Project Structure<br>## Commands |
| `capa-java-aws/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `capa-java/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `capa/AGENTS.md` | Project/root guide | Rich | 31 | # Capa Runtime Maintenance Guide<br>## Project State<br>## Before Editing |
| `cloud-runtimes-golang/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `cloud-runtimes-jvm/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `cloud-runtimes-python/AGENTS.md` | Project/root guide | Thin | 7 | # Repository Guidelines |
| `docs/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `dog-agent/AGENTS.md` | Project/root guide | Rich | 35 | # PawPal Dog Agent Maintenance Guide<br>## Project State<br>## Before Editing |
| `english-agent/AGENTS.md` | Project/root guide | Rich | 23 | # Repository Notes<br>## Working Rules<br>## Validation |
| `fish-agent/AGENTS.md` | Project/root guide | Rich | 23 | # Repository Notes<br>## Working Rules<br>## Validation |
| `harness/AGENTS.md` | Project/root guide | Rich | 31 | # Harness Working Guide<br>## Scope<br>## Validation |
| `harness/mini-harness/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `health-agent/AGENTS.md` | Project/root guide | Rich | 25 | # Repository Notes<br>## Working Rules<br>## Validation |
| `ikun/.github/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/Chinese-iKUN/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/CXK_IKUN_Dataset/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-2.5B/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-basics/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-call/AGENTS.md` | Nested package/subproject guide | Rich | 21 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `ikun/ikun-deploy/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-Distill/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-DPO/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-GRPO/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-MoE/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-mouse/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-pretrain/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-Reason/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-tokenizer/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun-ui/AGENTS.md` | Nested package/subproject guide | Medium | 18 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `ikun/ikun-V/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ikun/ikun/AGENTS.md` | Nested package/subproject guide | Thin | 7 | # Repository Guidelines |
| `ikun/ji/AGENTS.md` | Nested package/subproject guide | Medium | 17 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `ikun/Jilehe/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ios/embodied-agent/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ios/unitree_mujoco/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `ios/unitree_sdk2_python/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `kevinten10.github.io/next-portfolio/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `kimi/Kimi_Agent_二手智能定价/app/AGENTS.md` | Nested package/subproject guide | Rich | 33 | # AI Secondhand Pricing Maintenance Guide<br>## Project State<br>## Before Editing |
| `langchain/ai-agent-langgraph/AGENTS.md` | Nested package/subproject guide | Rich | 33 | # AI Agent LangGraph Maintenance Guide<br>## Project State<br>## Before Editing |
| `law-agent/AGENTS.md` | Project/root guide | Rich | 27 | # Law Agent Maintenance Guide<br>## Project State<br>## Before Editing |
| `leetcode/AGENTS.md` | Project/root guide | Medium | 18 | # Repository Notes<br>## Working Rules<br>## Checks |
| `Life/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `Lifecat/AGENTS.md` | Project/root guide | Rich | 30 | # Lifecat Maintenance Guide<br>## Project State<br>## Before Editing |
| `maichong/AGENTS.md` | Project/root guide | Rich | 56 | # Repository Guidelines<br>## Project Structure & Module Organization<br>## Build, Test, and Development Commands |
| `mcp-3d-gen/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `mcp-content-styles/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `mcp-ecosystem/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `mcp-ffmpeg/AGENTS.md` | Project/root guide | Thin | 6 | # Repository Guidelines |
| `mcp-http-proxy/AGENTS.md` | Project/root guide | Rich | 32 | # MCP HTTP Proxy Maintenance Guide<br>## Project State<br>## Before Editing |
| `minimind/AGENTS.md` | Project/root guide | Rich | 22 | # Repository Notes<br>## Working Rules<br>## Relevant Commands |
| `minimind/website/AGENTS.md` | Nested package/subproject guide | Thin | 5 | # This is NOT the Next.js you know |
| `money-agent/AGENTS.md` | Project/root guide | Rich | 49 | # Repository Guidelines<br>## Project Structure<br>## Commands |
| `name-agent/AGENTS.md` | Project/root guide | Rich | 30 | # Name Agent Working Guide<br>## Local Rules<br>## Commands |
| `open-octopus/.github/AGENTS.md` | Nested package/subproject guide | Thin | 7 | # Repository Guidelines |
| `open-octopus/casa/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `open-octopus/community/AGENTS.md` | Nested package/subproject guide | Thin | 7 | # Repository Guidelines |
| `open-octopus/coral/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `open-octopus/homebrew-tap/AGENTS.md` | Nested package/subproject guide | Thin | 7 | # Repository Guidelines |
| `open-octopus/mcp-discord/AGENTS.md` | Nested package/subproject guide | Rich | 22 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `open-octopus/openoctopus-ansible/AGENTS.md` | Nested package/subproject guide | Rich | 31 | # OpenOctopus Ansible Maintenance Guide<br>## Project State<br>## Before Editing |
| `open-octopus/openoctopus.club/AGENTS.md` | Nested package/subproject guide | Rich | 32 | # openoctopus.club Maintenance Guide<br>## Project State<br>## Before Editing |
| `open-octopus/realmhub/AGENTS.md` | Nested package/subproject guide | Rich | 22 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `open-octopus/realms/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `open-octopus/reef-bot/AGENTS.md` | Nested package/subproject guide | Rich | 24 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `open-octopus/soul-gallery/AGENTS.md` | Nested package/subproject guide | Thin | 6 | # Repository Guidelines |
| `openclawpool/AGENTS.md` | Project/root guide | Thin | 5 | # This is NOT the Next.js you know |
| `Papers/AGENTS.md` | Project/root guide | Medium | 18 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `pua-cli/AGENTS.md` | Project/root guide | Rich | 22 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `sb/AGENTS.md` | Project/root guide | Rich | 26 | # S.B. Smart Brain Maintenance Guide<br>## Project State<br>## Before Editing |
| `trip-ava/AGENTS.md` | Project/root guide | Rich | 28 | # Trip-AVA Maintenance Guide<br>## Project State<br>## Before Editing |
| `trip-map/AGENTS.md` | Project/root guide | Rich | 23 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `vedio-agent/AGENTS.md` | Project/root guide | Rich | 36 | # Repository Guidelines<br>## Project Structure<br>## Commands |
| `vietnam-agent/AGENTS.md` | Project/root guide | Medium | 19 | # Repository Guidelines<br>## Project Shape<br>## Commands |
| `yuanjie-ar-mp/AGENTS.md` | Project/root guide | Rich | 30 | # Yuanjie AR Mini Program Maintenance Guide<br>## Project State<br>## Before Editing |
| `yuanjie/AGENTS.md` | Project/root guide | Rich | 29 | # Yuanjie Working Guide<br>## Local Rules<br>## Verification |

## Recommended Cleanup Order

1. Ignore temporary `.claude/worktrees` copies unless actively debugging that worktree.
2. Review rich guides for active P0 projects first: `trip-map`, `ai-chat-chrome`, `brag`, `health-agent`, `kevinten10.github.io`, `maichong`, `name-agent`, `dog-agent`.
3. For thin active product guides, expand only when a project is selected for real work.
4. For CLAUDE-only active projects, migrate key persistent instructions into `AGENTS.md`; keep historical Claude-specific notes in `CLAUDE.md`.
5. For reference/archive repos, keep a short status-oriented `AGENTS.md`; do not add build/test instructions that are not real.

## Validation

Refresh this index with a filesystem scan after adding, renaming, or migrating agent instructions.

Safe scan commands:

```bash
find /Users/kevinten/projects -path '*/.git' -prune -o -path '*/node_modules' -prune -o -iname 'AGENTS.md' -print | sort
find /Users/kevinten/projects -path '*/.git' -prune -o -path '*/node_modules' -prune -o -iname 'CLAUDE.md' -print | sort
```
