# Parallelizing Claude Code

Running **multiple Claude instances simultaneously** to complete different tasks in parallel.

## Core Problem

Multiple Claude instances modifying the same files at the same time creates conflicts and invalid code.

## Solution: Git Work Trees

Git work trees provide **isolated workspaces** per Claude instance.

**Git Work Trees** — a Git feature that creates complete project copies in separate directories, each corresponding to a different branch.

## Workflow

```
create work tree
  → assign a task to a Claude instance
  → work in isolation
  → commit changes
  → merge back to main branch
```

## Custom Commands

Automate work-tree creation/management via the `.claude/commands` directory, containing Markdown files with prompts.

**Command structure:** `.claude/commands/filename.md`, using an `$ARGUMENTS` placeholder for dynamic values.

## Benefits

A single developer can command a virtual team of software engineers — major productivity scaling, limited only by your capacity to manage simultaneous tasks.

## Merge Conflicts

Claude automatically resolves conflicts during the branch-merging process.

## Cleanup

Claude handles work-tree removal after feature completion.

## Key Advantage

Scales to unlimited parallel instances, based on the developer's capacity to manage them.
