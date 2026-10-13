---
name: setup
description: Set up or diagnose this Vinnslan plugin, sign in when needed, and verify accessible capabilities without changing customer data.
---

# Set up Vinnslan

This package targets only https://vinnslan.edvald.workers.dev/mcp, with MCP server name `vinnslan-edvald-workers-dev-3bed09c1d95d`.
A setup request authorizes connection checks and starting sign-in, not choosing permissions,
reading private document contents, changing customer data or granting additional access.

## Check before asking the user to act

Discover the installed plugin's tools using the host's available tool discovery. If get_instance
is available, call it and verify the returned origin. Stop on a different instance. Then use
list_workspaces, list_website_projects and list_resources only as available and consented, to
check discovery and resource metadata. Do not read document contents or run business reports for
setup. Report each category as verified, not granted, not configured, or not checked; a discovery
failure is not proof that no resources exist. Preserve successful checks when another one fails.
If already connected, finish with the confirmed instance and a few available next actions.
Do not reconnect, add another MCP server, or request every permission just to complete setup.

## Start sign-in only when needed

Use the host's supported connection/authentication action if one is available for this installed
server. Keep browser consent with the human. Never invent a tool, login URL, token or credential.
If the host has command execution and an installed Codex CLI, you may start
`codex mcp login vinnslan-edvald-workers-dev-3bed09c1d95d --oauth-client-registration dcr` and track that process while the
user completes the browser step. This uses the existing installed server; do not run mcp add.
Do not install a CLI or require a terminal merely to use the desktop plugin.

If the host cannot initiate authentication, give the applicable exact steps:
- Codex desktop: open Settings → MCP servers, find `vinnslan-edvald-workers-dev-3bed09c1d95d`, and click Authenticate.
  If the plugin is absent, open Plugins, install this instance's plugin from its marketplace,
  then run its setup action or ask “Set up my Vinnslan connection” in a new chat.
- Claude: open Customize → Connectors, find Vinnslan for `vinnslan.edvald.workers.dev`, and click
  Connect. If it is missing, finish adding the plugin in Customize → Plugins first. Do not create
  a second custom connector for an installed plugin. Organization policy can require an owner.

The browser opens https://vinnslan.edvald.workers.dev. Ask the user to sign in using the same account they normally use in
Vinnslan. On “Authorize Codex” or the corresponding Claude page, they verify the client and origin,
select only the capabilities they want, and click Connect. Workspace discovery is useful for the
initial check; context, business data, development, outputs, workflows, commerce and delivery are
separate choices. Explain only the choices needed for their intended work. Never click consent or
select permissions on their behalf. Returned data leaves Vinnslan's sandbox.

Wait for the client's sign-in result. If Vinnslan approved access but the browser callback is
blocked, the user can click “finish signing in” on that approval page. After an expired request,
start a fresh login. Do not repeatedly replay a pending login or create parallel login attempts.
A client-details loading failure can use the explicit DCR command above if command execution is
available; otherwise show it as a troubleshooting fallback, clearly identifying the limitation.
Never ask for a password, API key, client secret or infrastructure credentials in chat.

## Verify after sign-in

Refresh tool discovery and repeat only the missing read-only checks. If the host cannot refresh,
ask the user to start a new chat with this plugin enabled and say “Check my Vinnslan connection”.
Do not claim sign-in from a browser page alone. A successful authenticated tool result verifies it.
Missing permissions require the user's separate consent; missing gadgets require owner enablement
in Vinnslan Connections; missing business connectors require native account/resource assignment.
Report which one blocks the requested task, using actual tool results. Existing roles, reviews,
hook enablement and technical-admin promotion requirements still apply after installation.
