# First setup on the user's computer

Run this workflow for a setup request or the Codex onboarding conversation.
It is part of the existing `augelab` skill. Claude Code users invoke
`/augelab:augelab Set up Studio`; clients without onboarding support can ask
`$augelab Set up Studio` in a new local chat.

## Windows x64

Explain that setup installs the official AugeLab Studio desktop application
when missing and then helps activate the user's own license. Use local shell
execution on the same Windows computer as Studio. A hosted/cloud shell cannot
install software onto the user's computer. Run the concrete command shown in
the main skill, omitting `-CheckOnly` for an authorized installation. Claude
Code resolves the skill directory in that command when loading `SKILL.md`.
For other clients, use the installed directory containing the loaded skill's
`SKILL.md`, not the user's project directory. Do not search the user profile.

The execution policy option applies to this child process only. It does not
change machine policy. If organizational policy blocks the script, explain the
block and use the official interactive installer rather than weakening policy.

The script probes the bundled local MCP address, discovers Studio in standard
locations and its uninstall registry entry, and downloads only if missing.
It verifies the pinned SHA-256 before running the AWS EXE with
`--silent --install-dir <absolute-directory> --start-menu-shortcut`. The default
destination is `%LOCALAPPDATA%\Programs\AugeLab Studio`. It starts Studio for
activation, without editing project files, licenses, or MCP settings.
An existing installation is reused, not upgraded. An unrecognized nonempty
destination requires repair or an explicitly chosen alternative directory.

Use `-CheckOnly` to inspect without downloading, installing, or launching.
Use `-DownloadOnly` to download and verify without executing. Optional
`-IncludeAI` adds the GPU/AI bundle for a requested GPU workflow after confirming
compatible NVIDIA hardware and drivers. Base setup does not install that bundle.
Do not silently substitute a Python/source installation for the Windows EXE.

Installation can take several minutes because the EXE downloads runtime
dependencies. Run it with a shell tool that can yield a session and poll that
session; keep the user informed instead of launching a second installer.
Windows may show a permission prompt for a missing VC++ runtime.

Interpret the JSON output:

- `checked`: inspection only; `changed` is false.
- `downloaded`: hash verified; `executed` is false.
- `needs-activation-or-mcp`: Studio was found or installed and launched, but
  the configured MCP endpoint is not yet ready. Continue account/license setup.
- `mcp-ready`: a Studio MCP initialization response was received. Read the
  actual Studio status and agent instructions using the client's MCP tools.

On a download or hash failure, execute nothing and report the specific error.
An updated AWS binary requires a reviewed hash update in a new plugin version;
do not replace the pin with whatever was downloaded. Installer errors are in
`%TEMP%\augelab-installer-startup.log`. Do not repeatedly reinstall on license
or MCP errors. Success requires the launcher as well as installer exit code 0.

## Account, license, and MCP

If the running Studio is already activated, keep that license and proceed.
Otherwise follow [account-and-license.md](account-and-license.md). When Studio
has accepted the user's key, open **Chat > Settings > MCP > Start** (using
available UI tools or user guidance), then follow [connection.md](connection.md).
Do not claim full readiness until MCP tools read the Studio status and instructions.

Automatic installation is attached to the Codex **Run setup** onboarding step,
not an unattended plugin-install lifecycle hook. Plugins with lifecycle hooks
are ineligible for the public OpenAI directory. Older clients and Claude Code
need an explicit first setup invocation. See the official
[onboarding documentation](https://developers.openai.com/plugins/build/plugins).

## Other operating systems or missing local tools

The bundled EXE setup supports Windows x64 only. Explain the platform/tool
limitation and direct the user to the official Studio installation flow at
https://account.augelab.com. Do not run a Windows EXE on another platform or
pretend that a remote agent's successful install sets up the user's computer.
