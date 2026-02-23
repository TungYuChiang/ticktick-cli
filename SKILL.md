---
name: ticktick
description: TickTick task management CLI for tasks, projects, and reminders. Use when the user mentions TickTick, todos, tasks, task lists, or wants to manage their tasks, create reminders, or organize projects.
---

# ticktick

Use `ticktick` for managing tasks, projects, and reminders in TickTick. Requires OAuth setup.

## Setup (once)

- `ticktick setup` — Interactive OAuth wizard (opens browser)
- `ticktick auth status` — Verify authentication

## Projects

- List all projects: `ticktick projects list`
- Get project detail: `ticktick projects get <projectId>`
- Create project: `ticktick projects create "Project Name" --color "#ff6b6b"`

## Tasks

- Create task (inbox): `ticktick tasks create "Buy groceries"`
- Create task (specific project): `ticktick tasks create <projectId> "Deploy v2.0"`
- Create with options: `ticktick tasks create "Meeting prep" --due 2026-03-01T09:00:00 --priority high --tags "work" --reminder 1h`
- List tasks in project: `ticktick tasks list <projectId>`
- Get task detail: `ticktick tasks get <projectId> <taskId>`
- Update task: `ticktick tasks update <taskId> --title "Updated title" --priority medium`
- Complete task: `ticktick tasks complete <projectId> <taskId>`
- Delete task: `ticktick tasks delete <projectId> <taskId>`

## Query & Search

- Tasks due soon (default 7 days): `ticktick tasks due`
- Tasks due in N days: `ticktick tasks due 3`
- High priority tasks: `ticktick tasks priority`
- Search by keyword: `ticktick tasks search "meeting"`
- Search by tag: `ticktick tasks search --tags "work"`
- Search by priority: `ticktick tasks search --priority high`

## Task Options

- `--content "description"` — Task body/description
- `--due "2026-03-01"` — Due date (YYYY-MM-DD or ISO 8601 with time)
- `--priority none|low|medium|high` — Priority level
- `--tags "tag1,tag2"` — Comma-separated tags
- `--reminder 15m|1h|1d` — Reminder offset before due time
- `--title "New title"` — For updates only

## Notes

- Use `--format json` for scripting and machine-readable output.
- IDs are displayed as 8-char short IDs (e.g., `685cfca6`). Use these in commands.
- Run `ticktick projects list` first to find project IDs.
- Omit project ID when creating tasks to use the default inbox.
- Tokens auto-refresh. Run `ticktick auth refresh` if authentication fails.
- **Always confirm before completing or deleting tasks.**