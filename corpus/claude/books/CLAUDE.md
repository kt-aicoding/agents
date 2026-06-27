# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **编神纪 (CodeGodChronicles)** — an open-source Chinese web novel that blends xianxia/cultivation fiction with computer science concepts. The story follows 叶辰 (Ye Chen), a data labeling worker with an ancient sealed code fragment, as he navigates a world where cultivation is programming and combat techniques are algorithms.

## Repository Structure

The repo contains **two parallel directory trees** for the same project:

- **`编神纪/`** — Original working drafts (Chinese directory names). Contains outlines, chapters, and art prompts. The `_private/` content here is gitignored in the public version.
- **`CodeGodChronicles/`** — Public-facing GitHub repository structure (English directory names). This is the canonical version for publishing.

### CodeGodChronicles layout:
- `novel/vol-XX_<name>/` — Chapter markdown files (the actual story text)
- `worldbuilding/` — World lore: `overview.md`, `cultivation-system.md`, `combat-system.md`, `glossary.md`, plus subdirs for `characters/`, `factions/`, `locations/`
- `art/` — Cover art and illustration prompt files
- `_private/` — Detailed outlines and strategy docs (gitignored)
- `community/` — Fan fiction and community-submitted spells (placeholder)

## Key World-Building Concepts

When writing or editing content, maintain consistency with these core mappings:

| 修炼概念 | CS概念 |
|---------|--------|
| 灵力 (spiritual power) | 算力 (computing power) |
| 丹田 (dantian) | 内核 (Kernel) |
| 经脉 (meridians) | 总线 (Bus) |
| 神识 (divine sense) | 线程 (Thread) |
| 术式 (techniques) | 程序/函数 (Program/Function) |

Cultivation ranks: 码农境 → 调试境 → 重构境 → 架构境 → 编译境 → 内核境 → 根权境 → 造物境(传说)

## Commit Message Convention

Uses conventional commits with Chinese scope descriptions:

```
<type>(<scope>): <description>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `chore`, `community`

Example: `feat(卷一): 新增第四章正文`

## Writing Guidelines

- All novel content is in Markdown
- Chapter files use naming pattern: `ch-XX_<title>.md`
- Draft files (`*.draft.md`) and `_private/` dirs are gitignored
- License: CC BY-NC-SA 4.0 for prose, MIT for any tool/website code
- Current progress: Volume 1, 3 of 18 chapters published (~19K words of ~1M planned)
