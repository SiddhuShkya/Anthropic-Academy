# How Computer Use Works

Computer use is implemented as a **tool system**, allowing Claude to interact with computing environments.

## Standard Tool Use Flow

```
User sends message + tool schema
  → Claude responds with a tool use request (ID, name, input)
  → server executes code
  → result sent back to Claude as a tool result
```

## Computer Use Follows the Identical Flow

- A special tool schema is sent to Claude (a small schema expands to a larger structure behind the scenes)
- The expanded schema includes an `action` function with arguments: mouse move, left click, screenshot, etc.
- Claude sends a tool-use request
- Developers must fulfill the request via the computing environment (typically a Docker container)
- The container executes programmatic key presses/mouse movements
- The response is sent back to Claude

## Key Points

- Claude does **not** directly manipulate computers
- Computer use = tool system + a developer-provided computing environment
- Anthropic provides a reference implementation (a Docker container with pre-built mouse/keyboard execution code)
- Setup requires Docker + a simple command execution
- Enables a direct chat interface for testing Claude's computer-use functionality

## Summary

Computer use is an abstraction layer: the tool system handles communication with Claude, while the Docker container handles the actual computer interactions.
