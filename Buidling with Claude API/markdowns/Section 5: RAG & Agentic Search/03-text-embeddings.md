# Text embeddings

After breaking a document into chunks, the next step in a RAG pipeline is finding which chunks are most relevant to a user's question. This is essentially a search problem - you need to look through all your text chunks and identify the ones that relate to what the user is asking about.

<img src="../../../images/Builiding-With-Claude-API/RAG/relevant-chunk.png" alt="image" width="100%"/>

## Semantic Search

The most common approach for finding relevant chunks is semantic search. Unlike keyword-based search that looks for exact word matches, semantic search uses text embeddings to understand the meaning and context of both the user's question and each text chunk.

<img src="../../../images/Builiding-With-Claude-API/RAG/semantic-search.png" alt="image" width="100%"/>

## Text Embeddings

A text embedding is a numerical representation of the meaning contained in some text. Think of it as converting words and sentences into a format that computers can work with mathematically.

<img src="../../../images/Builiding-With-Claude-API/RAG/text-embeddings.png" alt="image" width="100%"/>

Here's how the process works:

- You feed text into an embedding model
- The model outputs a long list of numbers (the embedding)
- Each number ranges from -1 to +1
- These numbers represent different qualities or features of the input text

## Understanding the Numbers

Each number in an embedding is essentially a "score" for some quality of the input text. However, here's the important caveat: we don't know precisely what each number represents.

<img src="../../../images/Builiding-With-Claude-API/RAG/embedding-numbers.png" alt="image" width="100%"/>

While it's helpful to imagine that one number might represent "how happy the text is" or "how much the text talks about oceans," these are just conceptual examples. The actual meaning of each dimension is learned by the model during training and isn't directly interpretable by humans.

## VoyageAI for Embeddings

Since Anthropic doesn't currently provide embedding generation, the recommended provider is VoyageAI. You'll need to:

- Sign up for a separate VoyageAI account
- Get an API key (free to get started)
- Add the key to your environment variables

<img src="../../../images/Builiding-With-Claude-API/RAG/voyageai-signup.png" alt="image" width="100%"/>

In your .env file, add:

```bash
VOYAGE_API_KEY="your_key_here"
```

## Implementation

First, install the VoyageAI library:

```bash
%pip install voyageai
```

Then set up the client and create a function to generate embeddings:

```python
from dotenv import load_dotenv
import voyageai

load_dotenv()
client = voyageai.Client()

def generate_embedding(text, model="voyage-3-large", input_type="query"):
    result = client.embed([text], model=model, input_type=input_type)
    return result.embeddings[0]
```

When you run this function on a text chunk, you'll get back a list of floating-point numbers representing the embedding. The process is quick and straightforward - the real challenge is understanding how to use these embeddings effectively in your RAG pipeline for finding the most relevant content.

<img src="../../../images/Builiding-With-Claude-API/RAG/generate-embedding.png" alt="image" width="100%"/>

The next step is learning how to compare embeddings to determine which chunks are most similar to a user's question, which forms the core of the semantic search process.