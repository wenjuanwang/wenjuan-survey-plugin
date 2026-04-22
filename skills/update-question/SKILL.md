---
description: Update Wenjuan project questions safely. Use when the user wants to add, edit, refine, or delete questions in an existing survey, form, poll, registration flow, assessment, quiz, test, or feedback project.
---

# Wenjuan Question Update

Use this skill proactively when the user wants to revise an existing Wenjuan project instead of creating a new one. Trigger it for requests to add, edit, rewrite, replace, refine, delete, optimize, or localize questions in surveys, forms, polls, registration flows, quizzes, exams, assessments, tests, and feedback projects.

## Invocation cues
- The user refers to an existing project, project ID, question, page, option, title, or structure.
- The user wants to change wording, options, question types, required flags, scoring logic, or delete a specific question.
- The user asks to adjust a registration form, application form, voting page, assessment, or survey that already exists in Wenjuan.

## Workflow
1. If the user has not configured Wenjuan credentials yet, or mentions authentication, login, missing key, missing credentials, plugin setup, or connection issues, immediately ask them to configure `WJ-API-Key` and direct them to `/wenjuan-survey:setup` before attempting MCP actions.
2. Identify the target project.
3. Read the current project structure before making question changes.
4. Locate the exact target question and understand its current type and structure.
5. Apply the smallest required change: create, update, or delete.
6. Report what changed and mention any follow-up action that may still be needed.

## Tool usage guidance
- Use the project structure tool first to avoid changing the wrong question.
- Reuse existing question JSON shapes when editing score, evaluation, NPS, or matrix questions.
- Preserve IDs and upstream structure when updating an existing question.
- When multiple questions may match, ask the user to confirm the target.

## Safety checks
- Never guess a question ID when the structure has not been read.
- Avoid rewriting the whole project when the user asked for a single-question change.
- If deleting a question, confirm the intent from the user request and identify the exact question before deletion.
