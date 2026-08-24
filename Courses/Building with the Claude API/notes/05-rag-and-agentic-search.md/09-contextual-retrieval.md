# Contextual Retrieval

A technique for improving RAG pipeline accuracy by adding context to document chunks *before* embedding them.

## The Problem

When documents are split into chunks, individual chunks lose the context of the original document — reducing retrieval accuracy.

## The Solution

A pre-processing step that adds contextual information to each chunk before inserting it into the retriever database.

## Process

1. Take an individual chunk + the original source document
2. Send both to an LLM (Claude) with a prompt asking it to generate situating context
3. The LLM generates a brief explanation of the chunk's relationship to the larger document
4. Join the generated context with the original chunk → a **"contextualized chunk"**
5. Use the contextualized chunk as input to the vector/BM25 indexes

## Handling Large Documents

If the source document is too large for a single prompt, use a selective context strategy:
- Include starter chunks (1–3) from the document's beginning for summary/abstract context
- Include chunks immediately before the target chunk, for local context
- Skip middle chunks that provide less relevant context

## Implementation

An `add_context` function takes a text chunk + the source text, generates context via the LLM, concatenates the context with the original chunk, and returns the contextualized version.

## Benefit

Chunks retain ties to the larger document's structure and cross-references, improving retrieval accuracy for complex, interconnected documents.
