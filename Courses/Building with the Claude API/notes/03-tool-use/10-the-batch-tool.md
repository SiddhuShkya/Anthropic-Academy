# The Batch Tool

A tool that lets Claude run **multiple tools in parallel** within a single assistant message, instead of making separate sequential requests.

## The Problem

Claude can technically send multiple tool-use blocks in one message, but rarely does so in practice — leading to unnecessary sequential tool calls.

## The Solution

Create a batch-tool schema that accepts a **list of invocations** (each containing a tool name + arguments). Instead of calling tools directly, Claude calls the batch tool with an array of desired tool executions.

## Implementation

- Add the batch tool to the schema with an `invocations` parameter
- Create a `run_batch` function that iterates through the invocations list
- Extract the tool name and JSON-parsed arguments from each invocation
- Call `run_tool` for each requested tool
- Return a `batch_output` list containing results from all tool executions

## Mechanism

It essentially "tricks" Claude into parallel tool execution by giving it a higher-level abstraction, which then manually handles what multiple simultaneous tool-use blocks would otherwise accomplish.

## Result

A single request-response cycle instead of multiple sequential rounds, for tasks that can run in parallel.
