# Repository Guidelines

## Project Shape

This is a Next.js 12 static/exportable web app for the `ji` dance simulator. Pages live in `pages/`, typed animation logic is in `src/`, and media assets live in `public/`.

## Commands

- `yarn dev` or `npm run dev` starts local development.
- `npm run build` runs `next build`.
- `npm run export` builds and exports the GitHub Pages artifact.
- `npm test` runs the Next lint smoke check.

## Editing Rules

- Preserve the `/ji` production base path in `next.config.js` unless the deployment target changes.
- Keep audio/image assets in `public/` stable; they are part of the user-facing simulator.
