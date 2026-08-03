# Defining Resources

**MCP Resources** = a mechanism allowing MCP servers to expose data to clients for read operations.

## Resource Types

- **Direct** — a static URI, e.g. `docs://documents`
- **Templated** — a parameterized URI, e.g. `docs://documents/{doc_id}`

**URI** = the address/identifier used to access a specific resource, defined when the resource is created.

## Resource Flow

```
client sends "read resource" request with URI
  → server matches URI to a function
  → server executes the function
  → returns data in a "read resource" result
```

## Implementation

Use the `@mcp.resource` decorator with a URI and a MIME-type parameter.

## MIME Types

A hint to the client about the returned data's format:
- `application/json` — for structured data
- `text/plain` — for plain text

## Templated Resources

URI parameters are automatically parsed by the SDK and passed as keyword arguments to the handler function.

## Resources vs. Tools

- **Resources** — provide data *proactively* (e.g. fetch document contents when `@` mentioned)
- **Tools** — perform actions *reactively* (when Claude decides to call them)

## Data Return

The SDK automatically serializes returned data to strings; the client is responsible for deserialization.

## Testing

The MCP Inspector can list direct and templated resources separately, letting you test individual resource calls.
