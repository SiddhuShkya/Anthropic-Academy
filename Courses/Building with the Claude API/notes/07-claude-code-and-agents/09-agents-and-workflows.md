# Agents and Workflows

Two strategies for handling user tasks that can't be completed by Claude in a single request.

## Decision Rule

- **Use workflows** when you have precise task understanding and know the exact sequence of steps
- **Use agents** when task details are unclear

## Workflow

A series of calls to Claude for a specific problem, where the steps are predetermined.

### Example Workflow: Image → 3D Model Converter

1. Claude describes the uploaded image in detail
2. Claude uses the CADQuery Python library to model the object from the description
3. Create a rendering of the model
4. Claude compares the rendering to the original image
5. If inaccurate, repeat from step 2 with feedback

This follows the **evaluator-optimizer pattern**:
- **Producer** — generates output (Claude + CADQuery modeling)
- **Evaluator** — assesses output quality (the comparison step)
- The loop continues until the evaluator accepts the output

## Key Point

Workflows are implementation patterns other engineers have successfully used. *Identifying* a workflow pattern doesn't automatically implement it — you still need to write the actual code.
