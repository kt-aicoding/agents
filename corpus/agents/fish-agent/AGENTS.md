# Repository Notes

This repository powers `fish.rxcloud.group`, an Expo/React Native pixel-art fishing simulation game with a Vercel-hosted web export.

## Working Rules

- Keep generated Expo, Vercel, Playwright, and local automation state out of git.
- Root-level PNG captures are local QA screenshots. Commit curated documentation images only under `screenshots/` or another explicit docs/assets directory.
- Treat Supabase credentials as optional and sensitive. Use `.env.example` for placeholders only.
- Preserve the Expo Router file structure under `app/` unless updating route docs and Vercel export behavior together.
- Prefer type-checking and web export validation for maintenance passes; native iOS/Android checks require local simulator/device setup.

## Validation

```bash
npm run lint
npm run test
npm run build
git diff --check
```

`lint` and `test` currently delegate to TypeScript type-checking. Add dedicated lint/test tooling later if this project starts receiving larger feature changes.

