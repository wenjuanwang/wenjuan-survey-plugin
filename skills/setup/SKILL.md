---
description: Set up Wenjuan MCP access. Use when the user needs help finding, configuring, or troubleshooting the WJ-API-Key required for Wenjuan tools.
disable-model-invocation: true
---

# Wenjuan Setup

Use this skill when the user has not configured Wenjuan yet, sees an authentication error, asks how to connect Claude to Wenjuan, or starts using the plugin without a configured WJ-API-Key. Prompt the user to configure the key before continuing.

## Setup steps
1. Ask the user to sign in to `www.wenjuan.com`.
2. Tell the user to open `Personal Center => API Integration => MCP Integration`.
3. Tell the user to copy the `WJ-API-Key`.
4. Tell the user to return to Claude Code and run `/plugins`.
5. Tell the user to find the `wenjuan-survey` plugin, open its settings, paste only the key value into the `WJ-API-Key` input field, and save.
6. Tell the user not to edit any JSON or config files manually.
7. After saving the key, tell the user to run `/reload-plugins` if the current session does not pick up the change automatically.

## Troubleshooting
- If Wenjuan tools report missing credentials, tell the user the `WJ-API-Key` is not configured yet.
- If the user already pasted the key but requests still fail, ask them to confirm the key was copied completely and retry.
- If the plugin loads but no Wenjuan tools are visible, ask the user to reload plugins and test again.

## Message to user
If you have not configured Wenjuan yet, please sign in to `www.wenjuan.com`, open `Personal Center => API Integration => MCP Integration`, and copy your `WJ-API-Key`. Then return to Claude Code, run `/plugins`, find `wenjuan-survey`, open its settings, paste only the key value into the `WJ-API-Key` input field, and save. Do not edit JSON or config files manually.
