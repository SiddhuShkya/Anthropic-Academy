# Handling Message Blocks

## Making Tool-Enabled Requests

Include the tool schema in the request alongside the user message, using the `tools` keyword argument.

## Multi-Block Messages

Message content now contains **multiple blocks** instead of a single text block.

A tool-use response from the assistant includes:
- **Text block** — user-facing explanation
- **Tool use block** — the function name + arguments to execute

## Message History Management

**Critical requirement:** manually maintain conversation history, since Claude stores nothing between requests.

**Multi-block handling:** append the assistant's *entire* `response.content` (all blocks) to the messages list — not just the text.

**Helper function updates needed:** `add_user_message` and `add_assistant_message` must support multiple blocks, not just single text strings.

## Conversation Flow

```
user message → assistant response (with tool use block) → execute tool → respond back to Claude with full history
```
