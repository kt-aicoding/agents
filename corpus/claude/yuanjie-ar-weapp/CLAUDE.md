# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Iron Art Museum AR WeChat Mini Program (铁艺博物馆AR小程序)
- Framework: Taro 3.6.23 + React 18 + TypeScript
- Backend: Supabase (project: kevinten10)
- State Management: Zustand
- Styling: SCSS with CSS variables

## Common Commands

```bash
# Development
cd /Users/kevinten/projects/yuanjie-ar-weapp && npm run dev:weapp

# Build
cd /Users/kevinten/projects/yuanjie-ar-weapp && npm run build:weapp

# Install dependencies
cd /Users/kevinten/projects/yuanjie-ar-weapp && npm install
```

## Project Structure

```
src/
├── app.tsx              # App entry
├── app.config.ts        # Mini program config (no TypeScript types)
├── app.scss             # Global styles
├── pages/               # Mini program pages
│   ├── index/           # Home page
│   ├── ar-scan/         # AR scanning page
│   ├── ai-assistant/    # AI assistant page
│   ├── forum/           # Forum page
│   └── user-center/     # User profile page
├── components/          # Shared components
├── services/
│   └── supabase.ts      # Supabase client & API
├── stores/              # Zustand stores
└── utils/               # Utility functions
```

## Key Configuration Notes

1. **app.config.ts** - Must use plain JS object, no TypeScript types (Taro limitation)
2. **TabBar** - Currently text-only (icons removed due to missing assets)
3. **Supabase** - Uses table prefix `museum_` (e.g., museum_users, museum_exhibits)
4. **Build output** - Import `dist/` directory into WeChat DevTools

## Coding Standards

- Use functional components with hooks
- SCSS for styling, variables in `app.scss`
- Zustand for state management
- Supabase client at `services/supabase.ts`
- Use Taro APIs instead of web APIs

## Common Issues

1. **Missing app.json** - Run `npm run build:weapp` to compile
2. **TabBar icons missing** - Add PNG files to `src/assets/images/` and update `app.config.ts`
3. **WeChat DevTools import** - Always import the `dist/` folder, not project root
