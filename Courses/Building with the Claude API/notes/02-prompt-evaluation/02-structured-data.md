# Structured Data

A technique combining **assistant message pre-filling** + **stop sequences** to get raw output without Claude's natural explanatory headers, footers, or commentary.

## The Problem

Claude tends to automatically add markdown formatting, headers, and commentary when generating JSON/code/structured content. Often, users just want the raw data for copy/paste or programmatic use.

## The Solution Pattern

1. **User message** — request for structured data
2. **Assistant message pre-fill** — the opening delimiter (e.g. ` ```json `)
3. **Stop sequence** — the closing delimiter (e.g. ` ``` `)

## How It Works

Claude sees the pre-filled message, assumes it already started the response, generates only the requested content, then stops the moment it hits the delimiter.

## Result

Raw structured data with no extra formatting or commentary — directly usable, no manual parsing required.

## Applications

Works for any structured data type: JSON, Python code, lists, and more — not just JSON.

## Key Benefit

Output can be used or copied directly, without manually stripping out unwanted explanatory text.
