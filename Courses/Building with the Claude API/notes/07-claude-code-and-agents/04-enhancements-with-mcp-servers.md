# Enhancements with MCP Servers

Claude Code has an embedded MCP client that can connect to MCP servers to expand its functionality.

## MCP Server Integration

Connect an external tool/service to Claude Code with:

```bash
claude mcp add [server-name] [startup-command]
```

## Example Implementation

A document-processing server exposing a "Document Path to Markdown" tool, letting Claude Code read PDF/Word documents by running `uv run main.py`.

## Dynamic Capability Expansion

MCP servers add new functions to Claude Code in real time, without any core modifications.

## Common Use Cases

- Production monitoring (Sentry)
- Project management (Jira)
- Communication (Slack)
- Custom development-workflow tools

## Key Benefit

A significant flexibility increase for development workflows, through modular server connections.

## Setup Process

1. Create an MCP server with tools
2. Add the server to Claude Code with a name and startup command
3. Restart Claude Code to access the new capabilities
