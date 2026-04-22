# wenjuan-survey

Claude Code plugin for Wenjuan survey workflows. The plugin connects Claude to the remote Wenjuan MCP service over HTTP and packages the integration in the directory structure required by Claude plugins and Marketplace distribution.

## What this plugin provides

- Remote MCP connection to `https://mcp.wenjuan.com`
- User-friendly authentication with `WJ-API-Key`
- Setup guidance through `/wenjuan-survey:setup`
- Three scenario skills with broader trigger coverage:
  - `/wenjuan-survey:create-survey` for questionnaires, surveys, forms, polls, registration, applications, exams, assessments, quizzes, tests, payment collection, and 360 review setups
  - `/wenjuan-survey:update-question` for refining question structures in existing survey-style projects
  - `/wenjuan-survey:view-data` for reports, metrics, exports, participation status, and analytics
- Access to Wenjuan capabilities such as:
  - project creation, listing, update, and structure lookup
  - question create, update, and delete
  - publish and stop collection
  - report page lookup
  - overview metrics
  - raw data export

## Plugin structure

```text
.
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── skills/
│   ├── create-survey/
│   │   └── SKILL.md
│   ├── setup/
│   │   └── SKILL.md
│   ├── update-question/
│   │   └── SKILL.md
│   └── view-data/
│       └── SKILL.md
└── README.md
```

## Authentication experience

Users do not need to edit config files manually.

First-time setup: on the first use of this plugin, the user needs to configure `WJ-API-Key` once in Claude Code. Claude should keep the saved plugin setting for future sessions, so users usually do not need to configure it again unless the key is changed or cleared.

When the plugin is enabled or first used, Claude should prompt for:

- `WJ-API-Key`: copied from Wenjuan and stored securely by Claude

If the key is missing or the user needs help finding it, run:

```text
/wenjuan-survey:setup
```

Then configure the key in Claude Code like this:

1. Run `/plugins`.
2. Find the `wenjuan-survey` plugin.
3. Open its settings.
4. Paste only the key value into the `WJ-API-Key` input field.
5. Save the setting.
6. Run `/reload-plugins` if the current session does not pick up the change automatically.

Example:

```text
WJ-API-Key input field: wj_live_xxxxxxxxxxxxx
```

Do not paste JSON. Do not edit `.mcp.json`, `plugin.json`, or any config file manually.

The setup skill tells the user to sign in to `www.wenjuan.com`, then open `Personal Center => API Integration => MCP Integration` to copy the key.

The plugin automatically injects the request header:

```text
WJ-API-Key: <your key>
```

## Local development

Load the plugin locally:

```bash
claude --plugin-dir /Users/hp/data/codebase/wenjuan-survey-plugin
```

After Claude starts:

1. Enable the plugin if needed.
2. Paste your `WJ-API-Key` when prompted.
3. Run `/help` to confirm the namespaced skills are available.
4. If authentication is missing or unclear, run `/wenjuan-survey:setup`.
5. Use `/reload-plugins` after local changes.

## Recommended smoke tests

- Run `/wenjuan-survey:view-data` for a known project and verify read-only Wenjuan MCP tools are available.
- Confirm the plugin can access project list, project structure, or overview data successfully.
- Confirm no manual edits to `.mcp.json` or `settings.json` are required for authentication.

## Notes

- `.claude-plugin/plugin.json` contains plugin metadata and user configuration schema.
- `.mcp.json` lives at the plugin root, per Claude plugin conventions.
- The plugin is designed to reference only files inside the plugin directory so it remains compatible with Claude’s plugin cache behavior.
