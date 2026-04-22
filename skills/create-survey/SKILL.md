---
description: Create Wenjuan projects for surveys, questionnaires, forms, polls, voting, contests, applications, registration, sign-up, event signup, exams, assessments, quizzes, psychological tests, fun tests, scoring tests, feedback collection, satisfaction studies, payment collection, or 360 review workflows. Use when the user wants to build a new project or draft a complete structure.
---

# Wenjuan Survey Creation

Use this skill proactively when the user wants to create, design, draft, generate, build, or scaffold a new Wenjuan project. Trigger it for requests about surveys, questionnaires, forms, polls, votes, contests, applications, registration flows, sign-up pages, event signup, check-in forms, exams, assessments, quizzes, tests, feedback collection, satisfaction studies, payment collection, or 360 review setups.

## Invocation cues
- The user wants a brand-new project rather than edits to an existing one.
- The user describes goals, audiences, question ideas, or collection scenarios and expects Claude to turn them into a structured project.
- The user references Wenjuan, wenjuan.com, survey links, sign-up forms, voting pages, assessments, or questionnaire design.

## Workflow
1. If the user has not configured Wenjuan credentials yet, or mentions authentication, login, missing key, missing credentials, plugin setup, or connection issues, immediately ask them to configure `WJ-API-Key` and direct them to `/wenjuan-survey:setup` before attempting MCP actions.
2. Confirm the project goal, target audience, and project type (`survey`, `vote`, `form`, or `assess`).
3. Gather the title and the full question list before creating the project.
4. Prefer creating a complete initial structure in one pass when the requirements are clear.
5. If the question design is incomplete, ask follow-up questions before calling the create tools.

## Tool usage guidance
- Use project creation tools to create the base project.
- For complex score, NPS, evaluation, or matrix questions, first inspect an existing structure or carefully match the expected JSON shape.
- Keep question text and option text aligned with the user’s wording.
- After creation, summarize the created project and offer to continue with question refinement or publishing.

## Safety checks
- Do not invent unavailable question types.
- If required fields for a question structure are unclear, ask the user instead of guessing.
- If the user asks to clone or modify an existing survey, read the project structure first rather than recreating blindly.
