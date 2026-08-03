# Sending Tool Results

**Tool results** = the outputs of executed tool functions, sent back to Claude in a follow-up request.

## Process

1. Execute the tool function Claude requested
2. Create a tool-result block
3. Send a follow-up request with the full conversation history

## Tool Result Block Structure

- `tool_use_id` — matches the ID from the original tool-use block, pairing the request with its result
- `content` — the tool function's output, converted to a string (usually JSON)
- `is_error` — boolean flag for execution errors (default `false`)

## Purpose of `tool_use_id`

Links multiple tool requests to the correct results when Claude makes simultaneous tool calls — each tool use gets a unique ID, and each result must reference the matching ID.

## Follow-up Request Requirements

- Include the complete message history (original user message + assistant tool-use message + new user message containing the tool result)
- Include the original tool schemas, even if you're not using tools again
- The tool-result block goes in a **user** message, not an assistant message

## Full Conversation Flow

```
User request
  → Claude's assistant response (text + tool use blocks)
  → server executes the tool
  → user message with tool result block
  → Claude's final response, integrating the results
```
