# Implementing the RAG Flow

A practical walkthrough of the 5-step retrieval-augmented generation process.

## Step 1 — Text Chunking
Split a document into sections using a `chunk_by_section` function on a `report.md` file.

## Step 2 — Embedding Generation
Create vector representations for each chunk using a `generate_embedding` function (supports either a single string or a list of strings as input).

## Step 3 — Vector Store Population
Create a vector-index instance, loop through chunk-embedding pairs with `zip()`, and store each pair via `store.add_vector(embedding, {content: chunk})`. Storing the original text alongside the embedding enables meaningful retrieval results.

## Step 4 — Query Processing
The user asks: *"What did the software engineering department do last year?"* — generate an embedding for this query.

## Step 5 — Similarity Search
Use `store.search(user_embedding, 2)` to find the 2 most relevant chunks. Returns results with cosine distances — e.g. `0.71` for section two, `0.72` for the methodology section.

## Key Components

- **Vector Index Class** — a custom vector-database implementation
- **Cosine Distance** — the similarity metric between query and stored embeddings
- **Metadata Storage** — storing original text content alongside embeddings enables meaningful retrieval

> This workflow is complete but has limitations that require further improvements (see Reranking, Contextual Retrieval, BM25).
