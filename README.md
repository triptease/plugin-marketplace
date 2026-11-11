<p align="center">
  <img src="triptease/assets/icon.png" alt="Triptease logo" width="128" height="128">
</p>

<h1 align="center">Triptease agent plugins</h1>

The public plugin marketplace from Triptease. It works with Claude (Claude Code) and with
OpenAI (ChatGPT and Codex).

## Install

### Claude desktop app or claude.ai

1. Open **Customize > Plugins**.
2. Select **Add > Add marketplace** and enter `triptease/plugin-marketplace`.
3. Find **Triptease** on the **Discover** tab and select **Add**.
4. Open the plugin, go to its **Connectors** tab, then add and connect the Triptease connector.
   Sign in with your Triptease account when asked.

The plugin is saved to your Claude account, so it also works in Cowork and Claude Code. To get
updates without checking by hand, turn on **Sync automatically** for the marketplace.

On Team and Enterprise plans, an Owner may need to allow you to add your own marketplaces, or
add this one for the whole organization.

### ChatGPT desktop app

1. Open **Plugins**, then select **Add > Add a marketplace**.
2. Enter `triptease/plugin-marketplace` as the **Source** and select **Add marketplace**.
3. Select **Browse directory**, go to the **Personal** tab and open **Triptease**.
4. Select **Install plugin**, then sign in with your Triptease account and select **Allow**.

ChatGPT marks the plugin **Desktop only** because it adds an MCP server, so install and use it
in the ChatGPT desktop app.

On Team and Enterprise workspaces, an admin can add the marketplace for everyone instead:

1. Open **Admin > Plugins** and select **Add > Import marketplace**.
2. In **Source**, enter `https://github.com/triptease/plugin-marketplace`. Leave **Path** empty.
3. Select **Import marketplace** and authorize GitHub.
4. Open the **Triptease** plugin and set who can install it.

Members then find **Triptease** on the workspace's tab in **Plugins** and install it from there.

### Claude Code

```
/plugin marketplace add triptease/plugin-marketplace
/plugin install triptease@triptease
```

Run `/mcp` afterwards to sign in.

### Codex

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
