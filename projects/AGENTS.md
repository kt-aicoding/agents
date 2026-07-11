# Project Workspace Guide

This directory is a local umbrella for independent website and Agent/AI projects. It is not part of the archived instruction corpus.

## Rules

- Treat every child Git repository as independent; do not stage it in the outer `agents` repository.
- Follow the nearest child `AGENTS.md`, then `CLAUDE.md`, then `README.md`.
- Keep project-specific commands, dependencies, environment templates, and deployment settings inside the owning project.
- Do not copy or expose `.env` values, tokens, cookies, private keys, or other credentials while moving or maintaining projects.
- Run checks only in the project being changed; do not run one package manager or formatter across this umbrella directory.
- When moving projects again, preserve their Git history and local changes and update the migration manifest.
