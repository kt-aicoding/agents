# Repository Guidelines

## Project Shape

This package is an MCP server that exposes Discord bot operations. Source files are in `src/`; `dist/` is the package runtime output referenced by the `mcp-discord` bin entry.

## Commands

- `pnpm install` installs dependencies.
- `pnpm run dev` watches TypeScript compilation.
- `pnpm run build` compiles `src/` into `dist/`.
- `pnpm test` and `pnpm run lint` run `tsc --noEmit` smoke checks.

## Environment

- `DISCORD_BOT_TOKEN` is required for runtime use.
- `HTTP_PROXY` is optional and enables proxy support for Discord API calls.

## Editing Rules

- Avoid logging Discord tokens, channel IDs from private servers, or message contents from real communities.
- If source changes require published package updates, keep `src/`, `dist/`, and declarations in sync intentionally.
