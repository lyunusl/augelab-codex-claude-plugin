# Desktop smoke test

Run against an installed Studio and sample data you may use for this test.
Do not use a project connected to production machinery.

## Fresh Windows setup

Use a disposable Windows x64 test machine with internet access and an account
whose owner authorizes registration and activation. Do not reuse a production
machine's license or create repeated accounts to obtain licenses.

1. Install the plugin and run the Codex setup entry point (or invoke the shared
   skill explicitly in Claude Code). Confirm it downloads the official S3 EXE,
   checks its SHA-256, installs into the per-user directory, and opens Studio.
2. Confirm hash mismatch/download failure executes no installer. A failed install
   must stop without automatic retry. Base setup must not install the GPU bundle.
3. With an authorized Gmail or Outlook account, follow official registration and
   email confirmation if required. Verify only the relevant mail is read. User-only
   password/terms/MFA steps must hand off clearly, then resume.
4. Use the account's own available license key in Studio. Verify explicit activation
   success; the key must not appear in transcripts, logs, screenshots, or artifacts.
5. Start MCP and verify actual Studio status/instructions through client tools.
6. Run setup again. Confirm it reuses Studio without downloading or reinstalling.
7. Repeat with mail/browser/UI tools unavailable: verify exact manual steps and
   an honest partial-setup result rather than a success claim.

This full fresh-machine registration/activation test has not yet been performed.
The automated Windows tests cover setup decisions and failure paths with stubs;
they do not prove account creation, mail delivery, licensing, or fresh installation.

## Existing Studio workflow

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
