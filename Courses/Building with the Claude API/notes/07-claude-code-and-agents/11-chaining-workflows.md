# Chaining Workflows

Breaking a large task into a series of distinct, **sequential steps**, rather than a single complex prompt.

## Core Concept

Instead of one massive prompt with multiple requirements, split it into separate calls, where each call focuses on one specific subtask.

## Example Workflow

```
User enters topic
  → search trending topics
  → Claude selects the most interesting
  → Claude researches the topic
  → Claude writes a script
  → generate video
  → post to social media
```

## Key Benefit

Allows the AI to focus on individual tasks, rather than juggling multiple constraints simultaneously.

## Primary Use Case

When Claude consistently ignores constraints in complex prompts, despite repetition. This is especially common with long prompts containing many "don't do X" requirements.

### Problem Scenario

A long prompt with constraints (don't mention AI, no emojis, professional tone) → Claude violates some constraints regardless of how many times they're repeated.

### Solution

1. **Step 1** — send the initial prompt, accept an imperfect output
2. **Step 2** — send a follow-up prompt, asking Claude to rewrite based on the specific violations found

## Critical Insight

Even a simple-seeming task can benefit from a workflow when dealing with constraint-heavy prompts that AI struggles to follow completely in a single pass.
