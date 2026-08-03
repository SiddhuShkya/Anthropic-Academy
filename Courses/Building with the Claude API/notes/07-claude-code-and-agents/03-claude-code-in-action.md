# Claude Code in Action

Claude Code functions as a **collaborative engineer** on your project — not just a code generator.

## Key Capabilities

Project setup, feature design, code writing, testing, deployment, and fixing production errors.

## Setup Workflow

1. Download the project, open it in your editor
2. Run `claude` to launch
3. Ask Claude to read the README and follow the setup directions
4. Run the `init` command — Claude scans the codebase's architecture and coding style, and creates a `claude.md` file
5. `claude.md` — automatically included as context for all future requests

## Memory Types

- **Project** memory (shared)
- **Local** memory
- **User** memory files

## Context Management

- Use the `#` symbol to add specific notes to memory
- You can manually edit `claude.md`, or rerun `init` to refresh it
- Claude can handle Git operations (staging, committing)

## Effective Prompting Strategies

### Method 1 — Three-Step Workflow
1. Identify relevant files, ask Claude to analyze them
2. Describe the feature, ask Claude to plan a solution (no code yet)
3. Ask Claude to implement the plan

### Method 2 — Test-Driven Development
1. Provide relevant context
2. Ask Claude to suggest tests for the feature
3. Select and implement chosen tests
4. Ask Claude to write code until the tests pass

## Core Principle

Claude Code is an **effort multiplier**. More detailed instructions lead to significantly better results — treat it as a collaborative engineer, not just a code generator.
