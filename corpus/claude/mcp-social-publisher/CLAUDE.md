# CLAUDE.md — mcp-social-publisher

## Project Overview

Multi-platform social media content publishing MCP server. 4 platforms (X, Weibo, Bilibili, Xiaohongshu) with direct publishing where APIs exist and formatted content for manual posting where they don't.

## Architecture

- **Entry**: `src/social_publisher/__init__.py` -> `server.main()` via asyncio
- **Core**: `src/social_publisher/server.py` — 3 MCP tool handlers, platform registry init
- **Platforms**: `src/social_publisher/platforms/` — one file per platform, all implement `BasePlatform`

## Key Design Decisions

- **Registry pattern**: Platforms register at import time via `_init_platforms()`, gated by env var presence
- **Xiaohongshu always registered**: No API needed — manual posting provider is always available
- **Preview without auth**: `preview_content` creates temporary platform instances for unconfigured platforms (preview doesn't need API keys)
- **Two publish modes**: `status="success"` for direct publish, `status="manual"` for platforms without APIs
- **Platform-specific formatting**: Each provider handles its own hashtag format (#tag vs #tag#), character limits, and media rules

## Platform Patterns

All platforms follow this structure:
1. `__init__` takes API credentials (or nothing for Xiaohongshu)
2. Properties: `name`, `display_name`, `description`, `supports_direct_publish`, `supports_images`, `supports_video`, `env_vars`
3. `publish(title, content, image_paths, video_path, tags)` -> `PublishResult`
4. `preview(title, content, tags)` -> formatted string

## Publishing Modes

| Platform | Mode | Returns |
|---|---|---|
| X | Direct | post_url + post_id |
| Weibo | Direct | post_url + post_id |
| Bilibili | Direct | post_url + post_id |
| Xiaohongshu | Manual | formatted content + posting instructions |

## Common Pitfalls

- **Weibo hashtag format**: Weibo uses `#tag#` (double hash), not `#tag`
- **X character limit**: 280 chars including hashtags; auto-truncated
- **Bilibili cookie expiry**: SESSDATA + bili_jct expire when browser session ends
- **Weibo token expiry**: OAuth access tokens expire after a few days
- **Xiaohongshu title limit**: 20 characters max (Chinese characters count as 1)
- **X media upload**: Requires separate upload step before tweeting; max 4 images

## Development

```bash
uv sync
uv run social-publisher
npx @modelcontextprotocol/inspector uv --directory . run social-publisher
```
