# Repository Notes

This repository powers the Shanghai prenatal health-check guide intended for `health.rxcloud.group`. The app source lives under `app/` and uses Vite, React, Supabase Edge Functions, and an OpenAI-compatible chat backend.

## Working Rules

- Treat this as health-related content. Do not present AI responses as medical diagnosis or individualized medical advice.
- Preserve visible disclaimers that users should consult qualified clinicians and verify hospital pricing/policy details with official sources.
- Keep real Supabase, OpenAI-compatible API, and Vercel credentials out of git. Use `app/.env.example` for placeholders only.
- Run frontend commands from `app/`.
- Keep Supabase Edge Function changes and frontend UI changes in separate commits when possible.
- Verify the live domain carefully: at triage time, `health.rxcloud.group` returned a page titled `二手物品智能定价工具`, which does not match this project.

## Validation

```bash
cd app
npm run lint
npm run test
npm run build
git diff --check
```

`npm run test` currently delegates to lint as a conservative smoke check. Add focused tests for the AI assistant, age-based package recommendations, disclaimer rendering, and Supabase API mode when those flows change.

