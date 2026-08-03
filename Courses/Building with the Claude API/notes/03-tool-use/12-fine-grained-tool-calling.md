# Fine-Grained Tool Calling

*(Transcript notes)*

**Tool streaming** = streaming API responses while Claude is using tools.

## Key Components

- Standard streaming returns `content_block_delta` events
- Tool streaming adds `input_json_delta` events, containing:
  - `partial_json` — a chunk
  - `snapshot` — the cumulative sum so far
- Implementation requires handling this additional event type in your streaming pipeline

## Fine-Grained Tool Calling

A feature that **disables JSON validation** for faster streaming.

### Default Behavior

- Claude generates JSON chunks for tool arguments
- The API buffers chunks until a complete top-level key-value pair is generated
- It validates the JSON against the schema before sending chunks to the server
- Result: delays, followed by a burst of chunks arriving all at once

### Fine-Grained Mode (`fine_grained: true`)

- Disables API-side JSON validation
- Sends chunks immediately as they're generated
- Provides a more traditional, smooth streaming experience
- Requires client-side handling for potentially invalid JSON

## Trade-offs

| Mode | Speed | Validation |
|---|---|---|
| Default | Slower | Fully validated JSON |
| Fine-grained | Faster streaming | Possible invalid JSON (e.g. `"undefined"` instead of `null`) |

> Invalid JSON in default mode gets wrapped as a string, rather than a proper object structure.

## Use Cases

Fine-grained mode is useful for immediate UI updates or early processing of tool arguments. Default mode is fine when validation delays are acceptable.
