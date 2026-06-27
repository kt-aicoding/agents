# Repository Guidelines

## Project Shape

`ikun-call` is a FastAPI/WebSocket voice chat app backed by `ikun-2.5B` and browser speech recognition. The backend lives in `server.py` and `engine/`; the frontend is static HTML/CSS/JS under `static/`.

## Commands

- `pip install -r requirements.txt` installs runtime dependencies.
- `python3 server.py` starts the local FastAPI app on `PORT` or `8000`.
- `python3 -m compileall server.py config.py engine` is the low-cost syntax smoke check.

## Environment

- `PORT` controls the HTTP server port.
- The model path is resolved from `../ikun-2.5B` when present, otherwise it falls back to the Hugging Face model ID.

## Editing Rules

- Keep browser ASR behavior in `static/app.js` compatible with Chrome and Edge.
- Avoid committing model weights or generated audio artifacts.
