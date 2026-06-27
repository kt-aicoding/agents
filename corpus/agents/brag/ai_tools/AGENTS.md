# Repository Guidelines

## Project Structure & Module Organization
This repository is documentation- and asset-focused (no application source code). The main areas are:
- `调研/`: research notes and guides in Markdown.
- `需求/`: requirements notes in Markdown.
- `ai_stack/202503/`: AI stack materials (Markdown, images, PPTX).
- `tools.png`: a top-level reference image.

If you add new sections, keep them grouped by purpose and prefer putting related assets next to their Markdown (e.g., `调研/` images next to the guide that uses them).

## Build, Test, and Development Commands
There is no build system or runtime. Work is done by editing Markdown and updating assets.
- `rg --files` (optional) to list repository files quickly.
- Use your editor’s Markdown preview for visual checks.

If you introduce scripts or automation, document the command in this section and keep it cross-platform where possible.

## Coding Style & Naming Conventions
- Markdown is the primary format. Use clear `#`/`##` headings, short paragraphs, and tables where they improve scan-ability.
- Keep filenames descriptive and consistent with the surrounding folder’s language (Chinese names are already used in `调研/` and `需求/`).
- Use relative links between documents (e.g., `./AI_Stack.md`).
- Keep images and slides referenced from the nearest relevant folder.

## Testing Guidelines
No automated tests exist. If you add scripts or data processing steps, include a simple validation command and expected output in this guide.

## Commit & Pull Request Guidelines
Git history is not present in this workspace, so no established commit convention can be inferred. If you add commits, prefer Conventional Commits (e.g., `docs: update AI tool guide`) and keep changes scoped.

PRs should include:
- A short summary of what changed and why.
- Links to related documents or requirements.
- Screenshots for any visual asset updates.

## Security & Configuration Tips
Do not add secrets or personal data to Markdown or images. Large binary assets should be intentional and documented near the content that uses them.
