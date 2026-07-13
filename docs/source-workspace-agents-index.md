# Workspace AGENTS Index Pointer

The workspace instruction inventory is generated from the current filesystem and maintained at:

`/Users/kevinten/projects/workspace/reports/PROJECTS_AGENTS_INDEX.md`

Do not maintain a second snapshot in this repository. Run the workspace inventory generator after
project moves or instruction-file changes:

```bash
cd /Users/kevinten/projects
python3 tools/project_workspace_inventory.py
```

Historical copies under `agents/corpus/` remain excluded from the active index.
