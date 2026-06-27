# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI Meeting Planner (一站式会议助手) — a Chinese-language SPA for AI-powered meeting planning. Users fill in meeting details through a multi-step wizard and generate agendas, speeches, posters, and gift recommendations. Currently a **UI prototype** with mock AI services (no real backend or API integration yet).

## Commands

- `npm run dev` — start dev server on port 3000
- `npm run build` — type-check with tsc then build with Vite
- `npm run lint` — ESLint with zero warnings tolerance
- `npm run preview` — preview production build

No test framework is configured.

## Architecture

**Stack:** React 18 + TypeScript + Vite + Tailwind CSS 3 + React Router 6

**Routing:** All routes defined in `src/App.tsx` using `BrowserRouter`. Pages: `/` (home), `/login`, `/register`, `/dashboard`, `/planner`, `/templates`. No auth guards — `Header.tsx` has a hardcoded `isLoggedIn = false` placeholder.

**AI Service Layer:** `src/services/aiService.ts` exports a singleton `aiService` class. All methods (`generateAgenda`, `generateSpeech`, `generatePoster`, `generateGifts`, `generateAllContent`) are currently **mock implementations** using `setTimeout` delays and template strings. The `baseURL` property references `REACT_APP_AI_API_URL` which is a CRA-style env var — Vite requires `VITE_` prefix to expose env vars to client code.

**Styling System:** Tailwind with custom design tokens in `tailwind.config.js`:
- Custom color palettes: `primary` (blue), `secondary` (sky), `accent` (fuchsia)
- Custom fonts: Inter (body), Poppins (display)
- Custom shadows: `soft`, `medium`, `large`
- Custom animations: `fade-in`, `slide-up`, `bounce-subtle`
- Reusable component classes defined via `@layer components` in `src/index.css`: `btn-primary`, `btn-secondary`, `btn-outline`, `btn-ghost`, `card`, `card-hover`, `input-primary`, `hero-gradient`, `gradient-bg`, `text-gradient`, `glass-effect`, `loading-spinner`

**Components:** `src/components/` contains reusable UI primitives (Button, Card, Input, Loading, Modal) barrel-exported from `index.ts`. Note: pages often use the CSS component classes (e.g. `btn-primary`) directly instead of the React component wrappers.

**Core page:** `MeetingPlanner.tsx` is a 4-step wizard (basic info → config → AI generation → preview/export) managing form state and generation state locally with `useState`.

## Conventions

- All UI text is in Chinese (zh-CN)
- Functional components with hooks only, no class components
- Icons from `@heroicons/react` (outline/solid) and `lucide-react`
- Strict TypeScript: `noUnusedLocals`, `noUnusedParameters`, `noFallthroughCasesInSwitch` enabled
