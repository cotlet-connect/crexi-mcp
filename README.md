# How to connect Crexi to Claude Code, ChatGPT and any AI agent

**Yes, Claude, ChatGPT and other AI agents can work in your Crexi account.** Crexi's Listing API is only for MLSs and large brokerages. Cotlet.dev connects your own Crexi account to any AI agent, so the AI searches listings, saves deals and tracks them for you.

## What you can ask

> Find retail properties for sale in Austin under $2M with a cap rate above 6%.

> Save the 10 newest industrial listings in Phoenix to my "Q4 deals" list.

> Compare these three listings: price per sq ft, cap rate, days on market.

> Which of my saved properties dropped in price this week?

> Export the contacts of brokers for my saved listings.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install crexi-mcp        # or run it once: uvx crexi-mcp connect
crexi-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 crexi_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 crexi_agent.py status    # is Crexi ready in your Cotlet.dev account
python3 crexi_agent.py guide     # Crexi screens and sign-in link
python3 crexi_agent.py read      # open Crexi, read the page, close the browser
python3 crexi_agent.py tools     # list Cotlet.dev tools
```

## Questions from Crexi users

**Does Crexi have an API?**

Crexi has a Listing API only for qualifying MLSs, brokerages and data providers. Cotlet.dev works in your own Crexi account, so your AI agent can search and track deals without it.

**How do I connect Crexi to ChatGPT?**

Add Cotlet.dev as an app in ChatGPT (Settings → Apps, connector URL `https://cotlet.dev/mcp/v1`), sign in to Crexi once in your Cotlet.dev Cloud Browser, and ask ChatGPT in plain words. No code and no Crexi API key.

**Is there a way to use Claude with Crexi?**

Yes. In Claude Code run the one-line `claude mcp add` command above; in the Claude app add `https://cotlet.dev/mcp/v1` as a custom connector. Claude then works in your own Crexi account.

**Is there a Crexi MCP server?**

Crexi has no official MCP server. Cotlet.dev is a hosted MCP server that works in Crexi for you, 24/7, with Claude, ChatGPT, Cursor, Codex, n8n, Make and Zapier.

## Also works with

- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/crexi-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=crexi

Start free: https://cotlet.dev/signup?app=crexi&utm_source=github&utm_medium=readme&utm_campaign=crexi
