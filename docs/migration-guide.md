# CLAUDE.md 到 AGENTS.md 迁移指南

当项目已有有价值的 `CLAUDE.md`，但缺少同级 `AGENTS.md`，或希望让 Codex、Gemini CLI 等其他工具复用同一套稳定规则时，使用本指南。

## 迁移目标

迁移不是简单复制。目标是把稳定、跨工具、项目级的事实沉淀到 `AGENTS.md`，同时让 `CLAUDE.md` 保留 Claude Code 专属内容。

推荐最终形态：

```md
@AGENTS.md

## Claude Code

- Claude-only slash commands、MCP 名称或 memory 约定写在这里。
- 只保留其他工具不应继承的内容。
```

## 迁移到 AGENTS.md 的内容

- 项目结构
- build/test/dev 命令
- 包管理器和 lockfile 约定
- 部署目标和预览方式
- 环境变量名称和模板文件
- 验证要求
- 已知风险和常见坑
- 项目状态：active、maintenance、reference、archive、experiment
- 可复用 workflow 的入口，例如应该使用哪个 skill

## 继续留在 CLAUDE.md 的内容

- Claude-specific slash commands
- Claude-only MCP 工具名
- Claude memory 或 `/memory` 工作流
- Claude Code plan mode 等工具行为偏好
- conversation history
- 临时规划笔记
- 个人 scratch instructions

## 不应公开迁移的内容

- `CLAUDE.local.md`
- auto memory 里的个人发现
- `.env` 值、token、cookie、私钥
- 本地账号、私有 URL、私有测试数据
- 一次性任务计划或已经过期的调试记录

## 建议流程

1. 读取 `CLAUDE.md`、`README.md`、package scripts、部署配置和已有 docs。
2. 标注内容类型：跨工具项目事实、Claude 专属、历史信息、临时计划、敏感信息。
3. 只把稳定项目事实迁移到 `AGENTS.md`。
4. 在 `CLAUDE.md` 顶部使用 `@AGENTS.md` 导入通用规则。
5. 将 Claude 专属内容放在 `## Claude Code` 下。
6. 如果某个 checklist 很长且跨项目重复，把它做成 skill，不要复制进每个仓库。
7. 运行 docs-only 验证和敏感扫描。

## Minimal AGENTS.md 模板

```md
# Repository Guidelines

## Project State

Describe whether this is an active product, platform, reference, archive, generated demo, or experiment.

## Structure

- `src/`: ...
- `docs/`: ...

## Commands

- `...`: local development
- `...`: build/test/lint

## Environment

List variable names and template paths only. Do not include values.

## Editing Rules

- Keep project-specific conventions local.
- Do not print or commit secrets.
- Preserve unrelated user changes.

## Verification

Describe the smallest meaningful check by change type.
```

## 迁移优先级

优先迁移：

- 活跃项目
- Codex 或其他 coding agents 经常处理的项目
- `CLAUDE.md` 已包含真实命令、部署、验证、安全边界的项目
- 当前 agent 经常误判或重复查找信息的项目

暂缓迁移：

- 历史归档
- 参考资料
- 无活跃运行时
- 只有 Claude 临时会话笔记的项目

不要为了“覆盖率”机械迁移所有历史 `CLAUDE.md`。
