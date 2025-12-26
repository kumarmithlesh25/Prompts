# Claude Code Memory Basics

Two essential commands for managing persistent instructions in Claude Code.

## /init

Bootstraps a new `CLAUDE.md` file in your project root.

**Usage:**
```
/init
```

**What it does:**
- Creates a starter `CLAUDE.md` with project context
- Analyzes your codebase to suggest relevant instructions
- Sets up the foundation for project-specific memory

**When to use:**
- Starting a new project with Claude Code
- Adding Claude Code to an existing project that lacks a `CLAUDE.md`

## /memory

Opens your memory file for editing during a session.

**Usage:**
```
/memory
```

**What it does:**
- Opens the appropriate `CLAUDE.md` file in your editor
- Changes take effect immediately in your current session
- Persists across future sessions

**When to use:**
- Adding new coding conventions or preferences
- Updating project-specific instructions
- Recording commands you frequently use

## Memory File Locations

| File | Scope |
|------|-------|
| `./CLAUDE.md` | Project (shared via git) |
| `./CLAUDE.local.md` | Project (personal, not committed) |
| `~/.claude/CLAUDE.md` | Global (all your projects) |

## Quick Tips

- Be specific: "Use 2-space indentation" beats "Format code nicely"
- Group related instructions under markdown headings
- Use `CLAUDE.local.md` for personal preferences you don't want to commit
