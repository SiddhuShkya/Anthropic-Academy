# Providing Examples

**One-shot / multi-shot prompting** = providing examples in a prompt to guide model behavior.
- One-shot = a single example
- Multi-shot = multiple examples

## Implementation

Structure examples with XML tags containing a sample input and its ideal output. Always wrap examples clearly so they're distinguished from the actual prompt content.

## Key Applications

- Handling corner cases (e.g. sarcasm detection, edge scenarios)
- Complex output formatting (e.g. specific JSON structures)
- Clarifying the expected response quality/style

## Best Practices

- Add context for corner cases — e.g. *"be especially careful with sarcasm"*
- Include reasoning that explains **why** an output is ideal
- Use the highest-scoring examples from prior prompt evaluations as templates
- Place examples **after** the main instructions and guidelines

## Effectiveness Boost

Combining examples with explanations of what makes them ideal reinforces the desired output characteristics even further.
