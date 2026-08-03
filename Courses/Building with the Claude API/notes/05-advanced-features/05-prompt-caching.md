# Prompt Caching

A feature that speeds up Claude's responses and reduces text-generation costs by reusing computational work from previous requests.

## Normal Request Flow (Without Caching)

```
User sends message
  → Claude processes input (internal data structures, calculations)
  → Claude generates output
  → Claude discards all processing work
  → Ready for the next request
```

## The Problem

When a follow-up request contains identical input, Claude must repeat all the same computational work it just threw away — pure inefficiency.

## The Solution

Prompt caching **stores** the results of input processing in a temporary cache, instead of discarding them. When identical input reappears in a later request, Claude retrieves the cached work instead of reprocessing it — dramatically speeding up response generation.

## Key Benefit

Reuses prior computational work to avoid redundant processing of repeated content.
