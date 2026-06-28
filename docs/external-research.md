# 外部资料研究笔记

研究日期：2026-06-28。

本文记录用于补充本仓库实践总结的官方或 primary sources。更新最佳实践时，优先使用官方资料；如果是推论，必须明确标注为“本仓库结论”。

## Codex 与 AGENTS.md

来源：[OpenAI Developers: Custom instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)

官方事实：

- Codex 会在开始工作前读取 `AGENTS.md`。
- Codex 的指令链分为 global scope 和 project scope。global scope 默认来自 `~/.codex/AGENTS.md`，也支持 `AGENTS.override.md`。
- Project scope 会从项目根目录向当前工作目录逐层读取，每层最多读取一个指令文件。
- 同一目录中 `AGENTS.override.md` 优先于 `AGENTS.md`。
- 更靠近当前工作目录的指令出现在合并提示词后面，因此可以覆盖更上层的指导。
- Codex 默认会在 `project_doc_max_bytes` 限制内加载项目指令；官方文档当前给出的默认值是 32 KiB。
- Codex 支持通过 `project_doc_fallback_filenames` 配置额外的项目指令文件名。

本仓库结论：

- `AGENTS.md` 应作为跨工具、跨代理的默认项目契约。
- 根级 `AGENTS.md` 应短而稳定；子目录指令用于局部例外。
- 如果一个项目指令过长，应拆成更近的子目录指令、普通文档或 skill，而不是继续堆到根文件。
- `AGENTS.override.md` 更适合临时覆盖，不适合作为公开最佳实践模板的默认文件。

## AGENTS.md 开放格式

来源：[AGENTS.md](https://agents.md/)

官方事实：

- `AGENTS.md` 被描述为“给 agents 看的 README”：为编码代理提供构建步骤、测试、约定和上下文。
- README 主要面向人类，`AGENTS.md` 用来承载会让 README 变嘈杂的 agent-focused guidance。
- 推荐内容包括项目概览、构建和测试命令、代码风格、测试说明和安全注意事项。
- 对大型 monorepo，可在子项目中放置嵌套 `AGENTS.md`。
- `AGENTS.md` 是普通 Markdown，没有必填字段。

本仓库结论：

- 不要为了满足模板而编造章节；普通 Markdown 足够。
- 最有价值的内容是“代理执行任务前必须知道的事实”：真实命令、边界、验证、风险。
- README 和 `AGENTS.md` 应互补：README 解释项目给人看，`AGENTS.md` 指导代理如何安全改动。

## Codex Skills

来源：[OpenAI Developers: Agent Skills](https://developers.openai.com/codex/skills)

官方事实：

- Skill 用来给 Codex 增加 task-specific capabilities。
- 一个 skill 是包含 `SKILL.md` 的目录，可选包含 `scripts/`、`references/`、`assets/` 等。
- Skills 使用 progressive disclosure：Codex 初始只看到 name、description、path；选择 skill 后才读取完整 `SKILL.md`。
- Skills 可以显式调用，也可以由 Codex 根据 description 隐式选择。
- OpenAI 文档区分 skills 和 plugins：skill 是 workflow 的作者格式，plugin 是可安装分发单元。

本仓库结论：

- 当一个流程是跨项目、可重复、步骤较长的操作时，应沉淀为 skill。
- `AGENTS.md` 只需要写“什么时候使用哪个 skill”或本项目特有边界，不应复制完整长流程。
- Skill 的 description 要清楚写触发条件和不适用场景，避免误触发。

## Claude Code 与 CLAUDE.md

来源：[Anthropic Claude Code Docs: Memory](https://docs.anthropic.com/en/docs/claude-code/memory)

官方事实：

- Claude Code 读取 `CLAUDE.md`，而不是直接读取 `AGENTS.md`。
- 如果仓库已经使用 `AGENTS.md`，Anthropic 建议创建 `CLAUDE.md` 并用 `@AGENTS.md` 导入，必要时再追加 Claude-specific instructions。
- `CLAUDE.local.md` 可用于个人本地偏好，应加入 `.gitignore`。
- Claude Code 会沿目录层级加载 `CLAUDE.md` / `CLAUDE.local.md`；更靠近启动目录的内容更晚进入上下文。
- `.claude/rules/` 可用于大型项目的模块化规则。
- 自动 memory 和 `CLAUDE.md` 是不同机制：`CLAUDE.md` 适合用户写的规则，auto memory 适合 Claude 发现的模式。
- 官方文档提醒，过长或模糊的 `CLAUDE.md` 会降低遵循效果。

本仓库结论：

- 跨工具稳定规则优先写入 `AGENTS.md`。
- Claude 专属命令、memory 行为、Claude-only MCP 名称、`/memory` 工作流可以保留在 `CLAUDE.md`。
- 推荐迁移策略：`CLAUDE.md` 使用 `@AGENTS.md` 导入通用规则，再追加 Claude 专属段落。
- 不应把 `CLAUDE.local.md`、自动 memory 或个人偏好归档到公开语料。

## Gemini CLI 与 GEMINI.md

来源：[Gemini CLI: Provide Context with GEMINI.md Files](https://google-gemini.github.io/gemini-cli/docs/cli/gemini-md.html)

官方事实：

- Gemini CLI 默认使用 `GEMINI.md` 作为 context file。
- Gemini CLI 会按层级加载 global、project/ancestor、sub-directory context files。
- `/memory show` 可查看当前合并后的上下文，`/memory refresh` 可刷新，`/memory add` 可追加到 global context。
- `@file.md` import 可用于模块化 context。
- `settings.json` 中的 `context.fileName` 可以配置其他文件名，例如 `AGENTS.md`。

本仓库结论：

- 分层指令不是 Codex 独有机制，主流 coding agents 都在收敛到“全局 + 项目 + 子目录”的上下文结构。
- 如果希望 Gemini CLI 复用本仓库规则，可以配置 `context.fileName` 读取 `AGENTS.md`，避免维护 `GEMINI.md` 和 `AGENTS.md` 两份内容。

## 工作结论

本仓库后续优化以这套分工为准：

- `AGENTS.md`：跨工具项目契约，记录稳定事实、真实命令、验证、安全边界。
- `CLAUDE.md`：Claude Code 专属入口，推荐 `@AGENTS.md` 导入通用规则后追加 Claude-only 内容。
- `GEMINI.md`：可通过 Gemini CLI 配置复用 `AGENTS.md`；仅在需要 Gemini-specific 内容时单独维护。
- Codex skills：承载跨项目重复长流程。
- README：面向人类解释项目目标、结构和如何使用本知识库。
- `docs/`：承载 rubric、迁移指南、研究笔记和模板。
