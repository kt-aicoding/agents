# Repository Notes

This repository stores LeetCode practice snippets, interview preparation notes, and job-description reference material.

## Working Rules

- Treat files under `jd/` and `en/` as potentially personal or interview-sensitive. Review and redact names, company-specific details, contact details, compensation, and private interview answers before publishing.
- Do not print full JD, resume, or interview-prep contents in automation logs. File names and short category summaries are acceptable.
- Keep `.idea/workspace.xml`, `.DS_Store`, and Java build outputs out of commits.
- Some files under `src/` may be notes or problem statements rather than compile-ready Java. Confirm file intent before renaming, compiling, or deleting them.
- Prefer small commits by category: repository metadata, interview notes, job descriptions, and source snippets should be separated when practical.

## Checks

- Run `git diff --check` before committing.
- If Java snippets are intended to compile, run `javac src/<file>.java` for the specific file and remove generated `*.class` files afterward.
- For published materials, run a manual privacy pass over `jd/` and `en/` before pushing.

