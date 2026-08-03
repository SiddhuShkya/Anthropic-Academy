# Agents and Tools

**Agents** = AI systems that create their own plans to complete a task, using the tools they're given. Effective when the exact steps needed are unknown.

**Workflows** = better when the precise steps are already known.

## Key Differences

Workflows require predetermined steps; agents dynamically plan using their available tools.

## Agent Advantages

- Flexibility to solve a variety of tasks with the same toolset
- Can combine tools in unexpected ways

## Tool Abstraction Principle

Provide **generic/abstract tools**, rather than hyper-specialized ones.

> Example: Claude Code uses abstract tools like `bash`, `web_fetch`, and `file_write` — rather than narrow, single-purpose tools like `refactor_tool` or `install_dependencies`.

## Tool Combination Example

`get_current_datetime` + `add_duration` + `set_reminder` can solve a wide variety of time-related tasks, through different combinations.

## Agent Behavior

- Can request additional information when needed
- Combines tools creatively to achieve goals
- Works best with a small set of flexible tools

## Design Approach

Give an agent abstract tools that can be pieced together, rather than single-purpose specialized ones. This enables dynamic problem-solving and unexpected, emergent use cases.
