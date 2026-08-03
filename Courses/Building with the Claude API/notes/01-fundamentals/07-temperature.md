# Temperature

> Video Link: [Temperature](https://anthropic.skilljar.com/claude-with-the-anthropic-api/287728)

> Notebook: [004_temperature.ipynb](../../notebooks/004_temperature.ipynb)

Temperature is a powerful parameter that controls how predictable or creative Claude's responses will be. Understanding how to use it effectively can dramatically improve your AI applications.

## How Claude Generates Text

Before diving into temperature, it helps to understand Claude's text generation process. When you send Claude a prompt like "What do you think?", it goes through three key steps:

- `Tokenization` - Breaking your input into smaller chunks
- `Prediction` - Calculating probabilities for possible next words
- `Sampling` - Choosing a token based on those probabilities

<img src="../../images/fundamentals/claude-text-generation.png" alt="image" width="100%"/>

In this example, Claude might assign a 30% probability to "about", 20% to "would", 10% to "of", and so on. The model then selects one token and repeats this entire process to build complete sentences.

<img src="../../images/fundamentals/selection-probability.png" alt="image" width="100%"/>

## What Temperature Does

Temperature is a decimal value between 0 and 1 that directly influences these selection probabilities. It's like adjusting the "creativity dial" on Claude's responses.

<img src="../../images/fundamentals/temperature-change.png" alt="image" width="100%"/>

At low temperatures (near 0), Claude becomes very deterministic - it almost always picks the highest probability token. At high temperatures (near 1), Claude distributes probability more evenly across options, leading to more varied and creative outputs.

## Interactive Temperature Demo

You can see temperature in action with Claude's interactive demo. Watch how the probability distribution changes as you adjust the temperature slider:

<img src="../../images/fundamentals/temperature-change-demo.png" alt="image" width="100%"/>

At temperature 0.0, "about" gets 100% probability - completely deterministic. At temperature 1.0, probabilities spread more evenly across all possible tokens, introducing randomness and creativity.

## Choosing the Right Temperature

Different tasks call for different temperature ranges:

<img src="../../images/fundamentals/temp-ranges.png" alt="image" width="100%"/>

### Low Temperature (0.0 - 0.3)

- Factual responses
- Coding assistance
- Data extraction
- Content moderation

### Medium Temperature (0.4 - 0.7)

- Summarization
- Educational content
- Problem-solving
- Creative writing with constraints

### High Temperature (0.8 - 1.0)

- Brainstorming
- Creative writing
- Marketing content
- Joke generation

## Implementing Temperature in Code

Adding temperature support to your chat function is straightforward. Here's how to modify your existing function:

```python
def chat(messages, system=None, temperature=1.0):
    params = {
        "model": model,
        "max_tokens": 1000,
        "messages": messages,
        "temperature": temperature
    }
    
    if system:
        params["system"] = system
    
    message = client.messages.create(**params)
    return message.content[0].text
```

The key changes are adding temperature=1.0 as a parameter and including "temperature": temperature in the params dictionary.

## Testing Temperature Effects

To see temperature in action, try generating movie ideas with different settings:

```python
# Low temperature - more predictable
answer = chat(messages, temperature=0.0)

# High temperature - more creative  
answer = chat(messages, temperature=1.0)
```

At temperature 0.0, you might consistently get responses like "A time-traveling archaeologist must prevent ancient artifacts from being stolen." At temperature 1.0, you'll see much more variety in themes, characters, and plot elements.

## Key Takeaways

Remember that temperature doesn't guarantee different outputs - it just changes the probability of getting them. Even at high temperatures, Claude might occasionally produce similar responses. The key is matching your temperature choice to your specific use case:

- Need consistent, factual responses? Use low temperature
- Want creative brainstorming? Dial up the temperature
- Somewhere in between? Medium temperatures work well for most general tasks

Temperature is one of the most practical parameters you can adjust to fine-tune Claude's behavior for your specific needs.