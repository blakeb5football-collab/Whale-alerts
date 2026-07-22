# Whale-alerts

## TradingView MCP setup

This project registers a [TradingView MCP server](https://pypi.org/project/tradingview-mcp-server/)
so Claude Code (and other MCP clients) can pull TradingView data.

The server is defined in [`.mcp.json`](./.mcp.json) at the project scope, which is
the checked-in equivalent of running:

```
claude mcp add tradingview -- "C:\Users\blake\.local\bin\uvx.exe" --from tradingview-mcp-server --python 3.13 tradingview-mcp
```

### Requirements

- [`uv` / `uvx`](https://docs.astral.sh/uv/) installed. `uvx` runs the
  `tradingview-mcp-server` package in an isolated environment.
- Python 3.13 (fetched automatically by `uvx --python 3.13` if not present).

### Usage

Open this folder with Claude Code. When prompted, approve the project-scoped
`tradingview` MCP server. Verify it is connected with:

```
claude mcp list
```

### Portability note

`.mcp.json` currently points at an absolute Windows path
(`C:\Users\blake\.local\bin\uvx.exe`). If you run this project on another machine
or OS where `uvx` is on your `PATH`, change the `command` to just `"uvx"`:

```json
{
  "mcpServers": {
    "tradingview": {
      "command": "uvx",
      "args": ["--from", "tradingview-mcp-server", "--python", "3.13", "tradingview-mcp"]
    }
  }
}
```
