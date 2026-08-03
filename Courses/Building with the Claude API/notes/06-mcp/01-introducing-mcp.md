# Introducing MCP

**MCP (Model Context Protocol)** = a communication layer that provides Claude with context and tools, without requiring developers to write tedious integration code.

## Architecture

An **MCP client** connects to an **MCP server**. The server contains tools, resources, and prompts as internal components.

## Problem Solved

Eliminates the burden of authoring and maintaining numerous tool schemas and functions for every service integration.

> Example: a GitHub chatbot would otherwise require implementing separate tools for repositories, pull requests, issues, and projects — significant developer effort.

## Solution

The MCP server handles tool definition and execution, instead of your application server. MCP servers act as interfaces to outside services, wrapping their functionality into ready-to-use tools.

## Key Benefits

Developers avoid writing tool schemas and function implementations themselves.

## Common Questions

- **Who creates MCP servers?** Anyone — often service providers build official implementations (AWS, etc.)
- **vs. direct API calls?** MCP eliminates the need to author tool schemas/functions yourself
- **vs. tool use?** MCP and tool use are complementary — MCP determines *who* does the work (server vs. developer); both still ultimately involve tools

## Core Value

Shifts the integration burden from application developers to MCP server maintainers.
