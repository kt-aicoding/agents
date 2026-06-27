# Lifecat Maintenance Guide

## Project State

- Repository: `lifecat-stack/Lifecat`
- Category: legacy/reference full-stack portfolio project
- Public host referenced by the README: `lifecat.club`
- Main surfaces: Java Web/Spring Boot backends, Vue web clients, Android, WeChat Mini Program, Python ML, Hadoop, STM32, and Docker assets.

## Before Editing

- Treat this repository as a multi-era reference project. Confirm which subproject you are changing before editing.
- Preserve existing screenshots, diagrams, and legacy source links unless the target project has been verified dead.
- Do not commit local IDE files, generated build output, database dumps, or real credentials.

## Useful Commands

- Docker deployment smoke path: `cd docker && docker compose config`
- Legacy Maven modules, when present locally: run Maven commands from the specific module directory.
- Frontend modules, when present locally: run npm commands from the specific web module directory.

## Environment

- Copy `.env.example` only as a reference; individual historical modules may have their own config files.
- Required runtime services depend on the selected module, commonly MySQL, Java 8+, Maven, Node.js, and Docker.

## Deployment Notes

- The root README includes historical demo URLs and source repositories for each module.
- Use `DEPLOYMENT.md` as the operational checklist before changing DNS, host ports, or Docker configuration.
