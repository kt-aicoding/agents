# Awesome AI Ideas Working Guide

This repository is a public AI product-idea knowledge base plus a local Next.js site in `site/`.

## Scope

- Treat Markdown idea documents as public product/reference content.
- Keep generated QA screenshots, local browser caches, Vercel metadata, `node_modules/`, and `.next/` out of commits.
- `site/` has its own `AGENTS.md`; follow it before changing Next.js app code.
- Do not commit real environment files. Use `site/.env.example` for documented placeholders only.

## Validation

- For content-only changes, run `git diff --check`.
- For `site/` changes, run:

```bash
cd site
npm run lint
npm run type-check
npm run test
npm run build
```

## Local Notes

- `evaluation_report.json` is currently an untracked evaluation artifact and is not valid JSON because some nested quote characters are not escaped.
- The screenshot files in the repository root are local QA/design artifacts. Review them before deciding whether to commit or archive them.

