# AugeLab for Codex and Claude Code

Describe a visual inspection task and work with AugeLab Studio through its local
MCP server. One shared skill uses the running Studio's tools and documentation.

**0.1.0 beta:** Codex local installation is verified. Live Studio workflows and
Claude Code runtime testing are still pending. [Türkçe kurulum](README.tr.md).

## Prerequisites

- AugeLab Studio with MCP support, installed and running on the same computer as
  your local Codex or Claude Code session.
- Start the server in Studio: **Chat > Settings > MCP > Start**.
- The default endpoint is `http://127.0.0.1:8765/mcp`.
- This plugin does not include Studio, a Studio license, or Studio dependencies.

## Install from GitHub

The commands below apply after this repository is published at
`AugelabTech/augelab-codex-claude-plugin`.

### Codex

```sh
codex plugin marketplace add AugelabTech/augelab-codex-claude-plugin
codex plugin add augelab@augelab-plugins
```

Start a new local chat and use `$augelab`, for example:

> $augelab Inspect Studio's current status without changing or running a project.

### Claude Code

Run these commands inside Claude Code:

```text
/plugin marketplace add AugelabTech/augelab-codex-claude-plugin
/plugin install augelab@augelab-plugins
```

Start a new session and invoke `/augelab:augelab`, or ask Claude to use AugeLab.
This configuration targets **Claude Code**, not the separate Claude Desktop chat
configuration file. Claude discovers the plugin's shared `.mcp.json` and `skills/`.

## Install from a local folder or ZIP

Extract the marketplace ZIP first. From the extracted root:

```sh
codex plugin marketplace add .
codex plugin add augelab@augelab-plugins
```

For Claude Code, from that directory:

```sh
claude plugin marketplace add .
claude plugin install augelab@augelab-plugins
```

## Connection troubleshooting

Check the **active address** shown in Studio. Enabling startup alone does not start
the current MCP server. If the configured port is occupied, Studio may start on
the next port.

For a custom port, use a local checkout and change `plugins/augelab/.mcp.json` to
the displayed loopback address. Keep the connection local. Reinstall through the
client's plugin manager and start a new chat; do not edit generated cache files.
Do not add both a Git-backed and a local marketplace with the same name: choose
one source. Removing a marketplace does not remove the source files.

For updates to a Git-backed installation:

```sh
codex plugin marketplace upgrade augelab-plugins
codex plugin add augelab@augelab-plugins
```

In Claude Code use `/plugin marketplace update augelab-plugins`, then
`/plugin update augelab@augelab-plugins`. Restart the client session afterward.

## Validate and package

Python 3.12+, standard library only:

```sh
python scripts/package.py
```

Outputs:

- `dist/augelab-0.1.0.zip`: plugin root, including both hidden client manifests.
- `dist/augelab-marketplace-0.1.0.zip`: both catalogs, plugin, and installation docs.
- `dist/SHA256SUMS.txt`: archive checksums.

The packager uses explicit file allowlists and validates archive contents.
GitHub Actions runs the same command on pushes and pull requests. Package checks
do not replace the [desktop smoke test](docs/smoke-test.md).

## What is included

```text
.agents/plugins/marketplace.json       Codex catalog
.claude-plugin/marketplace.json        Claude Code catalog
plugins/augelab/
  .codex-plugin/plugin.json            Codex metadata
  .claude-plugin/plugin.json           Claude Code metadata
  .mcp.json                           Shared local MCP connection
  skills/augelab/SKILL.md              One shared entry-point skill
```

This repository contains the plugin only, not the proprietary Studio source.
GitHub distribution does not imply listing in either vendor's official directory.
See [OpenAI submission preparation](docs/openai-submission.md) for that separate process.

## Report an issue

Include the client and Studio versions, OS, installation method, and a redacted
error message. Do not attach credentials, license files, customer images, or
private project files. For connection errors, include the port, not private logs.

## References

- [Codex plugin packaging](https://developers.openai.com/plugins/build/plugins)
- [Claude Code marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
- [Claude Code plugin manifests](https://code.claude.com/docs/en/plugins-reference)
