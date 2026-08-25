# Model Based Grading

An evaluation system that takes model outputs and assigns objective scores (typically on a 1–10 scale, where 10 = highest quality).

## Three Grader Types

1. **Code graders** — programmatic checks (length, word presence, syntax validation, readability scores)
2. **Model graders** — an additional API call to evaluate the original output; highly flexible for quality/instruction-following assessment
3. **Human graders** — a person evaluates responses; most flexible, but time-consuming and tedious

## Key Requirements

- Must return an objective, usually numerical, signal
- Evaluation criteria must be defined upfront

## Implementation Pattern for Model Graders

1. Create a detailed prompt requesting strengths, weaknesses, reasoning, *and* a score — not just a bare score, to avoid defaulting to middling values
2. Use JSON response format with pre-filled assistant message + stop sequences
3. Parse the returned JSON for the score and reasoning
4. Calculate average scores across all test cases for a final metric

## Trade-off

Model graders offer high flexibility but can be inconsistent — still, they provide a solid objective baseline for prompt optimization.
