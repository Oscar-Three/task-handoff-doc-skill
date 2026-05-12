---
name: task-handoff-doc
description: Create or update an AI-readable project handoff document after completing work. Use when the user asks for an explanation file, handoff file, continuation document, project status document, AI context file, task wrap-up, implementation summary, progress summary, or documentation that lets Codex or another AI understand a project and continue the work later.
---

# Task Handoff Doc

## Overview

Create a concise but complete handoff document that another AI agent can read to understand the project, what was changed, why it was changed, how it works, what was verified, and what remains.

Prefer updating an existing handoff document over creating a duplicate. Default to `AI_HANDOFF.md` at the project root unless the user names another file or the repository already has a clear convention such as `AGENTS.md`, `CLAUDE.md`, `CONTEXT.md`, `docs/handoff.md`, or `docs/ai-handoff.md`.

## Workflow

1. Identify the project root and the user's task scope.
2. Inspect existing project context files before writing:
   - `README*`
   - `AGENTS.md`
   - `CLAUDE.md`
   - `CONTEXT.md`
   - `docs/**`
   - existing handoff or progress files
3. Summarize the current state from source files, tests, command output, git diff, and conversation context. Do not invent progress that is not supported by artifacts.
4. Create or update the handoff document.
5. Keep the document useful for a future AI: specific paths, concrete commands, current blockers, and next actions matter more than polished prose.

## Document Structure

Use this structure by default. Omit sections only when they truly do not apply.

```markdown
# AI Handoff

## Project Snapshot

- Project:
- Purpose:
- Main stack:
- Current task:
- Last updated:

## What Changed

- ...

## Current Progress

- Done:
- In progress:
- Not started:

## Implementation Notes

- Key approach:
- Important files:
- Data flow / control flow:
- Design decisions:

## How To Continue

- Next recommended steps:
- Commands to run:
- Files to inspect first:

## Verification

- Commands run:
- Results:
- Not run / why:

## Known Issues And Risks

- ...

## Context For Future AI

- User preferences:
- Constraints:
- Things not to change:
- Useful assumptions:
```

## Writing Rules

- Write for another competent AI, not for marketing or end-user docs.
- Prefer bullets with concrete file paths and commands.
- Include absolute or repo-relative paths exactly as they appear in the project.
- Mention important user decisions and preferences from the conversation.
- Record uncertainty explicitly with words like `unclear`, `assumed`, or `not verified`.
- Include verification commands and their outcomes, including failures.
- Include tests or checks that were not run and why.
- Preserve existing handoff content that is still true; update stale content instead of appending contradictions.
- If the project has multiple active threads of work, separate them clearly.
- Keep the file concise enough to scan. For large projects, summarize first and point to deeper docs.

## Update Strategy

When a handoff file already exists:

1. Read it fully.
2. Keep durable project facts.
3. Replace outdated task state with the latest state.
4. Add a new dated entry only if the file is organized chronologically.
5. Avoid duplicate sections with near-identical meanings.

When no handoff file exists:

1. Create `AI_HANDOFF.md` at the project root.
2. Add the default structure.
3. Fill unknown fields with `Unknown` or `Not verified`, not guesses.

## Triggering From Task Completion

If the user asks to make this part of task wrap-up, apply this skill at the end of substantive implementation, debugging, research, or documentation work. The handoff should describe the actual completed task rather than the whole repository in exhaustive detail.
