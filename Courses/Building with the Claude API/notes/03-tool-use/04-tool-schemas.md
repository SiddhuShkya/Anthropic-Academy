# Tool Schemas

JSON Schema specifications that describe tool functions and their parameters for the language model.

**JSON Schema** = a general-purpose data validation specification (not ML-specific), adopted by the ML community for tool calling.

## Tool Schema Structure

- `name` — the tool identifier
- `description` — 3–4 sentences explaining what the tool does, when to use it, and what data it returns
- `input_schema` — the actual JSON schema describing the function's arguments, with types and descriptions

## Schema Generation Trick

1. Take your tool function to Claude.ai
2. Prompt: *"Write a valid JSON schema spec for tool calling for this function, following best practices in the attached documentation."*
3. Attach the Anthropic API tool-use documentation page
4. Copy the generated schema

## Implementation Pattern

- Name functions descriptively
- Name schemas as `[function_name]_schema`
- Import `ToolParam` from `anthropic.types`
- Wrap the schema dictionary with `ToolParam()` to prevent type errors

## Purpose

Informs Claude about available tools, their required arguments, and when to use them — all in a standardized JSON-validation format.
