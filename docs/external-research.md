# External Research Notes

Research date: 2026-06-27.

This page records source-backed guidance that supplements the local corpus. Prefer official or primary sources when updating best practices.

## AGENTS.md

OpenAI's Codex documentation says Codex reads `AGENTS.md` before work and builds a layered instruction chain from global guidance, project root, and nested directories. Files closer to the current working directory appear later and can override earlier guidance. Codex also has a default project instruction size limit, so large instruction files should be split or kept concise.

Source: [OpenAI Developers: Custom instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)

The public AGENTS.md format describes the file as a predictable, agent-focused complement to README files. Its sample sections emphasize setup commands, test commands, and code style.

Source: [agents.md](https://agents.md/)

Implication for this repository:

- Treat `AGENTS.md` as the default cross-agent contract.
- Put durable instructions near the code they affect.
- Keep global rules short enough to fit context limits.
- Link to deeper docs instead of copying long operational manuals.

## Codex Skills

OpenAI's Codex skills documentation frames skills as reusable workflows packaged as a `SKILL.md` file with optional scripts, references, and assets. Codex initially sees compact skill metadata, then loads full instructions only when a skill is selected.

Source: [OpenAI Developers: Agent Skills](https://developers.openai.com/codex/skills)

Implication for this repository:

- Do not overload `AGENTS.md` with long repeated workflows.
- Promote repeated multi-step procedures into skills.
- Keep project instructions focused on local facts and hazards.

## CLAUDE.md

Anthropic's Claude Code memory documentation distinguishes user-written `CLAUDE.md` instructions from automatic memory. `CLAUDE.md` is for instructions and rules; automatic memory is for learned patterns. Anthropic also notes that instructions should be specific and concise.

Source: [Anthropic Claude Code Docs: Memory](https://docs.anthropic.com/en/docs/claude-code/memory)

Anthropic's "How Anthropic teams use Claude Code" report describes teams using detailed `Claude.md` files for workflows, tooling, expectations, onboarding, and continuous improvement after sessions.

Source: [Anthropic report PDF](https://www-cdn.anthropic.com/58284b19e702b49db9302d5b6f135ad8871e7658.pdf)

Implication for this repository:

- Keep useful historical `CLAUDE.md` files in the corpus.
- Migrate stable, cross-agent guidance into `AGENTS.md`.
- Keep Claude-specific commands and memory practices in `CLAUDE.md`.
- Review session outcomes and update instructions when repeated friction appears.

## GEMINI.md

Gemini CLI documentation describes hierarchical context files named `GEMINI.md`, including global, project, ancestor, and subdirectory scopes. It also documents `/memory show`, `/memory refresh`, and `/memory add`, plus import support with `@file.md`.

Source: [Gemini CLI: Provide Context with GEMINI.md Files](https://google-gemini.github.io/gemini-cli/docs/cli/gemini-md.html)

Implication for this repository:

- The same layering principle appears across tools.
- Cross-tool instructions should stay portable where possible.
- Tool-specific files can reference `AGENTS.md` rather than duplicating everything.

## Working Conclusion

The strongest pattern across local practice and external docs is layered, scoped, concise instruction:

- Global files define stable user preferences and safety rules.
- Project files define real commands, architecture, hazards, and verification.
- Subdirectory files define package-local exceptions.
- Tool-specific memory files keep tool-specific workflows.
- Skills capture repeated procedures that are too long for normal project instructions.

