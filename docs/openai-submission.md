# OpenAI directory submission draft

Prepared 2026-10-28. This is preparation material, not a submitted application.

## Listing copy

- Name: AugeLab
- Publisher: AugeLab (subject to verified publishing identity)
- Short description: Build computer vision and AI workflows
- Description: Connect Codex to AugeLab Studio to build and inspect computer vision
  and AI workflows, from image processing and visual inspection to model training.
  Windows setup can install Studio; a valid license and enabled MCP are required.
- Example prompt: Use AugeLab to build a visual inspection project from my sample images.
- Execution: Desktop only, on the same computer as Studio.

## Architecture to explain during eligibility review

The plugin packages one skill and a loopback HTTP connection to an independently
installed desktop application. The plugin does not bundle Studio. Its Windows
setup skill downloads the official AWS EXE, checks a reviewed SHA-256 pin, and
installs it if missing. The same skill helps registration, authorized email
confirmation, and license activation through the official account and Studio UI.
It declares `extensions.com.openai.onboardingSkill` and contains no lifecycle hooks.
Mail/browser/desktop tools depend on the user's client; manual instructions are
provided when unavailable. Installing the plugin grants no Studio license.
Studio exposes MCP tools, instructions, and resources. The skill retrieves current
guidance from that application instead of carrying copies of its tool schemas.
The package contains no credentials, remote hosted MCP endpoint, or lifecycle hooks.

## Before submission

- Confirm local-MCP submission eligibility with the OpenAI representative; official
  documentation limits these submissions to approved partners.
- Confirm whether this external Studio/loopback HTTP architecture is accepted.
  The documented local-MCP example uses bundled stdio server code and dependencies;
  our tested local installation is not evidence of public-directory acceptance.
- Verify the publishing organization and submission access in the portal.
- Complete clean-install and live workflow tests in `smoke-test.md`.
- Supply approved branding, installation/support links and any privacy/terms URLs
  required by the portal. Do not invent legal URLs or assert data never leaves the
  machine: tool results are made available to the agent client.
- Upload the plugin-only ZIP, not the marketplace ZIP, after adapting to any
  reviewer requirements. Do not remove MCP merely to bypass local-MCP eligibility.

## Review scenarios

- Read Studio version/capabilities without changing a project.
- Create and execute the sample-image workflow in the smoke test.
- Change a parameter in the intended project while preserving another document.
- Recover clearly when Studio is closed or the MCP endpoint is unavailable.
- Respect a disabled Studio tool and report the limitation.

Actual results and a recording must come from a real test session; none is claimed here.

## Official references

- https://developers.openai.com/plugins/build/plugins
- https://developers.openai.com/plugins/deploy/desktop-only
- https://developers.openai.com/plugins/deploy/submission
