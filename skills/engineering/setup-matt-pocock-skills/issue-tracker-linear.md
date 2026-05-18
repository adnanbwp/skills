# Issue tracker: Linear

Issues and PRDs for this repo live in Linear. Use the MCP Linear tools for all operations — no CLI needed.

## Conventions

- **Create an issue**: `mcp__claude_ai_Linear__save_issue` with `title`, `description` (markdown), `teamId`, and optionally `labelIds`, `stateId`, `priority`.
- **Read an issue**: `mcp__claude_ai_Linear__get_issue` with the issue `id` (a UUID, not the display identifier).
- **List issues**: `mcp__claude_ai_Linear__list_issues` with filters such as `teamId`, `labelIds`, `stateId`. Returns paginated results.
- **Comment on an issue**: `mcp__claude_ai_Linear__save_comment` with `issueId` and `body` (markdown).
- **Apply labels**: `mcp__claude_ai_Linear__save_issue` with `labelIds` — pass the full list of label UUIDs to apply (Linear replaces, not appends).
- **List available labels**: `mcp__claude_ai_Linear__list_issue_labels` with `teamId`.
- **Create a label**: `mcp__claude_ai_Linear__create_issue_label` with `name`, `color`, and `teamId`.
- **List workflow statuses**: `mcp__claude_ai_Linear__list_issue_statuses` with `teamId`. Use to find the UUID for states like "Cancelled".
- **Close / cancel an issue**: `mcp__claude_ai_Linear__save_issue` with `stateId` set to the "Cancelled" state UUID.
- **List teams**: `mcp__claude_ai_Linear__list_teams` — run once to find the `teamId` for this project.
- **List projects**: `mcp__claude_ai_Linear__list_projects` — find the project this issue belongs to.

## Issue ID format

Linear displays issues as `TEAM-NNN` (e.g. `AHA-42`, `ENG-17`). The MCP tools use UUID `id` fields internally. When referencing issues in commit messages or PRs, use the display identifier: `AHA-42` or `Fixes AHA-42`.

To look up a UUID from a display identifier, call `mcp__claude_ai_Linear__list_issues` and filter by the identifier field, or call `mcp__claude_ai_Linear__get_issue` if you already have the UUID.

## Triage labels in Linear

The canonical triage roles map to Linear **Labels** (not workflow states):

| Canonical role | Label name | Notes |
|---|---|---|
| `needs-triage` | `needs-triage` | Maintainer needs to evaluate |
| `needs-info` | `needs-info` | Waiting on reporter |
| `ready-for-agent` | `ready-for-agent` | Fully specified, AFK-ready |
| `ready-for-human` | `ready-for-human` | Requires human implementation |
| `wontfix` | `wontfix` | Use with "Cancelled" workflow state |

Create these labels once via `mcp__claude_ai_Linear__create_issue_label` if they don't exist. The actual label strings may differ — check `docs/agents/triage-labels.md` for the mapping used in this repo.

## When a skill says "publish to the issue tracker"

Call `mcp__claude_ai_Linear__save_issue` to create a new Linear issue.

## When a skill says "fetch the relevant ticket"

Call `mcp__claude_ai_Linear__get_issue` with the issue UUID. If you only have the display identifier (e.g. `AHA-42`), call `mcp__claude_ai_Linear__list_issues` to find the UUID first.
