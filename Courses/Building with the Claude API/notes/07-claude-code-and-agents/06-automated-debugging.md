# Automated Debugging

Using Claude to automatically detect, analyze, and fix production errors, without manual intervention.

## Core Workflow

1. A GitHub Action runs daily, checking the production environment
2. It fetches CloudWatch logs from the last 24 hours
3. Claude identifies errors and deduplicates them
4. Claude analyzes each error and generates a fix
5. Creates a pull request with the proposed solution(s)

## Key Components

- **GitHub Actions** — for scheduling/automation
- **AWS CLI** — for log retrieval
- **Claude Code** — for error analysis and code fixes
- **CloudWatch** — for production error monitoring

## Benefits

- Catches production-only errors (issues not present in development)
- Reduces manual log-hunting and debugging time
- Provides context-aware fixes with explanations
- Creates reviewable pull requests for changes

## Common Use Case

Configuration errors between environments — e.g., invalid model IDs, API keys — that work locally but fail in production.

## Implementation Requirements

Repository access, a cloud logging service, an AI coding assistant, and CI/CD pipeline integration.
