# Claude Code MCP Basics

MCP (Model Context Protocol) connects Claude Code to external tools, databases, and services.

## What is MCP?

MCP is an open standard for AI-tool integrations. With MCP servers, Claude can:

- Query databases directly
- Access issue trackers (GitHub, Jira, Asana)
- Read monitoring data (Sentry, DataDog)
- Integrate with services (Notion, Figma, Slack)

## Adding MCP Servers

### Remote HTTP Server (Recommended)

```bash
claude mcp add --transport http <name> <url>
```

**Examples:**
```bash
# Sentry error monitoring
claude mcp add --transport http sentry https://mcp.sentry.dev/mcp

# GitHub integration
claude mcp add --transport http github https://api.githubcopilot.com/mcp/

# With authentication
claude mcp add --transport http api https://api.example.com/mcp \
  --header "Authorization: Bearer your-token"
```

### Local Stdio Server

```bash
claude mcp add --transport stdio <name> -- <command> [args...]
```

**Examples:**
```bash
# Database connection
claude mcp add --transport stdio db -- npx -y @bytebase/dbhub \
  --dsn "postgresql://user:pass@localhost:5432/mydb"

# Airtable
claude mcp add --transport stdio airtable \
  --env AIRTABLE_API_KEY=YOUR_KEY \
  -- npx -y airtable-mcp-server
```

## Server Scopes

| Scope | Storage | Use Case |
|-------|---------|----------|
| Local (default) | `~/.claude.json` | Personal, experimental |
| Project | `.mcp.json` | Team-shared via git |
| User | `~/.claude.json` | Personal across all projects |

**Set scope:**
```bash
claude mcp add --transport http api --scope project https://api.example.com/mcp
```

## Managing Servers

```bash
# List all servers
claude mcp list

# Get server details
claude mcp get github

# Remove a server
claude mcp remove github

# Check status in Claude Code
/mcp
```

## Using MCP Resources

Reference resources with `@` in your prompts:

```
> Analyze @github:issue://123
> Review @docs:file://api/authentication
> Query @postgres:schema://users
```

## Using MCP Prompts

Access server prompts with `/`:

```
> /mcp__github__list_prs
> /mcp__github__pr_review 456
```

## Project Configuration

Create `.mcp.json` in project root for team-shared servers:

```json
{
  "mcpServers": {
    "api": {
      "type": "http",
      "url": "https://api.example.com/mcp",
      "headers": {
        "Authorization": "Bearer ${API_TOKEN}"
      }
    },
    "local-db": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@bytebase/dbhub", "--dsn", "${DB_URL}"],
      "env": {
        "DEBUG": "true"
      }
    }
  }
}
```

Environment variables use `${VAR}` or `${VAR:-default}` syntax.

## Authentication

For OAuth-based servers:

1. Add the server
2. Run `/mcp` in Claude Code
3. Click authenticate and complete browser flow
4. Tokens auto-refresh

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Connection timeout | Set `MCP_TIMEOUT=10000` env var |
| Output too large | Set `MAX_MCP_OUTPUT_TOKENS=50000` |
| Windows stdio errors | Use `cmd /c` wrapper |
| Server not appearing | Restart Claude Code, check `/mcp` |

## Quick Reference

| Command | Purpose |
|---------|---------|
| `claude mcp add` | Add a new server |
| `claude mcp list` | List all servers |
| `claude mcp get <name>` | Show server config |
| `claude mcp remove <name>` | Remove a server |
| `/mcp` | Check status & authenticate |

## Tips

- Use project scope (`.mcp.json`) for team consistency
- Store credentials in environment variables, not config files
- Test local servers before sharing with team
- Use `/mcp` to verify server connections
