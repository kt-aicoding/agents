# Repository Working Guide

This repository stores reusable agent instruction practices and archived `AGENTS.md` / `CLAUDE.md` examples.

## Rules

- Do not add secrets, `.env` values, private tokens, cookies, or private keys.
- Keep actual archived files under `corpus/` and synthesized guidance under `docs/`.
- Preserve source paths in manifests so examples remain traceable.
- Do not rewrite archived examples unless refreshing from the source workspace.
- Prefer concise, reusable guidance over large generic rule dumps.

## Validation

Before publishing changes:

```bash
gitleaks dir . --no-banner --redact
find corpus -type f | wc -l
python3 - <<'PY'
from pathlib import Path
import hashlib, json
root = Path('.')
data = json.loads((root / 'manifests/files.json').read_text())
missing = []
bad_hash = []
for item in data['files']:
    path = root / item['archive_path']
    if not path.exists():
        missing.append(item['archive_path'])
    elif hashlib.sha256(path.read_bytes()).hexdigest() != item['sha256']:
        bad_hash.append(item['archive_path'])
print({'total': data['total'], 'counts': data['counts'], 'missing': len(missing), 'bad_hash': len(bad_hash)})
PY
```

If changing Markdown structure, inspect rendered headings and links.
