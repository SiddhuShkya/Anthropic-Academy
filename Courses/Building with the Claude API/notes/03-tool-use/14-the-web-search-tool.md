# The Web Search Tool

A **built-in** Claude tool for searching the web to find up-to-date or specialized information.

## Implementation

No custom code needed — Claude handles search execution automatically.

## Schema Requirements

```json
{
  "type": "web_search_20250305",
  "name": "web_search",
  "max_uses": 5,
  "allowed_domains": ["optional", "list", "of", "domains"]
}
```

- `max_uses` — limits total searches (default 5)
- `allowed_domains` — optional, restricts search to specific domains

## Response Structure

- **Text blocks** — Claude's explanatory text
- **Tool use blocks** — the search queries Claude executed
- **Web search result blocks** — found pages (title, URL)
- **Citation blocks** — specific text supporting Claude's statements

## Key Features

- Multiple searches per request, up to `max_uses`
- Domain restriction for quality control
- A citation system linking statements back to source material

## UI Rendering Pattern

- Display text blocks as normal text
- Show search results as a reference list
- Highlight citations with source attribution (domain, title, URL, quoted text)

## Use Case Example

Restricting search to `NIH.gov` for medical/exercise advice ensures scientifically-backed information, versus generic web content.
