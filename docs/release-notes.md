# AugeLab 0.1.0 beta - Codex and Claude Code

The first AugeLab plugin package connects a local coding agent to an existing
AugeLab Studio installation using MCP. It contains one shared `augelab` skill,
client-specific manifests, and installation instructions in English and Turkish.

## Install

Codex:

```sh
codex plugin marketplace add lyunusl/augelab-codex-claude-plugin
codex plugin add augelab@augelab-plugins
```

Claude Code:

```text
/plugin marketplace add lyunusl/augelab-codex-claude-plugin
/plugin install augelab@augelab-plugins
```

Run Studio on the same computer and start its MCP server first.

## Assets

- `augelab-0.1.0.zip`: plugin only.
- `augelab-marketplace-0.1.0.zip`: extract to install from a local marketplace.
- `SHA256SUMS.txt`: SHA-256 checksums for both archives.

## Beta limitations

Codex local installation and package checks passed. Live Studio workflows and
Claude Code runtime testing remain unverified. Studio is installed separately;
the plugin does not supply a Studio license. This release is not an OpenAI or
Anthropic directory listing.
