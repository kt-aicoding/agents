# Agents Knowledge Base Optimization Goal

## Outcome

全面探索并优化 `/Users/kevinten/projects/agents`，使其成为中文优先、可公开分享、基于真实 `AGENTS.md` / `CLAUDE.md` 实践并结合官方资料的 AI 编程代理指令最佳实践知识库。

最终仓库应包含清晰 README、图示、实践总结、外部研究、迁移指南、评分 rubric、可复用模板、敏感数据检查记录，并已提交推送到 `kt-aicoding/agents`。

## Context

- Workdir: `/Users/kevinten/projects/agents`
- Remote: `https://github.com/kt-aicoding/agents`
- Source workspace: `/Users/kevinten/projects`

恢复或上下文压缩后必须先读：

1. `README.md`
2. `AGENTS.md`
3. `docs/practices.md`
4. `docs/best-practice-framework.md`
5. `docs/external-research.md`
6. `docs/migration-guide.md`
7. `manifests/files.json`
8. `git status --short --branch`
9. `git log --oneline -5`

## Scope

In scope:

- README 中文表达、信息架构、图示和入门路径
- `docs/` 下最佳实践、外部研究、迁移指南、模板和 rubric
- `corpus/agents` 与 `corpus/claude` 的模式分析
- `manifests/` 与 corpus 一致性校验
- 当前官方资料补充：Codex `AGENTS.md`、Codex Skills、Claude Code memory、Gemini CLI context、agents.md format
- 敏感信息扫描和公开分享安全检查

Out of scope unless approved:

- 删除或大规模改写 corpus 原文
- 暴露、复制、打印 secrets、`.env` 值、token、cookie、私钥
- 修改 unrelated 项目
- 强制改写 git history
- 生产部署、付费操作、账号权限变更

## Constraints

1. 中文优先，保留必要英文术语、文件名和官方链接。
2. 结论优先来自真实 corpus，再用官方资料补齐机制和边界。
3. 不编造工具行为；外部资料要记录来源 URL、日期和结论。
4. README 面向公开读者，docs 面向深入维护者。
5. Mermaid 图示必须能在 GitHub Markdown 直接渲染。
6. 修改前检查 dirty worktree，只提交目标相关文件。
7. 不输出、不提交敏感值；只允许记录变量名、平台名或脱敏结论。

## Milestones

1. Inventory: 盘点 README、docs、corpus、manifest 的现状和缺口。
2. Research: 搜索并阅读当前官方资料，更新 `docs/external-research.md`。
3. Synthesis: 从 corpus 提炼高频章节、有效模式、反模式和评分 rubric。
4. Optimization: 优化 README、图示、模板、实践文档和迁移指南。
5. Verification: 完成 Markdown、manifest、敏感扫描、远端同步检查。
6. Audit: 做完成审计，确认每个要求都有当前证据。

## Per-Item Loop

1. 明确当前优化对象：README、某个 docs 文件、模板、manifest 或研究项。
2. 读取相关本地文件和必要官方资料。
3. 分析目标读者、缺口、重复、冲突和公开分享风险。
4. 做最小完整修改。
5. 运行验证。
6. 只提交相关文件。
7. 在最终报告中记录变更、验证结果、commit 和遗留事项。

## Done When

- README 清楚说明项目目标、目录结构、核心原则、读取顺序、最佳实践工作流、维护方式和参考资料。
- README 至少包含 2-3 个可渲染 Mermaid 图示。
- `docs/practices.md`、`docs/best-practice-framework.md`、`docs/external-research.md`、`docs/migration-guide.md` 一致且无明显冲突。
- 明确说明 `AGENTS.md`、`CLAUDE.md`、Codex skills 的分工。
- 外部研究包含官方来源链接，并区分事实、推论和本仓库实践结论。
- `manifests/files.json` 与 corpus 路径、数量、哈希一致。
- 敏感扫描通过，无真实 secret 泄露。
- 所有目标相关修改已 commit 并 push 到 `origin/main`。
- `git status --short --branch` 显示本仓库干净并同步远端。

## Verification

至少运行：

```bash
git status --short --branch
git diff --check
gitleaks dir . --no-banner --redact
git log --oneline -5
gh repo view kt-aicoding/agents --json url,visibility,defaultBranchRef
```

还要运行 manifest 一致性检查：确认 `manifests/files.json` 中每个 `archive_path` 存在，sha256 与当前文件一致，统计数量正确。

还要运行敏感模式扫描：覆盖 provider token、GitHub token、AWS access key、JWT、长 secret 赋值等常见形态。扫描报告不得输出原始值；如果命中文档里的扫描规则、普通英文说明或占位符，应明确标为 false positive。

## If Blocked

- 如果 web research 失败，记录失败 URL/查询、时间、原因，并继续本地可完成工作。
- 如果扫描发现疑似 secret，不打印值；只报告路径、行号、类型和修复动作。
- 如果 push 失败，保留本地 commit，记录脱敏错误、命令和下一步。
- 如果遇到 unrelated dirty worktree，不回滚；只绕开或记录。
- 只有当没有任何安全本地工作可继续，且同一外部阻塞反复出现时，才标记 blocked。

## Completion Audit

完成前逐条核对：

- [ ] 最新上下文下重读了关键文件。
- [ ] 所有 in-scope 项都有完成、无需处理或外部阻塞状态。
- [ ] 每个完成项都有当前验证证据。
- [ ] 敏感扫描通过。
- [ ] manifest 校验通过。
- [ ] 所有提交已推送，远端 ref 匹配。
- [ ] 最终报告包含变更摘要、commit、验证命令、阻塞和遗留事项。
