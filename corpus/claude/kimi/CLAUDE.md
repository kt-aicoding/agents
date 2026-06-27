# Kimi AI Ideas 项目

> 管理从 kimi.com 生成的 AI 产品项目，统一部署到 GitHub + Vercel

## 项目结构

```
/Users/kevinten/projects/kimi/
├── CLAUDE.md          # 本文件，项目规则
├── prompts.md         # 18 个 Kimi 提示词 + 进度跟踪
└── Kimi_Agent_*/      # Kimi 生成的项目（每个一个目录）
```

## 部署规则

1. **前端**：Vercel（连接 GitHub 自动部署）
2. **后端**：Supabase（需数据库/认证）或 CloudBase（国内场景）
3. **AI 能力**：GLM Coding Plan（glm-5.1，通过 ANTHROPIC_AUTH_TOKEN 调用）
4. **代码托管**：`gh` CLI → `ai-ideas-lab` GitHub 组织
5. **全流程**：使用 `/kimi-project-launch` skill 执行

## 仓库名规范

`ai-<英文关键词>`，短横线分隔，全部在 `ai-ideas-lab` 组织下。

## 进度跟踪

所有项目进度在 `prompts.md` 中维护。
