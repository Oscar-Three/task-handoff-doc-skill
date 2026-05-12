# Task Handoff Doc Skill

A Codex skill for creating or updating an AI-readable project handoff document after completing implementation, debugging, research, or documentation work.

The skill helps future agents understand:

- what changed
- why it changed
- how the project is currently structured
- what was verified
- what remains to do
- where to continue next

## Contents

```text
task-handoff-doc/
  SKILL.md
  agents/
    openai.yaml
```

## Install

Copy the skill directory into your Codex skills folder:

```powershell
Copy-Item -Recurse -Force .\task-handoff-doc "$env:USERPROFILE\.codex\skills\task-handoff-doc"
```

On macOS or Linux:

```bash
cp -R task-handoff-doc ~/.codex/skills/task-handoff-doc
```

## Usage

Ask Codex for a handoff, progress summary, continuation document, implementation summary, or AI context file after project work.

Example:

```text
Create an AI handoff for this project so another agent can continue later.
```

By default, the skill writes or updates `AI_HANDOFF.md` at the project root unless the repo already has a clearer convention.
