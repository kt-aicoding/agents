# openoctopus.club Maintenance Guide

## Project State

- Repository: `open-octopus/openoctopus.club`
- Category: official OpenOctopus marketing/landing site
- Public site: `https://openoctopus.club`
- Stack: Astro static output, Tailwind CSS, Vercel, GitHub integration.

## Before Editing

- Keep the first viewport focused on OpenOctopus and its family home hub positioning.
- Avoid committing generated output, local Vercel metadata, `.astro/`, or dependency folders.
- Rebuild after content, image, SEO, or asset path changes.

## Useful Commands

- Install: `pnpm install`
- Develop: `pnpm dev`
- Build: `pnpm build`
- Preview: `pnpm preview`
- Smoke test: `pnpm test`

## Environment

- Copy `.env.example` for local public site URL values if needed.
- This is a static site; do not add server-only secrets to client-exposed variables.

## Deployment Notes

- See `DEPLOYMENT.md` for Vercel and custom domain checks.
- Public CNAME/domain references should stay aligned with `openoctopus.club`.
