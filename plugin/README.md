# Xenition plugin

One package for every place Xenition is installed from: the MCP server, the
skills that tell the model how to use it, and the MCP Registry entry.

## One address

**`https://api.xenition.com/mcp`** does everything: documents, decks, sheets,
boards, forms, apps, automations, ledger, calculators, and AI images, video and
voice. It is the address to give users, testers and every assistant: ChatGPT,
Claude, Claude Code, VS Code, Cursor and Microsoft 365 Copilot.

A second address exists for one case:

| Address | What it is | Used for |
|---|---|---|
| `https://api.xenition.com/mcp/workspace` | `/mcp` without AI image, video and audio | The Claude connector-directory submission, which does not accept connectors that generate media with AI. |

Same account, same sign-in and same credits on both.

## What is in this folder

| Path | What it is |
|---|---|
| `.claude-plugin/plugin.json` | Claude Code / Claude plugin manifest |
| `.mcp.json` | the server: `/mcp` |
| `skills/` | `xenition-workspace` plus four workflow skills: `app-from-idea`, `weekly-report-automation`, `explainer-video`, `deck-from-conversation` |
| `registry/server.json` | MCP Registry entry `com.xenition.api/xenition` (schema 2025-12-11, validated) |
| `../.claude-plugin/marketplace.json` | lets `/plugin marketplace add <this repo>` find the plugin |

## Check before release

```sh
claude plugin validate plugin     # manifest + skills
claude plugin validate .          # marketplace
```

## Try it locally

```sh
claude --plugin-dir ./plugin
```

## Publish to the MCP Registry

The `com.xenition.api/*` name is proved by owning `api.xenition.com`, which
serves the registry proof at `https://api.xenition.com/.well-known/mcp-registry-auth`.

```sh
mcp-publisher login http --domain api.xenition.com --private-key <key>
mcp-publisher publish registry/server.json
```

Bump `version` in `plugin.json` and `registry/server.json` together.

## Store submissions

- **ChatGPT:** submit `https://api.xenition.com/mcp` and upload the `skills/`
  folder.
- **Claude connector directory:** submit
  `https://api.xenition.com/mcp/workspace`, the one address without AI media.
  Claude users who want images, video and voice add
  `https://api.xenition.com/mcp` as a custom connector instead.
