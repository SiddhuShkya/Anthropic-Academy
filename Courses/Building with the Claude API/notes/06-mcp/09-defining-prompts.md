# Defining Prompts

**MCP Prompts** = pre-defined, tested prompt templates that MCP servers expose to client applications for specialized tasks.

## Purpose

Instead of users writing ad-hoc prompts, server authors create high-quality, evaluated prompts tailored to their server's domain.

## Implementation

Use the `@mcpserver.prompt` decorator with a name/description, and define a function that returns a list of messages (user/assistant messages that can be sent directly to Claude).

## Example Use Case

A document-formatting prompt that takes a document ID, instructs Claude to read the document using tools, reformat it to Markdown, and save the changes.

## Key Benefits

- Server-specific expertise
- Pre-tested quality
- Reusable across client applications
- Better results than user-generated, ad-hoc prompts

## Message Structure

Returns `base.UserMessage` objects containing the formatted prompt text, with interpolated parameters.

## Client Integration

Prompts appear as autocomplete options (slash commands) in client applications — they prompt the user for required parameters, then execute the pre-built prompt workflow.
