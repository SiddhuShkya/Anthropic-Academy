# Multi-Turn Conversations with Tools

Conversations in which Claude uses **multiple tools sequentially** to answer a single user query.

## Tool Chaining Process

```
user asks question
  → Claude requests first tool
  → tool executed, result returned
  → Claude requests second tool
  → tool executed, result returned
  → Claude provides final answer
```

**Example:** User asks *"what day is 103 days from today?"* → Claude calls `get_current_datetime` → Claude calls `add_duration_to_datetime` → Claude provides the answer.

## Implementation Pattern

A `while` loop that keeps calling Claude until no more tool requests appear, checking each response for `tool_use` blocks.

## `run_conversation` Function

Takes the initial messages, loops through Claude calls, executes requested tools, adds the results to the conversation, and continues until a final response is produced.

## Required Refactors

- `add_user_message` / `add_assistant_message` — updated to handle multiple message blocks, not just plain text
- `chat` function — accepts a `tools` parameter, returns the entire message (not just the first text block)
- `text_from_message` helper — extracts all text blocks from a multi-block message

## Key Insight

You can't predict how many tools a given query will require, so the system must handle **arbitrary chains** of tool calls automatically.
