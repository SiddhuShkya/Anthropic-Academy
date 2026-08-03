# Project Setup — CLI Chatbot

A CLI-based chatbot project used to teach MCP client-server interaction through hands-on implementation.

## Project Components

- **MCP client** — connects to a custom MCP server
- **MCP server** — provides 2 tools (read document, update document)
- **Document collection** — fake documents stored purely in memory

> **Key distinction:** normal projects typically implement *either* the client OR the server, not both. This project implements both, for educational purposes.

## Setup Process

1. Download the `CLI_project.zip` starter code
2. Extract and open it in a code editor
3. Follow the `readme.md` setup directions
4. Add your API key to the `.env` file
5. Install dependencies (with or without UV)
6. Run the project: `uv run main.py` or `python main.py`
7. Test with a chat prompt

## Expected Outcome

A working chat interface that responds to basic queries, ready for MCP feature additions.
