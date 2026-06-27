# Repository Guidelines

## Project Shape

`reef-bot` is a TypeScript Discord bot for the OpenOctopus community. Source lives in `src/`, SOUL/personality material lives in `souls/`, and `dist/` is the runtime build output.

## Commands

- `pnpm dev` runs the bot in watch mode.
- `pnpm test` runs Vitest.
- `pnpm run typecheck` runs TypeScript no-emit checks.
- `pnpm run lint` runs oxlint.
- `pnpm run build` creates `dist/index.mjs`.

## Environment

- `DISCORD_BOT_TOKEN`
- `INK_GATEWAY_URL`
- `DISCORD_GUILD_ID`

## Editing Rules

- Never log or commit Discord tokens, guild-private content, or gateway credentials.
- Keep `src/`, `dist/`, and `.env.example` aligned when release packaging changes.
