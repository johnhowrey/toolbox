# Toolbox

Small tools for people shipping with agents. Each one does a single mundane job, runs as a web form, a JSON endpoint and an MCP tool, and never calls a model.

**Live:** https://toolbox.allthepossibles.com (docs: `/docs`, machine-readable: `/llms.txt`)
**Built by:** [All the Possibles](https://allthepossibles.com)
**Registry:** `com.allthepossibles/toolbox` in the official MCP Registry

## The tools

| MCP tool | REST | What it does |
| --- | --- | --- |
| `check_tells` | `POST /api/tells` | Finds AI-writing tells in text (em-dashes, negative parallels, triads, stock vocabulary, hedges, smart quotes, hidden Unicode) and hands back a cleaned copy. |
| `manifest_cost` | `POST /api/manifest-cost` | Does the full handshake against an MCP endpoint, or reads a pasted tools array, and reports what `tools/list` costs per session, per tool, with the expensive descriptions named. |
| `lint_agent_md` | `POST /api/agent-md-lint` | Lints a CLAUDE.md, AGENTS.md or MEMORY.md: line count against the 200-line memory index cap, estimated tokens, duplicate lines, empty headings, leftover TODOs, contradicting rules. |
| `mcp_install_snippets` | `POST /api/mcp-install` | From an endpoint URL, generates `claude mcp add`, Claude Desktop JSON, Cursor `mcp.json`, Codex config and a curl handshake, after probing the URL once. |
| `check_ai_crawlers` | `POST /api/ai-crawlers` | Reads a site's robots.txt, reports which AI crawlers are allowed or blocked, checks for llms.txt, and drafts one. |

## Using it

**As an MCP server:**

```json
{
  "mcpServers": {
    "toolbox": { "url": "https://toolbox.allthepossibles.com/mcp" }
  }
}
```

**REST:**

```
curl -X POST https://toolbox.allthepossibles.com/api/tells \
  -H "content-type: application/json" \
  -d '{"text": "Paste anything here."}'
```

Full reference: https://toolbox.allthepossibles.com/docs

## Pricing

Free with daily caps per tool and no signup. Pro is $5/month: no daily caps, 300 requests a minute, larger inputs, and a key that works on `/mcp` too. Included in the [Studio Bundle](https://allthepossibles.com).

## Issues

Open one here. Which tool would you cut, and what small thing would you add instead?
