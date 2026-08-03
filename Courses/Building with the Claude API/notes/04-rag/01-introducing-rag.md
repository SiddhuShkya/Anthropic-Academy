# Introducing Retrieval Augmented Generation (RAG)

A technique for querying large documents using a language model.

## The Problem

How do you extract specific information from large documents (100–1000+ pages) with Claude, without hitting context limits?

## Option 1 — Direct Approach

Place the entire document text directly into the prompt.

**Limitations:**
- Hard token limits
- Decreased effectiveness with longer prompts
- Higher costs
- Slower processing

## Option 2 — RAG Approach

A two-step process:

1. Break the document into small chunks
2. For each user question, find the most relevant chunks and include *only* those in the prompt

## RAG Benefits

- The model focuses on relevant content
- Scales to large or multiple documents
- Smaller prompts
- Lower costs
- Faster processing

## RAG Downsides

- More implementation complexity
- Requires preprocessing
- Needs a search mechanism to find relevant chunks
- No guarantee that chunks contain complete context
- Multiple chunking strategies are possible (equal portions vs. header-based, etc.)

## Key Challenge

Defining "relevance" and choosing an optimal chunking strategy for your specific use case.

> RAG trades simplicity for scalability and efficiency — but requires careful implementation and evaluation.
