# Agent 指令最佳实践框架

这个框架把本仓库的真实语料转化为可审查、可迁移、可持续优化的 `AGENTS.md` / `CLAUDE.md` 评估体系。

## 语料显示的高价值章节

本地归档中反复出现并且最有用的章节包括：

- Project overview / Project state
- Commands / Useful commands
- Architecture / Project structure
- Environment
- Before editing
- Validation
- Deployment notes
- Common pitfalls / Known hazards

这些章节之所以有价值，是因为它们回答了代理动手前必须知道的问题：

- 这是活跃产品、库、参考资料、实验还是归档？
- 哪些目录、生成文件、迁移或外部系统有边界？
- 真实安装、开发、测试、构建、部署命令是什么？
- 最小但足够的验证方式是什么？
- 什么绝不能打印、提交、回滚或部署？

## 文件角色分工

### `AGENTS.md`

作为跨工具项目契约，适合记录：

- 项目目的和当前状态
- 目录结构和边界
- 真实 setup/dev/build/lint/test/deploy 命令
- secrets、dirty worktree、生成文件、迁移、部署等安全规则
- 验证要求
- 指向更深文档或 skill 的链接

### `CLAUDE.md`

作为 Claude Code 专属入口，适合记录：

- `@AGENTS.md` 导入
- Claude slash commands
- Claude-only MCP 工具名
- Claude memory 或 `/memory` 工作流
- 本地 Claude 会话约定
- 暂时还不适合迁移到跨工具规则的历史经验

### Codex Skill

作为可复用工作流，适合承载：

- 发布 checklist
- 项目 triage
- 浏览器 QA
- 安全审查
- 迁移流程
- 工具安装和登录盘点

## 推荐 AGENTS.md 结构

```md
# Repository Guidelines

## Project State

说明这是活跃产品、库、参考仓库、归档、生成 demo 还是实验。

## Structure

列出重要目录，并解释边界。

## Commands

- `...`: 安装或同步依赖
- `...`: 本地开发
- `...`: lint/test/typecheck/build
- `...`: 部署或预览，如果适用

## Environment

只列变量名和模板文件路径，不包含值。

## Working Rules

- 编辑前检查 git 状态。
- 不回滚 unrelated user changes。
- 相关时保持生成文件、schema、迁移同步。
- 优先复用现有模式，不轻易发明新抽象。

## Verification

按 docs、backend、frontend、database、deployment 等变更类型列最小有效检查。

## Known Hazards

记录易错 API、脆弱迁移、平台限制、生成代码边界和私有数据规则。
```

## 评分 Rubric

每项 0-2 分。

| 维度 | 0 分 | 1 分 | 2 分 |
| --- | --- | --- | --- |
| Scope | 无项目状态 | 只写了大概用途 | 清楚说明状态和边界 |
| Commands | 缺失或疑似编造 | 有命令但用途不清 | 真实命令且解释用途 |
| Verification | 缺失 | 泛泛而谈 | 按变更类型给出窄验证 |
| Safety | 缺失 | 泛泛提醒 secrets | 明确 secrets、git、破坏性操作规则 |
| Architecture | 缺失 | 只有目录列表 | 解释关键边界和所有权 |
| Maintenance | 无更新规则 | 有人工备注 | 说明何时更新指令 |
| Tool Fit | 假设只有一种工具 | 提到多工具 | 清楚区分 AGENTS、CLAUDE、skill |

解释：

- 0-5：风险较高，基本只是装饰性文档。
- 6-9：可用，但容易漏上下文。
- 10-14：足够支撑常规 agent 工作。

## 反模式

- 把所有项目命令集中到全局 `AGENTS.md`。
- 为归档项目补造测试或部署命令。
- 在公开指令里写 `.env` 值、token、cookie、私钥或个人路径。
- 把 Claude-only MCP 工具名写成跨工具要求。
- 把一次性任务计划写进长期项目指令。
- 用“运行测试”替代具体可执行命令。
- README、`AGENTS.md`、`CLAUDE.md` 三份文档复制同一大段内容，最终互相漂移。

## 持续优化循环

真实 agent 会话结束后，如果出现以下情况，就应该更新指令层：

- 代理必须重新从 package scripts 或 README 找命令。
- 代理使用了错误验证方式。
- 代理误判项目是否活跃。
- 代理差点触碰 secrets、生成文件、迁移或 unrelated user changes。
- 同一 checklist 在多个项目重复出现，适合模板化或 skill 化。

保持短而准。好的指令文件减少重复发现成本，但不应该变成第二份完整 README。
