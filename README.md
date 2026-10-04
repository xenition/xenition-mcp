# Xenition MCP

Your Xenition workspace in the chat: documents, decks, sheets, boards, forms,
apps you can build and deploy, scheduled automations, and AI images, video and
voiceover — over the [Model Context Protocol](https://modelcontextprotocol.io).

This repository is the public distribution for the Xenition MCP server: the
connection details, the Claude Code plugin, the skills, and the MCP Registry
entry. The server itself is hosted by Xenition — there is nothing to run or
install from source.

## Connect

One remote address does everything:

```
https://api.xenition.com/mcp
```

It is a standard remote MCP server (Streamable HTTP, OAuth 2.1 sign-in) and
works with ChatGPT, Claude, Claude Code, VS Code, Cursor and Microsoft 365
Copilot.

### Claude Code

Add it as a plugin marketplace, then install the `xenition` plugin:

```sh
/plugin marketplace add xenition/xenition-mcp
/plugin install xenition@xenition
```

Or add the remote server directly:

```sh
claude mcp add --transport http xenition https://api.xenition.com/mcp
```

### VS Code / Cursor

Add an MCP server with URL `https://api.xenition.com/mcp` (HTTP transport). You
will be prompted to sign in to Xenition on first use.

### ChatGPT

Add `https://api.xenition.com/mcp` as a connector.

### Claude connector directory

Use `https://api.xenition.com/mcp/workspace` — the same server without the AI
image, video and audio tools, which the directory does not accept. Everything
else is identical. Users who want media tools add `https://api.xenition.com/mcp`
as a custom connector instead.

## What's in here

| Path | What it is |
|---|---|
| `plugin/` | the Claude Code / Claude plugin: manifest, `.mcp.json`, skills, and the registry entry |
| `plugin/registry/server.json` | the MCP Registry entry `com.xenition.api/xenition` |
| `plugin/skills/` | skills that teach assistants how to use the tools |
| `.claude-plugin/marketplace.json` | makes `/plugin marketplace add` resolve this repo |

See [`plugin/README.md`](plugin/README.md) for packaging and release details.

## Links

- Website: https://xenition.com
- MCP Registry: `com.xenition.api/xenition`

## License

[Apache-2.0](LICENSE).
