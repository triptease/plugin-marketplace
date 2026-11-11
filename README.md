# Triptease agent plugins

The public plugin marketplace from Triptease. It works with Claude (Claude Code) and with
OpenAI (ChatGPT and Codex).

## Install

In Claude Code:

```
/plugin marketplace add triptease/plugin-marketplace
/plugin install triptease@triptease
```

In Codex:

```
codex plugin marketplace add triptease/plugin-marketplace
```

Then install the `triptease` plugin from the Triptease marketplace in `/plugins`.

## Plugins

| Plugin                   | What it does                  |
| ------------------------ | ----------------------------- |
| [`triptease`](triptease) | Connects to the Triptease MCP |

## Layout

Each plugin has one set of files for Claude and one for OpenAI. Skills are shared.

```
.claude-plugin/marketplace.json   # Claude marketplace
.agents/plugins/marketplace.json  # OpenAI marketplace
<name>/
  .claude-plugin/plugin.json      # Claude manifest
  .mcp.json                       # Claude MCP servers
  plugin.json                     # OpenAI manifest (Agent Plugins format)
  mcp.json                        # OpenAI MCP servers (Agent Plugins format)
  skills/<skill>/SKILL.md         # Skills, read by both (add when needed)
```

## Adding a plugin

1. Create the plugin folder with `.claude-plugin/plugin.json` and `plugin.json`.
2. Add the plugin to both marketplace files. The OpenAI entry also needs `policy` and `category`.
3. If it adds an MCP server, put it in `.mcp.json` (`"type": "http"`) and in `mcp.json`
   (`"type": "streamable-http"`).
4. Check it with `claude plugin validate .`.

Keep `name`, `version` and `description` the same in both manifests.
