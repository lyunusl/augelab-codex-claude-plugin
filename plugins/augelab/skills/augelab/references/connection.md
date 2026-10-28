# Connect to the local Studio

This plugin connects to an existing Studio process using Streamable HTTP at
`http://127.0.0.1:8765/mcp`. It does not install or start Studio. The local
connection requires the agent client and Studio to run on the same computer.

1. Check whether the plugin is installed and enabled in the client. A new chat
   or client restart may be needed after installation or a configuration change.
2. If Studio is installed, open it. In Studio, use **Chat > Settings > MCP** and
   start the MCP server. Enabling startup alone does not start the current server.
3. Compare the active address displayed by Studio with the plugin's `.mcp.json`.
   The default is port 8765, but the saved port is configurable and startup can
   fall back to the next port when the saved port is occupied. Use the displayed
   active address; do not scan ports or assume the saved port is active.
4. If a different port is intentional, update the source plugin configuration to
   that loopback address and refresh/reinstall the plugin. Keep it local. Do not
   change Studio's port or restart its server without accounting for other users
   of the running session. Use a local checkout for a custom port so marketplace
   updates do not overwrite it. Refresh/reinstall through the current client's
   plugin manager, then open a new chat. Do not edit the generated plugin cache.
5. Retry the MCP connection and read the advertised Studio status and instructions.
   A responding HTTP address alone does not establish MCP compatibility.

If Studio is not installed, explain that the desktop application is a prerequisite
and use the user's approved AugeLab installer or official installation source.
Do not install an unrelated public package with a similar name or require access
to the private Studio source repository.

If access still fails, report the concrete connection error and the next action
needed from the user. Do not replace missing Studio tools with direct edits to
`.pmod` files or an unrelated image processing implementation.

Studio also offers `studio mcp`, a stdio bridge to an already-running HTTP server.
It requires the Studio UI environment and reads the persisted port. The default
plugin uses direct HTTP so it does not depend on `studio` being on PATH or on the
bridge discovering a fallback port.
