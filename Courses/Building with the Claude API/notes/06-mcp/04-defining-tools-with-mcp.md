# Defining Tools with MCP

Implementing an MCP server with the Python SDK creates tools through **decorators**, rather than manual JSON schemas.

## MCP Python SDK

The official package auto-generates tool JSON schemas from Python function definitions, using the `@mcp.tool` decorator.

## Tool Definition Syntax

```python
@mcp.tool(name="tool_name", description="description")
def my_tool(arg: str = Field(description="...")):
    ...
```

## Two Example Tools

1. **`read_doc_contents`** — takes a `doc_id` string, returns the document's content from an in-memory `docs` dictionary
2. **`edit_document`** — takes `doc_id`, `old_string`, `new_string` parameters, performs a find/replace on the document's content

## Error Handling

Check whether `doc_id` exists in the `docs` dictionary; raise a `ValueError` if not found.

## Key Advantage

The SDK eliminates manual JSON-schema writing — schemas are generated automatically from your Python function signatures and decorators.

## Required Imports

- `Field` from `pydantic` — for parameter descriptions
- `mcp` package — for the server and tool decorators

## Implementation Pattern

The decorator defines tool metadata; function parameters define the tool's arguments (with types and descriptions); the function body contains the tool's logic.
