# Whale-alerts

## TradingView MCP setup

This project registers the
[TradingView MCP server](https://github.com/atilaahmettaner/tradingview-mcp)
([`tradingview-mcp-server`](https://pypi.org/project/tradingview-mcp-server/) on
PyPI) so Claude Code (and other MCP clients) can pull TradingView data —
price/market data, screeners, technical analysis, backtesting, and
news/sentiment (30+ tools).

The server is defined in [`.mcp.json`](./.mcp.json) at the project scope, which is
the checked-in equivalent of running:

```
claude mcp add tradingview -- "C:\Users\blake\.local\bin\uvx.exe" --from tradingview-mcp-server --python 3.13 tradingview-mcp
```

### Requirements

- [`uv` / `uvx`](https://docs.astral.sh/uv/) installed. `uvx` runs the
  `tradingview-mcp-server` package in an isolated environment.
- Python 3.10–3.13 (the config pins `--python 3.13`, fetched automatically by
  `uvx` if not present). Avoid 3.14.

### Optional: news & sentiment API key

The `financial_news` and `market_sentiment` tools use [Marketaux](https://www.marketaux.com/)
(free tier: 100 requests/day). Without a token they return a "not configured"
note; all other tools work from public endpoints with no key.

To enable them, set a `MARKETAUX_API_TOKEN` env var for the server in
`.mcp.json`:

```json
{
  "mcpServers": {
    "tradingview": {
      "command": "C:\\Users\\blake\\.local\\bin\\uvx.exe",
      "args": ["--from", "tradingview-mcp-server", "--python", "3.13", "tradingview-mcp"],
      "env": { "MARKETAUX_API_TOKEN": "your-token-here" }
    }
  }
}
```

Don't commit a real token — keep it local or use an environment reference.

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
