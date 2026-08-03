# Implementing a Client

## MCP Client

A wrapper class around the client session, used for resource cleanup and connection management to an MCP server.

## Client Session

The actual connection to the MCP server, provided by the MCP Python SDK — requires proper resource cleanup on close.

## Client Purpose

Exposes MCP server functionality to the rest of your codebase, enabling you to reach out to the server for tool lists and tool execution.

## Key Functions

```python
async def list_tools():
    result = await self.session.list_tools()
    return result.tools

async def call_tool(tool_name, tool_input):
    return await self.session.call_tool(tool_name, tool_input)
```

## Usage Flow

The client fetches tool definitions to send to Claude, then executes tools when Claude requests them.

## Common Pattern

Wrap the client session in a larger class for resource management, rather than using the session object directly.

## Testing

You can run the client file directly with a testing harness to verify the server connection and tool retrieval.

## Integration

Other code in the project calls client functions to interact with the MCP server — enabling Claude to inspect and edit documents through the defined tools.
