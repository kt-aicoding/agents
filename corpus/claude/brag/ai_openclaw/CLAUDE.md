# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **documentation repository** for OpenClaw, a desktop AI assistant built with Node.js (>= 22.0.0). OpenClaw enables local AI agents to execute real tasks: file operations, terminal commands, browser automation, and multi-platform messaging.

**Key Resources:**
- Official Website: https://openclaw.ai/
- GitHub: https://github.com/openclaw/openclaw
- Discord: https://discord.gg/openclaw

## Repository Structure

This is a **documentation-only repository** organized by topic:

```
ai_openclaw/
├── 01-快速入门/        # Quick start guide (empty - to be filled)
├── 02-使用指南/        # Complete usage guide
├── 03-技能开发/        # AgentSkills development guide
├── 04-命令参考/        # CLI command reference
├── 05-故障排除/        # Troubleshooting
├── 06-最佳实践/        # Best practices and use cases
└── README.md           # Project overview
```

## Documentation Standards

### File Naming Convention

All documentation files follow the format: `YYYY-MM-DD-描述性名称.md`

Examples:
- `2026-02-07-OpenClaw使用指南.md`
- `2026-02-07-OpenClaw技能开发指南.md`
- `2026-02-07-OpenClaw命令速查表.md`

### Tagging System

Use `#标签` format for categorization:

**AI Technology**: `#ai` `#agent` `#llm` `#prompt` `#mcp`
**System Architecture**: `#architecture` `#microservices`
**Tools & Platforms**: `#openclaw` `#automation` `#desktop-agent`
**Development**: `#skill-development` `#cli` `#commands`

### Content Quality Standards

Each document should include:
- Clear title and background context
- Detailed technical implementation steps
- Practical results or verification data
- Lessons learned and best practices

Avoid:
- Pure theoretical discussion (needs practical application)
- Oversimplified content lacking detail
- Commercially sensitive information

## OpenClaw Core Architecture

### Gateway Architecture

OpenClaw uses a **Gateway-based architecture** with a central service (default port 18789) that:
- Manages connections to messaging platforms
- Orchestrates AI agent sessions
- Provides WebSocket and HTTP interfaces
- Handles skill loading and execution

### Agent System

- **Model Support**: Anthropic Claude (Opus 4.6, Sonnet 4.5), OpenAI GPT-4o, GPT-4o-mini
- **Agent Type**: Tool-using agents with extended thinking capabilities
- **Session Management**: Multiple concurrent sessions with isolation
- **Sandboxing**: Docker-based sandbox for non-main sessions

### Skills System (AgentSkills)

OpenClaw follows the **AgentSkills Specification** by Anthropic:

Three skill types:
1. **Bundled Skills** - Built-in skills
2. **Managed Skills** - Skills from ClawHub marketplace
3. **Workspace Skills** - Custom skills in `~/.openclaw/workspace/skills/`

Skill file structure:
```
my-skill/
└── SKILL.md    # Markdown-based skill definition
```

### Available Tools

| Tool | Purpose |
|------|---------|
| `read` | Read file contents |
| `write` | Create new files |
| `edit` | Modify existing files |
| `bash` | Execute shell commands |
| `list` | List directory contents |
| `search` | Search file contents |
| `browser` | Browser automation |
| `canvas` | Visualization output |

### Multi-Channel Integration

Supported platforms:
- WhatsApp, Telegram, Slack, Discord
- Google Chat, Signal, iMessage, Teams, Matrix
- WebChat (built-in)

## Common OpenClaw Commands

### Installation & Setup

```bash
# Install globally
npm install -g openclaw@latest

# Run configuration wizard
openclaw onboard --install-daemon

# Start Gateway
openclaw gateway --port 18789 --verbose
```

### Gateway Management

```bash
openclaw gateway start       # Start in background
openclaw gateway stop        # Stop Gateway
openclaw gateway restart     # Restart Gateway
openclaw gateway status      # Check status
```

### Agent Interaction

```bash
# Interactive session
openclaw agent

# Single message
openclaw agent --message "Analyze project structure"

# With thinking level
openclaw agent --message "Refactor code" --thinking high
```

### Skills Management

```bash
openclaw skills list                    # List installed skills
openclaw skills search <keyword>        # Search ClawHub
openclaw skills install <skill-name>    # Install skill
openclaw skills validate <skill-name>   # Validate skill
```

### Configuration

```bash
openclaw config get                    # View configuration
openclaw config set <key> <value>      # Set config value
openclaw config edit                   # Edit config file
openclaw config validate               # Validate configuration
```

### Chat Commands (in-session)

| Command | Purpose |
|---------|---------|
| `/status` | Show session status |
| `/new` / `/reset` | Reset session |
| `/compact` | Compress context |
| `/think <level>` | Set thinking level (off/minimal/low/medium/high/xhigh) |
| `/verbose on/off` | Toggle verbose output |
| `/usage <mode>` | Show usage stats (off/tokens/full) |

## Configuration Locations

```
~/.openclaw/
├── openclaw.json           # Main configuration
├── credentials/            # API keys and tokens
├── workspace/              # Working directory
│   ├── skills/            # Custom skills
│   ├── AGENTS.md          # Agent configuration
│   ├── SOUL.md            # Agent personality
│   ├── TOOLS.md           # Tool configuration
│   └── USER.md            # User preferences
├── logs/                  # Log files
└── cache/                 # Cache directory
```

## Security Best Practices

1. **DM Pairing Mode** - Default security for Discord/Telegram
2. **Allowlists** - Restrict allowed users/channels
3. **Sandboxing** - Docker sandbox for group/non-main sessions
4. **Environment Variables** - Store sensitive data in env vars
5. **Regular Updates** - Keep OpenClaw and skills updated

## Minimum Configuration

```json
{
  "agent": {
    "model": "anthropic/claude-opus-4-6"
  }
}
```

## Development Workflow for Documentation

When adding or updating documentation:

1. **Determine the appropriate directory** (01-06 based on content type)
2. **Use the correct filename format** `YYYY-MM-DD-描述.md`
3. **Include relevant tags** at the bottom of the document
4. **Update README.md** if adding new categories or major documents
5. **Follow Chinese language** for content with English technical terms preserved

## Document Template

```markdown
# 文档标题

> 简短描述文档内容

- 标签：#tag1 #tag2 #tag3

## 目录

- [章节一](#章节一)
- [章节二](#章节二)

## 内容章节

详细内容...

## 相关资源

- [相关链接](https://example.com)

---

**更新日期**: YYYY-MM-DD
**标签**: #tag1 #tag2
```

## Contributing

When contributing to this documentation repository:

1. Focus on practical, actionable content
2. Include examples and commands that can be executed
3. Test all commands before documenting
4. Cross-reference related documents
5. Maintain consistency with existing documentation style

## Related Resources

- [OpenClaw Official Docs](https://docs.openclaw.ai/)
- [AgentSkills Spec](https://github.com/anthropics/agent-skills-spec)
- [ClawHub Skills Marketplace](https://github.com/openclaw/clawhub)
