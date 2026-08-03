# The Server Inspector

**MCP Inspector** = an in-browser debugger for testing MCP servers, without needing to connect them to a full application.

## Access

Run in your terminal:

```bash
mcp dev [server_file.py]
```

This opens the server on a port — navigate to the provided URL in your browser.

## Interface

- Left sidebar — a **connect** button
- Top menu — resources / prompts / tools sections
- Tools section — lists available tools; click one to open a testing panel on the right

## Testing Workflow

1. Connect to the server
2. Navigate to **Tools**
3. Select a specific tool
4. Input the required parameters
5. Click **Run Tool**
6. Verify the output

## Key Features

- Live development testing
- Manual tool invocation
- Parameter input forms
- Success/failure feedback
- No need for full application integration

> Note: the UI is actively changing during development, but core functionality remains similar.

## Example Usage

Test document tools by inputting document IDs, verifying read operations, testing edit operations, and chaining operations to confirm changes.

## Primary Benefit

Efficiently debug MCP server implementations during the development phase.
