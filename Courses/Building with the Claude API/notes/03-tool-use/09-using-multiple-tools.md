# Using Multiple Tools

Adding additional tools to an existing tool system after the initial framework is set up.

## Process (3 Steps)

1. Add the new tool's schema to the `RunConversation` function's `tools` list
2. Add a conditional case in `RunTool` to handle the new tool name
3. Implement the actual tool function

## Key Components

- **`RunConversation` function** — contains the tools list that makes Claude aware of what's available
- **`RunTool` function** — routes tool calls to the appropriate function based on name
- **Tool schemas** — define the tool's structure for the model
- **Tool functions** — the actual implementation code

## Example Tools Added

- `AddDurationToDateTime` — calculates a date/time with a duration offset
- `SetReminder` — creates a reminder (mock implementation that just prints a confirmation)

## Tool Chaining

The AI can use multiple tools sequentially within a single conversation — e.g., calculate a date first, then set a reminder using that result.

## Message Structure

Assistant responses can contain multiple blocks: text blocks *and* tool-use blocks in the same message.

## Scalability

Once the framework is in place, adding new tools becomes a simple, repeatable pattern: **schema + routing + implementation.**
