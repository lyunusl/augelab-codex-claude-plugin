# AugeLab 0.1.4 beta - Codex and Claude Code

First setup now downloads the official Windows EXE from AugeLab's AWS S3 bucket,
checks its reviewed SHA-256, and installs Studio silently when missing. Existing
installations are reused. Existing Codex users can update the plugin:

Claude Code now receives the installed skill's exact setup-script path, including
for inspection-only requests, so it can find the helper without scanning the
user's profile. A fresh Claude desktop Code session verified `-CheckOnly` against
the running Studio using an isolated test plugin.

```sh
codex plugin marketplace upgrade augelab-plugins
codex plugin add augelab@augelab-plugins
```

The single shared skill is also the Codex onboarding entry point. It helps
register or sign in at the official account website, read the relevant
confirmation/license email through authorized Gmail or Outlook tools, and apply
the user's own license key in Studio. User-only sign-in, terms, password,
CAPTCHA, and MFA steps hand off clearly. Missing tools or unavailable licenses
produce specific manual instructions. The plugin grants no license.

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

Select **Run setup** if offered in Codex, or start a new local chat and ask
`$augelab Set up Studio and help activate my license`. In Claude Code use
`/augelab:augelab Set up Studio and activate my license`. Setup installs onto
the same computer as the local agent; it does not use an unattended install hook.

## Assets

- `augelab-0.1.4.zip`: plugin only.
- `augelab-marketplace-0.1.4.zip`: extract to install from a local marketplace.
- `SHA256SUMS.txt`: SHA-256 checksums for both archives.

## Beta limitations

Windows regression tests, package inventory, and local existing-Studio/MCP
detection passed. The real S3 EXE download and pinned hash were checked; the EXE's
silent argument validation returned the documented error code for an invalid path.
A full clean-machine install and fresh account/email/license activation remain
pending. This release is not an OpenAI or Anthropic directory listing.
