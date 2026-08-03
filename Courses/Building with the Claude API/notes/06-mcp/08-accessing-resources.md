# Accessing Resources

## Resource Reading Function

A client-side function to request and parse resources from an MCP server.

**Function parameter:** `uri` — the resource identifier.

## Implementation Steps

1. Import the `json` module and `AnyURL` from `pydantic`
2. Call `await self.session.read_resource(AnyURL(uri))`
3. Extract the first element from `result.contents[0]`
4. Check `resource.mime_type` to decide how to parse it

## Content Parsing Logic

```python
if resource.mime_type == "application/json":
    return json.loads(resource.text)
else:
    return resource.text
```

## Server Response Structure

`result.contents` is a list, where the first element contains type/mime-type metadata.

## Resource Integration

MCP client functions are called by other application components to fetch document contents for prompts.

## End Result

Document contents are automatically included in Claude prompts, without requiring an explicit tool call.

## Key Point

Resources expose server information directly to clients through a structured request/response pattern.
