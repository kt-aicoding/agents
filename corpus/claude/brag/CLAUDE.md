# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

Brag 是一个综合性技术经验和业务经验知识库，专注于 AI 技术、系统架构和业务解决方案的实战经验记录。项目采用模块化组织结构，涵盖从 AI Agent 开发到系统架构设计的全方位技术实践。

## 项目结构

### 核心目录

```
brag/
├── ai_agent/          # AI Agent 开发与多 Agent 协作
├── ai_rag/            # RAG 检索增强生成系统
├── ai_mcp/            # MCP 协议实现与工具矩阵（14+ MCP 服务器）
├── ai_skills/         # Claude Skills 开发（34+ 个技能分类）
├── ai_tools/          # AI 工具集（ai-tools 项目）
├── ai_chrome/         # Chrome AI 插件开发
├── ai_coding/         # AI 编程辅助工具
├── ai_workflow/       # AI 工作流编排
├── ai_claude_code/    # Claude Code 使用经验
├── ai_cursor/         # Cursor IDE 使用经验
├── ai_prompt/         # Prompt 工程实践
├── 技术方案/           # 具体技术解决方案
├── AI创意/            # AI 创意项目与比赛
└── 项目管理/           # 项目管理实践
```

### AI 技术栈

- **Agent 框架**：AgentScope、LangGraph、CrewAI、AutoGen
- **RAG 平台**：Dify、Flowise、LlamaIndex
- **协议标准**：MCP (Model Context Protocol)
- **开发语言**：Python（AI 项目为主）、TypeScript/JavaScript（前端/插件）、Java（企业级 Agent）

## 开发规范

### 文档命名规范

采用日期前缀 + 描述性名称的格式：
```
YYYY-MM-DD-描述性名称.md
```

### 标签系统

使用 `#标签` 进行内容分类：

**AI 技术**：`#ai` `#agent` `#rag` `#llm` `#prompt` `#mcp`
**系统架构**：`#architecture` `#microservices` `#performance`
**业务技术**：`#business` `#frontend` `#backend`
**工具平台**：`#devops` `#docker` `#ide`

### 文档质量标准

每个文档应包含：
- 清晰的标题和背景说明
- 详细的技术实现过程
- 实际效果数据或验证结果
- 经验教训和最佳实践总结

避免内容：
- 纯理论探讨（需结合实战）
- 过度简化或缺乏细节
- 商业敏感信息

## 常用开发命令

### ai-tools 项目

```bash
cd ai_tools/ai-tools/website
npm run dev                # 开发服务器
npm run build              # 生产构建
npm run preview            # 预览生产构建
npm run lint               # 代码检查（自动修复）
npm run format             # 代码格式化
npm run test               # 运行测试
npm run test:coverage      # 运行测试并生成覆盖率报告
```

### MCP 相关项目

```bash
# llm-mcp-http-helper
cd ai_mcp/llm-mcp-http-helper
npm run build              # TypeScript 编译
npm run start              # 启动生产服务
npm run dev                # 开发模式（ts-node）
npm run test               # 运行测试
npm run lint               # 代码检查
npm run clean              # 清理构建产物

# mcp-health-checker
cd ai_mcp/mcp-health-checker
npm run build              # TypeScript 编译
npm run start              # 启动生产服务
npm run dev                # 开发模式（ts-node）
npm run test               # 运行测试
npm run lint               # 代码检查
npm run clean              # 清理构建产物
```

### ai-meeting-web-next（会议助手）

```bash
cd AI创意/一站式会议助手/ai-meeting-web-next
npm run dev                # 开发服务器（http://localhost:3000）
npm run build              # 生产构建
npm run start              # 启动生产服务器
npm run lint               # 代码检查
npm run lint:fix           # 代码检查并自动修复
npm run type-check         # TypeScript 类型检查
npm run format             # 代码格式化
```

## 技术架构要点

### 1. 多语言混合架构

- **Python**：AI/ML 项目、数据处理、Agent 开发
- **TypeScript**：前端应用、VS Code 插件、Chrome 插件
- **Java**：企业级后端服务

### 2. MCP 工具矩阵

项目构建了完整的 MCP 生态，包含多个 MCP 服务器实现：
- ck-mcp: 通用工具 MCP
- db-mcp: 数据库操作 MCP
- gitlab-mcp: GitLab 集成 MCP
- llm-mcp-http-helper: MCP HTTP 通信辅助工具
- mcp-health-checker: MCP 服务健康检查
- k8s-mcp: Kubernetes 操作 MCP
- log-mcp: 日志查询 MCP
- metric-mcp: 指标监控 MCP
- team-mcp: 团队协作 MCP

### 3. Claude Skills 分类系统

34 个 Claude Skills 按领域分类：
- **后端**：Node.js、Python、Java 相关技能
- **前端**：React、Vue、NFES、XTaro 技能
- **产品**：需求分析、方案设计技能
- **工具**：Git、Docker、CI/CD 技能

### 4. 代码风格

项目统一使用 EditorConfig 配置：
- 编码：UTF-8
- 换行：LF
- 缩进：2 空格（JavaScript/TypeScript）、4 空格（Python）
- 尾部空格：trim
- Markdown 文件保留尾部空格

### 5. Node.js 引擎要求

MCP 相关 TypeScript/Node.js 项目要求：
```json
"engines": {
  "node": ">=18.0.0"
}
```

## 贡献流程

1. Fork 项目并创建特性分支
2. 按照文档规范创建或修改内容
3. 提交更改并推送到远程
4. 创建 Pull Request

### PR Review 准则

- **相关性**：内容与项目主题相关
- **质量**：包含完整的技术实现和经验总结
- **完整性**：背景、实现、效果、经验四要素齐全
- **价值**：对后续开发者有参考价值

## 项目配置

- **EditorConfig**：`.editorconfig` - 统一代码风格
- **Python 依赖**：各子项目的 `requirements.txt`
- **TypeScript 配置**：各子项目的 `tsconfig.json`
- **贡献指南**：`CONTRIBUTING.md` - 详细的贡献规范

## 特殊工具

- **Trae**：用于文档管理和计划跟踪的工具
- **MCP HTTP Helper**：简化 MCP 服务器 HTTP 通信的辅助工具
- **Health Checker**：MCP 服务健康检查工具

## MCP 服务器架构

项目的 MCP 生态包含多个独立的服务器实现，每个都是独立的 npm 包：

### 通用 MCP 服务器模式

1. **传输层**：使用 `@modelcontextprotocol/sdk` 实现 MCP 协议
2. **HTTP 桥接**：通过 Express 暴露 HTTP API（llm-mcp-http-helper）
3. **健康检查**：独立的健康检查服务（mcp-health-checker）
4. **批量执行**：支持大模型批量调用 MCP 工具

### 开发新 MCP 服务器的模板

```bash
# 基础依赖
npm install @modelcontextprotocol/sdk express cors helmet winston zod

# 开发依赖
npm install -D typescript @types/node @types/express @types/cors
npm install -D ts-node eslint jest ts-jest
```

## 技术栈详情

### 前端项目（Vue 3）
- **构建工具**：Vite 5.x
- **状态管理**：Pinia
- **路由**：Vue Router 4.x
- **UI 框架**：Tailwind CSS 3.x
- **图标**：Lucide Vue Next
- **测试**：Vitest + Vue Test Utils

### 前端项目（Next.js）
- **框架**：Next.js 14.x
- **UI 组件**：Ant Design 5.x
- **状态管理**：Zustand
- **样式**：Tailwind CSS 3.x
- **Markdown**：react-markdown + react-syntax-highlighter
- **动画**：Framer Motion

### 后端项目（Node.js/TypeScript）
- **框架**：Express 4.x
- **安全**：Helmet、CORS
- **日志**：Winston 3.x
- **验证**：Zod 3.x
- **HTTP 客户端**：Axios
- **测试**：Jest + ts-jest

## 代码质量工具

### ESLint 配置
- **Vue 项目**：eslint-plugin-vue + eslint-plugin-prettier
- **Next.js 项目**：eslint-config-next
- **TypeScript 项目**：@typescript-eslint/eslint-plugin

### Prettier 配置
- 与 Tailwind CSS 集成（prettier-plugin-tailwindcss，仅 Next.js 项目 ai-meeting-web-next）
- 自动格式化集成在构建流程中
