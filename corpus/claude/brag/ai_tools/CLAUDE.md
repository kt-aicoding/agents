# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

`ai_tools` 是一个 AI 工具知识库项目，包含核心网站 `ai-tools/website` 和相关调研文档。网站是一个 Vue 3 单页应用，用于展示和评测 30+ 款 AI 工具（IDE、Deep Research、命令行等类别），提供 SWOT 分析、定价对比和使用建议。

## 开发环境

### 核心命令

```bash
cd ai-tools/website

# 开发服务器（端口 8765）
npm run dev

# 生产构建
npm run build

# 预览构建结果（端口 8766）
npm run preview

# 代码检查（自动修复）
npm run lint

# 代码格式化
npm run format

# 运行测试
npm run test

# 测试覆盖率报告
npm run test:coverage
```

### Docker 部署

```bash
# 构建镜像
docker build -t ai-tools .

# 运行容器
docker run -p 8080:80 ai-tools
```

## 技术架构

### 技术栈

- **框架**：Vue 3.4.0（Composition API + `<script setup>`）
- **构建工具**：Vite ^5.1.0
- **路由**：Vue Router 4.2.0（Hash 模式）
- **状态管理**：Pinia 2.1.0
- **样式**：Tailwind CSS 3.4.1（深色主题）
- **图标**：Lucide Vue Next
- **测试**：Vitest 1.2.0 + jsdom
- **云同步**：Supabase JS SDK（认证、数据库、云同步）

### 目录结构

```
ai-tools/website/
├── src/
│   ├── data/           # 工具数据源（tools.js 等 12 个数据文件）
│   ├── components/     # 可复用组件（30+）
│   ├── views/          # 页面组件（懒加载）
│   ├── stores/         # Pinia stores（tools, ui, auth, gamification, achievements, community）
│   ├── router/         # Vue Router 配置
│   ├── composables/    # 组合式函数
│   ├── lib/            # Supabase 集成与同步服务
│   ├── plugins/        # Pinia 本地存储插件
│   ├── utils/          # 工具函数
│   └── main.js         # 应用入口 + SW 注册
├── public/             # 静态资源
├── dist/               # 构建输出
├── vite.config.js      # Vite 配置
├── vitest.config.js    # 测试配置
└── nginx.conf          # Nginx 配置（Docker）
```

### 关键配置

**路径别名**：`@` 指向 `src/` 目录

**代码分割**：
- `vue-vendor`：Vue、Vue Router、Pinia
- `icons`：Lucide 图标库
- 路由级懒加载，使用 Vue Router 原生 `() => import(...)` 方式

**PWA 支持**：Service Worker 在 `main.js` 中注册，监听更新和网络状态

## 数据模型

### 工具数据结构

`src/data/tools.js` 导出 `aiToolsData` 数组，每个工具对象包含：

```javascript
{
  id: 'unique-id',
  name: '工具名称',
  logo: '工具图标 URL',
  category: 'ide|deep-research|cli|...',     // 主分类
  subcategory: '细分分类',
  developer: '开发者',
  versions: [{ type, pricing, models, link }],
  freeQuota: '免费额度说明',
  contextWindow: '上下文窗口',
  chineseSupport: 1-5,                       // 中文支持评分
  pros: ['优势列表'],
  cons: ['劣势列表'],
  bestFor: '适用场景',
  funRanking: '夯|夯夯|...',                  // 有趣排名
  personalExperience: {
    rating: 1-5,
    insights: '使用心得',
    pitfalls: ['避坑指南']
  },
  swot: { S, W, O, T },
  tags: ['标签数组'],
  video: '视频介绍 URL',
  radarChart: { 功能, 性能, 易用性, 生态, 性价比 }
}
```

### Store 架构

**`stores/tools.js`**：
- `filteredTools`：根据搜索、分类、标签过滤的工具列表（按评分降序）
- `categories`：动态提取的所有分类
- `allTags`：动态提取的所有标签
- Actions：`setSearchQuery`, `setSelectedCategory`, `toggleTag`, `clearFilters`

**`stores/ui.js`**：UI 状态管理

## 路由配置

使用 Hash 模式路由，所有页面组件懒加载：

| 路由 | 组件 | 用途 |
|------|------|------|
| `/` | Home | 首页，工具卡片网格 |
| `/tool/:id` | ToolDetail | 单个工具详情页 |
| `/comparison` | Comparison | 工具横向对比 |
| `/matcher` | Matcher | 智能工具匹配器 |
| `/pricing` | Pricing | 订阅定价指南 |
| `/workflows` | Workflows | 工作流最佳实践 |
| `/resources` | Resources | 资源中心 |
| `/quiz` | Quiz | AI 工具竞猜 |
| `/profile` | Profile | 个人档案 |
| `/:pathMatch(.*)*` | NotFound | 404 页面 |

路由元数据包含 `title` 和 `description`，用于 SEO。

## 代码规范

### ESLint（`.eslintrc.cjs`）
- 继承 `eslint:recommended` 和 `plugin:vue/vue3-recommended`
- 关闭 Vue 多单词组件名检查
- 未使用变量警告

### Prettier（`.prettierrc`）
- 无分号
- 单引号
- 2 空格缩进
- 100 字符行宽

### Vue 组件规范
- 使用 Composition API + `<script setup>`
- 组件命名：PascalCase（如 `ToolCard.vue`）
- 样式：Tailwind CSS 类名

## 测试

测试文件按模块分布于 `src/components/__tests__/` 和 `src/utils/__tests__/`，使用 Vitest + jsdom：

```bash
# 运行所有测试
npm run test

# 生成覆盖率报告
npm run test:coverage
```

覆盖率目标：80%+

## 性能优化要点

1. **路由懒加载**：所有 views 使用 Vue Router 原生 `() => import(...)` 方式
2. **代码分割**：手动 chunk 配置减少初始加载体积
3. **构建目标**：ES2020 + Chrome80 CSS
4. **资源指纹**：hash 命名支持长期缓存
5. **HMR 禁用 overlay**：开发体验优化

## SEO 优化

- 完整的 meta 标签（title, description, OG tags）
- Schema.org 结构化数据
- 路由守卫动态更新页面标题
- Nginx Gzip 压缩

## 添加新工具

编辑 `src/data/tools.js`，按数据模型添加工具对象。相关 computed 属性会自动更新分类、标签和过滤结果。
