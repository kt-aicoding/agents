# CLAUDE.md -- mcp-subtitle

## Project Overview

MCP server for AI subtitle generation, translation, and formatting. Transcribe audio to SRT via Google Chirp 2, translate via Google Translation v2, create bilingual subtitles, and convert to styled ASS format.

## Architecture

- **Entry**: `src/subtitle_gen/__init__.py` -> `server.main()` via asyncio
- **Core**: `src/subtitle_gen/server.py` -- 4 MCP tool handlers
- **STT**: `src/subtitle_gen/stt.py` -- Google Cloud STT v1 helper (Chirp 2 model)
- **Translation**: `src/subtitle_gen/translator.py` -- Google Cloud Translation v2 helper
- **Formats**: `src/subtitle_gen/formats.py` -- Pure Python SRT/ASS parsing, generation, conversion

## Key Design Decisions

- **API key at call time**: `_get_api_key()` reads `GEMINI_API_KEY` at call time, not import time, so env changes are picked up without restart.
- **Single API key for all**: Both STT and Translation APIs support the same GCP API key via `?key=` param.
- **Batch translation**: `translate_batch()` sends all subtitle texts in one API call (`"q": [text1, text2, ...]`) to minimize latency and cost.
- **Word grouping**: `words_to_srt_blocks()` groups words into subtitle blocks based on word count (max 8), duration (max 4s), and inter-word gaps (min 0.3s).
- **Bilingual via dataclass**: `SubtitleBlock.translated` field holds the translation. `blocks_to_srt(bilingual=True)` renders both lines.
- **SRT parsing is permissive**: Handles malformed indices, both `,` and `.` time separators, multi-line text blocks, mixed line endings.
- **ASS conversion preserves bilingual**: If SRT contains multi-line text blocks, `srt_to_ass` auto-detects and treats as bilingual (line 1 = original, line 2 = translation).

## Tool Flow

1. **transcribe_to_srt**: audio -> STT API -> words -> `words_to_srt_blocks()` -> `save_srt()`
2. **translate_srt**: read SRT -> `parse_srt()` -> `translate_batch()` -> new blocks -> `save_srt()`
3. **create_bilingual_srt**: read SRT -> `parse_srt()` -> `translate_batch()` -> merge into `block.translated` -> `save_srt(bilingual=True)`
4. **srt_to_ass**: read SRT -> `parse_srt()` -> `save_ass()` with styling params

## Common Pitfalls

- **STT v1 sync limit**: Max ~10 MB / ~1 min per request. For longer audio, split into segments first (e.g. with ffmpeg).
- **STT encoding mismatch**: If file extension doesn't match actual encoding, STT returns 400. Convert to mp3/wav first.
- **Translation language codes**: Use ISO 639-1 (zh, ja, es), NOT BCP 47 (cmn-CN). STT uses BCP 47, Translation uses ISO 639-1.
- **ASS color format**: `&HAABBGGRR` -- alpha, blue, green, red. NOT RGBA. White is `&H00FFFFFF`, yellow is `&H0000FFFF`.
- **SRT comma vs dot**: SRT standard uses comma (`00:00:01,500`), but some tools output dot. Parser handles both.
- **Batch translation order**: Google Translation v2 preserves input order in response -- critical for matching translations back to blocks.

## Development

```bash
uv sync           # install deps
uv run subtitle-gen   # run server
npx @modelcontextprotocol/inspector uv --directory . run subtitle-gen  # debug
```
