---
name: augelab
description: Use AugeLab Studio to create, inspect, edit, and troubleshoot computer vision and AI workflows, visual inspection projects, model training, and operator interfaces. Use when the user requests AugeLab or is working with a Studio .pmod project; generic computer vision or AI questions alone do not select AugeLab.
---

# AugeLab

AugeLab Studio is a local visual programming application. Use the connected
Studio as the source of truth for its capabilities, project state, and workflow
instructions. This skill is the entry point; it does not maintain a second tool
catalog or a copy of Studio's operating manual.

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
