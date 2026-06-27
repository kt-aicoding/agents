# AI / Ring Working Guide

This repository is a personal knowledge base with a few application prototypes. Follow `CLAUDE.md` for the full directory map and use Simplified Chinese for user-facing documents.

## Scope

- Treat `03-健康/`, `04-财务/`, `02-生活/旅游/`, `06-法律/`, and documents about banking, visas, medical records, family, or identity as sensitive personal material.
- Do not print or summarize private details from sensitive documents unless explicitly requested.
- Keep local Claude settings out of commits. `.claude/settings.local.json` is ignored.
- Use existing Chinese directory names for knowledge-base documents. Avoid temporary suffixes such as "合并" or "临时".
- Code projects are local subprojects. Run validation from the relevant package directory, not from the repository root.

## Validation

For documentation-only changes:

```bash
git diff --check
```

For the pet management app:

```bash
cd "07-宠物管理网站/frontend"
npm run build
npm run lint

cd "../backend"
npm run build
```

`02-生活/电脑桌面/mcp-client/package.json` currently has a placeholder failing `test` script, so do not treat `npm test` there as a meaningful validation gate until it is replaced.

