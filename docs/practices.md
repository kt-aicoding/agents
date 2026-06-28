# AGENTS.md 实践模式

本文从本仓库归档的真实 `AGENTS.md` / `CLAUDE.md` 语料中提炼可复用模式。完整评分标准见 `docs/best-practice-framework.md`，外部资料依据见 `docs/external-research.md`。

## 1. 使用分层指令

有效的 agent 指令通常是分层的：

- 工作区 `AGENTS.md`：全局安全规则、语言偏好、工具偏好、workspace 索引入口。
- 项目 `AGENTS.md`：项目状态、目录结构、真实命令、风险、验证方式、部署说明。
- 子包或模块 `AGENTS.md`：局部框架规则、包级命令、生成文件边界。
- `CLAUDE.md`：Claude Code 专属上下文、历史迁移来源或 `@AGENTS.md` 导入入口。
- Skill：跨项目重复出现、步骤较长、需要脚本或参考资料的工作流。

核心判断：越稳定、越跨工具，越适合放进 `AGENTS.md`；越工具特定，越应留在工具自己的入口里；越长、越流程化，越应做成 skill。

## 2. 根规则要短且稳定

根级规则应该覆盖长期有效的工作方式：

- 最近指令文件的读取顺序
- secrets 处理规则
- dirty worktree 保护
- workspace inventory 入口
- 验证默认原则
- 语言和沟通偏好

根规则不应包含某一个项目的包管理器、部署目标、数据库结构或临时任务计划。

## 3. 命令要靠近代码

项目级指令应记录真实存在的命令，并说明用途：

```md
## Commands

- `pnpm install`: 安装依赖。
- `pnpm dev`: 启动本地开发服务。
- `pnpm build`: 生产构建检查。
- `pnpm test`: 运行测试。
```

不要为参考仓库或历史归档仓库编造测试、构建、部署命令。薄指令比假命令更安全。

## 4. 明确项目状态

很多仓库是实验、参考资料、归档、生成 demo 或低频维护项目。好的指令会直接说明状态：

```md
## Project State

This repository is a reference archive. Preserve existing notes and do not add build or deployment automation unless the project becomes active again.
```

这能防止代理把归档仓库误当成活跃产品，进而乱加自动化、依赖或部署流程。

## 5. 活跃项目需要编辑前检查

活跃产品的 `AGENTS.md` 应包含简短 preflight：

- 读取 `README.md`
- 检查 package scripts、lockfile、构建配置
- 运行 `git status --short`
- 不回滚 unrelated user changes
- 只查看 env 模板和变量名，不读取或打印 secrets 值

## 6. 验证要窄而真实

验证应匹配修改类型：

- UI 项目：包内 lint/build/test；视觉或交互变更要做浏览器验证。
- Python/uv 项目：`uv sync`、`uv run ...` 或项目记录的测试命令。
- Go 项目：`go test ./...`。
- Maven 项目：`mvn test`。
- Docs-only 修改：检查标题、链接、路径、示例和敏感内容。

不要用过窄的检查证明过宽的完成条件。

## 7. PaaS 和云服务优先 CLI

对可重复的云平台、仓库和部署操作，优先 CLI，而不是常驻 provider MCP：

- GitHub: `gh`
- Vercel: `vercel`
- Supabase: `supabase`
- CloudBase: `tcb`
- Cloudflare: `wrangler`
- Netlify: `netlify`
- Fly: `flyctl`

MCP 更适合有明显 agent-native 价值的场景，例如浏览器自动化、文档检索、跨应用上下文或需要结构化交互的设计工具。

## 8. 薄指令是有效形态

短 `AGENTS.md` 适用于：

- reference/archive 仓库
- 无活跃运行时
- 主要保存历史资料
- 没有可确认构建或测试命令

薄指令的问题不在于短，而在于隐藏了真实风险或遗漏了活跃项目的必要命令。

## 9. 不把临时 worktree 当权威来源

`.claude/worktrees/.../AGENTS.md` 通常是临时工作树快照，不应作为 canonical source。归档、统计和迁移时应排除，除非正在调试该 worktree。

## 10. 稳定 Claude 经验迁移到 AGENTS.md

当满足这些条件时，把 `CLAUDE.md` 中的稳定内容迁移到 `AGENTS.md`：

- 项目仍然活跃
- Codex 或其他 coding agents 会经常处理该项目
- 内容不是 Claude Code 专属
- 内容描述项目事实、真实命令、验证方式或安全边界

Claude 专属 slash command、memory 行为、Claude-only MCP 名称和个人偏好应留在 `CLAUDE.md` 或本地文件。

## 11. 推荐 CLAUDE.md 复用 AGENTS.md

如果项目已经有 `AGENTS.md`，推荐让 `CLAUDE.md` 导入它：

```md
@AGENTS.md

## Claude Code

- 在涉及大范围重构时先进入 plan mode。
- Claude-only MCP 或 slash command 写在这里。
```

这样可以减少双份维护，避免 `AGENTS.md` 与 `CLAUDE.md` 内容漂移。

## 12. 重复流程应转为 skill

同一 checklist 多次出现在不同项目中时，应考虑做成 Codex skill：

- 发布流程
- 项目清点和 triage
- 浏览器 QA
- 安全审查
- `CLAUDE.md` 到 `AGENTS.md` 迁移
- CLI/MCP/skill 工具盘点

项目 `AGENTS.md` 只需要说明何时使用该 skill，以及本项目的边界和例外。

## 13. 从真实失败中更新指令

指令文件应在以下情况更新：

- 代理反复重新查找同一命令
- 代理误判项目状态
- 代理使用了错误验证方式
- 代理差点触碰 secrets、生成文件、迁移或 unrelated user changes
- 某个流程在多个项目中重复出现

避免添加没有来源的泛泛规则。好的 `AGENTS.md` 是压缩过的项目操作知识，不是第二份 README。
