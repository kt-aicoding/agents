# CLAUDE.md — mcp-media-toolkit

## Project Overview

MCP server for local image processing — background removal, stock media search, resize, format conversion, and collage creation. All tools are free and work locally (except Pexels search which uses a free API).

## Architecture

- **Entry**: `src/media_toolkit/__init__.py` → `server.main()` via asyncio
- **Core**: `src/media_toolkit/server.py` — all logic in one file
- **Libraries**: Pillow (resize, convert, collage), rembg (background removal), httpx (Pexels API)

## Key Design Decisions

- All tools save output to `IMAGE_OUTPUT_DIR` (default: `./output`) with timestamped filenames
- rembg model (~170MB) downloads automatically on first use — no manual setup needed
- `output_path` is optional on every tool — auto-generated if omitted
- SVG→PNG conversion uses cairosvg if available, otherwise returns an error with install instructions
- Pexels search requires `PEXELS_API_KEY` env var (free tier, no cost)

## Development

```bash
uv sync                    # install deps
uv run media-toolkit       # run server
```

## Common Pitfalls

- First call to `remove_background` is slow (~30s) because rembg downloads the U2Net model
- JPEG does not support transparency — `convert_format` auto-composites RGBA onto white background
- Pexels API has rate limits (200 req/hour on free tier) — no auth = immediate error with helpful message
