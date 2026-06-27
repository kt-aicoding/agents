# Repository Guidelines

## Project Shape

TripMap is a Vite/React/Supabase travel-footprint map deployed at `tripmemo.app`. The application uses Leaflet for map rendering, Zustand for client state, and Supabase for auth, database, and storage.

## Commands

- `npm run dev` starts the Vite app.
- `npm run lint` runs ESLint.
- `npm test` runs the TypeScript project check.
- `npm run build` produces the Vercel/Vite `dist/` artifact.

## Environment

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`

## Editing Rules

- Treat `.env`, `.env.production`, `.vercel/`, `.design/`, and `.playwright-mcp/` as local or generated state.
- Do not commit Supabase service-role keys or private storage artifacts.
- Preserve `vercel.json` SPA rewrites unless routing changes deliberately.
