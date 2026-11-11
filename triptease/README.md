# Triptease

Connects your agent to the Triptease MCP at `https://mcp.triptease.io/mcp`. It gives the agent the
tools from every Triptease product you have access to, behind one sign-in.

The first time the server is used, you are asked to sign in with your Triptease account. In
Claude Code, run `/mcp` to sign in or check the connection.

## Contents

| Path                         | Used by | What it does                  |
| ---------------------------- | ------- | ----------------------------- |
| `.claude-plugin/plugin.json` | Claude  | Plugin manifest               |
| `.mcp.json`                  | Claude  | Adds the Triptease MCP server |
| `plugin.json`                | OpenAI  | Plugin manifest               |
| `mcp.json`                   | OpenAI  | Adds the Triptease MCP server |
