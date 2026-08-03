# MCP Clients

**MCP Client** = the communication interface between your server and an MCP server, giving access to the server's tools.

## Transport Agnostic

Client and server can communicate over multiple protocols (stdio, HTTP, WebSockets). A common setup runs client and server on the same machine using standard input/output.

## Communication

Message exchange follows the MCP spec.

### Key Message Types

- **list tools request** — client asks the server for available tools
- **list tools result** — server responds with the tool list
- **call tool request** — client asks the server to run a tool with arguments
- **call tool result** — server responds with the tool's execution result

## Typical Flow

1. User queries the server
2. Server requests the tool list from the MCP client
3. MCP client sends a "list tools" request to the MCP server
4. MCP server responds with the "list tools" result
5. Server sends the query + tools to Claude
6. Claude requests a tool execution
7. Server asks the MCP client to run the tool
8. MCP client sends a "call tool" request to the MCP server
9. MCP server executes the tool (e.g., a GitHub API call)
10. Results flow back: MCP server → MCP client → server → Claude → user

## Purpose

Enables servers to delegate tool execution to specialized MCP servers, while still maintaining Claude integration.
