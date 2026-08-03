# Citations

A feature allowing Claude to reference source documents, showing users exactly where information comes from.

## Citation Types

- `citation_page_location` — for PDF documents; shows document index/title/start page/end page/cited text
- `citation_char_location` — for plain text; shows character position within a text block

## Implementation

1. Add `"citations": {"enabled": true}` to the request
2. Add a `"title"` field to identify the source document
3. Works with both PDF files and plain text sources

## Response Structure

Content becomes a list of text blocks, some of which include a `citations` array with location data.

## Purpose

Gives users transparency — they can verify Claude's information sources and check the accuracy of its interpretations.

## UI Benefit

Enables citation popups/overlays showing the source document, page numbers, and exact cited text on hover.

## Key Use Case

Ensuring users can investigate *how* Claude built a response from source materials, rather than the response appearing to come purely "from memory."
