# Local MCP: Server & Client Setup Guide

This project contains two main components:
- **mcp-server-example/**: A reference implementation of an MCP (Model Context Protocol) server.
- **mcp-client-python/**: A minimal Python client for connecting to a local MCP server.

---

## Prerequisites
- Python 3.11+ (recommended for both server and client)
- [`uv`](https://github.com/astral-sh/uv) package manager (recommended for fast dependency management)

---

## 1. Setting Up & Running the MCP Server

### 1.1. Install `uv` (if not already installed)
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```
Restart your terminal to ensure `uv` is available.

### 1.2. Set Up the Server
```bash
cd mcp-server-example
uv venv
source .venv/bin/activate
uv pip install -r pyproject.toml  # or use `uv add "mcp[cli]" httpx` if no requirements file
```

### 1.3. Run the Server
```bash
uv run main.py
```
The server will start and be ready to accept connections from MCP clients.

---

## 2. Setting Up & Running the MCP Client

### 2.1. Set Up the Client
```bash
cd ../mcp-client-python
python3 -m venv .venv
source .venv/bin/activate
pip install uv
uv pip install -r pyproject.toml
```

### 2.2. Configure Environment Variables
Create a `.env` file in `mcp-client-python/` with the following keys:
```env
# Your Anthropic API key (for Claude models)
ANTHROPIC_API_KEY=your_anthropic_key_here
# Your Serper API key (if used)
SERPER_API_KEY=your_serper_key_here
# Path to your local MCP server script (Python or JS)
SERVER_SCRIPT_PATH=/absolute/path/to/your/mcp-server-example/main.py
```

### 2.3. Run the Client API
```bash
uvicorn api/main:app --reload
```
API docs will be available at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

---

## 3. Workflow: How to Use
1. **Start the MCP server** (in `mcp-server-example`).
2. **Start the MCP client** (in `mcp-client-python`).
3. Interact with the client via its FastAPI endpoints or UI, which will communicate with the running server.

---

## Troubleshooting
- Ensure both server and client virtual environments are activated when running commands.
- Double-check `.env` paths and API keys.
- If the client cannot connect, verify the server is running and the `SERVER_SCRIPT_PATH` is correct.

---

## Credits
- Author: Khant Zwe Naing
- Inspired by open source LLM and MCP projects

## License
MIT 