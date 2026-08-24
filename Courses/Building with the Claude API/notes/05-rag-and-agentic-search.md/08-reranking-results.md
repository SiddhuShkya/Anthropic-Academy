# Reranking Results

A post-processing step that uses an LLM to **reorder search results by relevance** after initial retrieval.

## Process

```
run vector + BM25 search
  → merge results
  → pass to LLM with a prompt asking it to rank documents by relevance
  → get reordered results
```

## Implementation Details

- Use document IDs instead of full text, for efficiency
- The LLM receives: the user query + candidate documents + an instruction to return the most relevant docs in decreasing order
- Assistant message pre-fill + a stop sequence ensures structured JSON output

## Trade-offs

- ✅ Increases search accuracy by leveraging the LLM's understanding of semantic relevance
- ❌ Increases latency, due to the additional LLM call

Particularly effective when initial retrieval methods miss nuanced query intent — e.g., "ENG team" vs. "engineering team."

## Example Improvement

Query: *"What did the engineering team do with incident 2023?"* — reranking correctly prioritized the software-engineering section over the cybersecurity section, despite hybrid search initially ranking it lower.
