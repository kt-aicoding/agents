# Harness Working Guide

This repository combines an Agent Harness knowledge base with the Go project `aliyun-go-ops-agent/`.

## Scope

- Root-level `README.md`, `knowledge-graph/`, `learning-path/`, `references/`, and `docs/` are knowledge/reference material.
- `aliyun-go-ops-agent/` is the deployable Go project for Alibaba Cloud operations and MCP tooling.
- Keep real Alibaba Cloud credentials, DashScope keys, and generated config files out of commits. Use `aliyun-go-ops-agent/configs/config.yaml.example` as the template.
- Review Go dependency and module path changes carefully; the project currently uses module path `github.com/aliyun-go-ops-agent`.
- Do not commit build output, local config, coverage files, or temporary files.

## Validation

For knowledge-base only changes:

```bash
git diff --check
```

For `aliyun-go-ops-agent/` changes:

```bash
cd aliyun-go-ops-agent
make fmt
make test
make build
```

If `go` is unavailable in the local shell, record that gap in the maintenance note and run the checks before committing.

