# Capa Runtime Maintenance Guide

## Project State

- Repository: `capa-cloud/capa`
- Category: Go sidecar/runtime for the Capa ecosystem
- Related public docs/domain references: `capa-cloud.github.io`
- Main runtime entry points live under `cmd/`; reusable packages live under `pkg/`; API specs live under `spec/`.

## Before Editing

- Keep SDK/runtime boundaries explicit. This repo is the sidecar/runtime, not the language SDK.
- Review `spec/` changes together with SDK compatibility.
- Avoid committing local binaries, generated reports, vendored dependencies, or real service credentials.

## Useful Commands

- Build: `go build ./...`
- Test: `go test ./...`
- Format: `gofmt -w <changed-go-files>`
- Docker image: `docker build -f docker/Dockerfile -t capa-runtime:local .`

## Environment

- Start from `.env.example` when a local runtime needs configurable ports or component paths.
- Component-specific credentials should stay in local files or deployment secrets, not in the repository.

## Deployment Notes

- `DEPLOYMENT.md` records local Docker and sidecar deployment checks.
- Treat traffic interception features as production-sensitive because they can affect the main request path.
