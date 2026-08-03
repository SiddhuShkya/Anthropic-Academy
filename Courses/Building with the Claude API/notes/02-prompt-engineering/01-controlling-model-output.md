# Controlling Model Output

Two key techniques for steering Claude's output beyond editing the prompt itself.

## Pre-filling Assistant Messages

Manually add an assistant message at the end of the conversation to steer the response direction.

**How it works:**
- Assemble a messages list containing the user prompt + a manually written assistant message
- Claude treats the assistant message as already-authored content
- Claude continues the response from the *exact end* of the pre-filled text
- The output gets steered toward the pre-filled direction

> **Note:** Claude continues from the exact endpoint of the pre-fill — not from a complete sentence. You must stitch the pre-fill and the generated continuation together yourself.

**Example:** Pre-fill `"Coffee is better because"` → Claude continues with a justification for coffee.

## Stop Sequences

Force Claude to halt generation the moment a specific string is produced.

**How it works:**
- Provide a stop-sequence string in the chat call
- When Claude generates that exact string, generation stops immediately
- The stop-sequence text itself is **not** included in the final output

**Example:** Prompt "count 1 to 10" + stop sequence `"five"` → output stops at `"four, "` (the word "five" is excluded)

**Refinement:** Using stop sequence `", five"` produces a cleaner output: `"one, two, three, four"`

## Summary

Both techniques give precise control over response direction and length **without changing the core prompt**.
