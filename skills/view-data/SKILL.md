---
description: View Wenjuan project data and reporting outputs. Use when the user wants response metrics, report links, exports, participation data, collection progress, or other read-only analytics for surveys, forms, votes, registrations, assessments, quizzes, and feedback projects.
---

# Wenjuan Data Viewing

Use this skill proactively when the user wants to inspect existing Wenjuan results, participation, response metrics, reports, exports, or operational collection status. Trigger it for requests about analytics, report pages, response counts, completion rates, raw exports, vote results, registration results, feedback summaries, or project performance.

## Invocation cues
- The user asks to view data, check results, inspect performance, export responses, or open a report.
- The user wants read-only information such as metrics, statistics, report URLs, completion rates, participation status, or collection progress.
- The user mentions survey results, voting results, registration data, assessment results, feedback analytics, or response exports.

## Workflow
1. If the user has not configured Wenjuan credentials yet, or mentions authentication, login, missing key, missing credentials, plugin setup, or connection issues, immediately ask them to configure `WJ-API-Key` and direct them to `/wenjuan-survey:setup` before attempting MCP actions.
2. Identify the target project.
3. Determine whether the user wants summary metrics, the report page, or raw data export.
4. Prefer read-only tools first.
5. Present the result clearly and suggest the next useful action only if relevant.

## Tool usage guidance
- Use overview stats for quick operational metrics.
- Use the report tool when the user wants a report page link.
- Use raw-data export when the user wants detailed response data.
- If the user asks why data is missing, check project status and collection state before assuming an error.

## Safety checks
- Do not publish, stop, or modify the project when the request is only about viewing data.
- If exporting data may take time, explain that an export task is being created and wait for the result.
