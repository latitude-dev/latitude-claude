# Latitude — Claude Code plugin

One-click install of the [Latitude](https://latitude.so) MCP server inside Claude Code.

After installing and authorizing, Claude Code can read and manage your Latitude workspace: projects, members, keys, traces, annotations, scores, searches, issues, datasets, and more. The full tool catalog is dynamically generated from the [Latitude API](https://api.latitude.so/docs).

## Install

### From the marketplace
Install **Latitude** from the [Claude plugins directory](https://claude.com/plugins).

### Manual (CLI)
```bash
claude mcp add --transport http latitude https://api.latitude.so/v1/mcp --scope user
```

Or edit `~/.claude.json` directly:

```json
{
  "mcpServers": {
    "latitude": {
      "type": "http",
      "url": "https://api.latitude.so/v1/mcp"
    }
  }
}
```

Then inside Claude Code, type `/mcp`, select `latitude`, and **Authenticate**. The MCP server uses OAuth 2.1 with Dynamic Client Registration, so you only ever supply the URL — the client registers itself automatically and walks you through the consent screen to pick which Latitude organization to authorize.

## Local development

```bash
# From the repo root:
claude --plugin-dir ./claude
```

Then inside Claude Code, type `/mcp`, select `latitude`, and authenticate.

To pick up changes without restarting: `/reload-plugins`.

Validate before submitting:

```bash
claude plugin validate ./claude
```

## Layout

```
claude/
├── .claude-plugin/
│   └── plugin.json     # Manifest
├── .mcp.json           # Latitude MCP server config
├── assets/             # Icons
└── README.md
```

No `skills/`, `agents/`, `commands/`, `hooks/`, `monitors/`, `bin/`, `settings.json`, or `.lsp.json` — this plugin only registers the MCP server.

## Submission

Submit at <https://claude.ai/settings/plugins/submit> or <https://platform.claude.com/plugins/submit>. The review pipeline runs `claude plugin validate` and automated safety screening. Approved plugins land in [`anthropics/claude-plugins-community`](https://github.com/anthropics/claude-plugins-community) and sync nightly.

## License

[MIT](./LICENSE)
