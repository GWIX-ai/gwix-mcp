# GWIX MCP server

GWIX gives AI agents pay, hiring demand, company, occupation and workforce statistics for 247 countries. It combines job-ad data with official statistics (BLS, Census Bureau, ONS and others) in one taxonomy. Every answer carries its source, data release, sample size and a citation, and all tools are read-only.

This repository holds the public configuration for the hosted GWIX MCP server: connection files for MCP clients and the registry manifest. The server itself is hosted by GWIX; its source code is not published here.

| | |
|---|---|
| Server address | `https://api.gwix.ai/mcp` (streamable HTTP) |
| Free sample, no account | `https://api.gwix.ai/mcp/sample` (data about six months behind, a few questions a day) |
| Official MCP Registry | [`ai.gwix/gwix`](https://registry.modelcontextprotocol.io/v0.1/servers?search=gwix) |
| Setup guide | https://gwix.ai/mcp |
| API reference | https://api.gwix.ai/docs |

## Sign-in

- **OAuth sign-in** (default). Your client opens the GWIX sign-in page: sign in or create a free account, pick your organization and allow access. Clients without a browser can use OAuth device sign-in.
- **API key**. Create a key in the [GWIX console](https://api.gwix.ai/console) under API keys and send it as `Authorization: Bearer YOUR_GWIX_API_KEY`. Keep the key secret: store it in your agent's secrets, never in client-side code.

## Setup

### Claude (desktop, web and mobile)

1. Open Settings, then Connectors, and choose Add custom connector.
2. Name it GWIX, paste `https://api.gwix.ai/mcp` and click Add.
3. Click Connect, sign in to GWIX, pick your organization and allow access.
4. In a chat, open the tools menu and make sure GWIX is turned on.

### ChatGPT

1. Open Settings, then Apps and Connectors, and add a custom connector (your workspace may need developer mode turned on).
2. Paste `https://api.gwix.ai/mcp` and choose OAuth sign-in.
3. Sign in to GWIX, pick your organization and allow access.

### Cursor and other MCP clients

Add this to your client's MCP settings (in Cursor, `~/.cursor/mcp.json`). Your client opens the GWIX sign-in page in your browser.

```json
{
  "mcpServers": {
    "gwix": { "url": "https://api.gwix.ai/mcp" }
  }
}
```

### With an API key (servers and agents)

```json
{
  "mcpServers": {
    "gwix": {
      "url": "https://api.gwix.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_GWIX_API_KEY" }
    }
  }
}
```

## Tools

**Answers and reports**

| Tool | What it does |
|---|---|
| `get_job_summary` | Quick headline pay summary for an occupation in a place, with citation |
| `ask_gwix` | Full sourced report for any pay, hiring or job market question |
| `salary_and_hiring_report` | Full sourced salary and hiring report for a job and place |
| `job_offer_check` | Judges whether a job offer or current salary is competitive |
| `pay_by_experience_level` | Entry, intermediate and senior pay, with the premium for each step |
| `compare_pay_by_location` | Compares a job's pay across cities, states or countries |
| `pay_by_industry_or_setting` | How a job's pay varies by industry or work setting |
| `explain_pay_figures` | Explains why pay figures differ, moved or look the way they do |
| `hiring_demand_report` | Openings, whether hiring is rising, and where demand is growing |
| `company_hiring_report` | A named company's hiring focus and pay versus its market |
| `labor_market_report` | Hiring conditions and wage pressure for a city, state or country |
| `talent_supply_report` | An occupation's talent pool size and worker movement |
| `workforce_turnover_report` | Quits, separations and tenure from official statistics |
| `workforce_representation_report` | Aggregate gender representation in an occupation or industry |

**Lookups and raw data**

| Tool | What it does |
|---|---|
| `job_title_lookup` | Maps a plain job title to its occupation, code and specialty |
| `find_id` | Converts place, company, ticker or job family names into GWIX IDs |
| `describe_id` | Explains a GWIX ID's name, type, parents and attributes |
| `map_occupation_code` | Converts occupation codes across SOC, O*NET, ISCO, ESCO and GWIX roles |
| `get_pay` | Raw advertised pay percentile rows, for builders |
| `get_postings` | Raw job-ad count rows by period, for builders |
| `list_dimensions` | Accepted filters, their ID formats and lookups |
| `list_periods` | Converts period labels into exact start and end dates |
| `get_fx_rates` | Exchange rates GWIX used when reporting pay in USD |

**Reference and account**

| Tool | What it does |
|---|---|
| `what_gwix_covers` | Covered topics and which tool answers each kind of question |
| `read_guide` | Definitions, sample-size rules and wording for results |
| `get_data_status` | The live data release, last complete week and country coverage |
| `get_account_usage` | Your organization's credit balance, expiry and usage |

## Licence and terms

The files in this repository are released under the [MIT License](LICENSE). Use of the GWIX service is governed by the [GWIX Terms of Use](https://gwix.ai/terms) and [Privacy Policy](https://gwix.ai/privacy).

## Security

See [SECURITY.md](SECURITY.md).
