# Tools for Structured Data

An alternative method for extracting structured JSON from data — using Claude's **tool system** instead of message pre-fill and stop sequences.

## Differences from Prompt-Based Extraction

| | Prompt-based | Tool-based |
|---|---|---|
| Reliability | Lower | **More reliable** |
| Setup complexity | Simple | More complex |
| Requires JSON schema | No | **Yes** |

## Core Process

1. Define a JSON schema for the tool, where the inputs *are* the desired data structure
2. Send the prompt + schema to Claude
3. Claude calls the tool with structured arguments matching the schema
4. Extract the JSON from the tool-use block (no tool result needed)

## Critical Requirement: Force Tool Calling

Use the `tool_choice` parameter:

```python
tool_choice = {"type": "tool", "name": "your_tool_name"}
```

This ensures Claude *always* calls the specified tool.

## Implementation Steps

1. Create a schema definition for the extraction tool
2. Update the chat function to accept a `tool_choice` parameter
3. Pass `tool_choice` to `client.messages.create()`
4. Access the structured data via `response.content[0].input`

## When to Use

Prompt-based methods are better for quick, simple extractions. Tools are better when **reliability** matters more than simplicity — for complex, high-stakes extractions.
