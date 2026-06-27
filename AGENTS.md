# Repository Working Guide

This repository stores reusable agent instruction practices and archived `AGENTS.md` / `CLAUDE.md` examples.

## Rules

- Do not add secrets, `.env` values, private tokens, cookies, or private keys.
- Keep actual archived files under `corpus/` and synthesized guidance under `docs/`.
- Preserve source paths in manifests so examples remain traceable.
- Do not rewrite archived examples unless refreshing from the source workspace.
- Prefer concise, reusable guidance over large generic rule dumps.

## Validation

Before publishing changes:

```bash
gitleaks detect --source . --no-banner
find corpus -type f | wc -l
```

If changing Markdown structure, inspect rendered headings and links.

