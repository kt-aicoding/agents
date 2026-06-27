# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**铁艺博物馆AR小程序** — An AR-powered museum mini-program for traditional Chinese ironwork heritage (铁艺/秋艺大博馆). The project follows a SaaS architecture with three layers:

- **C端 (User)**: WeChat mini-program for consumers — AR scanning, AI virtual curator, community forum, e-commerce
- **B端 (Enterprise)**: Web SaaS dashboard for museums/businesses — product management, knowledge base, data analytics
- **P端 (Platform)**: Web admin panel — enterprise management, billing, content delivery, monitoring

## Repository Contents

### UI Mockups (C-end Mobile Interface)

Two visual themes exist:

**Adult Version (Dark Metallic Theme)**:
- **0.jpg**: 用户中心 (User Center / "My" page) — membership card, points, orders, digital collectibles, ironwork assets
- **1.jpg**: AR扫描成功页 (AR Scan Success) — scan result display, photo frames, sharing (WeChat/Moments/Xiaohongshu)
- **2.jpg**: 铁艺论坛 (Ironwork Forum) — topic tabs, UGC posts, product links, AR unlock
- **3.jpg**: AI虚拟馆长 (AI Virtual Curator) — blacksmith digital human, chat interface, product recommendations
- **4.jpg**: 首页 (Homepage) — banner, navigation grid, AI recommendation, product/content feed

**Kids Version (Cartoon Theme)**:
- **6.jpg**: 儿童版首页 (Kids Homepage) — cute characters, simplified navigation
- **7.jpg**: 儿童版论坛 (Kids Forum) — cartoon avatars, child-friendly UGC

**Architecture Document**:
- **5.jpg**: 脑图 (Mind Map) — complete information architecture for all 5 main modules

### Requirements

- **AR需求表.xlsx**: Requirements specification with 3 sheets:
  - 用户端 (User-side): Login, AR display, AI interaction, e-commerce, profile — with UI reference and version planning columns
  - 企业端 (Enterprise-side): Account management, product management, knowledge base, data dashboard, AR customization
  - 平台端 (Platform-side): Enterprise management, billing, delivery, data dashboard, content safety

### Review & Optimization Documents

- **AR优化清单.md**: Prioritized optimization checklist (P0/P1/P2) with 34 items across all categories
- **UI稿问题标注.md**: Per-page design issue annotations for designers
- **缺失页面清单.md**: Missing page specifications with wireframe layouts and priority ranking

### Technical Research (调研)

- **技术栈方案.md**: Master tech architecture document — framework, AR, backend, LLM, TTS, cost estimates, project structure
- **调研-AR技术栈.md**: AR SDK evaluation — xr-frame (recommended), Kivicube, EasyAR, 8th Wall, AR.js/MindAR.js
- **调研-Supabase与CloudBase.md**: Backend BaaS comparison — Supabase (blocked), MemFire, CloudBase (chosen)
- **调研-开发框架与最佳实践.md**: Mini-program framework comparison, UI libraries, state management, best practices

### API Documentation (docs/)

- **CloudBase-云开发入门.md**: WeChat CloudBase overview, capabilities, key doc links
- **xr-frame-概述.md**: xr-frame features, limitations, version requirements, demo links
- **Vant-Weapp-快速上手.md**: Installation (npm), TypeScript setup, component list, usage examples
- **讯飞TTS-WebSocket-API.md**: Full API spec — auth, parameters, request/response, error codes
- **火山方舟-Ark-API文档.md**: Ark chat/vision model configuration, sync/stream API, function call, HTTP examples

## Tech Stack (Confirmed)

```
开发框架：原生微信小程序 + TypeScript
UI组件库：Vant Weapp v1.11.7
状态管理：MobX miniprogram
AR渲染：  xr-frame（微信官方）
后端：    CloudBase 微信云开发（NoSQL文档数据库 + 云函数 + 云存储）
LLM：    火山方舟 Ark CodingPlan（日常对话与复杂查询）
TTS：    讯飞在线语音合成 WebSocket API
支付：    微信支付（CloudBase 云调用）
```

## Key Design Decisions

- Bottom tab bar has 5 tabs: 首页/论坛/AR扫描(center)/AI助手/我的
- AR scanning is the central feature (physically centered tab with elevated icon)
- AI Virtual Curator serves dual role: cultural education + product sales conversion
- Forum module exists in UI and mind map but was initially absent from requirements table (now added)
- Kids version uses different tab naming: 探索/畅聊/扫描/求助/我的

## Known Issues

- Product pricing inconsistency across pages (¥19/¥39/¥69 for same item)
- Missing core transaction flow pages (product detail, cart, checkout, payment)
- Login/registration page not designed
- Kids version only has 2 of 5 pages designed
- Forum module needs formal addition to requirements scope

## Notes

- This is a design asset repository with no build system or code
- No package managers, test frameworks, or linting tools are configured
- Primary language: Chinese (Simplified)
