# Text Chunking Strategies

The process of dividing documents into smaller pieces for a RAG pipeline.

## Core Problem

Chunking quality directly impacts RAG performance. Poor chunking leads to irrelevant retrieval — e.g., a medical "bug" chunk being retrieved for a software-engineering query about "bugs."

## Three Main Strategies

### 1. Size-Based Chunking
Divide text into equal-length strings.
- ✅ Easy to implement, most common in production
- ❌ Can cut off words mid-way, lacks context
- **Fix:** an *overlap* strategy — include characters from neighboring chunks to preserve context (trades some duplication for better meaning retention)

### 2. Structure-Based Chunking
Divide based on document structure — headers, paragraphs, sections.
- Best for structured documents (Markdown, HTML)
- Limitation: requires guaranteed, consistent document formatting
- Example: split on Markdown `##` headers to create section-based chunks

### 3. Semantic-Based Chunking
Use NLP to group related sentences/sections.
- Most advanced technique
- Groups consecutive sentences based on semantic similarity
- Most complex to implement

## Implementation Notes

| Approach | When to Use |
|---|---|
| Chunk by character | Most reliable fallback — works with any document type |
| Chunk by sentence | Good middle ground, if sentence detection is reliable |
| Chunk by section | Optimal results, but requires structured input |

**Rule of thumb:** there's no universal best chunking method — it depends on your document structure guarantees and use case.
