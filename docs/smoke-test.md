# Desktop smoke test

Run against an installed Studio and sample data you may use for this test.
Do not use a project connected to production machinery.

1. Start Studio, open Chat > Settings > MCP, and start the MCP server. Record the
   Studio version and displayed active port. Compare with the plugin endpoint.
2. Install the plugin in a fresh local Codex or Claude Code session.
3. Ask: "Use AugeLab to report the Studio version and available capabilities.
   Do not create, edit, or run a project." Confirm status and instructions load.
4. Ask: "Create a new AugeLab project that loads this sample image, converts it
   to grayscale and shows the output. Run it once and inspect the result."
   Attach a non-confidential sample image. Verify the visible graph, actual output,
   and reported node errors. Confirm unrelated open documents remain unchanged.
5. Ask for a small parameter or ROI change supported by the discovered blocks.
   Confirm only the requested project changes and the agent verifies the result.
6. Stop MCP in Studio and start a new agent session. Confirm the skill explains
   the connection problem without claiming to have edited a project.

Record the client/Studio versions, operating system, each result, and any error.
Package validation or an accepted tool request alone does not pass this test.
