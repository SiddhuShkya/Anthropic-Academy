# The Full RAG Flow

A 7-step process combining text chunking, embeddings, and vector search to retrieve relevant context for LLM queries.

## The 7 Steps

1. **Text Chunking** — split source documents into separate text pieces
2. **Generate Embeddings** — convert text chunks into numerical vectors using an embedding model
3. **Normalization** — scale vector magnitudes to 1.0 (usually handled automatically by embedding APIs)
4. **Vector Database Storage** — store embeddings in a database optimized for numerical vector operations
5. **Query Processing** — convert the user's question into an embedding, using the same model
6. **Similarity Search** — find the most similar stored embeddings via cosine similarity
7. **Prompt Assembly** — combine the user's question with the retrieved chunks, and send to the LLM

## Key Math Concepts

- **Cosine similarity** — the cosine of the angle between two vectors; ranges from -1 to 1, where closer to 1 means more similar
- **Cosine distance** — `1 - cosine similarity`; values closer to 0 mean higher similarity
- **Vector database** — performs the similarity calculations to find the closest matching embeddings

## Process Flow

```
Pre-processing (steps 1–4)
      ↓
   User Query
      ↓
Real-time retrieval (steps 5–7)
      ↓
  LLM Response
```
