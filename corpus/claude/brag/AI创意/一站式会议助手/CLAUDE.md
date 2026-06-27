# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an AI-powered meeting planning platform (一站式会议助手) that helps users generate complete conference materials including agendas, speeches, posters, and gift recommendations. The project contains two implementations:

1. **ai-meeting-web** - React 18 + Vite + TypeScript implementation
2. **ai-meeting-web-next** - Next.js 14 + Ant Design 5.x + TypeScript implementation (modern version)

## Common Development Commands

### ai-meeting-web (React + Vite)

```bash
cd ai-meeting-web
npm run dev          # Start dev server (http://localhost:3000)
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

### ai-meeting-web-next (Next.js)

```bash
cd ai-meeting-web-next
npm run dev          # Start dev server (http://localhost:3000)
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npm run lint:fix     # Run ESLint with auto-fix
npm run type-check   # TypeScript type checking
npm run format       # Format code with Prettier
```

## Architecture

### AI Service Pattern

Both implementations use a service-based architecture for AI content generation. The core `AIService` class (`aiService.ts`) provides:

- `generateAgenda()` - Generate meeting agendas
- `generateSpeech()` - Generate speech content
- `generatePoster()` - Generate poster designs
- `generateGifts()` - Generate gift recommendations
- `generateAllContent()` - Batch generate all content types

The service currently uses mock implementations with simulated delays. Real API integration is pending (see `REACT_APP_AI_API_URL` environment variable).

### State Management

**React version**: Uses React hooks and local component state
**Next.js version**: Uses Zustand 4.x with persistence via localStorage

Key Zustand store structure:
- `user` - Current user data
- `meetings` - Array of meeting objects
- `currentMeeting` - Active meeting being edited
- `loading` - Global loading state
- `sidebarOpen` - UI sidebar state

### Meeting Planning Workflow

The `MeetingPlanner` component implements a 4-step wizard:

1. **Basic Info** - Title, date, location, description
2. **Configuration** - Attendees, duration, type, budget
3. **AI Generation** - Generate agenda, speech, poster, gifts
4. **Preview/Export** - Review complete plan

### Design System

Both implementations share a consistent design language:

**Color Palette:**
- Primary: Blue (#2563eb - primary-600)
- Secondary: Sky blue (#0ea5e9)
- Accent: Purple (#d946ef)

**Component Styling:**
- Border radius: 12px (base), 8px (small), 16px (large)
- Custom Tailwind utility classes in `index.css` (React version)
- Ant Design theme customization in `lib/antd-theme.ts` (Next.js version)

**Tailwind Custom Classes (React version):**
- `.btn-primary` - Primary button style
- `.btn-secondary` - Secondary button style
- `.card` - Card container with shadow
- `.input-primary` - Form input styling
- `.loading-spinner` - Loading animation

## TypeScript Configuration

Both projects use strict TypeScript with:

**React version:**
- Target: ES2020
- JSX: react-jsx
- Strict mode enabled
- Unused locals/parameters checked

**Next.js version:**
- Path aliases: `@/*` maps to `./src/*`
- Next.js plugin for enhanced TypeScript support

## Code Quality Tools

**ESLint:**
- React version: `@typescript-eslint/recommended` + `react-refresh`
- Next.js version: `next/core-web-vitals` + `@typescript-eslint/recommended`

**Prettier (Next.js only):**
- Integration with Tailwind CSS (`prettier-plugin-tailwindcss`)

## Key Files Reference

### React Implementation
- `src/App.tsx` - Main routing with React Router
- `src/pages/MeetingPlanner.tsx` - Core 4-step meeting planning wizard
- `src/services/aiService.ts` - AI generation service (mock implementation)
- `src/index.css` - Global styles and Tailwind custom utilities

### Next.js Implementation
- `src/app/layout.tsx` - Root layout with Ant Design provider
- `src/lib/store.ts` - Zustand global state management
- `src/lib/antd-theme.ts` - Ant Design theme configuration

## Engine Requirements

Both projects require Node.js >= 16 (recommended Node.js 18+).

## Development Notes

- The AI service uses mock data with simulated delays (2-3 seconds per generation)
- Real AI API integration is a planned feature
- User authentication is UI-only (no backend integration yet)
- Data persistence uses localStorage in the Next.js version
- Both implementations are fully responsive with mobile-friendly designs
