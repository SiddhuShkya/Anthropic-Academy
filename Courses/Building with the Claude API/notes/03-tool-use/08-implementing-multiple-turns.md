# Implementing Multiple Turns

Continuously calling Claude until it stops requesting tools.

## Stop Reason Field

Indicates why Claude stopped generating text.
- `stop_reason = "tool_use"` — Claude wants to call a tool
- Other values exist, but `tool_use` is the one most commonly checked

## `run_conversation` Function (Main Loop)

1. Calls Claude with messages + available tools
2. Adds the assistant response to the conversation history
3. Checks `stop_reason` — if it's not `"tool_use"`, breaks the loop
4. If `tool_use`, calls `run_tools`
5. Adds the tool results as a user message
6. Repeats until no more tool requests

## `run_tools` Function

Processes multiple tool-use blocks:
1. Filters `message.content` for blocks with `type="tool_use"`
2. Iterates through each tool request
3. Runs the appropriate tool function via a `run_tool` helper
4. Creates `tool_result` blocks: `type="tool_result"`, `tool_use_id=original_id`, `content=JSON_encoded_output`, `is_error=boolean`
5. Returns the list of all tool result blocks

## `run_tool` Function (Dispatcher)

- Takes `tool_name` and `tool_input`
- Uses if/elif statements to match tool names to functions
- Executes the appropriate tool function
- Scalable — easy to add more tools

## Error Handling

Wrap tool execution in try/except:
- **Success** → `is_error=false`, `content=tool_output`
- **Failure** → `is_error=true`, `content=error_message`

## Key Architecture Points

- Assistant messages can contain multiple blocks (text + several tool_use blocks)
- Each `tool_use` block gets a separate `tool_result` response
- Tool results are sent back as a single user message containing *all* results
- The process repeats until Claude produces a final, text-only response
