# Parallelization Workflows

Breaking one complex task into **multiple simultaneous subtasks**, then aggregating the results.

## Example: Material Selection for Parts

- **Instead of:** one large prompt asking Claude to choose between metal / polymer / ceramic / composite, weighing all criteria at once
- **Use:** separate parallel requests, each evaluating one material's suitability, followed by a final aggregation step that compares the results

## Structure

```
Input → Multiple parallel subtasks → Aggregator → Final output
```

## Benefits

- **Focus** — each subtask handles one specific analysis, instead of juggling multiple considerations at once
- **Modularity** — individual prompts can be improved/evaluated separately
- **Scalability** — easy to add new subtasks without affecting existing ones
- **Quality** — reduces confusion caused by overly complex, single-shot prompts

## Key Principle

Decompose complex decisions into specialized parallel analyses, then synthesize the results.
