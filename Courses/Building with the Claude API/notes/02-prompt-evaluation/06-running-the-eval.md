# Running the Eval

The process of merging test cases with prompts, running them through the LLM, and grading the outputs.

**Test case** = an individual record from the dataset (a JSON object).

## Three Core Functions

| Function | Role |
|---|---|
| `run_prompt` | Merges a test case with the prompt, sends it to Claude, returns the output |
| `run_test_case` | Calls `run_prompt`, grades the result, returns a summary dictionary |
| `run_eval` | Loops through the dataset, calling `run_test_case` for each, and assembles the results |

## Starting Point (v1)

Basic prompt structure: `"Please solve the following task: [test_case_task]"`

**Current limitations:**
- No output formatting instructions
- Hardcoded scoring (`score = 10`)
- Verbose Claude responses

## Performance

Runtime ≈ 31 seconds for a full dataset run using the Haiku model.

## Output Format

An array of objects, each containing the Claude output, the original test case, and a score.

## Next Step

Implement a proper grading system to replace the hardcoded score.

> **Eval pipeline core:** dataset + prompt + LLM + grader — with minimal code complexity.
