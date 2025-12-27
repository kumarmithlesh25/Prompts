# Claude Code Context Basics

How Claude Code understands your project and manages conversation context.

## How Claude Code Reads Context

Claude Code automatically loads context from multiple sources when you start a session.

### Memory Files (CLAUDE.md)

Loaded automatically in this order (highest to lowest priority):

| Location | Scope | Shared? |
|----------|-------|---------|
| `./CLAUDE.md` | Project | Yes (via git) |
| `./.claude/CLAUDE.md` | Project | Yes (via git) |
| `./.claude/rules/*.md` | Modular rules | Yes (via git) |
| `~/.claude/CLAUDE.md` | All your projects | No |
| `./CLAUDE.local.md` | Project (personal) | No |

Claude also walks up parent directories looking for additional CLAUDE.md files.

### Codebase Exploration

Claude Code can explore your codebase on demand:

```
> give me an overview of this codebase
> find files that handle authentication
> explain the main architecture
```

## Using @ References

Include files directly in your prompt using the `@` prefix:

**Single file:**
```
> Explain the logic in @src/utils/auth.js
```

**Multiple files:**
```
> Compare @src/old-api.js and @src/new-api.js
```

**Directories:**
```
> What's in @src/components?
```

**MCP resources:**
```
> Show me @github:repos/owner/repo/issues
```

When you reference a file with `@`, Claude also loads any CLAUDE.md files from that file's directory.

## Importing Files in CLAUDE.md

Reference other files in your memory using `@path` syntax:

```markdown
See @README for project overview.

# Git workflow
@docs/git-instructions.md

# Personal preferences
@~/.claude/my-preferences.md
```

**Rules:**
- Relative and absolute paths supported
- Imports inside code blocks are ignored
- Maximum 5 levels of nested imports

## Context Window & Summarization

Claude Code has a limited context window. It manages this automatically.

### Auto-Compaction

When context reaches 95% capacity:
- Claude automatically summarizes the conversation
- Toggle with `/config` > "Auto-compact enabled"

### Manual Compaction

```
/compact
```

With specific focus:
```
/compact Focus on the API changes we discussed
```

### Customizing Compaction

Add to your CLAUDE.md:
```markdown
# Summary instructions

When compacting, focus on code changes and test results.
```

## Monitoring Context Usage

**Check token costs:**
```
/cost
```

**Clear conversation to free context:**
```
/clear
```

## Session Persistence

Resume previous conversations to maintain context:

| Command | Description |
|---------|-------------|
| `claude --continue` | Resume most recent session |
| `claude --resume` | Pick from all sessions |
| `/resume name` | Resume by session name |
| `/rename name` | Name current session |

## Extended Context

For larger context windows (Console/API users):

```bash
claude --model sonnet[1m]    # 1 million token context
```

## Quick Reference

| Command | Purpose |
|---------|---------|
| `/memory` | View loaded memory files |
| `/compact` | Manually summarize conversation |
| `/cost` | Check token usage |
| `/clear` | Clear conversation history |
| `/config` | Toggle auto-compact setting |

## Tips

- Use `@file` references for quick context inclusion
- Run `/compact` before starting a new topic in long sessions
- Name sessions with `/rename` for easy resumption
- Keep CLAUDE.md focused; use `.claude/rules/` for detailed guidelines
