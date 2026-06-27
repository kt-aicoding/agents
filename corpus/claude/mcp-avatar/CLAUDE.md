# CLAUDE.md — mcp-avatar

## Project Overview

Multi-provider MCP server for AI digital human / talking head video generation. Generate videos of portrait photos speaking from text or audio. 2 providers (Hedra + D-ID) under one unified interface.

## Architecture

- **Entry**: `src/avatar_gen/__init__.py` -> `server.main()` via asyncio
- **Core**: `src/avatar_gen/server.py` — 3 MCP tool handlers, provider registry init, download helpers
- **Providers**: `src/avatar_gen/providers/` — one file per provider, all implement `BaseProvider`

## Key Design Decisions

- **Registry pattern**: Providers register at import time via `_init_providers()`, gated by env var presence
- **Async two-step**: All avatar APIs are async — `generate()` returns task_id, `query()` polls until done
- **Input flexibility**: `image_path` accepts local file paths or URLs. Providers handle upload/encoding internally.
- **Text vs Audio**: Either `text` (provider does TTS) or `audio_path` (pre-recorded) required — server validates before calling provider.
- **Local file detection**: `query_avatar_status` checks if `video_url` starts with `/` to skip HTTP download.

## Provider Patterns

Providers follow this structure:
1. `__init__` takes API key
2. `generate(image_path, text, audio_path)` -> `AvatarResult(task_id, status="processing")`
3. `query(task_id)` -> `AvatarResult` with status and video_url

### Hedra
- Uses asset upload flow: upload image/audio first, then create character
- Auth: `X-API-Key` header
- API: `POST /v1/characters` (generate), `GET /v1/characters/{id}` (query)
- Status mapping: completed/complete/done -> success

### D-ID
- Uses data URLs for local files (base64 encoded)
- Auth: `Basic {api_key}` header
- API: `POST /talks` (generate), `GET /talks/{id}` (query)
- Status mapping: done -> success; error/failed/rejected -> failed

## Common Pitfalls

- **D-ID auth**: API key must be base64 encoded (the key itself is already base64)
- **Hedra upload**: Two-step upload (init + PUT). Some API versions use different upload flows.
- **Large images**: D-ID base64 encoding can create very large request bodies. Consider URL-based images for production.
- **Polling interval**: Both providers typically take 30-120 seconds. Recommend polling every 30 seconds.

## Development

```bash
uv sync
uv run avatar-gen        # run server
npx @modelcontextprotocol/inspector uv --directory . run avatar-gen  # debug
```
