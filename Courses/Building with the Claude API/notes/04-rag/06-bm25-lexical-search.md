# BM25 Lexical Search

**BM25** ("Best Match 25") = a lexical search algorithm commonly used in RAG pipelines to complement semantic search.

## Problem with Semantic Search Alone

It can miss exact term matches — returning irrelevant results even when specific terms appear frequently in certain documents.

## Hybrid Search Approach

Combine **semantic search** (embeddings/vector database) with **lexical search** (BM25) in parallel, then merge the results for a better balance.

## BM25 Algorithm Steps

1. Tokenize the user query into separate terms (strip punctuation, split on spaces)
2. Count the frequency of each term across all text chunks/documents
3. Assign relative importance to terms based on usage frequency — rare terms get higher importance, common terms (like "a") get lower importance
4. Rank text chunks by how often they contain the higher-weighted terms

## Key Insight

Frequently used terms across the corpus are *less* important for relevance than rare, specific terms.

## Advantages of BM25

- Better at finding exact term matches
- Prioritizes documents containing rare/specific search terms
- Complements the weaknesses of pure semantic search

## Implementation

Both semantic and lexical search systems use similar APIs (`add_document`, `search`), making them easy to combine.

**Next step:** merge results from both systems to get the benefits of semantic understanding *plus* exact term matching.
