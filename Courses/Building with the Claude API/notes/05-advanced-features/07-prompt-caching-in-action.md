# Prompt Caching in Action

Automatically caching tool schemas and system prompts to reduce token usage.

## Setup

Modify the chat function to enable caching by default for tools and system prompts.

## Tool Schema Caching

Add a `cache_control` field with `type: "ephemeral"` to the *last* tool in the list.

> **Best practice:** create a copy of the tools list, clone the last tool's schema, add cache control to the clone, then overwrite — avoiding mutation of the original schemas.

## System Prompt Caching

Wrap the system prompt in a text-block dictionary with `cache_control: {"type": "ephemeral"}`.

## Multiple Cache Breakpoints

You can set cache points for **both** tools and the system prompt in a single request.

## Cache Order

```
tools → system prompt → messages
```

## Token Usage Patterns

- `cache_creation_input_tokens` — tokens written to the cache on first use
- `cache_read_input_tokens` — tokens retrieved from the cache on subsequent identical requests
- Partial cache reads are possible when only some content matches cached data

## Cache Invalidation

Any change to cached content (tools or system prompt) invalidates the cache and forces a new cache creation.

## Use Cases

Identical content across requests — the same tool schemas, system prompts, or message sequences.
