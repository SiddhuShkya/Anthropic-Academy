# Code Based Grading

Automated validation for LLM outputs that should contain code, JSON, or regex.

## Core Implementation

| Validator | Behavior |
|---|---|
| `validate_json()` | Attempts JSON parsing → returns `10` if valid, `0` if error |
| `validate_python()` | Attempts AST parsing → returns `10` if valid, `0` if error |
| `validate_regex()` | Attempts regex compilation → returns `10` if valid, `0` if error |

## Dataset Requirements

- Must include a `"format"` key specifying the expected output type (JSON / Python / RegEx)
- Update the dataset-generation prompt template accordingly

## Prompt Engineering

- Instruct the model to respond only with raw code/JSON/regex
- No comments, explanations, or commentary
- Use a pre-filled assistant message with ` ```code``` ` blocks
- Add stop sequences to extract clean output

## Scoring System

```
final_score = (model_score + syntax_score) / 2
```

This combines semantic evaluation with syntax validation, measuring both correctness and technical validity.

## Key Limitation

Requires a known expected format up front, in order to select the correct validator.
