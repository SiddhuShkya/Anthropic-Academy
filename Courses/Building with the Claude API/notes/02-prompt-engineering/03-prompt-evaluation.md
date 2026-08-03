# Prompt Evaluation

**Prompt engineering** = techniques for writing and editing prompts to help Claude understand requests and produce the desired response.

**Prompt evaluation** = automated testing of prompts using objective metrics to measure their effectiveness.

## Three Paths After Writing a Prompt

1. Test once or twice, then deploy straight to production — ⚠️ a common trap
2. Test with a few custom inputs, tweak for edge cases — ⚠️ also a trap
3. Run the prompt through a full evaluation pipeline for objective scoring — ✅ recommended

## Key Takeaway

Engineers commonly **under-test** prompts. Use evaluation pipelines to get objective performance scores *before* iterating and deploying.
