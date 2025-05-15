# MCP Client (Python)

A minimal MCP client built in Python for connecting to a local MCP server.

## Highlights

- FastAPI-based API for local MCP tool orchestration
- LLM integration for tool-augmented conversations
- Simple, local-first setup

## Quickstart

- Python 3.11+
- Create a virtual environment:
  ```bash
  python3 -m venv .venv
  ```
- Activate the virtual environment:
  ```bash
  source .venv/bin/activate
  ```
- Install dependencies (recommended: [uv](https://github.com/astral-sh/uv)):
  ```bash
  pip install uv
  uv pip install -r pyproject.toml
  ```
  > **Note:** `requirements.txt` is not included. Use `uv` or `pip` with `pyproject.toml` for dependency management.
- Set up `.env` with your API keys and server script path
- Run:
  ```bash
  uvicorn api/main:app --reload
  ```
- API docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

> **Don't forget:** Always activate your virtual environment before running any commands or scripts.

## Environment Variables

Create a `.env` file in the project root with the following keys:

```env
# Your Anthropic API key (for Claude models)
ANTHROPIC_API_KEY=your_anthropic_key_here

# Your Serper API key (for search tool integration, if used)
SERPER_API_KEY=your_serper_key_here

# Path to your local MCP server script (Python or JS)
SERVER_SCRIPT_PATH=/absolute/path/to/your/mcp_server.py

# (Optional) Add other keys as needed for your LLM or tools
```

- `ANTHROPIC_API_KEY`: Required for Anthropic Claude LLM integration.
- `SERPER_API_KEY`: Required if your MCP server/tools use Serper for search.
- `SERVER_SCRIPT_PATH`: Required. Absolute path to your local MCP server script (e.g., `/home/user/mcp-server/main.py`).
- Add any other keys your setup or tools require.

## Config

- Edit `.env` for API keys (Anthropic, Serper, etc.)
- Point to your local MCP server script in `api/main.py` if needed

## Credits

- Built and maintained by Khant Zwe Naing
- Inspired by the FastAPI and Claude Desktop projects

## License

MIT
