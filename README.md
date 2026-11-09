<p align="center"><img src="assets/logo.svg" width="72" alt="Beefi logo"></p>

<h1 align="center">Beefi MCP</h1>

<p align="center">SEC EDGAR data for your AI app. Financials, insider trades, 13F holdings, filings and macro for every US public company.</p>

<p align="center">
  <a href="https://www.beefi.ai">Website</a> ·
  <a href="https://www.beefi.ai/docs/mcp">Docs</a> ·
  <a href="https://www.beefi.ai/pricing">Pricing</a> ·
  <a href="https://registry.modelcontextprotocol.io/v0.1/servers?search=ai.beefi">MCP Registry</a>
</p>

Beefi is a hosted MCP server at `https://mcp.beefi.ai/mcp`. Connect it to Claude, ChatGPT, Cursor or any MCP client and ask about US public companies. Answers come from SEC filings, and every statement period links back to the 10-K or 10-Q it came from.

This repo holds the install files for Claude Code, Cursor and other clients. The server itself is hosted by Beefi, so there is nothing to run.

## What you can ask

- "Show insider sales at NVIDIA in the last 3 months."
- "Compare Microsoft and Alphabet's operating margins over the last 3 years."
- "How has Apple's free cash flow changed over the last 5 years?"
- "List Tesla's 8-K filings from the last 6 months and what each was about."
- "Summarize the risk factors in Nvidia's latest 10-K."

## Install

### Claude Code

```bash
claude plugin marketplace add capaxelabs/plugins
claude plugin install beefi@capaxe
```

Then run `/mcp` in Claude Code, pick **beefi** and sign in to Beefi. No API key needed.

Prefer a plain MCP server over a plugin:

```bash
claude mcp add --transport http beefi https://mcp.beefi.ai/mcp
```

### Claude.ai and Claude Desktop

1. Open **Settings > Connectors** and select **Add custom connector**.
2. Name it **Beefi** and paste `https://mcp.beefi.ai/mcp`.
3. Select **Connect** and sign in.

### ChatGPT

1. Open **Settings > Apps & Connectors > Advanced settings** and turn on **Developer mode**.
2. In **Apps & Connectors**, select **Create**.
3. Name it **Beefi**, paste `https://mcp.beefi.ai/mcp` and choose **OAuth**.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "beefi": { "url": "https://mcp.beefi.ai/mcp" }
  }
}
```

### VS Code

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "beefi": { "type": "http", "url": "https://mcp.beefi.ai/mcp" }
  }
}
```

### Any other MCP client

| Setting | Value |
| --- | --- |
| URL | `https://mcp.beefi.ai/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth, or an API key in the `X-API-Key` header |

Create API keys in your [Beefi dashboard](https://www.beefi.ai/dashboard/api-keys).

## Tools

30+ read-only tools, grouped by what they cover:

| Area | Tools |
| --- | --- |
| Financial statements | `get_income_statement`, `get_balance_sheet`, `get_cash_flow`, `get_all_financials`, `get_segmented_financials` |
| Ratios and earnings | `get_financial_metrics`, `get_financial_metrics_snapshot`, `get_earnings`, `screen_stocks` |
| Insiders and owners | `get_insider_trades`, `get_insider_ownership`, `get_beneficial_ownership`, `get_institutional_holdings` |
| Filings | `get_sec_filings`, `get_filing_items`, `get_ipos` |
| Prices and macro | `get_stock_prices`, `get_price_snapshot`, `get_interest_rates`, `get_macro_data` |
| Discovery | `search_companies`, `get_company_facts`, `get_coverage` |

The full list is in the [MCP docs](https://www.beefi.ai/docs/mcp).

## Plans

The free plan includes 10,000 requests a month and 100 a minute. Every tool call counts as one request. See [pricing](https://www.beefi.ai/pricing) for higher limits.

## Links

- Website: https://www.beefi.ai
- Docs: https://www.beefi.ai/docs/mcp
- Privacy: https://www.beefi.ai/privacy-policy
- Terms: https://www.beefi.ai/terms-of-service
- Support: https://www.beefi.ai/contact

Data comes from SEC EDGAR filings. Beefi is not investment advice.

## License

The files in this repo are MIT licensed. Use of the Beefi service is covered by its [terms](https://www.beefi.ai/terms-of-service).
