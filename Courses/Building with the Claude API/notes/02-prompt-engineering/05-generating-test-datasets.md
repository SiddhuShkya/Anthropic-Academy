# Generating Test Datasets

A custom evaluation workflow: **build prompt → generate test dataset → evaluate performance.**

## Example Goal

An AWS code-assistance prompt that outputs *only* Python, JSON config, or regex — no explanations.

## Generating the Dataset

- Can be assembled manually, or generated automatically with Claude
- Use a fast, cheap model (like Haiku) for generation

## Dataset Structure

An array of JSON objects, each with a `task` property describing a user request.

## Generation Process

1. Prompt Claude to create test cases
2. Pre-fill the assistant message with ` ```json `
3. Set the stop sequence to ` ``` `
4. Parse the response as JSON
5. Save it to a file

## Key Implementation

A `generate_dataset()` function sends the prompt to Claude, receives a structured JSON list of test tasks, and saves it to `dataset.json` for later evaluation use.

This test dataset enables systematic evaluation of the prompt across many input scenarios, revealing performance consistency.
