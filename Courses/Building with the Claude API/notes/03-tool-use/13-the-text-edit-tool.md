# The Text Edit Tool

A **built-in** Claude tool for file/text operations — read, write, create, replace, and undo on files or directories.

## Key Characteristics

- One of the only tools with a JSON schema built into Claude itself — the implementation still has to be custom-coded
- A small schema *stub* sent to Claude gets auto-expanded into the full schema behind the scenes
- The schema `type` string varies by Claude model version (3.5 vs 3.7 use different dated schema strings)
- Enables Claude to act as a software engineer out-of-the-box

## Required Implementation

- A custom class/set of functions to handle Claude's tool-use requests
- Functions for: viewing files, string replacement, file creation, etc.
- Note: actual filesystem operations are **not** provided by Claude — you implement them

## Workflow

1. Send a minimal schema stub to Claude (name + version-specific `type` date)
2. Claude expands it into the full schema internally
3. Claude sends tool-use requests
4. Your custom implementation executes the actual file operations
5. Results are sent back to Claude

## Use Cases

- Replicating AI code-editor functionality
- Filesystem operations where a native editor is unavailable
- Automated code generation/refactoring
- Multi-file project manipulation

## Benefit

Approximates a full-featured code editor's capabilities through API calls, rather than requiring a GUI.
