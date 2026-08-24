# A Multi-Index RAG Pipeline

A system combining **semantic search** (vector index) and **lexical search** (BM25 index) for improved retrieval accuracy.

## Key Components

- **Vector Index** — semantic similarity search using embeddings
- **BM25 Index** — lexical / keyword-based search
- **Retriever Class** — a wrapper that forwards queries to both indexes and merges the results

## Reciprocal Rank Fusion (RRF)

A technique for merging search results from different indexes.

```
RRF_score = Σ (1 / (rank + 1))   across all search methods, for each document
```

Documents are ranked by their highest combined score.

### Example

- Vector search returns: `[doc2, doc7, doc6]`
- BM25 returns: `[doc6, doc2, doc7]`

After RRF calculation, the final ranking becomes `[doc2, doc6, doc7]` — because `doc2` ranked highly in *both* methods.

## Benefits

- Improved search accuracy by combining different search paradigms
- Modular design with a standardized API (`search()` and `add_document()`)
- Easy to extend with additional search indexes
- Better handling of edge cases where a single method fails

> This implementation pattern lets multiple search methodologies work together while keeping separate, isolated index classes.
