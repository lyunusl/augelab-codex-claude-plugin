---
name: augelab
description: Set up AugeLab Studio, install the Windows desktop app, help register and activate a license, and create, inspect, edit, or troubleshoot computer vision and AI workflows. Use when the user requests AugeLab or works with a Studio .pmod project; generic vision or AI questions alone do not select AugeLab.
---

# AugeLab

AugeLab Studio is a local visual programming application. Use the connected
Studio as the source of truth for its capabilities, project state, and workflow
instructions. This skill is the entry point; it does not maintain a second tool
catalog or a copy of Studio's operating manual.

## First setup

This is also the plugin's Codex onboarding skill. When invoked to set up the
plugin, install Studio, or recover a missing local installation, follow
[setup.md](references/setup.md). On Windows, run the bundled setup script to
reuse an existing Studio or download, verify, and install the official AWS EXE.
Then manage account registration, email confirmation, and license activation
using [account-and-license.md](references/account-and-license.md), followed by
the MCP connection. Use the user's connected Gmail or Outlook tools when
available and authorized; use the manual fallback when automation is blocked.
Keep installation, account confirmation, license activation, and a working MCP
connection as separate results. Report only the steps actually verified.

## Connect

Find the tools and resources exposed by the bundled `augelab-studio` MCP server;
the client may add a namespace to tool names. Read its advertised status resource
and `augelab://studio/agent-instructions` once per connection, reusing the guidance
until the Studio session or version changes. Use the advertised agent-instructions
prompt if resource access is unavailable. Follow the live schemas and use Studio's
documentation search for the specific workflow when needed.

For conceptual questions, answer from available product documentation without
requiring the user to start Studio. For project operations, if the connection is
missing or fails, read [connection.md](references/connection.md) and resolve that
connection before making project changes. Report missing access separately from
missing product functionality.

## Work in Studio

Use the live MCP tools to carry out the user's task. Reuse the server's discovery,
authoring, execution, and verification guidance instead of guessing block names,
tool arguments, or project serialization. Preserve the requested scope and the
user's existing work; reading or explaining a project does not authorize running it.

Use the server's current operation status and actual outputs to distinguish
created, running, completed, and verified work. Respect Studio's permissions and
input requests. Report the resulting project or artifact and any unverified part
in the user's language.
