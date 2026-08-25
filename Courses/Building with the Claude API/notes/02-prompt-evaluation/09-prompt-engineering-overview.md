# Prompt Engineering (Module Overview)

Prompt engineering = improving prompts to get more reliable, higher-quality outputs from language models.

## Module Structure

Start with an initial, poor prompt → apply prompt-engineering techniques step-by-step → evaluate improvement after each technique → observe performance gains over time.

## Example Goal

Generate a one-day meal plan for athletes based on height, weight, physical goal, and dietary restrictions.

## Technical Setup

- An updated eval pipeline with a flexible prompt-evaluator class
- Supports concurrency (adjust `max_concurrent_tasks` based on rate limits)
- `generate_dataset()` method creates test cases with specified inputs
- `run_prompt()` function processes each test case individually

## Key Components

- `prompt_input_spec` — dictionary defining required prompt inputs
- `extra_criteria` — additional validation requirements for model grading
- `output.html` — a formatted evaluation report showing test-case results and scores

## Process

Write initial prompt → interpolate test-case inputs → run evaluation → apply engineering techniques → re-evaluate → repeat until satisfactory.

## Initial Results

Expect poor scores at first (example: **2.32**) with basic prompts, especially on less capable models. Scores improve as techniques are applied.
