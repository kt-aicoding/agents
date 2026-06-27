# Yuanjie Working Guide

This repository is a Chinese-language work and operations knowledge base for 元界. It contains company/reference documents, interview and recruiting materials, assets, and links to related project repositories.

## Local Rules

- User-facing documents should be written in Simplified Chinese.
- Treat `assets/resumes/` and `个人/候选人` style materials as sensitive. Do not quote or copy personal details into generated reports.
- `ai-product-playbook/` is a nested Git repository tracked separately in the workspace. Do not add it to the parent `yuanjie` repository.
- `temp/`, `temp2/`, `.DS_Store`, `.vercel/`, and dependency/build directories are local noise and should remain ignored.
- Prefer dated Markdown filenames for task records: `YYYY-MM-DD-描述.md`.

## Verification

This is primarily a documentation repository. Use narrow checks:

```bash
git -c core.quotePath=false status --short
git diff --check
```

For document-only changes, verify paths, headings, links, and whether sensitive candidate information is being exposed.

## Related Materials

- Public/company site domain: `yuanjie.ai`
- Nested product playbook repo: `ai-product-playbook/`
- Candidate/interview records: `docs/tasks/`
- Reference materials: `docs/references/`
