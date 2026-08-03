# Extended Thinking

A Claude feature that allows the model reasoning time before generating its final response.

## Key Mechanics

- Displays a separate thinking process, visible to users
- Increases accuracy on complex tasks, but adds cost (thinking tokens are billed) and latency
- **Thinking budget** — a minimum of 1024 tokens allocated for the thinking phase
- `max_tokens` must exceed the thinking budget (e.g., a budget of 1024 requires `max_tokens ≥ 1025`)

## When to Use

- Enable it *after* prompt optimization alone fails to reach the desired accuracy
- Use prompt evals to determine whether it's actually necessary

## Response Structure

- **Thinking block** — contains the reasoning text + a cryptographic signature
- **Text block** — the final response
- **Signature** — prevents tampering with the thinking text (a safety measure)

## Special Cases

- **Redacted thinking blocks** — encrypted thinking text, flagged by safety systems
- Provided to preserve conversation continuity without losing context
- Can be forced for testing using the special string: `"entropic magic string triggered redacted thinking [special characters]"`

## Implementation

Set `thinking=true` and a `thinking_budget` parameter. Ensure `max_tokens > thinking_budget` for adequate response-generation capacity.
