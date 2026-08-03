# Rules of Prompt Caching

A system that saves processing work from an initial request, for reuse in follow-up requests with identical content.

## Core Mechanism

```
Initial request
  → Claude processes + saves work to cache
  → Follow-up request with identical content
  → Claude retrieves cached work instead of reprocessing
```

## Cache Duration

**1 hour maximum.**

## Activation

Cache activation requires manually adding a **cache breakpoint** to message blocks.

### Text Block Formats

- **Shorthand:** `content = "text string"` — cannot add cache control
- **Longhand:** `content = [{"type": "text", "text": "content", "cache_control": {...}}]` — required for caching

## Cache Scope

All content **up to and including** the breakpoint gets cached.

## Cache Invalidation

Any change in content *before* the breakpoint invalidates the entire cache.

## Content Processing Order

```
tools → system prompt → messages
```
(joined together, in that order)

## Cache Breakpoint Placement Options

- Tool schemas
- System prompts
- Message blocks (text, image, tool use, tool result)

## Limits

- **Maximum 4 breakpoints** per request
- Multiple breakpoints create multiple cache layers — partial cache hits are possible if only later content changes
- **Minimum 1024 tokens** required for content to be cached

## Best Use Cases

Repeated identical content — system prompts, tool definitions, static message prefixes.
