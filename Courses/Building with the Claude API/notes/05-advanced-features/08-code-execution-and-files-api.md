# Code Execution and the Files API

## Files API

Allows uploading files ahead of time and referencing them later via a **file ID**, instead of including raw file data in every request.

```
Upload file → get file metadata object with ID → use ID in future requests
```

## Code Execution

A server-based tool where Claude executes Python code inside isolated Docker containers.

- No implementation needed — just include the predefined tool schema
- Claude can run code multiple times, interpret results, and generate a final response

## Key Constraints

- Docker containers have **no network access**
- Data input/output relies on Files API integration

## Combined Workflow

```
Upload file via Files API
  → get file ID
  → include ID in a container upload block
  → ask Claude to analyze
  → Claude writes/executes code, with access to the uploaded file
  → returns analysis and results
```

## Generated Files

Claude can generate files (plots, reports) inside the container, downloadable using the file IDs returned in the response.

## Use Cases

Data analysis, file processing, and automated code generation for complex tasks. The response contains code blocks, execution results, and a final analysis.

## Implementation

Use a container-upload block with the file ID, include the analysis prompt, and let Claude handle code execution automatically.
