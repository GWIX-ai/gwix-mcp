Installing the GWIX MCP server

GWIX is a hosted remote MCP server. There is nothing to download, build or run locally: you only add the server address to your MCP settings.

Server address: https://api.gwix.ai/mcp
Transport: streamable HTTP
Setup guide: https://gwix.ai/mcp
Option 1: OAuth sign-in (recommended for people)

Add this to the MCP settings file (in Cline: cline_mcp_settings.json):

json
{
  "mcpServers": {
    "gwix": {
      "type": "streamableHttp",
      "url": "https://api.gwix.ai/mcp"
    }
  }
}

When the client connects, the GWIX sign-in page opens in the browser. The user signs in or creates a free account, picks their organization and allows access. No API key is needed.

Option 2: API key (for clients without OAuth, servers and agents)
Ask the user to sign in at https://api.gwix.ai/console and create an API key under API keys. Do not create or guess a key yourself.
Add the key as a Bearer token:
json
{
  "mcpServers": {
    "gwix": {
      "type": "streamableHttp",
      "url": "https://api.gwix.ai/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_GWIX_API_KEY"
      }
    }
  }
}

Replace YOUR_GWIX_API_KEY with the user's key. Keep the key in the settings file only; never paste it into chat or commit it to a repository.

Try it without an account

For a quick test, use the free sample server instead (data about six months behind, a few questions a day):

json
{
  "mcpServers": {
    "gwix-sample": {
      "type": "streamableHttp",
      "url": "https://api.gwix.ai/mcp/sample"
    }
  }
}
Check that it works

After connecting, the GWIX tools appear in the tool list. Ask a question such as "What do registered nurses earn in Houston?" or "Is hiring for data engineers growing in Germany?". Every answer includes its source and a citation. All tools are read-only.
