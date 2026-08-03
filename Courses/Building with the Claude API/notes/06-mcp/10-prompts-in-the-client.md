# Prompts in the Client

## Client Functions

```python
# List prompts
async def list_prompts():
    result = await self.session.list_prompts()
    return result.prompts

# Get a prompt
async def get_prompt(prompt_name, arguments):
    result = await self.session.get_prompt(prompt_name, arguments)
    return result.messages
```

## Prompt Workflow

1. Define a prompt in the MCP server with expected arguments (e.g., `document_id`)
2. The client calls `get_prompt` with the prompt name + an arguments dictionary
3. Arguments are passed as keyword arguments to the prompt function
4. The function interpolates the arguments into the prompt text
5. Returns a messages array, ready to be fed directly to the LLM

## Key Concept

Prompts are server-defined templates that clients can invoke with specific arguments to generate contextualized instructions for LLMs. Arguments flow:

```
client call → prompt function → interpolated prompt text → LLM consumption
```
